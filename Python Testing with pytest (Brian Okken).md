Links: [[PROGRAMMING]]
Tags: #book 
Ref: cmd + shift + B to open Books.app
Rel:  [[python]] - [[pytest]]

--- 

**CHAPTER 2:**

With a *setup.py* file, can local pip install
**pip install -e ./tasks_proj/**   # the -e flag 'editable' allows file changes to occur in the installed package

Using the **assert** keyword, any expression that would return a bool False will Fail

">" points out the actual lines of code (assert statements) failing

```py
@pytest.mark.get
@pytest.mark.smoke
def test_get_raises():
    """get() should raise an exception with wrong type param."""
    with **pytest.raises(TypeError)**:  # next block of code should produce a TypeError:
        tasks.get(task_id='123')


def test_start_tasks_db_raises():
    """Make sure unsupported db raises an exception."""
    with **pytest.raises(ValueError) as excinfo**:  # allows to check exception message 
        tasks.start_tasks_db('some/great/path', 'mysql')
    exception_msg = excinfo.value.args[0]
    assert exception_msg == "db_type must be a 'tiny' or 'mongo'"
```

“**Smoke tests** are by convention not all-inclusive, thorough test suites, but a select subset that can be run quickly and give a developer a decent idea of the health of all parts of the system.”

pytest -v -m get test_api_exceptions.py 
pytest -v -m smoke test_api_exceptions.py 
pytest -v -m 'smoke and get' test_api_exceptions.py
pytest -v -m 'smoke and not get' test_api_exceptions.py



```
@pytest.fixture(autouse=True)
def initialized_tasks_db(tmpdir):
    """Connect to db before testing, disconnect after."""
    # Setup : start db
    tasks.start_tasks_db(str(tmpdir), 'tiny')

    yield  # this is where the testing happens

    # Teardown : stop db
    tasks.stop_tasks_db()
```

**tmpdir** is a builtin Fixture (ch 4)
**autouse** is a builtin Fixture parameter
Code before **yield** runs before the test, code after runs after. This function just sets up and then tears down the database connection (used during testing).




**@pytest.mark.skip(reason= 'misunderstood the API' )**
^^ use the skip mark to pass over tests 

@pytest.mark.**skipif(tasks.__version__ <  '0.2.0' ,
 	                    reason= 'not supported until version 0.2.0' )**
^^ use the skipif to conditionally mark to pass over tests

“pytest **-rs** test_unique_id_3.py # -r + -s to get "reasons skipped" in output

**@pytest.mark.xfail()** when expected to fail 




pytest -v tests/func/test_add.py **::test_add_returns_valid_id**
**^^ run a single test function**


```
class TestUpdate():
	pass
```
^^ group tests occuring to the **update() function** into a single class
^^ **pytest -v tests/func/test_api_exceptions.py::TestUpdate** # run a single test class
^^ pytest -v tests/func/test_api_exceptions.py::TestUpdate **::test_bad_id** # add another :: to drill into a specific test method to run


Grouping Syntax Shown by Verbose Listing:
“Remember that the syntax for how to run a subset of tests by directory, file, function, class, and method doesn’t have to be memorized. The format is the same as the test function listing when you run **pytest -v.**”



The **-k option** enables you to pass in an expression to run tests that have certain names specified by the expression as a substring of the test name. You can use and, or, and not in your expression to create complex expressions.
^^ pytest -v **-k** **_raises**  # run all tests with "_raises" in definition
^^ pytest -v **-k** **' _raises and not delete' **




___________________________________________________________

**CHAPTER 1:**
Unit test: An isolated test (like on a function or class).

Integration test: A test on larger bit of code (several classes or a subsystem).

System test (end-to-end): A test that checks the entire system in an environment as close to the end-user environment as possible.

Functional test: A test on a single bit of functionality in the system. (e.g. how we will add or delete or update a task item in Tasks)



pip install pytest

pytest code/ch1/test_one.py
pytest code
pytest 
pytest -v 
pytest -v code/ch1/tasks/test_four.py::test_asdict # run a single test
pytest --help # list options

pytest -k "asdict or defaults" --collect-only # using -k EXPRESSION to filter specific tests



Test files must be named **test_**something.py
OR something**_ test**.py to be discovered by pytest.

Test methods and functions should be named **test_**something.

Test classes should be named **Test**Something.



A test *session* is a single invocation of pytest including the tests run in potentially multiple subdirectories. 


rootdir: the topmost comon directory to all of the directories being searched for test code.
The **inifile**lists the configuration file being used (can be pytest.ini, tox.ini, or setup.cfg).

F  -  failures (the test did not run successfully (or XPASS + strict)
E  - errors (an Exception happened outside the test function, in either a Fixture or Plugin)
s  - skips (was skipped with something like the **@pytest.mark.skipif()** decorator)
x  - xfails (the test was not suppose to pass -> ran, and failed. **@pytest.mark.xfail()**
X  - xpasses (the test was not supposed to pass -> ran, and passed.) 


**-m MARKER**

import pytest

@pytest.mark.run_these_please
@pytest.mark.this_is_my_mark_to_run_this

pytest -m run_these_please
pytest -m "mark1 and mark2"
pytest -m "mark1 and not mark2" # if multiple marks on tests



**-x, --exitfirst** stops the entire test when reaching a failed assert 
**--tb=no** turns off the stacktrace (when already seen and don't need to again)
**--maxfail=num** lets num number of fails to occur before exiting on -x
**-s** flag allows print statements to stdout while testing (useful to add print() statements to watch watch test flow) and **--capture=method** --capture=no is equivalent to -s.
**--capture=sys** replaces sys.std-out/stderr with in-mem files. **--capture=fd** points file descripters 1 and 2 to a temp file. 

**--lf, --last-failed**runs just the recent failed tests
**--ff, --failed-first** runs the recent failed -> runs the rest of the previous passing tests
**-q, --quiet** is the opposite of **-v, --verbose**; is nice in conjunction with **-tb=line** to report only the failing line of code

**-l, --showlocals** shows local vars and values w/ the traceback of failing tests.

**--tb=style**
=short prints just the assert and E evaluated line with no context; =line keeps the failure to one line, =no removes the traceback entirely; =long give most exhaustive traceback; =auto gives long version for first and last (if you have multiple failures), =native gives standard lib traceback and no extra information

**--durations=N** pytest --durations=3 tasks # show slowest 3x tests 

Each test has a call -> setup -> teardown phases
setup and teardown aree called Fixtures (a chance to add code to get data or the software system that is under test) 

**-h, --help** (a) cli options/flags (b) ini style conf options (c) environment variables, (d) **pytest --markers** and (e) **pytest --fixtures** to view available options.
pytest can take **conftest.py** files that can include hook functions that create new options, fixture definitions, and marker definitions. 



