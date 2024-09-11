Links: [[PYTHON]] - [[PROGRAMMING]]
Rel:
Ref: [docs](https://sly.readthedocs.io/en/latest/sly.html#writing-a-parser); [github](https://github.com/dabeaz/sly)

SLY (Sly Yex Yack) 

--- 
```pip install sly```

--- 

[David Beazley - Reinventing the Parser Generator - PyCon 2018](https://youtu.be/zJ9z6Ge-vXs?t=614) 

linguistic abstraction - essentially making your own programming language to the problem domain.

Tokenizer - lexing - breaking into tokens (tokenizing)
Parser - parsing the grammar (syntactic analysis)
-> abstract syntax trees

--- 

tparser.py 
```
from sly import Lexer, Parser

# 

class TrainingLexer(Lexer):
	tokens = {EXERCISE, NUMBER, MULTINUM, BY, SEP}
	# ignore = ' '

	EXERCISE = r'([a-zA-Z\s()&?]+)'
	MULTINUM = r'(\d+,)+(\d+)'
	NUMBER = r'\d+'
	# MULTI = r','

	# def MULTINUM(self, t):
	# 	t.value = [t.group[1] + t.group[2]]
	# 	return t


	# BY = r'x'
	EXERCISE['x'] = BY

	EXERCISE[r' '] = SEP
	

lexer = TrainingLexer()


class TrainingParser(Parser):
	tokens = TrainingLexer.tokens

	def __init__(self):
		pass
	# 	self.exercise = None
	# 	self.sets = None
	# 	self.reps = []
	# 	self.wts = []

	# @_('EXERCISE expr BY expr expr')
	# def statement(self, p):
	# 	self.exercise = p.EXERCISE.rstrip()
	# 	self.sets = p.expr0
	# 	self.reps = [p.expr1]
	# 	self.wts = [p.expr2]
	# 	return self.exercise, self.sets, self.reps, self.wts

	# @_('EXERCISE expr BY expr SEP expr')
	# def statement(self, p):
	# 	self.exercise = p.EXERCISE.rstrip()
	# 	self.sets = p.expr0
	# 	self.reps = [m for m in p.expr1]
	# 	self.wts = [p.expr2]
	# 	return self.exercise, self.sets, self.reps, self.wts


	@_('EXERCISE expr')
	def statement(self, p):
		return ('SETS', p.expr)


	@_('expr BY expr')
	def statement(self, p):
		return ('REPS', p.expr)

	@_('SEP expr')
	def statement(self, p):
		return ('WTS', p.expr)

	# @_('expr')
	# def expr(self, p):
	# 	return p.expr

	# @_('expr MULTI expr')
	# def multiexpr(self, p):
	# 	return [p.expr0, p.expr1]

	@_('EXERCISE')
	def expr(self, p):
		return ('EXERCISE', p.EXERCISE.rstrip())

	@_('NUMBER')
	def expr(self, p):
		return int(p.NUMBER)

	@_('MULTINUM')
	def expr(self, p):
		nums = [int(n) for n in p.MULTINUM.split(',')]
		return nums

	@_('SEP')
	def expr(self, p):
		return p.SEP

	@_('BY')
	def expr(self, p):
		return p.BY

	# @_('expr MULTI expr MULTI expr')
	# def expr(self, p):
	# 	return [p.expr0, p.expr1]


parser = TrainingParser()

expression = 'Bench Press 3x10 225,235,245'
for tok in lexer.tokenize(expression):
	print(tok)

parser.parse(lexer.tokenize(expression))




"""
exercisestr = r'([a-zA-Z\s()&?]+)\s'
needsaverage = r'(\d+\.?\d?)-(\d+\.?\d?)'
setsreps = r'[\s](\d+)x(\d+)'
changing_reps = r'[\s](\d+)x(\d,\d,?\d?,?\d?,?\d?)'

indicators = r',[^0-9\s,]+'
comments = r'\(.+\)'
full_comments = r'\(.*'
notes = r'\[.*\]'

exercisetxt = re.sub(exercisestr, r'\1, ', exercisetxt)
exercisetxt = re.sub(notes, r'', exercisetxt)
exercisetxt = re.sub(changing_reps, lambda x: str(' {}'.format(x.group(1)) + ', [' + x.group(2).replace(',', ' ') + '], '), exercisetxt)
exercisetxt = re.sub(needsaverage, lambda x: str(round((float((x.group(1)))+(float(x.group(2))))/2)), exercisetxt)
exercisetxt = re.sub(setsreps, r' \1,\2,', exercisetxt)
exercisetxt = re.sub(indicators, r'', exercisetxt)
exercisetxt = re.sub(comments, r'', exercisetxt)
exercisetxt = re.sub(full_comments, r'', exercisetxt)
"""
```

--- 
