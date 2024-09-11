Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[pip]], [[setuptools]]; [[open source license]]
Ref: https://www.pypa.io/en/latest/
- https://betterscientificsoftware.github.io/python-for-hpc/tutorials/python-pypi-packaging/
- -> https://pypi.org/
- ... https://packaging.python.org/guides/using-manifest-in/#using-manifest-in
- https://test.pypi.org/

--- 
https://packaging.python.org/tutorials/packaging-projects/
[.../including other files]()https://packaging.python.org/tutorials/packaging-projects/#including-other-files \# ignoring ts for now...

--- 
```pip install twine```
```python setup.py bdist_wheel```
```twine upload --repository testpypi dist/*```

```git commit -m "-> pnbp==0.8.6 (https://pypi.org/project/pnbp/)"```


--- 
nb <- https://github.com/psf/requests/blob/master/requests/__version__.py

```py
# <p>
__title__ = 'pnbp'
__description__ = 'pretty notebook parser'
__url__ = 'https://github.com/prettynb'
__version__ = '0.8.0'
__build__ = 0x111000 
__author__ = 'Ellenurb Sitruc'
__author_email__ = 'ellenurbsitruc@gmail.com'
__license__ = 'MIT License'
__copyright__ = 'Copyright (c) 2021 prettynb'
# <script>
__cake__ = None #\\ nb <- https://github.com/psf/requests/blob/master/requests/__version__.py
# </script>
# </p>
```







