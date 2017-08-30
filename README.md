

# Neural Embeddings for Automatic Sentiment Analysis

## Introduction
Automatic sentiment analysis under information extraction is an important field and continues to receive interest from the academic community. The aim is to extract sentiments and opinion from user reviews and use the extracted features and sentiment to classify the reviews which can be used for generating personalized recommendations.

For generating recommendations, Collaborative Filtering (CF) is the standard technique. It provides personalized recommendations to users based on a profile of user preferences, from which users having similar tastes are identified. It then recommends to a target user, the items liked by other similar users. Some music review banks, such as Amazon Customer Reviews on its music sales, allow users to provide comments in free text format. Such User generated reviews also come with a “user rating”, and connecting this rating with the sentiment in the text is a problem we will explore. Being free text generated by users, the reviews do not possess the same structure or format, and generally they are unstructured and of mixed sentiments, affecting the overall sentiment of the review. Previous approaches to sentiment analysis based on transfer learning have a critical problem in that they only work well on a single source domain and a single target domain. For example, the adjective ''unpredictable'' may have a negative orientation in an automotive review, in a phrase such as ''unpredictable steering'', but it could have a positive orientation in a movie review, in a phrase such as “unpredictable plot''. A word like “sick” has a negative sentiment in domains like medical or general conversation, but in the domain of music reviews, the word has a positive impact. Such incidents lower the quality of our recommendation engine if they are classified wrongly.

This research will be focused on exploring various techniques that shed a light on overcoming the stated problems in automatic sentiment extraction and analysis on Movies and TV reviews. In our work, we will first pre-process the user reviews using NLTK techniques. After which, the tokenized words would be plotted on a Word2Vec vector space model of around 500-600 dimensions. These word vectors would then be plotted on a Sent2Vec vector space model, where the polarity of these words would be classified using natural language processing tools in Python, like TextBlob. We will build a ternary task of classification of sentiment into positive, negative and neutral polarities. 
The job of classifying the sentiment polarity of a written text in natural language into positive, negative or neutral feeling is so complex that even if we conduct the classification manually, different people have different opinion regarding the sentiment polarity of a word. Such differences can be based on personal experience, cultural background, language they speak, etc. With influx of social networking and micro-blogging sites like Facebook and Twitter, analyzing text from these sources is more challenging, as most of them are short in length and sometimes worst written.

 
The task of sentiment analysis over text can be undertaken through two different approaches. For now, one can either utilize semantic approaches (Turney, 2002) or computational learning techniques (Pang, Lee, and Vaithyanathan, 2002).

## Approaches

Semantic approaches to language processing can be defined using lexicons (dictionaries of words with their semantic direction of polarity). This such systems commonly pre-processes the text by tokenizing it into individual words and then apply processes like stop-words removal, normalization with stemming or lemmatization. Then a global polarity value is supplied to the text by summing up all the polarity values of each individual word present in that text, by looking up each word in the lexicon.

Such approaches sometimes also consider conducting an advanced operation that includes modifier terms (like less, very, too, etc.) that either increase or decrease the polarity of the adjacent word, and negations or negative terms (like never, no, not) that reverses the polarity of the adjacent word.

The main reason why one considers following a semantic approach is because correction of errors is relatively easy and by just investing more time in creating a better lexicon, adding more words and terms, we can apparently get a precision as high as we want it to be. Such simplicity is lacking in learning-based approaches which often act as a black-box where error correction and addition or updating new words and terms is quite complicated, and often requires re-training of the whole model with more text data to learn from.

In contrast to semantic approaches, the learning-based approaches is based on utilizing machine-learning classifying algorithms, mostly a supervised learning algorithm based on Naïve Bayes, KNN (K-Nearest Neighbor) or SVM (Support Vector Machines). Apart from these mentioned classifier algorithms, a more advanced approach such as LSA (Latent Semantic Analysis) and Deep Learning, is being investigated recently. These classifiers are fed with annotated texts, where each text is typically represented by n-grams or skip-grams, bag of words or word vectors. These annotated texts can be combined with other features that can illustrate the semantic structure of the text being processed.

The advantage of a machine-learning based approach is that it is easy to implement and is quick to build a model that conducts sentiment or opinion analysis which is trained with tagged text documents. As building such models is simple, thus it is comparably easy to build such models revolving around a specific domain or domains. Lexicon-based approaches fail to provide such feature of domain independency and adaptability, as different domains require lexicons to be created specific to that domain, from scratch, which is a very daunting task as lexicon creation is done manually.


Machine-learning approaches are preferred over semantic approaches, when supplied with labelled collection, as these approaches is easily accustomed to different domains, thus saving a lot of manual effort in building lexicons for their respective domains. Hence, this method usually outperforms the semantic lexicon based methods which are much costlier to develop. 

With the arguments above, we can then infer that learning based models adapt better to target domain, but re-training a model always when it is required to be transferred to a different domain. The model here works quite well in not so complicated cases, but cases where a more complex operation is required over the natural language texts, they fail. The model seems to fail when the sentences have a mix of polarities and includes inverse terms, comparators, etc.

This is a  dissertation that aims to extend the application of Word2Vec model, which is a machine-learning based approach for natural language text processing that works on vector representation of words in a high dimensional vector space model. Word2Vec family models does not consider the contextual meaning of a word thus they face a problem called “polysemy”, where they fail to capture true meaning of a word when there are occurrences of polyseme words. A polyseme is a word that have two or more distinct meanings. As by some estimate English language have more than 40% words with multiple meanings, thus having just Word2Vec without any further adjustments do not possess high precision when similarity of words is in question.

In this project, we try to extend the functionality of the Word2Vec model, by training the model with part-of-speech tags attached to the words. The model then considers the words appearing with different meanings as different vectors in the model, rather than the same word. Because of this the new model does not predict the similarity between two words based on the surrounding words, rather the sense of the vector is predicted based on the surrounding senses. Hence, we call the new model as “Sense2Vec” (Trask et al.).

We conduct various evaluations between both Word2vec and Sense2Vec models, through queries to find most similar words and by clustering the most similar words using the t-SNE clustering method which collapses the high dimensional space into a 2-dimensional representation.

The plots generated when t-SNE cluster vectors are scattered on a chart are then evaluated, to which we found out that although Word2Vec was able to find the most similar words, but there were occurrences of many such words which were given high similarity score that were an error by the model or not in context with the surrounding words. On the other hand, Sense2Vec model surpassed the prediction power of a simple Word2Vec model, as the most similar words in a cluster were sharing the same contextual sense. With that we were tried to even identify relationships between a word to other words. As we investigated the relationship, we introduced sentiment polarity scores to the word vectors that were represented on the chart, and with the help of that we could visualize zones of positive and negative sentiment around a word vector.

This dissertation paves a way to future exploration in the field of sentiment analysis through word vector representation machine-learning based approach.
