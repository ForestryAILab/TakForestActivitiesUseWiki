### FreeTAKServer - install to FreeBSD jail - with pip
***

See: https://freetakteam.github.io/FreeTAKServer-User-Docs/Installation/Linux/Installation/

Follow the Linux --> Ubuntu thread

### References:
* https://docs.freebsd.org/en/books/handbook/
* https://freetakteam.github.io/FreeTAKServer-User-Docs/
* https://pypi.org/project/FreeTAKServer/
* https://docs.freebsd.org/en/books/developers-handbook/tools/
* https://docs.freebsd.org/en/books/developers-handbook/tools/https://www.pythonhelp.org/learn/introduction/setting-up-development-environment-freebsd/
* https://computingforgeeks.com/how-to-install-pip-python-package-manager-on-freebsd-12/
***
* Work inside jail from now on

```
$ bastille console FreeTakServer
```

* Install dependencies into jail
* Ubuntu dependencies:

```
$ apt update && sudo apt install python3 && sudo apt install python3-pip
$ apt install python3-dev python3-setuptools build-essential python3-gevent python3-lxml libcairo2-dev
```

* consult freshports to find FreeBSD equivalents or use $ pkg search  

##### Ubuntu ==> FreeBSD
* python3 ==> lang/python311
* python3-pip ==> devel/py-pip
* python3-dev ==> ??
* python3-setuptools ==> devel/py-setuptools (already installed with py-pip) 
* build-essential ==> gcc or clang development environment (clang already installed)
* python3-gevent ==> devel/py-gevent
* python3-lxml ==> devel/py-lxml
* libcairo2-dev ==> graphics/cairo (?? py39-cairo)

```
$ pkg install pkg
$ pkg install lang/python311 devel/py-pip bash git
$ pkg install devel/py-gevent devel/py-lxml graphics/cairo graphics/py-cairo devel/py-yaml
$ pkg install 
```

* Create service user freetakserver
* https://forums.freebsd.org/threads/how-to-create-add-a-system-account.70197/
* $ pw useradd foo -u 990 -c "Captain Foo,Testlab" -s /usr/sbin/nologin -G group1,group2,group3
```
```
```
$ pw useradd freetakserver -u 1001 -c "FreeTAKServer" -s /usr/sbin/nologin -G freetakserver
$ mkdir /opt
$ cd /opt
$ mkdir FreeTAKServer
$ cd FreeTAKServer
$ python3.11 -m venv venv3.11
$ bash
$ . venv3.11/bin/activate
$ pip install -U pip
$ pip install -U wheel
$ pip install FreeTAKServer[ui] - errors
* errors because pyyaml is version 6.0.1, but program wants v6.0 only
```
```
* pip install source locally after tuning module versions
* See: https://www.reddit.com/r/ATAK/comments/husyzl/howto_install_freetakserver_on_a_pi/
$ git clone https://github.com/ForestryAILab/FreeTakServer.git
$ cd FreeTakServer
$ vi setup.py --> "PyYAML==6.0" --> "PyYAML==6.0.1"
vi pyproject.toml --> "PyYAML==6.0" --> "PyYAML==6.0.1"
$ cd ..
$ pip install ./FreeTakServer[ui]
* suscessful install up to libxml2
*       Error: Please make sure the libxml2 and libxslt development packages are installed.
$ pkg install libxml2 textproc/py-libxml2 textproc/libxslt
```
```
$ pip install ./FreeTakServer[ui]
* error
          =============================DEBUG ASSISTANCE=============================
          If you are seeing a compilation error please try the following steps to
          successfully install cryptography:
          1) Upgrade to the latest pip and try again. This will fix errors for most
             users. See: https://pip.pypa.io/en/stable/installing/#upgrading-pip
          2) Read https://cryptography.io/en/latest/installation/ for specific
             instructions for your platform.
          3) Check our frequently asked questions for more information:
             https://cryptography.io/en/latest/faq/
          4) Ensure you have a recent Rust toolchain installed:
             https://cryptography.io/en/latest/installation/#rust
      
          Python: 3.11.7
          platform: FreeBSD-13.2-RELEASE-p8-amd64-64bit-ELF
          pip: n/a
          setuptools: 69.0.3
          setuptools_rust: 1.8.1
          =============================DEBUG ASSISTANCE=============================
      
      error: can't find Rust compiler
      
      If you are using an outdated pip version, it is possible a prebuilt wheel is available for this package but pip is not able to install from it. Installing from the wheel would avoid the need for a Rust compiler.
      
      To update pip, run:
      
          pip install --upgrade pip
      
      and then retry package installation.
      
      If you did intend to build this package from source, try installing a Rust compiler from your system package manager and ensure it is on the PATH during installation. Alternatively, rustup (available at https://rustup.rs) is the recommended way to download and update the Rust compiler toolchain.
      
      This package requires Rust >=1.41.0.
      [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
  ERROR: Failed building wheel for cryptography

$ pkg install rust

      The headers or library files could not be found for jpeg,
      a required dependency when compiling Pillow from source.

$ pkg install py-pillow
$ pip install ./FreeTakServer[ui]


```
