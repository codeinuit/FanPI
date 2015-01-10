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
##Configuration 
If you want to configure the temperature of cooling, you have just to change two line in `/python/fanpi.py`, line 28 and 31.

line 28 : `if get_cpu_temperature() > 25.0:` <br />
line 31 : `while get_cpu_temperature() > 15.0:`
