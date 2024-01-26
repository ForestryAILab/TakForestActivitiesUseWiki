FreeTAKServer - install to FreeBSD jail
---------------------------------------
See: https://freetakteam.github.io/FreeTAKServer-User-Docs/Installation/Linux/Installation/
  Follow the Linux --> Ubuntu thread

References:
https://docs.freebsd.org/en/books/handbook/
https://freetakteam.github.io/FreeTAKServer-User-Docs/
https://pypi.org/project/FreeTAKServer/
https://docs.freebsd.org/en/books/developers-handbook/tools/
https://docs.freebsd.org/en/books/developers-handbook/tools/https://www.pythonhelp.org/learn/introduction/setting-up-development-environment-freebsd/
https://computingforgeeks.com/how-to-install-pip-python-package-manager-on-freebsd-12/

* Work inside jail from now on
# bastille console FreeTakServer

* Install dependencies into jail
* Ubuntu dependencies:
* sudo apt update && sudo apt install python3 && sudo apt install python3-pip
* sudo apt install python3-dev python3-setuptools build-essential python3-gevent python3-lxml libcairo2-dev

* 
* consult freshports to find FreeBSD equivalents
* or use $ pkg search  

* Ubuntu ==> FreeBSD
* python3 ==> lang/python311
* python3-pip ==> devel/py-pip
* python3-dev ==> ??
* python3-setuptools ==> py39-setuptools (already install) 
* build-essential ==> gcc or clang development environment (clang already installed)
* python3-gevent ==> devel/py-gevent
* python3-lxml ==> devel/py-lxml
* libcairo2-dev ==> graphics/cairo (?? py39-cairo)

# pkg install pkg
# pkg install lang/python311 devel/py-pip 
# pkg install devel/py-gevent devel/py-lxml graphics/cairo


* Create user freetakserver 

* Switch to freetakserver user

