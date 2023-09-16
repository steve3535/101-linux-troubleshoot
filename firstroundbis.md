* user logs in and gets automatically disconnected  
  * the user shell is /bin/false (can we relate this to famous service account like git on github ?)
  * Another reason could be a messup with pam.d/sshd --> immediate consequences and possible lockout  
  * lastlog -u user
  * chsh instead of usermod -s  
* error 403 after a curl  
  * both basic permissions and selinux  
  * instead of memoriting semanage fcontext syntax, just restorecon -R -v  
* A good discovery, to have an idea of what a system is doing, just look at journalctl -f  
* `sos report -o xfs`  `sos report -l`  
* the scientific method  
> Idea: emulate old slow systems with qemu
* tlog to record sessions: tlog-rec -o and tlog-play -i
> more researches on tlog, especially the tlog-rec-session to couple with PAM in order to record session logins
> also the integration with journalctl
> we can build a small github project around this , especially that i read auditd can also provide such features, in a more robust way
* /etc/machine-id
* on Centos, one can directly do dnf -y install epel-release, but on rhel we need to call the full fedora url
* dmidecote -t 17 in lieu of dmidecode -t memory
* nproc in lieu of lscpu

