## master

### FEATURES

- Allow negative scores to reduce the weight of a mirror

### ENHANCEMENTS

- Support password protected rsync URLs
- Allow https URLs when adding a mirror
- Display location and score in the list output
- Display mirror status in the stats output
- Improvements in the selection algorithm
- Load OSM tiles using https
- Keep the list of mirrors sorted by score in the mirrorlist
- Set cache-control to disable caching
- Log unauthorized redirection from a mirror
- New option to set the maximum number of backup mirrors to return in link headers
- Improved error reporting

### BUGFIXES

- Fix a possible crash while Redis is loading the dataset
- Fix a race condition when updating mirrors state

## v0.3

### FEATURES

- Support for HA via Redis sentinel
- Clustering support (multiple Mirrorbits instances) [#6](https://github.com/etix/mirrorbits/issues/6)
- Support for Redis DB index
- SHA256 and MD5 hashing support (in addition to SHA1) [#4](https://github.com/etix/mirrorbits/issues/4)
- Configurable interval for sync and check
- CLI: get stats by matching regular expressions
- HTTP: get the checksum of any file by appending ?sha1, ?sha256 or ?md5 to any served file
- Added a Makefile to support different builds

### ENHANCEMENTS

- Improved systemd service file
- New mirrorlist template [#15](https://github.com/etix/mirrorbits/issues/15)
- Geoip databases are now updated (in memory) during a reload
- Reuse all Redis connections when possible
- Detect and wait until Redis has loaded the dataset into memory
- Improved handling of X-Forwarded-For IP addresses [#23](https://github.com/etix/mirrorbits/issues/23)
- Logging: enable the colored output only if supported by the terminal
- More configuration items can be applied with a simple reload
- Improved scan behavior for newly added mirror (healthcheck only after successful scan)
- Limit redis verbosity in CLI operations
- CLI: reduce the number of database requests required to fetch stats by time interval
- CLI: differentiate down vs disabled mirrors
- FTP: add a connection timeout
- Don't try to open download logs when using the cli
- process: ensure the file descriptor is valid before finalizing a seamless binary upgrade
- Mirrors with a weight less than 1% will show <1% instead
- Graceful exit is now faster
- General improvements on error reporting


### BUGFIXES

- Fix Redis password authentication
- Fix a crash in the weight randomization algorithm
- Fix a bug causing a rescan of all mirrors during startup
- Fix a bug causing some disabled mirrors to be health-checked
- Don't reload logs if outputting on stderr (journald is now happy)
- Fix a crash if no mirrors and no fallbacks are available
- CLI: fix matching of a mirror ID containing the same substring [#19](https://github.com/etix/mirrorbits/issues/19)
- scan: fix an issue causing a constant rehashing of all files [#18](https://github.com/etix/mirrorbits/issues/18)
- The geoip-lite-update script did not update the databases correctly

## v0.2

### FEATURES

- Request a scan using a specific protocol (rsync or ftp)
- Print basic download stats (mirrorbits stats <identifier>)

### ENHANCEMENTS

- Improve parse errors in the configuration
- Don't log if logdir in unset

### BUGFIXES

- Fix a minor corner case when the client and server are in the exact same location

## v0.1.2

### BUGFIXES

- Fix a possible division by zero during mirror selection

## v0.1.1

### FEATURES

- CLI: a parse error in the mirror configuration can now be retried
- CLI: add supports for taking notes / comments on a mirror
- CLI: add a command-line flag to auto-enable a mirror after a successful scan
- CLI: add a flag to scan all mirrors at once

### ENHANCEMENTS

- Improved mirror selection algorithm

### BUGFIXES

- Fix few corner cases in weight distribution

## v0.1.0

Initial release