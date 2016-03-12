Software Setup
==============

To get started, you only _need_ **Python 3**, but to get _everything_ setup and running on your own computer, you need the following:
* Python
* PyCharm
* Kivy
* Git

Each of these tools have their own instructions available online, but here I've attempted to compile all of the details you require for everything:

For All Operating Systems
-------------------------
*PyCharm:*  
* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* Download the Professional version of PyCharm for your OS: https://www.jetbrains.com/pycharm/download/index.html  
Enter your new account details when asked in PyCharm installation/setup.

Add KV language auto-completion and syntax highlighting (PyCharm does not know about KV language by default):
* Download this file https://github.com/Zen-CODE/kivybits/blob/master/IDE/PyCharm_kv_completion.jar?raw=true
* On Pycharm’s main menu, click "File"-> "Import" (or Import Settings)
* Select the .jar file you just downloaded and PyCharm will present a dialog with filetypes ticked. Click OK.
* Restart PyCharm.

Windows
-------
*Python:*  
On Windows, **you must get Python version 3.4.4 (not 3.5)** for Kivy 1.9.1 to work.  
Download and install Python 3.4 ​from: https://www.python.org/downloads  
Choose the option ​*Add python.exe to search path*​ when you install.  

*Kivy:*​  
The Windows instructions require you to type commands in a *Command Prompt* window.  
Run the Command Prompt: Hold the Windows key and press R (for run) then type `cmd.exe` and press Enter  
Then in the black window, type:  
`python --version`

If this shows you that you have Python 3.4.4 then continue with the commands below.  
If you get an error (python is an unknown command), then you either need to add python to your path or change into the directory you installed Python to. In most cases, this is C:\Python34 so type:  
`cd c:\Python34`  
`python --version`  

If that works, then enter the following commands.  
(Note that there's no shortcut key for pasting into a command prompt window, but you can access paste by right-clicking in the title bar, then choosing Paste from the Edit menu.)

`python -m pip install --upgrade pip wheel setuptools`  
`python -m pip install docutils pygments pypiwin32 kivy.deps.sdl2 kivy.deps.glew kivy.deps.gstreamer --extra-index-url https://kivy.org/downloads/packages/simple`  
`python -m pip install kivy`  

*Git*:  
Download and install git from https://git-scm.com/download  
There are a number of options for things like git-bash and what console you want to use... The defaults should be fine.

Mac OS X
--------
I recommend installing and using *homebrew* to do any software installations you can on Mac: http://brew.sh  
This is done using the *Terminal* on your Mac. If you haven't used the terminal much, you should try and get used to it. It's great!  
The instructions here are for using commands you type in at the terminal. Please note that some of these commands, like the first one, are long lines that should be copied and pasted in one go, even though the page here might show them word-wrapped.  
For installation methods other than using brew and pip, see the instructions on appropriate websites.

*Homebrew:*  
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

*Python 3:*  
`brew install python3`

*Git:*  
`brew install git`

*Kivy:*  
`brew install hg sdl sdl2`  
`pip3 install --upgrade pip`  
`pip3 install cython`  
`pip3 install hg+http://bitbucket.org/pygame/pygame`  
`pip3 install kivy`  

(The second command above should upgrade pip3 AND links the command `pip` to `pip3`, so you don't get `pip: command not found` errors. If you do, just use `pip3` anywhere you need `pip`.)

Test Setup
----------
To test it's all working, create a PyCharm project, create a new Python file, and enter the code from https://github.com/CP1404/Starter/blob/master/test_setup.py (or download this file to your project folder.  
Run it by right-clicking in the code window and choosing "Run..."  
If you can run it successfully, it's all good. **Celebrate!**  
If you need help, ask in our #cp1404 Slack channel.  


GitHub
------
Now that you have Git running, you will want to create a GitHub account.  
Go to https://github.com and sign up. *Be sure to use a username that easily identifies you.*

Then, go to https://education.github.com/discount_requests/new and enter your details so you can get free private repositories. Your assignment work should be in a private repository, so you need to do this step.