[Computational Linguistics Lab](http://compling.ucdavis.edu/)
===
[*Department of Linguistics*](http://linguistics.ucdavis.edu/), [*UC Davis*](https://www.ucdavis.edu/)

## Overview
Expanding linguistic resources for speech enabled systems

### tokenizer.py 
Wikipedia database dump tokenizer

1. First download the [Wikipedia database dump](https://dumps.wikimedia.org/)
2. Use [WikiExtractor](https://github.com/attardi/wikiextractor) to extract and clean text from the Wikipedia database dump
 ```
    $ git clone https://github.com/attardi/wikiextractor.git
 ```
3. Install the script by doing

 ```
    $ (sudo) python setup.py install
 ```
4. Apply the script to the Wikipedia database dump

 ```
    $ WikiExtractor.py (your-database-dump).xml.bz2
 ```
5. Specify the database path in the script and run **tokenizer.py**

  ```
    $ python tokenizer.py
 ```
6. Tokens are stored in **results.txt**, unless otherwise specified

### word2vec.py
Inspect Wikipedia database dump model with Word2Vec

1. Build [fastText](https://github.com/facebookresearch/fastText) using the following commands
 ```
   $ git clone https://github.com/facebookresearch/fastText.git
   $ cd fastText
   $ make
```
2. Learn word vectors for the Wikipedia database dump articles
 ```
   $ ./fasttext skipgram -input results.txt -output model
```
3. Running the command above will save two files: **model.bin** and **model.vec**. **model.vec** is a text file containing the word vectors, one per line. **model.bin** is a binary file containing the parameters of the model along with the dictionary and all hyper parameters. 
4. Running the following command will train the Wikipedia database dump model and store the "words" into the directory **vocabulary** 
```
   $ mkdir vocabulary
   $ python word2vec.py
```

## Built With
* [Python](https://www.python.org/)
* [fastText](https://github.com/facebookresearch/fastText) and [Word2Vec](https://radimrehurek.com/gensim/models/word2vec.html) - For learning word representations
* [NLTK](http://www.nltk.org/) - Used to tokenize words

## Contributors
* [Richard Kim](https://github.com/khgkim)
* [Lauren Namdar](https://github.com/lnamdar)
* Samuel Davidson
