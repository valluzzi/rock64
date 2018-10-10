# rock64


  //Instructions to install motioneye on rock64 - debian
  apt-get install -y motion ffmpeg v4l-utils
  apt-get install -y python-pip python-dev python-setuptools curl libssl-dev libcurl4-openssl-dev libjpeg-dev libz-dev
  apt-get install -y vim htop
  apt-get install -y python-pillow python-pycurl
  pip install --upgrade pip 

# -*- coding: utf-8 -*-
import re
import sys

from pip._internal import main as _main

if __name__ == '__main__':
    sys.argv[0] = re.sub(r'(-script\.pyw?|\.exe)?$', '', sys.argv[0])
    sys.exit(_main())
	
pip install motioneye

mkdir -p /etc/motioneye
cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf

mkdir -p /var/lib/motioneye

cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service
systemctl daemon-reload
systemctl enable motioneye
systemctl start motioneye
