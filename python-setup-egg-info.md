#### Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-q9jfc54i/psycopg2-binary/
How to fix the pip9.exceptions.InstallationError

Make sure the version of your pip and setuptools is sufficient for manylinux2014 wheels.

* For System Install
```
sudo python3 -m pip install -U pip
sudo python3 -m pip install -U setuptools
```
* For Virtual Env / pipEnv
```
#Within the venv

pip3 install -U pip
pip3 install -U setuptools
```
source : [Stackoverflow](https://stackoverflow.com/questions/64095094/command-python-setup-py-egg-info-failed-with-error-code-1-in-tmp)
