# awx-logo-change
AWX Logo Change Procedure

# How to find image files:
```bash
docker run -it ansible/awx:16.0.0 bash
docker> find /var -name logo-login.svg
```

File Location inside container:<br>
-> Main Login Page logo: /var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-login.svg<br>
-> After login / top menu logo:  /var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-header.svg<br>

# How to prepere logos for relacment:

```bash
mkdir /root/.awx/awxcompose/logo
wget https://png-pixel.com/1x1-ffff007f.png -O /root/.awx/awxcompose/logo/dot.png
```

Edit: 
```bash
/root/.awx/awxcompose/docker-compose.yml
```
Add volumes to awx_web:
```bash
      - "/root/ansiblelogo.png:/var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-header.svg:ro"
      - "/root/1x1-ffff007f.png:/var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-login.svg:ro"
```
