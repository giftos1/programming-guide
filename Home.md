CP1404 Getting Started

Software Setup
==============

To get everything setup and running on your own computer, you need the following:
* Python
* PyCharm
* Kivy
* Git

Each of these tools have their own instructions available online, but here are some custom details for our subject:

All OS
------
* Sign up for a free JetBrains account at: https://www.jetbrains.com/shop/eform/students using your JCU email address.
* *PyCharm*: Then dowload the Professional version: https://www.jetbrains.com/pycharm/download/index.html
Enter your new account details when asked in PyCharm installation/setup.

* Download and install *Git* for your OS: https://git-scm.com/download
PyCharm will use this.

Windows
-------
Download and install ​*Python*​: https://www.python.org/downloads 
On Windows, *you must get version 3.4.4 (not 3.5)*​ for Kivy to work. Choose the option ​*Add python.exe to search path*​ if you have it when you install.

*Kivy*​
- Windows users, follow the install instructions at: http://kivy.org/docs/installation/installation.html


Mac OS X
--------
- Mac users, get the current version of Python 3. 
I recommend installing and using *homebrew* to do any software installations you can on Mac: http://brew.sh

- create a PyCharm project, then go to PyCharm > Preferences > Project: <whatever> > Project interpreter, then click the + button and search for "kivy"; select it then click "Install", making sure you do NOT select "install to user's site package directory".


To test it's all working, create a PyCharm project, create a new Python file, and enter the code below. Run it by right-clicking on the code and choosing "Run..."
If you can run it successfully, it's all good.
If you need help, ask in our #cp1404 Slack channel.

`from kivy.app import App`
`from kivy.uix.button import Button`


`class TestApp(App):`

    `def build(self):`
        `return Button(text='hello world')`

`TestApp().run()`