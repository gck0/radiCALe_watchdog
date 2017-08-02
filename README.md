# radiCALe_watchdog
radiCALe 1.1.x watchdog/respawner script 

### what?
an init.d script to check if radiCALe daemon is accepting connections: if not, it kills and respawns the process  
tested on 1.1.x, it uses openSSL and works only if 'ssl=true' in radicale/config

### why?
radiCALe is a CalDAV and CardDAV server  
as many of you have experienced, radiCALe daemon may freeze randomly after some time: when (sh)it happens, only way is to kill -9 it and restart  
to avoid this issue it needs to run behind a dedicated web server  

as I am running it on a cheap nas (dns-320L with alt-f firmware) which simply hasn't the cpu power to run an httpd, I modified an user posted init.d script and added a respawn function  

### install
edit as you wish  
put the script in /etc/init.d/  
chmod +x  
set up a cronjob (recommended every hour)  


my crontab setup:
```
0 * * * *   /etc/init.d/S80radicale respawn
```
to suppress info/error messages:  
```
0 * * * *   /etc/init.d/S80radicale respawn >/dev/null 2>/dev/null
```


### links
http://radicale.org  
http://github.com/Kozea/Radicale/issues/266  
thanks to the author of the original post:  
http://groups.google.com/forum/#!topic/alt-f/vGUpfxmpfuQ  
