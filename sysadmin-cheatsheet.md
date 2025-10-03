## Environment/System check
- `whoami` : find the name of the current user
- `uname` : find the name of the operating system
  - -a : to diplay all information on the OS
- `uptime` : shows system uptime and load average
- `top` : to check CPU and memory usage
- `free` : provides memory usage stats
- `ps` : lists all user running processes
- `pgrep -f running_process.sh` : locates the PID for the process that is running
- `pkill running_procees.sh` : to force a process to terminate
  ### Network Interface
    -  `ip addr` : display status and configuration of all network inferfaces
    -  `ifconfig` : to verify IP address configuration
      - the inet field shows the IP address
    - `ping` : to test the servers connectivity (-c to specify the number of packets you want to send., also specify the address you are sending to ex.             8.8.8.8) Should send and receive  the number of packets specified with 0% packet loss
    - `ss` : (socket statistics) to check the web server processes.
    - `sudo ufw` : to manage the firewall
