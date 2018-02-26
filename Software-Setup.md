Software Setup
==============

To get started, you only _need_ **Python 3**, but to get _everything_ setup and running on your own computer, you need the following. *Note, please install these in the order below.*
* Python
* PyCharm
* Kivy
* Git

Each of these tools have their own instructions available online, but here I've attempted to compile all of the details you require for everything. Things change, and sometimes you'll find a different/better way is needed. If so, please contact me and let me know what needs updating.

*GitHub:*

If you do not have one already, create a GitHub account.  
Go to https://github.com and sign up with your JCU email address. *Be sure to use a username that easily identifies you.*

Then, go to https://education.github.com/discount_requests/new and enter your details so you can get free private repositories.  
**Note:** GitHub do not accept our my.jcu.edu.au addresses as student proof because non-student alumni also have these addresses. **So, choose the option that lets you upload proof, and upload a photo of your current student ID with the date on it.**

Once you're signed up, get your GitHub 'pack' with a bunch of free bonuses: http://education.github.com/pack

Windows
-------
*Git:*  
Download and install git from https://git-scm.com/download  
There are a number of options for things like git-bash and what console you want to use... The defaults should be fine.

*Python:*  
Download and install Python 3 ​from: https://www.python.org/downloads  
Choose the option ​*Add python.exe to search path*​ when you install.

*Kivy:*  
See https://kivy.org/docs/installation/installation-windows.html which are summarised/expanded below:  

The Windows instructions require you to type commands in a *Command Prompt* window.  
Run the Command Prompt: Tap the Windows key to get the Start menu, then start typing "command prompt"... when you see it, right-click and choose "Run as Administrator"
Then in the black window (that's the command prompt), type:  

    python --version

If this shows you that you have Python, then continue with the commands below.  
If you get an error (python is an unknown command), then you either need to add python to your PATH or change into the directory you installed Python to.  
E.g. if this were C:\Python36 then type:  

    cd c:\Python36  
    python --version  

If that works, then enter the following commands.  
(If the usual shortcut doesn't work for pasting into the command prompt window, you can access paste by right-clicking in the title bar, then choosing Paste from the Edit menu.)

    python -m pip install --upgrade pip wheel setuptools 
    python -m pip install docutils pygments pypiwin32 kivy.deps.sdl2 kivy.deps.glew
    python -m pip install kivy.deps.gstreamer
    python -m pip install kivy  

Now you can run PyCharm, select your interpreter (the Python you just installed), and you should be able to run Python programs.  
See below

*PyCharm:*  
After you have installed Python...  

* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* Download and install the Professional version of PyCharm for your OS: https://www.jetbrains.com/pycharm/download/index.html  
Enter your new account details when asked in PyCharm installation/setup.

Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On PyCharm’s main menu, click Import Settings or File > Import (depending on your OS)
* Select the .jar file you just downloaded and click OK on the dialog with file types ticked.
* Restart PyCharm.


MacOS
-----
I recommend installing and using *homebrew* to do any available software installations you can on Mac: http://brew.sh  
This is done using the *Terminal* on your Mac. If you haven't used the terminal much, you should try and get used to it as it is a very useful and common developer tool.  
The instructions here are for using commands you type in at the terminal.  
*Please note* that some of these commands, like the first one, are long lines that should be copied and pasted in one go, even though the page here might show them word-wrapped.  
For installation methods other than using brew and pip, see the instructions on appropriate websites.

*Homebrew:*  

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

*Python 3:*  

    brew install python3

*Git:*  

    brew install git

*Kivy:*  

    brew install pkg-config sdl2 sdl2_image sdl2_ttf sdl2_mixer gstreamer   
    pip3 install --upgrade pip  
    pip3 install Cython==0.26.1  
    USE_OSX_FRAMEWORKS=0 pip3 install https://github.com/kivy/kivy/zipball/master  

(The second command above should upgrade pip3 AND link the command `pip` to `pip3`, so you don't get `pip: command not found` errors. However, if you do get these errors, just use `pip3` anywhere it says `pip`.)

*PyCharm:*  
After you have installed Python...  

* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* Download and install the Professional version of PyCharm for your OS: https://www.jetbrains.com/pycharm/download/index.html  
Enter your new account details when asked in PyCharm installation/setup.

Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On PyCharm’s main menu, click Import Settings or File > Import (depending on your OS)
* Select the .jar file you just downloaded and click OK on the dialog with file types ticked.
* Restart PyCharm.


Test Setup
----------
To test it's working, create a PyCharm project, **making sure to select the local interpreter where you installed Kivy**.  
_DO NOT_ use a new virtual environment (venv) for this or any other projects.  

Create a new Python file, and enter the code from https://github.com/CP1404/Starter/blob/master/check_setup.py (or download this file to your project folder.  
Run it by right-clicking in the code window and choosing "Run..."  
If you can run it successfully, it's all good. **Celebrate!**  

You can also test your Git & GitHub setup by using PyCharm to clone a repository and run the code:  
Select *VCS > Checkout from Version Control > GitHub*  
Then enter your GitHub username and password (not token, unless you want to use one).  
Enter our starter repo URL: `https://github.com/CP1404/Starter` in the prompt, clone it to a new folder and open this as a new project.  
Try and run the check_setup.py file. If it works, you should see a nice big hello button.  

If you need help, please ask.
