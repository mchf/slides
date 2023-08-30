1. What to collect
==================
* as far as yast is used as the backend an internal call to save_y2logs (or reimplementing part of it to ommit some unneeded logs) should be fine, so it contains
  - yast logs
  - zypper logs
  - hw info
  - ...
* agama / cockpit specific things like
  - journalctl -u agama
  - journalctl -u cockpit
  - a web browser logs most probably not useful (browser has to be started with debugging option explicitly - at least chromuim)

2. Where to place it
====================
* standalone script like save_y2logs
* CLI command, can be just a way how to invoke another placements (like standalone script)
* agamactl subcommand, can be just a way how to invoke another placements (like standalone script)

3. What to use for implementation
=================================
* bash - should be always available
* ruby - should be available as long as yast is used as backend
* python - seems more popular in suse, cockpit uses it. But does it make sense to pull another language into agama project?
* rust - already used in agama, but sounds a bit overkill

4. Misc
=======
* User has to be able to use the tool during installation (!) even on installed system (?)
* where to place the implementation
  - agama project - then the script won't be available in installed system
  - yast project - doesn't make much sense, has almost nothing to do with yast
  - standalone package - any benefit? could cause troubles when requiring new package in installation images, installation patterns, ...
* multiple log files expected -> output should be a tarball (as in case of save_y2logs)
  - see file permissions in https://trello.com/c/uqSvbtGh/4599-improvements-in-savey2logs
* can support "run command" option, stdout/err of the command should be stored in a file, can be used multiple times e.g.:
  - save_agama_logs -c "uname -a" -c "ls /var/log"
  - as usual can be danger when used in a wrong way
