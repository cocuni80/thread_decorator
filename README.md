# Thread Decorator
Simple parallel processing interface for python

## Why?
Python's built in parallel processing and threading library is pretty simple to implement but sometimes you just want to chuck data at a function and make it run faster

## Requirements
Python 3+

## Installation
```shell
$ pip install thread_decorator
```

## Quickstart
Use the `threaded` decorator to turn a method into a threaded method.
```python
@threaded()
def my_func():
    '''Your Code'''
```

Alternatively, use `run_threaded` function
```python
run_threaded(my_func)
```

Both the `threaded` decorator and `run_threaded` method will return an instance of
`ResultThread`. This allow you to optionally wait for the function to finish executing 
and get the return value. To get the return value, use `.await_output()`
```python
result = threaded_print()
result.await_output()  # this will return 1
```

If you have a function that needs to execute on a large list of data, use `run_chunked`
```python
def update_items(items):
    ...

items = [...]
run_chunked(update_items, items)
```
`.await_output()` also work with `run_chunked` but will return a list of return values instead

## Run the tests
Run tests with
```python
python tests.py
```

## Todo
- [x] threaded function decorator
- [x] run something in a separate thread function
- [x] split data into chunk and run in separate threads
- [ ] add way for errors to fail loudly
- [ ] auto spawn to run fx on a set of data
- [ ] explore multi processing?