# awx-logo-change
AWX Logo Change Procedure

![LOGO](https://raw.githubusercontent.com/azdolinski/awx-logo-change/main/img/example_ansiblelogo.png)

# How to find image files:
```bash
docker run -it ansible/awx:16.0.0 bash
docker> find /var -name logo-login.svg
```

File Location inside container:<br>
-> Main Login Page logo [158x93]: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     /var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-login.svg<br>
-> After login / top menu logo [158x93]: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    /var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-header.svg<br>

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
![LOGO](https://raw.githubusercontent.com/azdolinski/awx-logo-change/main/img/docker-example-change.png)

# Restart awx components
```bash
cd /root/.awx/awxcompose/
docker-compose down
docker-compose up -d --build
```


# Alternative logo2 file:
```bash
wget https://raw.githubusercontent.com/azdolinski/awx-logo-change/main/img/ansiblelogo2.png -O /root/.awx/awxcompose/logo/ansiblelogo2.png
```
![LOGO2](https://raw.githubusercontent.com/azdolinski/awx-logo-change/main/img/example_ansiblelogo2.png)
