# awx-logo-change
AWX Logo Change Procedure


docker run -it ansible/awx:16.0.0 bash

File Location inside container:
-> Main Login Page logo: /var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-login.svg
-> After login / top menu logo:  /var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-header.svg


mkdir /root/.awx/awxcompose/logo
wget https://png-pixel.com/1x1-ffff007f.png -O /root/.awx/awxcompose/logo/dot.png


Edit: 
/root/.awx/awxcompose/docker-compose.yml

Add volumes to awx_web:
      - "/root/ansiblelogo.png:/var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-header.svg:ro"
      - "/root/1x1-ffff007f.png:/var/lib/awx/venv/awx/lib/python3.6/site-packages/awx/ui_next/build/static/media/logo-login.svg:ro"