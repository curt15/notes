Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[Sentdex]]; [[NLTK]]

--- 


installing:
```
import nltk
>>> nltk.download()
```
- brings up the “NLTK downloader” for managing packages
- stored Users/name/nltk_data

**tokenizing**:
```
from nltk.tokenize import sent_tokenize, word_tokenize

example_text = "Hello Mr. Smith, how are you doing today? The weather is great and Python is awesome. The sky is pinkish-blue. You should not eat cardboard."

# print(sent_tokenize(example_text))
# print(word_tokenize(example_text))

for i in word_tokenize(example_text):
	print(i)
```

**stopwords**:
- Stop words are words you filter out (e.g. scarcastic words), fluff words (a, the, and, ...) that are useless to data analysis, etc.
- print(stopwords) - to see the *list* of used common in nltk
```
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

example_sentence = "This is an example showing off stop word filtration."
stop_words = set(stopwords.words('english'))

words = word_tokenize(example_sentence)

filtered_sentence = []

for w in words:
	if w not in stop_words:
		filtered_sentence.append(w)

# or a one-liner:
# filtered_sentence = [w for w in words if not w in stop_words]

print(filtered_sentence)
```

**stemming**:
Form of data pre-processing of taking the root stem
e.g. "riding" stem = "rid-"
where "rid-" can be "ride, riding, ridden, ..."

Useful where meaning of the word is unchanged:
- I was taking a ride in the car.
- I was riding in the car.
```
from nltk.stem import PorterStemmer
from nltk.tokenize import word_tokenize

ps = PorterStemmer()

example_words = ["python", "pythoner", "pythoning", "pythoned", "pythonly"]

# for w in example_words:
	# print(ps.stem(w))


new_text = "It is very import to be pythonly while you are pythoning with python. All pythoners have pythoned poorly at least once."
words = word_tokenize(new_text)

for w in words:
	print(ps.stem(w))
```

**part of speech tagging**:
```
import nltk
from nltk.corpus import state_union
# state of the union addresses by pres from 60+yrs
from nltk.tokenize import PunktSentenceTokenizer
# unsupervised machine learning sentance tokenizer
# pretrained, but you can train yourself

train_text = state_union.raw("2005-GWBush.txt")
sample_text = state_union.raw("2006-GWBush.txt")

custom_sent_tokenizer = PunktSentenceTokenizer(train_text)

tokenized = custom_sent_tokenizer.tokenize(sample_text)

def process_content():
	try:
		for i in tokenized:
			words = nltk.word_tokenize(i)
			tagged = nltk.pos_tag(words)
			# after you tokenize by word, can pass into pos_tagging

			print(tagged)

	except Exception as e:
		print(str(e))

process_content()
```

**chunking**:
```
import nltk
from nltk.corpus import state_union
from nltk.tokenize import PunktSentenceTokenizer
# continued from 4partofspeechtagging.py

train_text = state_union.raw("2005-GWBush.txt")
sample_text = state_union.raw("2006-GWBush.txt")

custom_sent_tokenizer = PunktSentenceTokenizer(train_text)

tokenized = custom_sent_tokenizer.tokenize(sample_text)

def process_content():
	try:
		for i in tokenized:
			words = nltk.word_tokenize(i)
			tagged = nltk.pos_tag(words)

			chunkGram = r"""Chunk: {<RB.?>*<VB.?>*<NNP>+<NN>?}"""
			# 'Chunk:' can be called whatever you want.
			# <RB.?> POS Adverb
			# followed by (re identifier of) any character except new line
			# ? = 0 or 1 of them
			# * = match 0 or more
			# <NNP> without the * is required. With a + becomes one or more (Chunks PRESIDENT GEORGE W. BUSH together)
			chunkParser = nltk.RegexpParser(chunkGram)
			chunked = chunkParser.parse(tagged)
			print(chunked) #shows ugly chunked in terminal
			chunked.draw() #shows tree (why working w/o matplotlib?)


	except Exception as e:
		print(str(e))



process_content()
```

**chinking**:
Chinking = removing something from a chunk.
```
import nltk
from nltk.corpus import state_union
from nltk.tokenize import PunktSentenceTokenizer
# continued from 5chunking.py

train_text = state_union.raw("2005-GWBush.txt")
sample_text = state_union.raw("2006-GWBush.txt")

custom_sent_tokenizer = PunktSentenceTokenizer(train_text)

tokenized = custom_sent_tokenizer.tokenize(sample_text)

def process_content():
	try:
		for i in tokenized:
			words = nltk.word_tokenize(i)
			tagged = nltk.pos_tag(words)

			chunkGram = r"""Chunk: {<.*>+}
									}<VB.?|IN|DT|TO>+{""" 
									# denote a chink with }{ and add the POS + re to remove
									
			chunkParser = nltk.RegexpParser(chunkGram)
			chunked = chunkParser.parse(tagged)

			print(chunked)
			chunked.draw()


	except Exception as e:
		print(str(e))

process_content()
```

**named identity recognition**:

NE TYPE - Examples:

ORGANIZATION - Georgia-Pacific Corp., WHO
PERSON - Eddy Bonte, President Obama
LOCATION - Murray River, Mount Everest
DATE - June, 2008-06-29
TIME - two fifty a m, 1:30 p.m.
MONEY - 175 million Canadian Dollars, GBP 10.40
PERCENT - twenty pct, 18.75 %
FACILITY - Washington Monument, Stonehenge
GPE - South East Asia, Midlothian

```
import nltk
from nltk.corpus import state_union
from nltk.tokenize import PunktSentenceTokenizer

train_text = state_union.raw("2005-GWBush.txt")
sample_text = state_union.raw("2006-GWBush.txt")

custom_sent_tokenizer = PunktSentenceTokenizer(train_text)

tokenized = custom_sent_tokenizer.tokenize(sample_text)

def process_content():
	try:
		for i in tokenized:
			words = nltk.word_tokenize(i)
			tagged = nltk.pos_tag(words)

			namedEnt = nltk.ne_chunk(tagged)
			# namedEnt = nltk.ne_chunk(tagged, binary=True)
			# setting binary=True finds as NE vs specific types below
			namedEnt.draw()

	except Exception as e:
		print(str(e))

process_content()
```

Lemmatizing:
- similar to stemming,
but will return an actual word with meaning

e.g. the "lemma" for run, runs, ran, and running = run

default for pos="n"

```
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()

# print(lemmatizer.lemmatize("cats"))
# print(lemmatizer.lemmatize("cacti"))
# print(lemmatizer.lemmatize("geese"))
# print(lemmatizer.lemmatize("rocks"))
# print(lemmatizer.lemmatize("python"))

print(lemmatizer.lemmatize("better", pos="a")) #with pos as adj, returns good
print(lemmatizer.lemmatize("best", pos="a"))
print(lemmatizer.lemmatize("run"))

print(lemmatizer.lemmatize("run", pos="v"))
```

Corpora:
- A body of texts generally grouped by some sort of
defining chartacteristic

can be found in Users/name/nltk_data/corpora/
```
from nltk.corpus import gutenberg
from nltk.tokenize import sent_tokenize

sample = gutenberg.raw("bible-kjv.txt")
# As most are txt files the .raw method of extraction is typical

tok = sent_tokenize(sample)

print(tok[5:15])
```

**WordNet** is more of a giant Lexicon vs a Corpora.

**Synsets** are:
- Used for rewriting things like with paper writing services
- Used by schools in reverse to find cheaters

- Used by bots to scrape news, rewrite, and post
- Used by "google" to find via the opposite
```
from nltk.corpus import wordnet

syns = wordnet.synsets("program")

# syns are synonyms
print(syns)

# can retrive:
# individual synset
print(syns[0].name())

# just the word itself
print(syns[0].lemmas()[0].name())

# definition
print(syns[0].definition())

# examples in context
print(syns[0].examples())

print('\n')
########################


synonyms = []
antonyms = []

for syn in wordnet.synsets("good"):
	for l in syn.lemmas():
		synonyms.append(l.name())
		if l.antonyms():
			antonyms.append(l.antonyms()[0].name())

print(set(synonyms))
print('')
print(set(antonyms))

print('\n')
#############################


w1 = wordnet.synset("ship.n.01")
w2 = wordnet.synset("boat.n.01")

# wup stands for "Wu and Palmer"
# they wrote a paper on semantic similarity
print(w1.wup_similarity(w2))
# returns: 0.9090909090909091, meaning 90% similar

w1 = wordnet.synset("ship.n.01")
w2 = wordnet.synset("car.n.01")

print(w1.wup_similarity(w2)) #69%

w1 = wordnet.synset("ship.n.01")
w2 = wordnet.synset("cat.n.01")

print(w1.wup_similarity(w2)) #32%
```
--- 

--- 


--- 

#### PROJECT

1. Words as Features for Learning:
```
import nltk
import random
from nltk.corpus import movie_reviews
# continued from 11textclassification.py

documents = [(list(movie_reviews.words(fileid)), category)
              for category in movie_reviews.categories()
              for fileid in movie_reviews.fileids(category)]

random.shuffle(documents)

all_words = []
for w in movie_reviews.words():
	all_words.append(w.lower())

all_words = nltk.FreqDist(all_words)

# checking against the keys (not worried about freq here) of top 3000 words
word_features = list(all_words.keys())[:3000]

def find_features(document):
	words = set(document)
	features = {}
	for w in word_features:
		# in this features dict, the key (that is the word in the list of 3000 most freq words)
		# is the boolean value (True or False) of whether or not it is in this document
		features[w] = (w in words)

	return features

print((find_features(movie_reviews.words('neg/cv000_29416.txt'))))


# one-liner to:
# 1) create a dictionary of top 3000 words and whether or not they are contained in each review
# 2) followed by the category (pos/neg)
featuresets = [(find_features(rev), category) for (rev, category) in documents]

# this allows us to begin training, where True/False of top 3000 words are contained in pos/neg reviews
```
2. Naive Bayes Classifier:
posterior = prior occurences x liklihood / current evidence
(posterior = liklihood)
- good for text analysis because simplicity allows to be used at scale w/ minimal processing req on massive (text) data sets.
- dont tell the machine the category, ask machine to tell us w/
training from feed of featuresets for top 3000 words and high freq of words in neg or pos reviews
- high occurance likely means importance for each
1) create classifier based on set of shuffled documents.
2) feed (slightly) different documents and test accuracy.
3) see most important "features" (words) in determining accuracy of neg and pos reviews
```
import nltk
import random
from nltk.corpus import movie_reviews
# continued from 12textclassification.py and 11

documents = [(list(movie_reviews.words(fileid)), category)
              for category in movie_reviews.categories()
              for fileid in movie_reviews.fileids(category)]

random.shuffle(documents)

all_words = []
for w in movie_reviews.words():
	all_words.append(w.lower())

all_words = nltk.FreqDist(all_words)

word_features = list(all_words.keys())[:3000]

def find_features(document):
	words = set(document)
	features = {}
	for w in word_features:
		features[w] = (w in words)

	return features

# print((find_features(movie_reviews.words('neg/cv000_29416.txt'))))

featuresets = [(find_features(rev), category) for (rev, category) in documents]

# When you have a labeled dataset as above, you want to split into training and testing sets
# Don't want to be the same, as creates bias...
training_set = featuresets[:1900]
testing_set = featuresets[1900:]

# 1)
classifier = nltk.NaiveBayesClassifier.train(training_set)
# 2)
print("Naive Bayes Algo accuracy percent:", (nltk.classify.accuracy(classifier, testing_set))*100)
# 3)
classifier.show_most_in
```

3. PICKLE THE (NBC) CLASSIFIER:
Any of the above stuff can be pickled to save processing time.
This tutorial specifically pickled our trained Naive Bayes Classifier taken from the nltk library
```
import nltk
import random
from nltk.corpus import movie_reviews
import pickle

documents = [(list(movie_reviews.words(fileid)), category)
              for category in movie_reviews.categories()
              for fileid in movie_reviews.fileids(category)]

random.shuffle(documents)

all_words = []
for w in movie_reviews.words():
	all_words.append(w.lower())

all_words = nltk.FreqDist(all_words)

word_features = list(all_words.keys())[:3000]

def find_features(document):
	words = set(document)
	features = {}
	for w in word_features:
		features[w] = (w in words)

	return features

# print((find_features(movie_reviews.words('neg/cv000_29416.txt'))))

featuresets = [(find_features(rev), category) for (rev, category) in documents]

training_set = featuresets[:1900]
testing_set = featuresets[1900:]


# classifier = nltk.NaiveBayesClassifier.train(training_set)

classifier_f = open("naivebayes.pickle", "rb")
classifier = pickle.load(classifier_f)

print("Naive Bayes Algo accuracy percent:", (nltk.classify.accuracy(classifier, testing_set))*100)
classifier.show_most_informative_features(15)



#############1.) PICKLE THE CLASSIFIER:
# save_classifier = open("naivebayes.pickle", "wb")
# pickle.dump(classifier, save_classifier)
# save_classifier.close()
```

4. using SKLEARN instead:
```
import nltk
import random
from nltk.corpus import movie_reviews
from nltk.classify.scikitlearn import SklearnClassifier
import pickle

from sklearn.naive_bayes import MultinomialNB, GaussianNB, BernoulliNB
# MultinomialNB is not a binary distribuition, meaning can contain multiple categories
# Check out sci-kit learn for each algorythm, when best to use what, and parameters

from sklearn.linear_model import LogisticRegression, SGDClassifier
from sklearn.svm import SVC, LinearSVC, NuSVC


documents = [(list(movie_reviews.words(fileid)), category)
              for category in movie_reviews.categories()
              for fileid in movie_reviews.fileids(category)]

random.shuffle(documents)

all_words = []
for w in movie_reviews.words():
	all_words.append(w.lower())

all_words = nltk.FreqDist(all_words)

word_features = list(all_words.keys())[:3000]

def find_features(document):
	words = set(document)
	features = {}
	for w in word_features:
		features[w] = (w in words)

	return features

featuresets = [(find_features(rev), category) for (rev, category) in documents]

training_set = featuresets[:1900]
testing_set = featuresets[1900:]


# classifier = nltk.NaiveBayesClassifier.train(training_set)

classifier_f = open("naivebayes.pickle", "rb")
classifier = pickle.load(classifier_f)

print("Original Naive Bayes Algo accuracy percent:", (nltk.classify.accuracy(classifier, testing_set))*100)
classifier.show_most_informative_features(15)

"""
Testing the nltk NB classifier against a bunch found
 in the sck-kit learn module:
"""
MNB_classifier = SklearnClassifier(MultinomialNB())
MNB_classifier.train(training_set) #training the same way we trained our OG classifier
print("MNB_classifier accuracy percent:", (nltk.classify.accuracy(MNB_classifier, testing_set))*100)

BernoulliNB_classifier = SklearnClassifier(BernoulliNB())
BernoulliNB_classifier.train(training_set)
print("BernoulliNB_classifier accuracy percent:", (nltk.classify.accuracy(BernoulliNB_classifier, testing_set))*100)

LogisticRegression_classifier = SklearnClassifier(LogisticRegression())
LogisticRegression_classifier.train(training_set)
print("LogisticRegression_classifier accuracy percent:", (nltk.classify.accuracy(LogisticRegression_classifier, testing_set))*100)

SGDClassifier_classifier = SklearnClassifier(SGDClassifier())
SGDClassifier_classifier.train(training_set)
print("SGDClassifier_classifier accuracy percent:", (nltk.classify.accuracy(SGDClassifier_classifier, testing_set))*100)

SVC_classifier = SklearnClassifier(SVC())
SVC_classifier.train(training_set)
print("SVC_classifier accuracy percent:", (nltk.classify.accuracy(SVC_classifier, testing_set))*100)

LinearSVC_classifier = SklearnClassifier(LinearSVC())
LinearSVC_classifier.train(training_set)
print("LinearSVC_classifier accuracy percent:", (nltk.classify.accuracy(LinearSVC_classifier, testing_set))*100)

NuSVC_classifier = SklearnClassifier(NuSVC())
NuSVC_classifier.train(training_set)
print("NuSVC_classifier accuracy percent:", (nltk.classify.accuracy(NuSVC_classifier, testing_set))*100)
```



--- 
Stopped at 16/21 “Combining Algos with a Vote” on 2/13.
https://pythonprogramming.net/combine-classifier-algorithms-nltk-tutorial/ 
- 16-19 creates a poll of each classifer to make a decision on which to use
based on accuracy (cleaner / less bias)

https://pythonprogramming.net/twitter-sentiment-analysis-nltk-tutorial/ 
- 20 combines nltk w/ the below twitter api streaming tutorial, and requires api application sign-up @ https://apps.twitter.com/ . Most of the video can be skipped…
https://pythonprogramming.net/twitter-api-streaming-tweets-python-tutorial/ 

- 21 combines 20 with the below matplotlib tutorial
https://pythonprogramming.net/python-matplotlib-live-updating-graphs/ 

--- 
