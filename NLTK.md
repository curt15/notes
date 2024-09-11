Links: [[PROGRAMMING]] - [[TECHNOLOGY]] - [[PYTHON]]
Rel: 
Ref: 
Tags: #public 

Natural Language Toolkit

--- 
######  "A paragraph typically contains a main idea"  

**TERMS**:

- **tokenizing** \- word tokenizers vs sentence tokenizers (where separation occurs)
- **corpora** \- body of text. ex: medical journals, presidential speeches, ... Anything English language
- **lexicon** \- words and their meanings

investor-speak vs regular english-speak lexicon:

- investor speak 'bull' = someone who is positive about the market
- english speak 'bull' = large animal


\_\_\_\_\_\_

- **Stop words** can be...
something that you give up on (e.g. scarcastic words),
fluff words (a, the, and, ...) that are useless to data analysis


\_\_\_\_\_\_

- **Stemming**:

Form of data pre-processing of taking the root stem
e.g. "riding" stem = "rid-"
where "rid-" can be "ride, riding, ridden, ..."

Useful where meaning of the word is unchanged:
\# I was taking a ride in the car.
\# I was riding in the car.


\_\_\_\_\_\_

- **Part of Speech Tagging:**  

   
POS tag list: (part of speech)
- CC coordinating conjunction
- CD cardinal digit
- DT determiner
- EX existential there (like: "there is" ... think of it like "there exists")
- FW foreign word
- IN preposition/subordinating conjunction
- JJ adjective 'big'
- JJR adjective, comparative 'bigger'
- JJS adjective, superlative 'biggest'
- LS list marker 1)
- MD modal could, will
- NN noun, singular 'desk'
- NNS noun plural 'desks'
- NNP proper noun, singular 'Harrison'
- NNPS proper noun, plural 'Americans'
- PDT predeterminer 'all the kids'
- POS possessive ending parent\\'s
- PRP personal pronoun I, he, she
- PRP$ possessive pronoun my, his, hers
- RB adverb very, silently,
- RBR adverb, comparative better
- RBS adverb, superlative best
- RP particle give up
- TO to go 'to' the store.
- UH interjection errrrrrrrm
- VB verb, base form take
- VBD verb, past tense took
- VBG verb, gerund/present participle taking
- VBN verb, past participle taken
- VBP verb, sing. present, non-3d take
- VBZ verb, 3rd person sing. present takes
- WDT wh-determiner which
- WP wh-pronoun who, what
- WP$ possessive wh-pronoun whose
- WRB wh-abverb where, when


\_\_\_\_\_\_

- **Chunking:**
After you tag by POS, the noun (NN, NNS) is "generally" going to be the subject.

Next step is finding out words that modify or effect that(/those) noun(s).
Chunk into "noun phrases" where you have a noun and a bunch of modifiers around it

Downside = can only use regular expressions.
see re idenfifiers and modifiers @ **regularexpressions.py**


\_\_\_\_\_\_

- **Chinking** \= removing something from a chunk.


\_\_\_\_\_

- **Named Entity Recognition:**

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


\_\_\_\_\_\_

- **Lemmatizing:**
similar to stemming, but will return an actual word with meaning

e.g. the "lemma" for run, runs, ran, and running = run
default for pos="n"


\_\_\_\_\_\_

- **Corpora:**
A body of texts generally grouped by some sort of defining chartacteristic

\[ NLTK’s Corporas \] can be found in Users/name/nltk\_data/corpora/

\_\_\_\_\_\_

- **WordNet** is more of a giant Lexicon vs a Corpora.

- **Synsets** are:
	- Used for rewriting things like with paper writing services
	- Used by schools in reverse to find cheaters
	- Used by bots to scrape news, rewrite, and post
	- Used by "google" to find via the opposite

- **wup\_similarity** \= “Wu and Palmer” wrote a paper on semantic similarity

\_\_\_\_\_\_

- **Text Classification:**
	- Creating own algorythm or "text classifier"
	- can be used for sentiment analysis (here) or
	- things like stocks, politics, or economics writing, or
	- filtering spam vs not spam

Must be one of two choices/labels:
- positive or negative,
- spam or not,
- etc.


\_\_\_\_\_\_

**Words as Features for Learning:**


**\_\_\_\_\_\_**

- **Naive Bayes Classifier:**
good for text analysis because simplicity allows to be used at scale w/ minimal processing req on massive (text) data sets.

  
posterior ~= “likelihood”
posterior \= prior\_occurences x likelihood / current\_evidence

1) create classifier based on set of shuffled documents.
2) feed (slightly) different documents and test accuracy.
3) see most important "features" (words) in determining accuracy of neg and pos reviews

\- dont tell the machine the category, ask machine to tell us w/ training from feed of featuresets for top 3000 words and high freq of words in neg or pos reviews

\*\* high occurance likely means importance for each


