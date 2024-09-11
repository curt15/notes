Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: 
Ref: [docs](https://click.palletsprojects.com/en/8.0.x/); [complex applications](https://click.palletsprojects.com/en/8.0.x/complex/); [values from environment variables](https://click.palletsprojects.com/en/8.0.x/options/#values-from-environment-variables)Tags: #public 

command-line interfaces 

--- 
```pip install click```

--- 

```py
import click
```

```pip install --editable .```

--- 

hello.py
```
import click

@click.command()
@click.option('--count', default=1, help='Number of greetings.')
@click.option('--name', prompt='Your name',
              help='The person to greet.')
def hello(count, name):
    """Simple program that greets NAME for a total of COUNT times."""
    for x in range(count):
        click.echo('Hello %s!' % name)

if __name__ == '__main__':
    hello()
```

groups:
```py
import click

@click.group()
def cli():
	pass

@click.command()
@click.option('--count', default=1, help='Number of greetings.')
@click.option('--name', prompt='Your name',
              help='The person to greet.')
def hello(count, name):
    """Simple program that greets NAME for a total of COUNT times."""
    for x in range(count):
        click.echo('Hello %s!' % name)

@click.command()
def helloworld():
	click.echo('Hello World')


cli.add_command(hello)
cli.add_command(helloworld)

if __name__ == '__main__':
    cli()
```

--- 

how does the pass context work???

```py
class Something:
	def __init__(self, name='something', etc=None):
		self.name = name
		self.etc = etc
		print('Something.__init__() !!!')


	

pass_sm = click.make_pass_decorator(Something, ensure=True)

@click.command()
@pass_sm
def sampl(sm):
	print(sm)

@click.command()
@pass_sm
def sampl2(sm):
	print(sm)
	sampl(sm)


TypeError: 'Something' object is not iterable
-> sm=sm ...
TypeError: __init__() got an unexpected keyword argument 'sm'
```

--- 
setattr reqirement for any meta-defined commands
```py
	# setattr(sys.modules[__name__], 'attr1', 'attr1')

```