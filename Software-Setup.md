# Software Setup

[CP1404 students, skip the first section (only for CP1401) and start here](https://github.com/CP1404/Starter/wiki/Software-Setup#cp140418045639---programming-2)

## CP1401/1801/5639 - Programming 1 
Students in **CP1401** only need Python 3 and PyCharm:

1. Download and install Python 3 ​from: https://www.python.org/downloads/  
(Windows) Choose the option ​*Add python.exe to search path*​ when you install.
2. [Follow the instructions below to install PyCharm](https://github.com/CP1404/Starter/wiki/Software-Setup#pycharm)
3. Stop. Do not install Kivy or Git.


## CP1404/1804/5639 - Programming 2 

* Python (3.9+)
* PyCharm (2020.3+)
* Kivy (2.0+) - note that Kivy < 2.0 is not compatible with Python > 3.7
* Git

Each of these tools have their own instructions available online, but here I've attempted to compile all of the details you require for everything. Things change, and sometimes you'll find a different/better way is needed. If so, please contact me and let me know what needs updating.


## GitHub:

If you do not have one already, create a GitHub account.  
Go to https://github.com and sign up with your JCU email address. *Be sure to use a username that easily identifies you.*  

**Note:** GitHub do not accept our my.jcu.edu.au addresses as student proof because non-student alumni also have these addresses.  
**So, in the following step, please choose the option that lets you upload proof, and upload a photo of your current student ID card with the date on it.**

Go to https://education.github.com/discount_requests/new and enter your details so you can get free private repositories and your GitHub 'pack' with a bunch of free bonuses: http://education.github.com/pack

# Windows

## Git:
Download and install git from https://git-scm.com/download  
There are a number of options for things like git-bash and what console you want to use... The defaults should be fine.

## Python:
Download and install Python 3 ​from: https://www.python.org/downloads/  
Choose the option ​*Add python.exe to search path*​ when you install.

## Kivy:
See https://kivy.org/docs/installation/installation-windows.html which are summarised/expanded below:  

The Windows instructions require you to type commands in a *Command Prompt* window.  
Run the Command Prompt: Tap the Windows key to get the Start menu, then start typing "command prompt"... when you see it, right-click and choose "Run as Administrator"
Then in the black window (that's the command prompt), type:  

    python --version

If this shows you that you have Python, then continue with the commands below.  
If you get an error (python is an unknown command), then you either need to add python to your PATH or change into the directory you installed Python to.  
E.g. if this were C:\Python39 then type:  

    cd c:\Python39  
    python --version  

If that works, then enter the following commands.  
(If the usual shortcut doesn't work for pasting into the command prompt window, you can access paste by right-clicking in the title bar, then choosing Paste from the Edit menu.)

    python -m pip install --upgrade pip wheel setuptools 
    python -m pip install docutils pygments pypiwin32 kivy.deps.sdl2 kivy.deps.glew
    python -m pip install kivy.deps.gstreamer
    python -m pip install kivy  

Now you can run PyCharm, select your interpreter (the Python you just installed), and you should be able to run Python programs.  
See below

## PyCharm:
*After* you have installed Python...  

* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* Download and install the *Professional* version of PyCharm: https://www.jetbrains.com/pycharm/download/index.html  
Please note that the community edition lacks Flask project support and so is not recommended.  
Enter your new account details when asked in PyCharm installation/setup.

Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On PyCharm’s File menu, import the settings: Manage IDE Settings > Import Settings... or File > Import (depending on your OS)
* Select the .jar file you just downloaded and click OK on the dialog with file types ticked.
* Restart PyCharm.


# MacOS

I recommend installing and using *homebrew* to do any available software installations you can on Mac: http://brew.sh  
This is done using the *Terminal* on your Mac. If you haven't used the terminal much, you should try and get used to it as it is a very useful and common developer tool.  
The instructions here are for using commands you type in at the terminal.  
*Please note* that some of these commands, like the first one, are long lines that should be copied and pasted in one go, even though the page here might show them word-wrapped.  
For installation methods other than using brew and pip, see the instructions on appropriate websites.

## Homebrew:

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

## Python 3:

    brew install python3

## Git:

    brew install git

## PyCharm:
*After* you have installed Python...  

* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* Download and install the *Professional* version of PyCharm: https://www.jetbrains.com/pycharm/download/index.html  
Please note that the community edition lacks Flask project support and so is not recommended.  
Enter your new account details when asked in PyCharm installation/setup.

Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On PyCharm’s File menu, import the settings: Manage IDE Settings > Import Settings... or File > Import (depending on your OS)
* Select the .jar file you just downloaded and click OK on the dialog with file types ticked.
* Restart PyCharm.

## Kivy:

First, create a new project [https://github.com/CP1404/Practicals/tree/master/prac_01](see Prac 01) if you need help.  
Make sure that you select **System Interpreter** And chose the newly-installed Python 3.9+.  

Install Kivy as you would any Python package via PyCharm: Preferences > Project > Interpreter (you should see your current, NON-VENV! system interpreter), then click the + button, search for and install "Kivy").  
Note: If you incorrectly selected a venv (Virtual Environment) when you setup your project, then you must change your project to use the system interpreter, and select Python 3.9+, before installing Kivy. If you use a venv, then you need to install all packages again for each new project... and you don't want to do that.


# Test Setup

To test it's all working, create a PyCharm project, **making sure to select the local interpreter where you installed Kivy**.  
_DO NOT_ use a new virtual environment (venv) for this or any other projects.  

Create a new Python file, and enter the code from https://github.com/CP1404/Starter/blob/master/check_setup.py (or download this file to your project folder.  
Run it by right-clicking in the code window and choosing "Run..."  
If you can run it successfully, it's all good. **Celebrate!**  

You can also test your Git & GitHub setup by using PyCharm to clone a repository and run the code:  
Select *VCS > Checkout from Version Control > GitHub*  
Then enter your GitHub credentials. 
Enter our starter repo URL: `https://github.com/CP1404/Starter` in the prompt, clone it to a new folder and open this as a new project.  
Try and run the check_setup.py file. If it works, you should see a nice big hello button.  

If you need help, please ask.
