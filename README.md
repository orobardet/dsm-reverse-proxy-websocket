# dsm-reverse-proxy-websocket
Configuration fix for Synology DSM 6 reverse proxy to handle websocket

**BACKUP YOUR `portal.mustache` BEFORE MODIFYING IT!**

You need to edit the file `/usr/syno/share/nginx/Portal.mustache` to add the follonwings in the `Location` section:

```
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
proxy_read_timeout 86400;
```

A modified `Portal.mustache` is provided in this repo (warning: based on DSM 6.0-7321 Update 2).

