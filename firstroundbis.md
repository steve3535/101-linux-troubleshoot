* user logs in and gets automatically disconnected  
  * the user shell is /bin/false (can we relate this to famous service account like git on github ?)  
  * lastlog -u user
  * chsh instead of usermod -s  
* error 403 after a curl  
  * both basic permissions and selinux
  * instead of memoriting semanage fcontext syntax, just restorecon -R -v
