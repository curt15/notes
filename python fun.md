Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python bs]]
Ref: 
Tags: #public 


--- 

**cards.py**

```py
from collections import namedtuple
import random


# Card = namedtuple('Card', ['suit', 'value'])

class Card(namedtuple('Card', ['suit', 'value'])):

	def __str__(self):
		return f'{self.value} of {self.suit}'

	def __repr__(self):
		return f'Card({self.value}, {self.suit})'



class Std52:
	"""
	J spades & J hearts = One-eyed Royals
	J diamonds = "laughing boy"
	"""
	def __init__(self):

		self.suits = ['clubs', 'diamonds', 'hearts', 'spades']
		self.deck = []
		for suit in self.suits:
			self.deck.append(Card(suit=suit, value='Ace'))
			for n in range(2,11):
				self.deck.append(Card(suit=suit, value=n))
			for f in ('Jack', 'Queen', 'King'):
				self.deck.append(Card(suit=suit, value=f))


	def shuffle(self):
		""" overly robotic *actual* mechanical card deck shuffle """

		freshly_ordered_deck = []
		num_cards = len(self.deck)
		top_stack = self.deck[int(num_cards/2):]
		bottom_stack = self.deck[:int(num_cards/2)]

		for n in range(0, num_cards):
			if n % 2 == 0:
				freshly_ordered_deck.append(top_stack.pop())
			else:
				freshly_ordered_deck.append(bottom_stack.pop())

		self.deck = freshly_ordered_deck


	def shuffle_x(self, times: int):
		for i in range(0, times):
			self.shuffle()


```

--- 

**dsix.py**

```py
def dsix(num_dice, countsix=False):
	"""
	Return a list of random d6 dice outputs.
	
	param num_dice: number of dice to roll
	param countsix: (also) returns a count of 6's outputted
	"""
	die_outputs = [random.randint(1,6) for _ in range(number_of_dice)]

	if countsix == True:
		return sum([1 for x in dieList if x==6])
    return 
```

--- 

**mbti.py**

```py
from collections import namedtuple

Term = namedtuple('Term', ['verbose', 'abbv'])


attitudes = [
	Term(verbose='Introverted', abbv='i'),
	Term(verbose='Extroverted', abbv='e')
	]

phenomena = [
	Term(verbose='Thinking', abbv='T'),
	Term(verbose='Feeling', abbv='F'),
	Term(verbose='Sensing', abbv='S'),
	Term(verbose='iNtuition', abbv='N'),
	]


functions = []
for p in phenomena:
	for a in attitudes:
		functions.append(Term(verbose=f'{a.verbose} {p.verbose}', abbv=f'{p.abbv}{a.abbv}'))



types16 = {
	'ISTP': 'Ti/Se/Ni/Fe', 
	'INTP': 'Ti/Ne/Si/Fe', 
	'ISFP': 'Fi/Se/Ni/Te',
	'INFP': 'Fi/Ne/Si/Te',

	'INFJ': 'Ni/Fe/Ti/Se',
	'INTJ': 'Ni/Te/Fi/Se',
	'ISFJ': 'Si/Fe/Ti/Ne',
	'ISTJ': 'Si/Te/Fi/Ne',
	
	'ESTP': 'Se/Ti/Fe/Ni',
	'ESFP': 'Se/Fi/Te/Ni',
	'ENTP': 'Ne/Ti/Fe/Si',
	'ENFP': 'Ne/Fi/Te/Si',
	
	'ESTJ': 'Te/Si/Ne/Fi',
	'ENTJ': 'Te/Ni/Se/Fi',
	'ENFJ': 'Fe/Ni/Se/Ti',
	'ESFJ': 'Fe/Si/Ne/Ti',
}

for t, f in types16.items():
	types16[t] = {i+1: x for i,x in enumerate(f.split('/'))}




class MBTIType:
	def __init__(self, name, lettercode):
		self.name = name
		# self.fxns = 


for p in phenomena:
	pass
```