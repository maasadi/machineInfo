# machineInfo
Go script to get and print the machine information (operating system, network interfaces, ...)

### How to use:
```
$ go run machineInfo.go -h
Usage of ./machineInfo:
  -cpu
    	if 'cpu=true' => print cpu info
  -hostname
    	if 'hostname=true' => print hostname
  -network
    	if 'network=true' => print network interfaces info
  -os
    	if 'os=true' => print operating system info
```

### Constants: 
```
SYSINFO_LOADS_SCALE   =  1<<16; // 2^16 
SYSINFO_MEM_UNIT      =  1024 * 1024; // MB
```
### Types:
 * `sys_t` is go version of **sysinfo** struct, for Linux versions Since 2.3.23 (i386) and  2.3.48 (all architectures).
 
### Functions:
  * `func GetHostName() string` is like *gethosname()* function in **unistd.h**, returns the hostname.
  * `func GetOSName() (string, string)` returns *GOOS* and *GOARCH* variables as strings.
  * `func GetSysInfo() sys_t` is like *sysinfo()* in **sys/sysinfo.h**, returns system information as sys_t type.
  * `func GetCPUInfo() []cpu.InfoStat`is like *sysinfo* in **sys/sysinfo.h**, returns the cpu information in */proc/cpuinfo*.
  * `func GetNetworkInterface() []net.Interface` is like *ifconfig*, returns the network interfaces of */sys/class/net* 
  
### References:
  * http://man7.org/linux/man-pages/man2/sysinfo.2.html
  * https://github.com/shirou/gopsutil
  * https://golang.org/pkg/net/
