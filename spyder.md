[[PYTHON]]
# spyder
> ------------------------  
> **important note:**  
> use *pipx*!!  
> pipx solves all problems  
> ------------------------  

if there are problems with installing *spyder* with *conda*,
then it can be installed with *pip*
**BUT**  
*conda* and *pip* can not be mixed
 
## install spyder with pip
- create new environement:
    - `conda create -n NAME python=3`
    - `conda activate NAME`
- install spyder:
    - `pip install spyder-kernels`
    - `pip install spyder`
- change the path to python in spyder:
    - find out the path:
        - `conda info --envs`
        - copy the one which leads to your NAME environement
    - `spyder->tools->preferences`
    - `python interpreter->use new python interpreter`
    - enter the new path and add */bin/python* to it
- from now on use ONLY *pip*

## pipenv  
- create a virtual environment (see pipenv)
- install spyder (that easy):
    - `pipenv install spyder`

**BUT**
it's a bit messy to start spyder from *one* virtual environment
in order to program in *another* virtual environment.  

## pipx  
pipx solves all problems!  
- install pipx
- install spyder globally but contained at the same time:
    - `pipx install spyder`


