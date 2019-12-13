# RdpThief

RdpThief by itself is a standalone DLL that when injected in the mstsc.exe process, will perform API hooking, extract the clear-text credentials and save them to a file. 

An aggressor script accompanies it, which is responsible for managing the state, monitoring for new processes and injecting the shellcode in mstsc.exe. The DLL has been converted to shellcode using the sRDI project (https://github.com/monoxgas/sRDI). When enabled, RdpThief will get the process list every 5 seconds, search for mstsc.exe, and inject to it.

When the aggressor script is loaded on Cobalt Strike, three new commands will be available:

* rdpthief_enable – Enables the hearbeat check of new mstsc.exe processes and inject into them.
* rdpthief_disable – Disables the hearbeat check of new mstsc.exe but will not unload the already loaded DLL.
* rdpthief_dump – Prints the extracted credentials if any.

## Screenshot

![Example Usage](images/screenshot.png)

Demonstration Video : https://www.youtube.com/watch?v=F77eODhkJ80

More details can be found on : https://www.mdsec.co.uk/2019/11/rdpthief-extracting-clear-text-credentials-from-remote-desktop-clients/

And: https://3gstudent.github.io/3gstudent.github.io/%E6%B8%97%E9%80%8F%E6%8A%80%E5%B7%A7-%E4%BB%8E%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E5%AE%A2%E6%88%B7%E7%AB%AF%E6%8F%90%E5%8F%96%E6%98%8E%E6%96%87%E5%87%AD%E6%8D%AE/
