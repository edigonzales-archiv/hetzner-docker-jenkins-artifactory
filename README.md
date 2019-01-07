# hetzner-docker-jenkins-artifactory

1. Server mit user-data.txt aufsetzen
2. Floating-IP setzen (in GUI und auf Server)
3. `/etc/resolv.conf` ggf. anpassen -> `8.8.8.8`
4. `systemctl disable nginx`
5. `service nginx stop`
6. `/etc/resolv.conf` anpassen (8.8.8.8)
7. certbot certonly: (2) wählen
8. `cp /etc/letsencrypt/live/jenkins.sogeo.services/fullchain.pem  /home/appuser/certs/jenkins.sogeo.services.crt`
9. `cp /etc/letsencrypt/live/jenkins.sogeo.services/privkey.pem  /home/appuser/certs/jenkins.sogeo.services.key`
10. `chown appuser:appuser jenkins.sogeo.services.*`
11. `sudo su appuser`
12. `cd /home/appuser/`
13. `git clone https://github.com/edigonzales/hetzner-docker-jenkins-artifactory.git `
14. `docker-compose build`
15. `docker-compose up -d`

List with all plugins:


```
def plugins = jenkins.model.Jenkins.instance.getPluginManager().getPlugins()
plugins.each {println "${it.getShortName()}: ${it.getVersion()}"}
```