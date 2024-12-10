### Environment
```
python -m venv .venv
```
create local environment in folder .venv.
```
source .venv/bin/activate[.<shell>]
```
activate local environment.
```
deactivate
```
deactivate local environment.
___
### Packages
```
pip list
```
list installed packages.
```
pip list --outdated
```
list outdated installed packages.
```
pip install <package>
```
install a package.
```
pip install -r requirements.txt
```
install required packages.
```
pip freeze > requirements.txt
```
generate list of required packages.
```
pip install --upgrade <package>
```
upgrade a package.
___
### Notebooks
```
pip install notebook
```
install Jupyter notebook.
```
jupyter notebook [<file>]
```
run Jupyter notebook.