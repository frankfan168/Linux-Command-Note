# Chap 14-15 Package Management and Storage

### Several Common Commandline for Debian

* **apt-get install** : Install package from repositary

* **apt-get update** : Update package from repositary

* **apt-get upgrade** : Upgrade package from repositary

* **apt-get remove** : Uninstall existing package

* **dpkg --install package_file** : Install from package directly from local

* **md5sum** : Calculate an MD5 checksum



### Examples of Commandlines

* **dpkg --list package name** : Display a list of all the packages installed on the system

```
jiazhen@ubuntu:~$ dpkg --list
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  a11y-profile-m 0.1.10-0ubun amd64        Accessibility Profile Manager - U
ii  account-plugin 0.12+16.04.2 all          GNOME Control Center account plug
......
```


* **dpkg --status package name** : Display whether a specified package is installed

```
jiazhen@ubuntu:~$ dpkg --status vim
Package: vim
Status: install ok installed
Priority: optional
Section: editors
Installed-Size: 2400
```

* **dpkg --search package name** : To determine what package is responsible for the installation of a particular file

```
jiazhen@ubuntu:~$ dpkg --search vim | head
vim-runtime: /usr/share/vim/vim74/keymap/bulgarian-bds.vim
vim-runtime: /usr/share/vim/vim74/syntax/hitest.vim
vim-runtime: /usr/share/vim/vim74/lang/menu_fi_fi.utf-8.vim
vim-runtime: /usr/share/vim/vim74/keymap/greek_utf-8.vim
vim-runtime: /usr/share/vim/vim74/plugin/zipPlugin.vim
vim-runtime: /usr/share/vim/vim74/doc/ft_sql.txt
vim-runtime: /usr/share/vim/vim74/macros/urm/urm.vim
vim-runtime: /usr/share/vim/vim74/lang/menu_af_af.utf-8.vim
vim-runtime: /usr/share/vim/vim74/doc/print.txt
vim-runtime: /usr/share/vim/vim74/syntax/jovial.vim
```
