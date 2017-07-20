# dsm-reverse-proxy-websocket
Configuration fix for Synology DSM 6 reverse proxy to handle websocket

**BACKUP YOUR `portal.mustache` BEFORE MODIFYING IT!**

You need to edit the file `/usr/syno/share/nginx/Portal.mustache` to add the follonwings in the `Location` section:

```
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
proxy_read_timeout 86400;
```

Then restart the httpd with: 
```
sudo synoservicecfg --restart nginx
```

*This will restart ALL http service running, not only reverse proxy, as a single instance of NGinX runs everything.*


A modified `Portal.mustache` is provided in this repo (warning: based on DSM 6.0-7321 Update 2).

# Known DSM upgrade impacts on the `Portal.mustache` file

> In **bold** versions overwriting the `Portal.mustache`

- 6.1.3-15152-1 : leaves the `Portal.mustache` file unchange
- **6.1.3-15152** : overwrites the `Portal.mustache`
- **6.1.2-15132** : overwrites the `Portal.mustache`
- 6.1.1-15101-4 : leaves the `Portal.mustache` file unchange
- **6.1.1-15101** : overwrites the `Portal.mustache`
