# rock64

### Instructions to install motioneye on rock64 - debian
~~~~
apt-get install -y motion ffmpeg v4l-utils
apt-get install -y python-pip python-dev python-setuptools curl libssl-dev libcurl4-openssl-dev libjpeg-dev libz-dev
apt-get install -y vim 
~~~~

### install pillow and pycurl from binary instead of using pip
~~~~
apt-get install -y python-pillow python-pycurl
~~~~

### upgrade pip (if needed)
~~~~
pip install --upgrade pip 
~~~~


### patch pip (if needed)
#### patch file /usr/bin/pip
~~~~
# -*- coding: utf-8 -*-
import sys

from pip._internal import main as _main

if __name__ == '__main__':
    sys.exit(_main())
~~~~

### finally install motioneye
~~~~
pip install motioneye
~~~~

### some other things to do 
~~~~
mkdir -p /etc/motioneye
cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf

mkdir -p /var/lib/motioneye
cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service
~~~~

### start the service
~~~~
systemctl daemon-reload
systemctl enable motioneye
systemctl start motioneye
~~~~

### check the browser at 192.168.1.XXX:8765
~~~~
Optionally you can change the port of the service 
/etc/motioneye/motioneye.conf
~~~~
