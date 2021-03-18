---
title:  "Jupyter notebook"
permalink: /posts/2021/03/jupyter-notebook
date: 2021-03-18-00
---



Prerequisites
==========
In order to complete this guide, you should have a fresh Ubuntu 18.04 server instance with a basic firewall and a non-root user with sudo privileges configured.

* * *


Step 1 — Set Up Python
==========
To begin the process, we’ll install the dependencies we need for our Python programming environment from the Ubuntu repositories. Ubuntu 18.04 comes preinstalled with Python 3.6. We will use the Python package manager pip to install additional components a bit later.

We first need to update the local apt package index and then download and install the packages:

```bash
sudo apt update
```

Next, install pip and the Python header files, which are used by some of Jupyter’s dependencies:

```bash
sudo apt install python3-pip python3-dev
```
We can now move on to setting up a Python virtual environment into which we’ll install Jupyter. 

* * *

Step 2 — Create a Python Virtual Environment for Jupyter
==========
Now that we have Python 3, its header files, and pip ready to go, we can create a Python virtual environment to manage our projects. We will install Jupyter into this virtual environment.

To do this, we first need access to the `virtualenv` command which we can install with pip.

Upgrade pip and install the package by typing:
```bash
sudo -H pip3 install --upgrade pip
sudo -H pip3 install virtualenv
```


The -H flag ensures that the security policy sets the home environment variable to the home directory of the target user.

With virtualenv installed, we can start forming our environment. Create and move into a directory where we can keep our project files. We’ll call this my_project_dir, but you should use a name that is meaningful for you and what you’re working on.

```bash
mkdir ~/my_project_dir
cd ~/my_project_dir
```

Within the project directory, we’ll create a Python virtual environment. For the purpose of this tutorial, we’ll call it my_project_env but you should call it something that is relevant to your project.

```bash
virtualenv my_project_env
```

This will create a directory called `my_project_env` within your `my_project_dir` directory. Inside, it will install a local version of Python and a local version of pip. We can use this to install and configure an isolated Python environment for Jupyter.

Before we install Jupyter, we need to activate the virtual environment. You can do that by typing:

```bash
source my_project_env/bin/activate
```

* * *


Step 3 — Install Jupyter
==========
> **_NOTE:_**  Note: When the virtual environment is activated (when your prompt has (my_project_env) preceding it), use pip instead of pip3, even if you are using Python 3. The virtual environment’s copy of the tool is always named pip, regardless of the Python version.

With your virtual environment active, install Jupyter with the local instance of pip.

```bash
pip install jupyter
```

At this point, you’ve successfully installed all the software needed to run Jupyter. We can now start the Notebook server.

* * *



Step 4 — Run Jupyter Notebook
==========
ou now have everything you need to run Jupyter Notebook! To run it, execute the following command:

```bash
jupyter notebook
```

A log of the activities of the Jupyter Notebook will be printed to the terminal. When you run Jupyter Notebook, it runs on a specific port number. The first Notebook you run will usually use port 8888. To check the specific port number Jupyter Notebook is running on, refer to the output of the command used to start it:

```
Output
[I 21:23:21.198 NotebookApp] Writing notebook server cookie secret to /run/user/1001/jupyter/notebook_cookie_secret
[I 21:23:21.361 NotebookApp] Serving notebooks from local directory: /home/sammy/my_project_dir
[I 21:23:21.361 NotebookApp] The Jupyter Notebook is running at:
[I 21:23:21.361 NotebookApp] http://localhost:8888/?token=1fefa6ab49a498a3f37c959404f7baf16b9a2eda3eaa6d72
[I 21:23:21.361 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[W 21:23:21.361 NotebookApp] No web browser found: could not locate runnable browser.
[C 21:23:21.361 NotebookApp]

    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=1fefa6ab49a498a3f37c959404f7baf16b9a2eda3eaa6d72

```

If you are running Jupyter Notebook on a local computer (not on a server), you can navigate to the displayed URL to connect to Jupyter Notebook. If you are running Jupyter Notebook on a server, you will need to connect to the server using SSH tunneling as outlined in the next section.

At this point, you can keep the SSH connection open and keep Jupyter Notebook running or you can exit the app and re-run it once you set up SSH tunneling. Let’s choose to stop the Jupyter Notebook process. We will run it again once we have SSH tunneling set up. To stop the Jupyter Notebook process, press CTRL+C, type Y, and then ENTER to confirm. The following output will be displayed:


* * *
## Source: 
* [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-set-up-jupyter-notebook-with-python-3-on-ubuntu-18-04)