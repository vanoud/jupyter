1.

[tux]$ cd /etc 
[tux]$ pwd 
/etc 

2.

[tux]$ ls r* 
rc        rc.sysinit      resolv.conf              rmt        rndc.key 
rc.local  redhat-release  resolv.conf.predhclient  rndc.conf  rpc 
 
racoon: 
certs  psk.txt  racoon.conf 
 
rc0.d: 
K01yum                 K24irda           K72autofs     K89rdisc 
K02cups-config-daemon  K25sshd           K73ypbind     K90bluetooth 
K02haldaemon           K30sendmail       K74apmd       K90network 
... 
Le motif r* correspond bien à tous les noms de fichiers commençant par la lettre "r", dont certains sont des noms de répertoires. La commande ls affiche donc le contenu de ces répertoires.

3.

[tux]$ ls -d r* 
racoon  rc2.d  rc6.d       redhat-lsb               rhgb       rpc 
rc      rc3.d  rc.d        redhat-release           rmt        rpm 
rc0.d   rc4.d  rc.local    resolv.conf              rndc.conf 
rc1.d   rc5.d  rc.sysinit  resolv.conf.predhclient  rndc.key 

4.

[tux]$ ls -d *rc*  
bashrc     inputrc  Muttrc.local  rc0.d  rc3.d  rc6.d     rc.sysinit  wgetrc 
csh.cshrc  mail.rc  pinforc       rc1.d  rc4.d  rc.d      slrn.rc 
imrc       Muttrc   rc            rc2.d  rc5.d  rc.local  vimrc 

5.

[tux]$ ls -d ??? 
gtk  hal  lvm  ntp  opt  pki  ppp  rmt  rpc  rpm  ssh  X11  xdg  xml  yum 

6.

[tux]$ ls -d rc?.d 
rc0.d  rc1.d  rc2.d  rc3.d  rc4.d  rc5.d  rc6.d 

7.

[tux]$ ls -d rc[234].d 
rc2.d  rc3.d  rc4.d 

8.

[tux]$ ls -d [!abc]* 
dbus-1                ldap.conf           rc0.d 
default               ld.so.cache         rc1.d 
dev.d                 ld.so.conf          rc2.d 
DIR_COLORS            ld.so.conf.d        rc3.d 
DIR_COLORS.xterm      lftp.conf           rc4.d 
dumpdates             libuser.conf        rc5.d 
enscript.cfg          localtime           rc6.d 
environment           log.d               rc.d 
esd.conf              login.defs          rc.loca 
... 

9.

[tux]$ ls -d [[:upper:]]*      
DIR_COLORS  DIR_COLORS.xterm  Muttrc  Muttrc.local  X11 

10.

[tux]$ ls -d *{conf,config} 
asound.conf       jwhois.conf     named.conf         scsi_id.config 
auditd.conf       krb5.conf       nscd.conf          sestatus.conf 
cdrecord.conf     krb.conf        nsswitch.conf      sysconfig 
cpuspeed.conf     ldap.conf       ntp.conf           sysctl.conf 
esd.conf          ld.so.conf      pam_smb.conf       syslog.conf 
gconf             lftp.conf       pbm2ppa.conf       updatedb.conf 
gpm-root.conf     libuser.conf    pnm2ppa.conf       warnquota.conf 
grub.conf         logrotate.conf  prelink.conf       wvdial.conf 
gssapi_mech.conf  ltrace.conf     pwdb.conf          yp.conf 
host.conf         man.config      resolv.conf        yum.conf 
idmapd.conf       modprobe.conf   rndc.conf 
initlog.conf      mtools.conf     scrollkeeper.conf 

11.

[tux]$ ls -d [[:lower:]]*a?{.conf,.config}   
ldap.conf  man.config  wvdial.conf 