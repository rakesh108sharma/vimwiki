[[LINUX]]
# system hardening

* check for zombies and show parents
    * `ps aux | grep 'Z'`
    * `pstree -s PID`
    * kill if possible

* *umask* should be more restrictive  
  change (maybe): `umask 027` in
  * /etc/profile
  * /etc/login.defs
  * ~/.bashrc

* ? *deleted files* still in use
  * `sudo find /proc/*/fd -ls | grep '(deleted)'`
  * OR `lsof | grep '(deleted)'`

* check for errors in *passwd* file
  `pwck`

* consider disabling unused kernel modules in /etc/modprobe.d/SOME_FILE.conf. eg
  ```
  sudo nano /etc/modprobe.d/blacklist.conf
  options ipv6 disable=1
  install dccp /bin/true
  install sctp /bin/true
  install tipc /bin/true
  install rds /bin/true
  ```
* tweak kernel with *sysctl*

## browsers
### firefox
Visit firefox [profilemaker](https://ffprofile.com/)  
check your browser on [panopticlick](https://panopticlick.eff.org/)  

