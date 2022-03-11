# Enable-Autorun-in-Linux-on-rc.local
Enable autorun in linux on rc.local


sudo systemctl status rc-local
sudo systemctl enable rc-local
sudo nano /etc/systemd/system/rc-local.service
>>>>> paste it in rc-local.service <<<<<<<
[Unit]
Description=/etc/rc.local Compatibility
ConditionPathExists-/etc/rc.local

[Service]
Type=forking
ExecStart=/etc/rc.local start
TimeoutSec=0
StandardOutput=tty
RemainAfterExit=yes
SysVStartPriority=99

[Install]
WantedBy=multi-user.target 
--------------------------------------------------
sudo nano /etc/rc.local
>>>>> paste it in rc-local <<<<<<<
#!/bin/bash

note- enter your path which you want to run after boot
ex- python3 /DEsktop/atul/iot/developer/run.py

exit 0

--------------------------------------------------
sudo chmod +x /etc/rc.local

sudo systemctl enable rc-local
====================================================================================================================
Created symlink /etc/systemd/system/multi-user.target.wants/rc-local.service → /etc/systemd/system/rc-local.service.
====================================================================================================================

sudo systemctl start rc-local

sudo systemctl status rc-local

sudo shutdown -r now
