# Python Packaging

- [ ] In your `__init__.py` files export that classes and functions you want to export.
- [ ] Create a pypi account
- [ ] upload your package to github.com
- [ ] create the files pypi requires
  - setup.py
  - setup.cfg
  - LICENSE
  - README
- [ ] Upload the package to pypi
- [ ] Maintain package

## __init__.py file

Dir structure:
```
MyLib
-__init__.py
-File1.py
-File1.py
```
__init__.py
```python
# Inside of __init__.py
from MyLib.File1 import ClassA, ClassB, ClassC
from MyLib.File2 import ClassX, ClassY, ClassZ
```

## Pypi Required Files

setup.py:
```python
from distutils.core import setup
setup(
  name = 'YOURPACKAGENAME',         # How you named your package folder (MyLib)
  packages = ['YOURPACKAGENAME'],   # Chose the same as "name"
  version = '0.1',      # Start with a small number and increase it with every change you make
  license='MIT',        # Chose a license from here: https://help.github.com/articles/licensing-a-repository
  description = 'TYPE YOUR DESCRIPTION HERE',   # Give a short description about your library
  author = 'YOUR NAME',                   # Type in your name
  author_email = 'your.email@domain.com',      # Type in your E-Mail
  url = 'https://github.com/user/reponame',   # Provide either the link to your github or to your website
  download_url = 'https://github.com/user/reponame/archive/v_01.tar.gz',    # I explain this later on
  keywords = ['SOME', 'MEANINGFULL', 'KEYWORDS'],   # Keywords that define your package best
  install_requires=[            # I get to this in a second
          'validators',
          'beautifulsoup4',
          'numpy',
          'Django',
      ],
  classifiers=[
    'Development Status :: 3 - Alpha',      # Chose either "3 - Alpha", "4 - Beta" or "5 - Production/Stable" as the current state of your package
    'Intended Audience :: Developers',      # Define that your audience are developers
    'Topic :: Software Development :: Build Tools',
    'License :: OSI Approved :: MIT License',   # Again, pick a license
    'Programming Language :: Python :: 3',      #Specify which pyhton versions that you want to support
    'Programming Language :: Python :: 3.4',
    'Programming Language :: Python :: 3.5',
    'Programming Language :: Python :: 3.6',
  ],
)
```
- `download_url` -- You have previously uploaded your project to your github repository. Now, we create a new release version of your project on github. This release will then be downloaded by anyone that runs the “pip install YourPackage” command.
- `install_requires` -- Here, you define all the dependencies your package has — all the pip packages that you are importing.

setup.cfg
```
# Inside of setup.cfg
[metadata]
description-file = README.md
```

## Uploading the package to pypi

Now, we create a source distribution with the following command:
```
$ python setup.py sdist
```
We will need twine for the upload process, so first install twine via pip:
```
$ pip install twine
```
Then, run the following command:
```
$ twine upload dist/*
```
You will be asked to provide your username and password. Provide the credentials you used to register to PyPi earlier.

## Maintain Package

Simply upload your new code to github, create a new release, then adapt the setup.py file (new download_url — according to your new release tag, new version), then run the setup.py and the twin command again (navigate to your folder first!)
```
python setup.py sdist
twine upload dist/*
```
Finally, update your package via pip to see whether your changes worked:
```
pip install YOURPACKAGE --upgrade
```