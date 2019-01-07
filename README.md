# hetzner-docker-jenkins-artifactory

```
docker run -d --rm -u root -v /var/run/docker.sock:/var/run/docker.sock -v /Users/stefan/tmp/jenkins-data:/var/jenkins_home -e VIRTUAL_HOST=jenkins.localhost -e VIRTUAL_PORT=8080 jenkinsci/blueocean
```

```
docker run -d --rm -p 80:80 -p 443:443 -v /var/run/docker.sock:/tmp/docker.sock:ro  jwilder/nginx-proxy
```

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