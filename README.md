# Confchange:  
A shell script to look for new and backup configuration files; should hopefully work with any POSIX-compliant shell and requires sudo. Files matching the following patterns are searched for:  
`*.new-*` `*.new` `*.NEW` `*.old-*` `*.old` `*.OLD` `*.bak` `*.pacnew` `*.pacorig` `*.pacsave` `*.pacsave.[0-9]*`  
Files are opened in editor for comparison with original/new version(s) using sudoedit for privilege escalation. Please be aware that this script requires elevated privileges to carry out editing and/or deleting; whilst it works for me, and I have had no issues with it, I highly recommend you read the code fully before using a script from a random person on the internet and giving it access to your files. Default editor used for file comparison and the path(s) searched for configuration files are set in `/etc/confchange.conf` .  
### Usage: 
```
confchange [ -e <editor> ] [ -p <path> ] [ -d | -h | -v ]  
```
### Options: 
 - `-e/--editor <editor>` Temporarily change editor from default (set as [Meld](https://github.com/GNOME/meld) as that works for me) to `<editor>`. Incorrect program name selection will default to environment variable `$EDITOR`  
 - `-p/--path <path>` Temporarily change path(s) from default (`/boot /etc /usr /var`) to `<path>`. `/var/log` is excluded   
 - `-d/--defaults` Permanently change defaults (/etc/confchange.conf file edited with environment variable `$EDITOR`)
 - `-h/--help` Display usage information  
 - `-v/--version` Display version
