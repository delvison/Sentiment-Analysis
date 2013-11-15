Summary
	This is a sentiment analysis program that can classify a movie critique as either a positive or negative critique. The program is written entirely in python (version 2.7.3) and utilizes components of the Natural Language Toolkit.

Explanation
	This program utilizes the method of supervised classification. The data set that was used for the training component is listed below. Initially, I had intended to use full critique examples taken from the web but the amount of irrelevant words within these critiques proved for very little accuracy. Instead, I chose to use brief one-line critiques as the training input simply because they were straight to the point and larger fuller critiques can be atomically comprised of these smaller ones. I start by reading my sample input, removing punctuation and any words that contain a length less than 3 from every live. This is mainly to get rid of neutral words such as 'it' and 'the'. The resulting words are then considered to be the features. I generate a training set by utilizing the nltk.classify.apply_features function with my feature extractor function and list of critiques as parameters. The feature extractor of this program takes in a tokenized review, checks what words it contains in relation to the features that were extracted from my sample data and returns a dictionary of this information. The dictionary essentially has boolean values of what words the tokenized review contains in relation to the training feature set.  After I have my training set I generate my classifier model by utilizing the nltk.NaiveBayesClassifier.train function with my training set as a parameter. Once I have my classifier model, I am ready to start making predictions. I take a movie critique as an input, tokenize it, extract its features using my feature extractor and pass the list of features into the classifier model's classify function. The result is a label which in this case can be 'positive' or 'negative'.

Heres example of what the feature extractor of this program returns when considering a movie review:

Example:  “It was a great movie.” --> (tokenize) --> ['It', 'was', 'a', 'great', 'movie'] → pass this set into feature extractor. The return resembles something like this:
{'contains(great)' : True,
  'contains(movie)' :True
  'contains(terrible)': False,
  (etc)...}
