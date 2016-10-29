Setting up Python on Mac
=========================

Brew Installation
---------------------
Homebrew is a popular package manager for Macs. So, go to 

    http://brew.sh/index.html

and run the first command there::

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

This will install ``brew`` by compiling it first. It takes some time, so be patient.

Once it's done, move on to the python install step.

Python3 Installation
----------------------
You might already have ``python3`` installed on your system. But it doesn't hurt to do it again with brew. So, type::
    
    brew install python3

Again, this will download and install python3, if needed, and set it up for you. It might take some time.

Once done, your computer is setup for Python3. Python comes with its own package manager called ``pip``. However, in this case, since you installed Python3, the pip command is actually ``pip3``.
Anytime you need to install a python library or module, you just type::
    pip3 install <name of module>

Virtualenv Installation
-----------------------
This will make things easier because with this program you can create virtual python environments.
It's nice because once you create a virtual environment, all the python packages and libraries you install will stay in one folder. Later you can even move the folder and the environment to another location or computer. 
If you need to switch between Python2 and Python3, virtual environments make it easy. 

To install virtualenv, type::
    pip3 install virtualenv
    
One last piece of software that will help manager virtualenvs much easier is virtualenvwrapper. So, let's install that also::
    pip3 install virtualenvwrapper

**Setting up Virtualenv**
There are a couple of actions you'll have to take to set virtualenv up properly. Type these commands into the terminal::
    cd ~
    mkdir virtualenvs

Check where your python3 is installed by typing::
    where python3
This should output something like::
    /usr/local/bin/python3

Now open a text editor in your home directory and create or open (if it already exists) the file ``.bash_profile``. The dot in the beginneing of the filename is important.
Add these lines at the end of the file::
    export WORKON_HOME=~/virtualenvs # point to the virtualenvs folder created above
    export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3   # make sure this is the python3 path that we got previously
    export VIRTUALENVWRAPPER_VIRTUALENV=/usr/local/bin/virtualenv
    export VIRTUALENVWRAPPER_VIRTUALENV_ARGS='--no-site-packages'
    source /usr/local/bin/virtualenvwrapper.sh
    
Save this file in your home directory. Then run it by typing::
    source ~/.bash_profile

Now you're all setup to use python3 with virtualenv.

Creating a virtual environment
------------------------------
Let's create our virtual environment for python3 now. The way to do this is::
    mkvirtualenv --python=/usr/local/bin/python3 py3

Make sure that the path you specify above is the one you got from ``where python3``.
At this point it must already have switched to the py3 environment. You should see a ``(py3)`` next to your prompt. If not, type::
    workon py3

You should be in the py3 environment now. Python3 is now available to you as simply ``python``. The pip3 command is also simply ``pip`` now.
The mapping can be changed for different environments depending on whether you need python2 or python3.

Installing Python Packages
---------------------------
Finally, let's install some useful python packages with pip::
    pip install pandas numpy jupyter
    
This will take some time to download and install these packages. Pandas, Numpy, and Jupyter are mostly what you need for data analysis in Python
For machine learning, you could also install ``scikit-learn``, but that's not needed right now.

Running Jupyter Notebook
========================
Jupyter notebooks are great because they let you run commands in a live python environment and keep track of what you're doing. To start the interface, type::
    jupyter notebook

This will start a webserver, and then open a webpage to the local address that shows the Jupyter interface. You can then start a new notebook and play around with python.
    


