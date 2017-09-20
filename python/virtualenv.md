#### install Virtualenv
`pip install virtualenv`

#### basic usage for virtualenv
```
tommy@hzloni01:~/Work/python$ virtualenv ENV
New python executable in /home/tommy/Work/python/ENV/bin/python
Installing setuptools, pip, wheel...done.
tommy@hzloni01:~/Work/python$ cd ENV/
tommy@hzloni01:~/Work/python/ENV$ ls
bin  include  lib  local  pip-selfcheck.json
tommy@hzloni01:~/Work/python/ENV$
```
##### lib
all installed python libs will be installed in `lib/python[x.x]/site-package`
##### bin
`bin/python`: the interpreter of current env

#### active virtualenv
`source ./bin/activate` to active virtualenv

#### exit for virtualenv
`deactivate`

#### set python version for virtualenv
use `-p PYTHON_EXE` to set python version when create virtual env
for example, use `virtualenv -p /usr/bin/python2.7 ENV2.7` to create a python2.7 env in ENV2.7