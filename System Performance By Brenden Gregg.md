
- [93] Workloads that perform frequent I/O, such as web servers, execute mostly in kernel context. Workloads that are compute-intensive usually run in user mode, uninterrupted by the kernel.
- [93] All system calls mode switch. Some system calls also context switch: those that are blocking, such 
as for disk and network I/O, will context switch so that another thread can run while the first is 
blocked.
- [100] The fork(2) or clone(2) syscall may use a copy-on-write (COW) strategy to improve performance. This adds references to the previous address space rather than copying all of the contents. Once either process modifies the multiple-referenced memory, a separate copy is then made for the modifications. This strategy either defers or eliminates the need to copy memory, reducing memory and CPU usage.
- [102] On Linux, each thread has its own user stack and a kernel exception stack.