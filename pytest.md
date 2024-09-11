Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[Python Testing with pytest (Brian Okken)]]
Ref: [docs](https://docs.pytest.org/en/6.2.x/)
Tags: #public 

testing in [[PYTHON]] 

--- 
```pip install pytest```

```assert```

```pytest -v path/to/file/or/directory/ accepts/multiple/paths```
- looks for files starting with **test_** or ending with **\_test** in all subdirectories to run 
- convention: def test_\<name_of_function>, class Test\<Something>
- @pytest.mark.skip() @pytest.mark.skip_if() @pytest.mark.xfail()
- ```pytest -v path/to/test_file.py::test_one_fxn```

```pytest --help```




--- 


