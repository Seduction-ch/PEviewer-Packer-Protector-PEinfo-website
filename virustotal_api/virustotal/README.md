# VirusTotal

A simple [Python](http://python.org)-based command-line script to interact with [blacktop](https://github.com/blacktop)'s [virustotal-api](https://pypi.python.org/pypi/virustotal-api).

## License
GPLv3

## Requirements
* [virustotal-api](https://pypi.python.org/pypi/virustotal-api)

## Installation
```
python setup.py install
```

## Configuration
A configuration file is used to store your VirusTotal API key. It uses the following format:

```
[virustotal]
apikey: <your API key here>
```

The configuration file can be specified using the `--config` command-line option. By default `$HOME/.vtapi` is used.

## Usage
### File Scan
Submit a file to be scanned.
```
python vt_driver.py file-scan [-h] file

Positional arguments:
 file        File path

Optional arguments:
 -h, --help  Show this help message and exit
```

### Rescan
Rescan previously submitted file(s) without having to resubmit, thus saving bandwidth.
```
python vt_driver.py rescan [-h] hash [hash ...]

Positional arguments:
 hash        List of MD5/SHA1/SH256 hashes (up to 25)

Optional arguments:
 -h, --help  Show this help message and exit
```

### File Report
Retrieve file scan results.
```
python vt_driver.py file-report [-h] hash [hash ...]

Positional arguments:
 hash        List of MD5/SHA1/SHA256 hashes (up to 25)

Optional arguments:
 -h, --help  Show this help message and exit
```

### Behaviour
Get a report on the behaviour of a file in a sandbox environment.
```
python vt_driver.py behaviour [-h] hash

Positional arguments:
 hash        An MD5/SHA1/SHA256 hash

Optional arguments:
 -h, --help  Show this help message and exit
```

### Pcap
Get a dump of the network traffic generated by the file.
```
python vt_driver.py pcap [-h] [-o OUTPUT_DIR] hash

Positional arguments:
 hash        An MD5/SHA1/SHA256 hash
 
Optional arguments:
 -h, --help  Show this help message and exit
 -o OUTPUT_DIR, --output-dir OUTPUT_DIR
             Output directory to write downloaded pcap file to
             (defaults to the current working directory)
```

### Search
Search for files.
```
python vt_driver.py search [-h] [-o OFFSET] query

Positional arguments:
 query       A comma-separated search query. See
             https://www.virustotal.com/intelligence/help/file-search/#search-modifiers
             for valid search modifiers

Optional arguments:
 -h, --help  Show this help message and exit
 -o, --offset
             Offset returned by the previous search query. Allows for
             pagenation of results
```

### Download
Download a file.
```
python vt_driver.py download [-h] [-o OUTPUT_DIR] hash

Positional arguments:
 hash        An MD5/SHA1/SHA256 hash
 
Optional arguments:
 -h, --help  Show this help message and exit
 -o OUTPUT_DIR, --output-dir OUTPUT_DIR
             Output directory to write downloaded file to
             (defaults to the current working directory)
```

### URL Scan
Submit URL(s) to be scanned.
```
python vt_driver.py url-scan [-h] url [url ...]

Positional arguments:
 url         URL(s) (up to 25)

Optional arguments:
 -h, --help  Show this help message and exit
```

### URL Report
Get URL scan results.
```
python vt_driver.py url-report [-h] url [url ...]

Positional arguments:
 url         URL(s) (up to 25)

Optional arguments:
 -h, --help  Show this help message and exit
```

### IP Report
Get information about an IP address.
```
python vt_driver.py ip-report [-h] ip

Positional arguments:
 ip          An IPv4 address
 
Optional arguments:
 -h, --help  Show this help message and exit
```

### Domain Report
Get information about a domain.
```
python vt_driver.py domain-report [-h] domain

Positional arguments:
 domain      A domain name
 
Optional arguments:
 -h, --help  Show this help message and exit
```