FreeTAKServer - install to FreeBSD jail
---------------------------------------
* Work inside jail from now on
# bastille console FreeTakServer

* Install dependencies into jail
* Ubuntu dependencies:
* sudo apt update && sudo apt install python3 && sudo apt install python3-pip
* sudo apt install python3-dev python3-setuptools build-essential python3-gevent python3-lxml libcairo2-dev

* https://www.pythonhelp.org/learn/introduction/setting-up-development-environment-freebsd/
* consult freshports to find FreeBSD equivalents
# pkg install pkg
* current freebsd 13.2 python is 3.9 
# pkg install python py39-pip 

py39-dev


* Create user freetakserver 

* Switch to freetakserver user

