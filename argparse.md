Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]] 
Ref: 
Tags : #public 

--- 

```py
import argparse
```

--- 


argparse_calculator (sentdex)
```py
import argparse #argument parser
import sys
def main():
	parser = argparse.ArgumentParser()
	parser.add_argument('--x', type=float, default=1.0,
		help='What is the first number?')
	parser.add_argument('--y', type=float, default=1.0,
		help='What is the first number?')
	parser.add_argument('--operation', type=str, default='add',
		help='What operation? (add, sub, mul, div)')

	args = parser.parse_args()
	sys.stdout.write(str(calc(args)))
	# brings output to console

def calc(args):
    if args.operation == 'add':
        return args.x + args.y
    elif args.operation == 'sub':
        return args.x - args.y
    elif args.operation == 'mul':
        return args.x * args.y
    elif args.operation == 'div':
        return args.x / args.y
```
```
# $ python 2argparse_sys.py --x=5 --y=2 --operation=mul
# 10.0

# $ python 2argparse_sys.py -h, --help
# usage: 2argparse_sys.py [-h] [--x X] [--y Y] [--operation OPERATION]
# optional arguments:
#   -h, --help            show this help message and exit
#   --x X                 What is the first number?
#   --y Y                 What is the first number?
#   --operation OPERATION
#                         What operation? (add, sub, mul, div)
```
