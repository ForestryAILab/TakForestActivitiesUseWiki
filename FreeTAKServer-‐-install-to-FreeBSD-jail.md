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
$ pkg install lang/python311 devel/py-pip bash
$ pkg install devel/py-gevent devel/py-lxml graphics/cairo graphics/py-cairo devel/py-yaml
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

