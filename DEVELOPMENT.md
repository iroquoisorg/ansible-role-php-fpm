# Development and testing

## Development

You can develop this role using Vagrant virtual machine. It can be started using Vagrant directly by running
`vagrant up` while in `vagrant/` subdirectory. This machine will be provisioned with playbook 
`molecule/default/playbook.yml`, which will run this role and all required dependencies. After that, you can connect
to this machine with `vagrant ssh` command.

You can also start this virtual machine using molecule testing framework (see below for instructions about installation
and running). Just run following command:

```
$ molecule test --destroy never --driver-name vagrant
```

This command will provision the test virtual machine, run the test suite, and quit without destroying the VM. You can
connect to the console using VirtualBox console.

# Testing

For testing this role *molecule* framework is used. The tests themselves are written using `testinfra` package.


## Installation

To install molecule:

1. Have python installed on your system
   * installed by default on many operating systems
   * can be installed from _HomeBrew_ on macOS by issuing `brew install python@2` command
2. Install pip - python package manager

    ```
    curl https://bootstrap.pypa.io/get-pip.py | sudo /usr/local/bin/python2
    ```

3. Install virtualenv package using pip
   Install location might vary. Usually pip will be installed in a location on system path, so it should be available
   by just running `pip`. It is known that in recent versions of python installed by _HomeBrew_ on macOS systems
   the binary location is a bit convoluted. For instance, it might be `/usr/local/Cellar/python@2/2.7.15_1/Frameworks/Python.framework/Versions/2.7/bin/pip`.
   To make it easier to use, you can create a symbolic link in a directory on system path. For instance:
   
    ```
    sudo ln -s /usr/local/Cellar/python@2/2.7.15_1/Frameworks/Python.framework/Versions/2.7/bin/pip
    ``` 

4. Install `virtualenv`

    ```
    virtualenv --no-site-packages ~/.venv
    ```

5. Activate `virtualenv` (this step will need to be executed before running molecule in a new shell)

    ```
    source ~/.venv/bin/activate
    ```

6. Install required packages

    ```
    pip install molecule ansible
    ```

7. [option] for running tests in docker container, install docker from [Docker website](https://www.docker.com/products/docker-desktop)
   and install docker python package
   
    ```
    pip install docker-py
    ```

8. [option] for running tests in a vagrant environment, install [vagrant](https://www.vagrantup.com/), 
   [VirtualBox](http://virtualbox.org/), and python package for vagrant
   
    ```
    pip install python-vagrant
    ```

In the instructions above location of python binary may need to be adjusted.

## Running

In the role main directory, activate virtualenv:

```
source ~/.venv/bin/activate
```

Then you can run the tests:

```
molecule test
```

By default, the tests are being run in a docker container. To run it in vagrant/virtualbox virtual machine, run:

```
molecule test --driver-name vagrant
```
