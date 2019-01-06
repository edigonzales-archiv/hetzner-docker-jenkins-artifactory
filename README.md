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
4. certbot certonly: (2) wählen
/etc/resolv.conf anpassen.
nginx -s stop
