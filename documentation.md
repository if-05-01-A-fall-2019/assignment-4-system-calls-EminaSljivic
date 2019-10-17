## Emina Sljivic

## System Calls Understanding

### fork
- Main functionality: Creates a copy of itself and it is usually a system call, implemented in the kernel.
- Function argument: void

### stat
- Main functionality: These functions return information about a file, in the buffer pointed to by statbuf.
- Function argument:
  * const char * restrict path ->  path to the file
  * struct stat * restrict buf -> information about the file

### kill
- Main functionality: Sends the signal specified by sig to pid, a process or a group of processes
- Function argument:
  * int sig -> type of signal
  * pid_t pid -> who will receive the signal

### mmap
- Main functionality: Causes the pages starting at addr and continuing for at most len bytes to be mapped from the object described by fd, starting at byte offset offset
- Function argument:
  * void * addr -> starting address of the mapping
  * size_t len -> length to be mapped
  * int prot -> specifies the protections
  * int flags -> specifies the type of the mapped object, mapping options
  * int fd -> descriptor
  * off_t offset -> starting"point"

### chmod
- Main functionality: Sets the file permission bits of the file specified by the pathname path to mode
- Function argument:
  * const char * path -> path to the file
  * mode_t mode -> which mode should be added/removed

### waitpid
- Main functionality: Provides a more general interface for programs that need to wait for certain child processes
- Function argument:
  * pid_t pid -> Specifies the set of child processes for which to wait
  * int * stat_loc -> Location where waitpid() can store a status value
  * int options -> Contains the bitwise OR of any of the following options

## System Calls Fail

### fork
[ENOMEM]  There is insufficient swap space for the new process.

### exec
[E2BIG]   The argument list exceeds the system limit.

### unlink
[EACCES]  Search permission is denied for a component of the path prefix.

### read
[EISDIR]  An attempt is made to read a directory.

### mount
Enteres a path that is a file and not a directory.
[ENOTDIR] A component of the path is not a directory.

### chmod
Enters chmod -j *path*
[EINVAL]  Mode is not a valid file mode.

### kill
Enters kill -2 2:
[ESRCH]   No process or process group can be found corresponding to that specified by pid.

## Traps
A trap is an exception in a user process. It's caused by division by zero or invalid memory access. It's also the usual way to invoke a kernel routine (a system call) because those run with a higher priority than user code.
