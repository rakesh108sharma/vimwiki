[[INDEX]]
# PYTHON
A wiki for my python _studies_

## virtual environments
### env
- create a virtual environment:
    - `python3 -m venv PROJECTNAME`
    - `source PROJECTNAME/bin/activate`
    - *OR* vreate an env in a directory and call it 'venv':
        - `mkdir PROJECTNAME`
        - `python3 -m venv PROJECTNAME/venv`
        - `source PROJECTNAME/venv/bin/activate`  
*DO NOT* put your project files within the virtual-environment-folder.
(here it would be the *PROJECTNAME* OR *PROJECTNAME/VENV* folders)
*ALSO:* when using git, put the env-foolder in your *.gitignore*

- deactivate env:
    - `deactivate`
- install some usefull stuff:
    - `pip install requests`
    - `pip instal  pytz`
    - `pip list`
- make an install list of the current pip install:
    - `pip freeze > requirements.txt`
- make an env from requirements.txt:
    - `pip install -r requirements.txt`

### pipenv  
pipenv is now the preferred method.  
 
- create a new project:
    - create PROJECT folder
    - within the PROJECT folder, create a hidden **.venv** folder
    - `pipenv`
- installing packages:
    - you have to be within the PROJECT folder
    - `pipenv install PACKAGE`
- uninstalling packages:
    - `pipenv uninstall PACKAGE`
- updating all packages:
    - `pipenv update`
- enter the virtual environment:
    - `pipenv shell`
- run a program out of the virtual environment without entering it:
    - `pipenv run PROGRAM`


### conda (anaconda)

## Index
* [qtile](qtile.md)
* [linters & fixers](linters & fixers.md)
* [spyder](spyder.md)
* 
