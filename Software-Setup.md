# Software Setup

## CP1401/5639 - Programming 1 
Students in **CP1401** ONLY need Python 3 and PyCharm:

1. Download and install Python 3 ​from: https://www.python.org/downloads/  
(Windows) Choose the option ​*Add Python to PATH*​ when you install.

2. Install PyCharm
* Download and install the free *Community* version of PyCharm: https://www.jetbrains.com/pycharm/download/index.html  

3. Stop. Do not install Kivy or Git.


## CP1404/5632 - Programming 2 

Students in Programming 2 need the following installed: 
* Python (3.9+)
* PyCharm (2020.3+)
* Kivy (2.0+) - note that Kivy < 2.0 is not compatible with Python > 3.7
* Git

Each of these tools have their own instructions available online, but here I've attempted to compile all of the details you require in one place.  
Things change and your system might be different, and sometimes you'll find a different/better way is needed. If so, please contact me and let me know what needs updating in this guide.


## GitHub:

If you do not have one already, create a GitHub account.  
Go to https://github.com and sign up with your JCU email address. *Be sure to use a username that easily identifies you.*  

**Note:** GitHub do not accept our my.jcu.edu.au addresses as student proof because non-student alumni also have these addresses.  
**So, in the following step, please choose the option that lets you upload proof, and upload a photo of your current student ID card with the date on it.**

Go to https://education.github.com/discount_requests/new and enter your details so you can get free private repositories and your GitHub 'pack' with a bunch of free bonuses: http://education.github.com/pack

# Windows

## Git:
Download and install git from https://git-scm.com/download  
There are a number of options for things like git-bash and what console you want to use... All of the defaults should be fine.

## Python:
Download and install Python 3 ​from: https://www.python.org/downloads/  
Choose the option ​*Add Python to PATH*​ when you install.  
The Windows default location can be hard to find, so I recommend changing this to something more obvious and memorable. Choose to customise your installation:

![Choose to customise your Python installation and add to PATH](https://github.com/CP1404/Starter/blob/master/images/Python-Windows-Install-1.png)
![Choose a simple folder location for your Python installation](https://github.com/CP1404/Starter/blob/master/images/Python-Windows-Install-2.png)

## PyCharm:
*After* you have installed Python...  

Currently, JetBrains doesn't accept `my.jcu.edu.au` addresses as proof of student status. If you would like the Professional versions of JetBrains software, you will need to provide official documentation, not just your email address: 

* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* Download and install the *Professional* version of PyCharm: https://www.jetbrains.com/pycharm/download/index.html  
Please note that the community edition lacks Flask project support and so is not recommended.  
Enter your new account details when asked in PyCharm installation/setup.

## Kivy:

Kivy is a Pthon package, and you can install it and any other packages via PyCharm. First, create a new PyCharm project and select the previously configured interpreter, NOT a virtual environment.

![Select Previously configured interpreter in the new project window](https://github.com/CP1404/Starter/blob/master/images/Python-Windows-Install-3-Project-1.png)  

Click the dots ("meatball menu") to choose a new interpreter and select the System Interpreter you installed earlier. (This is why it's useful to install Python in a directory you can find.)  
![Select the System Interpreter you installed](https://github.com/CP1404/Starter/blob/master/images/Python-Windows-Install-4-Project-2.png)

When your new project loads, you can install the Kivy package as you would any Python package via PyCharm: File > Settings > Project > Interpreter (you should see your current, NON-Virtualenv! system interpreter), then click the + button, search for and install "Kivy").  
![Install Kivy package in the Settings window](https://github.com/CP1404/Starter/blob/master/images/Python-Windows-Install-5-Kivy-Package.png)


Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On PyCharm’s File menu, import the settings: File > Manage IDE Settings > Import Settings... or File > Import (depending on your OS)
* Select the .jar file you just downloaded and click OK on the dialog with file types ticked.
* Restart PyCharm.


# MacOS

I recommend installing and using *homebrew* to do any available software installations you can on Mac: http://brew.sh  
This is done using the *Terminal* on your Mac. If you haven't used the terminal much, you should try and get used to it as it is a very useful and common developer tool.  
The instructions here are for using commands you type in at the terminal.  
*Please note* that some of these commands, like the first one, are long lines that should be copied and pasted in one go, even though the page here might show them word-wrapped.  
For installation methods other than using brew, see the instructions on appropriate websites.

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

## Kivy:

First, create a new project - the Windows instructions above are similar enough to help you.  
Make sure that you select **System Interpreter**, NOT a virtual environment, and choose the newly-installed Python 3.9+.  

Install Kivy as you would any Python package via PyCharm: Preferences > Project > Interpreter (you should see your current, NON-Virtualenv! system interpreter), then click the + button, search for and install "Kivy").  
Note: If you incorrectly selected a Virtualenv (venv, Virtual Environment) when you setup your project, then you must change your project to use the system interpreter, and select Python 3.9+, before installing Kivy. If you use a Virtualenv, then you need to install all packages again for each new project... and you don't want to do that.

Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On PyCharm’s File menu, import the settings: Manage IDE Settings > Import Settings... or File > Import (depending on your OS)
* Select the .jar file you just downloaded and click OK on the dialog with file types ticked.
* Restart PyCharm.


# Test Setup

To test it's all working, create a PyCharm project (if you haven't already), **making sure to select the interpreter where you installed Kivy**.  
_DO NOT_ use a new virtual environment (Virtualenv) for this or any other projects.  

Create a new Python file, and enter the code from https://github.com/CP1404/Starter/blob/master/check_setup.py (or download this file to your project folder.  
Run it by right-clicking in the code window and choosing "Run..."  
If it works, you should see a nice big `hello world` button. **Celebrate!**  

You can also test your Git & GitHub setup by using PyCharm to clone a repository and run the code:  
Select *VCS > Get from Version Control > GitHub*  
Then login with your GitHub credentials. 
Enter our starter repo URL: `https://github.com/CP1404/Starter` in the prompt, clone it to a new folder and open this as a new project.  

If you need help, please ask.
