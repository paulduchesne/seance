##### Notes on setting up Pure Data on a Raspberry Pi 3B+

/ flash microSD with Raspberry Pi OS Lite

/ connect to WIFI network, change password and enable SSH

/ install git

> sudo apt-get update
>
> sudo apt-get install git

/ git clone seance repository to home directory

> git clone https://github.com/paulduchesne/seance.git

/ install pure data

> sudo apt-get install puredata
>
> pd -version

/ fix security issues

> sudo nano /etc/security/limits.conf
> @audio   -  rtprio     98
> @audio   -  memlock    unlimited
> @audio   -  nice      -19

/ run patch from command line

> pd -nogui -verbose /home/pi/seance/seance.pd

/ create startup script

> sudo nano /home/pi/pd
>
> pd -nogui /home/pi/seance/seance.pd &
>
> sudo chmod 755 /home/pi/pd

/ add to boot

> sudo nano /etc/rc.local
>
> /home/pi/pd