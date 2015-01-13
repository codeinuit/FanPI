# FanPI
######A small program to automatically cool your Raspberry Pi according to the temperature of its CPU. Warranty 100% Python.

<img src="http://porostase.fr/upload/IMG_20150110_1828256.jpg">


##What you requiere to build that 
- Raspberry Pi (used Raspbian)
- A little fan (omg no?)
- 2 jumpercables females
- 8 jumpercables males
- 1 transistor (a KN2222A is used here)
- 1 resistance (1KOHM)
- A Breadboard

##Requiert to build that if you don't have all of the components ~ 
- Raspberry Pi (used Raspbian)
- A little fan (too expensive D:)
- 2 jumpercables females

That's all ? Oh.

##What's the difference between both ?
The voltage of a GPIO is approximately equal to 3.3v, it is a bit too low to cool normally. So, I advise to use the +5v to have a great cooling, but you can choos what you prefer, both work with the same program. (IT'S MAGIC °3°)

##Assembling
The less easy part. Hehe, he. No. <br />
####Part 1 : With all requierement
Connect a cable to the `+5v`, `GND` and to the `GPIO18` of your Raspberry Pi. We are going to use a transistor as a switch to use the `+5v` as `Vcc` and to use the `GPIO18` as an interrupter.
<br /><br />
<img src="http://porostase.fr/upload/FanPi_bb.jpg">

####Part 2 : With the minimal components (not recommended)
Connect the `+` cable to the `GPIO18`, and the `-` to the `GND` pin.
<br /><br />
<img src="http://porostase.fr/upload/FanPi_bb4.jpg">

##Software requierement 
You need to have Python to execute the program and Psutil to get informations about your CPU. So here we go ~

```
sudo apt-get update
sudo apt-get install python python-psutil
```

##Setup
You can copy your program using a FTP client or using `git-core` using SSH. If you use SSH, check the version of the packages with 'git --version'. Now, we are going to clone the git in your Raspberry and try it. 
```
git --version
// if git-core is not installed
  sudo apt-get update
  sudo apt-get install git-core
  
cd 
sudo mkdir python
cd /python
sudo git clone git://github.com/P147x/FanPI FanPI
cd FanPi
```

Now, you can try, just do 
```
sudo python fanpi.py 
```
It works ! Stop it with `CTRL+C`

To start this program in background automatically (you should do it. Really), type `crontab -e` and add on last line `@reboot sudo python /home/pi/python/FanPi/fanpi.py`. `CTRL+X` and `O` to save.

##Configuration 
####Calibrate
You can calibrate your program with your fan, to make some tests and adapt it for your utilisation.
```
sudo nano /home/pi/python/FanPi/calibrate.py
```
Modify the line 30 and 31 (starting temp and stop), and type `sudo python /home/pi/python/FanPi/calibrate.py` and make your own tests !

####Configure the main file o/ !
If you want to configure the temperature of cooling, you just have to change two lines in `/home/pi/fanpi.py`, line 28 and 31.

line 28 : `if get_cpu_temperature() > 38.0:` <br />
line 31 : `while get_cpu_temperature() > 32.0:`

Keep at least a difference of ~10°C between the two temperatures, the first value design the temperature of starting the fan, and the second design the temperature of stop. 

##Start it !
Let it be independant with a reboot (`sudo reboot`) and it's all !<br />
ENJOY IT /o/ !<br /><br />

<br />
##Update notes
####V1.1
- Patch some bugs 
- Found better temperatures (max-min)
- New file : `calibration.py` !
- More bananas
<br /><br />
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Licence Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">FanPi</span> de <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">P147x</span> est mis à disposition selon les termes de la <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">licence Creative Commons Attribution - Pas d’Utilisation Commerciale 4.0 International</a>.
