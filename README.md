# pimpmykali.sh

[![pmk132tkab.png](https://i.postimg.cc/Qd9VCRrd/pmk132tkab.png)](https://postimg.cc/18SyY7tk)

# Fixes for new imported Kali Linux virtual machines
  - Author assumes zero liability for any data loss or misuse of pimpmykali
  - Can be used on a bare metal machines, but thats on you
  - Menu breakdown added below revision history

# Github index updated added +x permission:
  - Script is now be executable upon clone (perms: 755 rwxr-xr-x added to github)
  - There is no need to chmod +x pimpmykali.sh upon git clone

# Installation script:
  - rm -rf pimpmykali/
  - git clone https://github.com/Dewalt-arch/pimpmykali
  - cd pimpmykali
  - sudo ./pimpmykali.sh
  - For a new kali vm, run menu option N

# Special Thanks to Pimpmykali-Mirrors Testers!!
  - Crazy_Man - https://github.com/The-Crazy-Man
  - Andro

# Code Contributors
  - blindpentester https://github.com/blindpentester
  - pswalia2u https://github.com/pswalia2u
  - Alek https://github.com/onomastus
  - Gr1mmie https://github.com/Gr1mmie
  - Aksheet https://github.com/Aksheet10
  - 0xC0FFEE VirtualBox Home Lab Build (updated link!)
    https://benheater.com/building-a-security-lab-in-virtualbox/
  - TheMadHuman https://github.com/TMH-Sec
  - Aashiksamuel https://github.com/aashiksamuel  (sublime install fix)
  - m4ul3r

# Writeups / Honorable Mentions
  - ip3c4c_n00b https://ip3c4c.com/2202_homelab_vmware/

# Revision 1.5.7 - Fix SSH Function 
  - Menu option letter O Only (is not included in N, 0 or 1 at this time)
  - added function to set ssh to wide compatibility mode
  - file created : /etc/ssh/ssh_config.d/kali-wide-compat.conf
  - resolves issues with ssh -i id_rsa and various other legacy ciphers
  - older revision history moved to changelog.txt 

# Menu Breakdown of Pimpmykali

- Menu option N  (New Users/New VM's Should start here!)
  - executes menu option 0 fix all ( options 1 thru 8 )
  - executes menu opiion 9 (pimpmyupgrade)


- Menu option = Pimpmykali-Mirrors (rev 1.3.2)
  - obtain kali mirror list and process
    - round-trip-time ping test to all mirrors, select top 10 with shortest rtt
    - small download >1MB from the top 10 mirrors, select top 5 fastest transfers
    - large download 10MB test the final 5 mirrors, select fastest transfer
    - generate new /etc/apt/sources.list with the new selected mirror
    - prompt Y or N to write new changes to /etc/apt/sources.list
      - Y writes changes /etc/apt/sources.list
      - create backup of original sources.list in /etc/apt/sources.list_date_time
      - write new deb and deb-src lines with new mirror to /etc/apt/sources.list
      - N exits and makes no change to /etc/apt/sources.list


- Menu Option ! - Nuke Impacket (yes its literally the ! character)
  - removes any prior installation of impacket (gracefully and forcefully)
  - installs impacket-0.9.19


- Menu Option 1 - Fix missing
  - fix_sources
    - uncomment #deb-src from /etc/apt/sources.list
  - python-pip installation via curl
  - python3-pip installed
  - seclists installed
  - gedit installed (feature request)
  - flameshot installed (feature request)
  - locate installed (feature request)
  - fix_rockyou function
    - gunzip /usr/share/wordlists/rockyou.gz to /usr/share/wordlists/rockyou.txt
  - fix_golang function
    - installs golang
    - adds golang GOPATH to .bashrc and .zshrc
  - installs htop
  - installs python requests
  - installs python xlrd==1.2.0
  - disables xfce power management
  - blacklists pcspkr kernel module /etc/modprobe.d/nobeep.conf
  - intalls python pyftpdlib


- Menu Option 2 - Fix smb.conf
  - adds below [global] in /etc/samba/smb.conf
    - client min protocol = CORE  below [global]
    - client max protocol = SMB3  below [global]


- Menu Option 3 - Fix Golang
  - Installs golang
    - checks for GOPATH in .bashrc and .zshrc
    - if GOPATH is found, adds nothing
    - if not found, adds GOPATH statements to both .zshrc and .bashrc


- Menu Option 4 - Fix Grub
  - adds mitigations=off to GRUB_CMDLINE_LINUX_DEFAULT


- Menu Option 5
  - installs Impacket-0.9.19


- Menu Option 6 - Enable root login
  - installs kali-root-login
    - prompts for root password
    - copy /home/kali/* to /root prompt (1.1.2)
    - prompt are you sure? to copy /home/kali to /root prompt (1.1.3)


- Menu Option 7
  - installs Atom text editor


- Menu Option 8 - Fix Nmap
  - wget nmap script fixes
    - clamav-exec.nse
    - http-shellshock.nse (Thank you Alek!)


- Menu Option 9 - Pimpmyupgrade
  - additional notes will be added
  - fix : Hypervisor detection (vmware, virtualbox, qemu/libvirt)
    - add additional details here
  - fix : virtualbox shared folder fix applied     


- Menu Option 0 - Fix all (1-8)
  - Executes ONLY Menu options 1 thru 8


- Menu Option B  ( Changed 02.21.2022 )  
  New Function:
  - Downgrade Bloodhound from v4.1.0 (current) to v4.0.3

  Previous Function: (will be moved elsewhere in Pimpmykali)
  - BlindPentesters The_Essentials tools and utilities collection
  - Install all of BlindPentesters favorite tools and utilities to /opt (aprox 8GB)
  - Click the link below for a full list of the_essentials.sh script and its inner workings
  - https://github.com/blindpentester/the-essentials


- Menu Option C
  - Install Google-Chrome


- Menu Option D - Downgrade metasploit-framework from 6 to 5
  - downgrades metasploit-framework (msfconsole) from msf6 to msf5


- Menu Option F
  - Fixes XFCE Broken Icons "TerminalEmulator" Not Found
  - Fixes XFCE Open Catfish instead of Thunar when double clicking Home or FileSystem Icon
  - this fix is a temporary fix and will be removed once xfce has been corrected


- Menu Option G
  - Apply gedit unable to open display as root fix


- Menu Option K
  - Reconfigure Keyboard, Language and Layout + Variant


- Menu Option M
  - Kali linux setup for Mayors Movement Pivoting and Persistance Course
    - installs covenant  

- Menu Option O 
  - Fix SSH Function
    - checks for /etc/ssh/ssh_config.d/kali-wide-compat.conf
    - if file exists, no changes are made and exists 
    - if file does not exist, it is created and legacy ciphers added
    - restarts ssh service

- Menu Option P  (was disable power management - updated 01.05.22)
  - PPA Course Prerequisites installation
    - installs whois and bind9-dnsutils
    - git clone spoofpoint to /opt/spoofpoint
    - creates symlink to spoofpoint in /usr/bin/spoofpoint

  - Disable Power Management function moved to Menu options 0, N or 1
    - Based upon detection disable power management for that environment
      - Detect desktop environment
        - XFCE
        - Gnome


- Menu Option S - Fix Spike
    - Fixes undefined symbol error thrown when using generic_send_tcp
    - this fix is temporary and will be removed once a corrected version is available


- Menu Option T
  - Reconfigure Timezone


- Menu Option V
  - Install MS VSCode


- Menu Option W
  - Install GoWitness precompiled binary


# TODO   
  - clean up todo list :)
