# FanPI
######A little program to cool automatically your Raspberry Pi with the temperature of your CPU. Works with Python.

<img src="http://porostase.fr/upload/IMG_20150110_1828256.jpg">


##What you requiert to build that 
- Raspberry Pi (used Raspbian)
- A little fan (omg no?)
- 2 jumpercables females
- 8 jumpercables males
- 1 transistor (here used a KN2222A)
- 1 resistance (1KOHM)
- A Breadboard

##Requiert to build that if you don't have some components ~ 
- Raspberry Pi (used Raspbian)
- A little fan (too expensive D:)
- 2 jumpercables females

That's all ? Oh.

##What's the difference about the both ?
The voltage of a GPIO is approximately equal to 3.3v, and is a bit too low to cool normally. So, I advice to use the +5v to had a great cooling, but you can choice what you prefer, the both works with the same program. (IT'S MAGIC °3°)

##Assembling
The less easy part. Hehe, he. No. <br />
####Part 1 : With all requierement
Connect a cable to the `+5v`, `GND` and to the `GPIO18` of your Raspberry Pi. We are going to use a transistor like a switch to use the `+5v` as `Vcc` and to use the `GPIO18` as a interrupter.
<img src="http://porostase.fr/upload/FanPi_bb.jpg">

####Part 2 : With the minimal components (not recommended)
Connect the `+` cable to the `GPIO18`, and the `-` to the `GND` pin.
<img src="http://porostase.fr/upload/FanPi_bb4.jpg">

##Software requierement 
You need to have Python to execute the program and Psutil to get information about your CPU. So here we go ~

```
sudo apt-get install python
sudo apt-get install python-psutil
sudo apt-get update
```

##Setup
You can copy your program using a FTP client or using `git-core` using SSH. If you use SSH, check the version of the packages with 'git --version'. Now, we are going to clone the git in your Raspberry and try it. 
```
git --version
// if git-core is not installed
  sudo apt-get install git-core
  sudo apt-get update
  
cd /
mkdir python
cd /python
git clone git://github.com/P147x/FanPI FanPI
```

Now, you can try, just do 
```
sudo python fanpi.py 
```
It's work ! Stop it with `CTRL+C`

To start this program in background automatically (you should do it. Really), type `crontab -e` and add on last line `@reboot sudo python /python/fanpi.py`.

##Configuration 
If you want to configure the temperature of cooling, you have just to change two line in `/python/fanpi.py`, line 28 and 31.

line 28 : `if get_cpu_temperature() > 38.0:` <br />
line 31 : `while get_cpu_temperature() > 32.0:`

let at least a difference of 10 between the two temperatures, the primary value design the temperature of starting the fan, and the second design the temperature of stop. 

###Enjoy !
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Licence Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">FanPi</span> de <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">P147x</span> est mis à disposition selon les termes de la <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">licence Creative Commons Attribution - Pas d’Utilisation Commerciale 4.0 International</a>.
