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
wget https://raw.githubusercontent.com/azdolinski/awx-logo-change/main/img/ansiblelogo.png -O /root/.awx/awxcompose/logo/ansiblelogo.png
wget https://raw.githubusercontent.com/azdolinski/awx-logo-change/main/img/dot.png -O /root/.awx/awxcompose/logo/dot.png
```

Edit: 
```bash
/root/.awx/awxcompose/docker-compose.yml
```
Add volumes to awx_web:
```bash
      - "/root/.awx/awxcompose/logo/ansiblelogo.png:/var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-header.svg:ro"
      - "/root/.awx/awxcompose/logo/dot.png:/var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-login.svg:ro"
```
