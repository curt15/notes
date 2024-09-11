Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python 3rd party packages]]
Ref: 

--- 

PyPy - python implemented in python
Rpython- small subset of python library that pypy uses to implement the python intreperter 

def main(argv):
    pass

If name == main:
    import sys 
    main(sys.argv)


Add: 
def target(*args):
    return main, None

translate.py -> c code 


pypy translates itself using its own byte code interpreter 