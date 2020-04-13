---
title: "The journey from raw text to a good dataset"
sub_title: "Let's go on an adventure"
categories:
  - Machine Learning
elements:
  - datasets
  - data
  - nlp
last_modified_at: 2020-01-28
---

In this blog post I want to describe the journey that comes before all the “AI”s, “ML”s and other buzzwords - the tedious data collecting, analyzing, and processing. I’ll be focusing on textual data, and how to build a good dataset for your NLP problems.  

> Data science is 80% preparing data, 20% complaining about preparing data.


# What is data?

Data is, basically, information. In the context of computer science and business, data refers to information that is collected for further analysis. That information is often machine-readable as opposed to human-readable.

## Human-readable vs Machine-readable

Machine-readable data, or computer-readable data, is data (or metadata) in a format that can be easily processed by a computer, while a human-readable medium or human-readable format is a representation of data or information that can be naturally read by humans. Machine-readable data can be automatically transformed for human-readability but, generally speaking, the reverse is not true. An example would be a sentence, where we can easily understand it’s sentiment and emotion (most of the time at least), but typically it’s difficult for machines to interpret the same.

# Let's begin the journey

## Collecting data

To generalize, there are two ways to gather data:
  1. Collecting it from a primary source yourself, where you are the first one to obtain the data
  2. Collecting data from a secondary source, where you would be re-using data that has already been collected by other sources, such as data used by certain scientific research

Depending on the type of data, this could be either a walk in the park or a nasty headache. Regardless of the domain, it’s important to keep in mind that the data has to be relevant to the problem, otherwise, we won’t be able to solve the problem or we might reach false conclusions. To keep this from happening, the data collection process should be carefully built.

### Domain knowledge

Understanding the problem and the data that it requires is important. For certain issues, this might require talking with a domain expert about the required data, or, if you have the time and resources, to learn about the specific field yourself! You should be able to answer the following questions:

  * Where can I get the relevant data?
  * How can I collect it effectively?
  * How can I verify the data I collected?

### Collection issues

 A lot of problems can occur while trying to collect data, like:

  * Unavailable data
  * Redundant data (duplicate data)
  * Incomplete data
  * Old data; it hasn't been updated...

>  There are two kinds of data scientists. 1.) Those who can extrapolate from incomplete data.



## Analyzing and transforming data

Now that we have real-life data, we can get down to business! Data analysis includes inspecting features, keeping the most useful ones, and cleaning up the rest. 

### Preprocessing raw text data

In this section, I am going to describe the usual preprocessing steps for preparing generic textual data. These steps make it possible for us to get the most useful information out of a textual dataset. 

#### Tokenization

Tokenization splits longer strings into smaller ones, called tokens. We tokenize the text into sentences, the sentences are then tokenized into words. Tokenization is usually the first step in preprocessing text. This process is also referred to as text segmentation or lexical analysis. Sounds easy, right? It isn’t as straightforward as it seems. Let’s take sentence tokenization as an example. The first thing that comes to my mind is to split the text by punctuation marks to achieve this. It could work for some examples:

`The quick brown fox jumps over the lazy dog.`

But we couldn’t say the same for the following case:

`Please arrive by 12:30 p.m. sharp.`

What about word tokenization? If we only considered splitting the words by whitespaces, instances like     she’s wouldn’t be tokenized correctly. This apostrophe brings up an interesting question -  how to approach this? Is it actually important to memorize where punctuation is placed, or should we drop it altogether? In general, I would suggest testing out both cases, and see which one works better for your issue. A lot of solutions in data science were empirically discovered. 

#### Removing stopwords 

When processing natural language, we often filter out stopwords. These lists usually refer to most common words in a certain language, that don’t add any extra meaning to the text, such as ‘the’ in English. Dropping stopwords helps us to clean up the data, and to bring more attention to words that actually carry meaning and useful features. 

One of the ways we can analyze which words are stopwords in a certain collection of documents is by looking at the frequency of the word (how often does the word appear in a document) combined with inverse document frequency (in how many different documents does the word actually appear, in regards to the whole collection of documents). 

#### Stemming and lemmatization

Because of grammar, we will often find different forms of a word, like `write`, `writes`, `wrote` and `writing`. Contextually, these words represent the same idea, but are formed differently. It is often useful to reduce the number of different forms of the same word by replacing them with a common base form. This is achieved by both stemming and lemmatization of the words. By doing this we make the data more consistent.
For example, this is the result we would want to achieve for these words:

<pre>
    am, are, is → be

    write, writes, wrote, writing → write
</pre>

So, how do we exactly achieve this? Stemming is a process that usually roughly chops off the end of the word, hoping to achieve the desired goal, which happens most of the time. Lemmatization however usually refers to doing this properly, with the help of vocabulary and morphological analysis of words, aiming to return the base of the word, known as a lemma. If confronted with the tokens write and wrote, by stemming we would get two different results, whereas lemmatization would attempt to return write.

Stemmers use language-specific rules and are easier to implement than a lemmatizer, which requires a complete vocabulary and morphological analysis to correctly lemmatize words. Some tokens may require special rules to be implemented as well.
    
For apparent reasons, this process differs from language to language.


#### Data normalization

Normally, raw data consists of attributes with varying scales. Data normalization is the process of rescaling one or more attributes to the range of 0 to 1. In general, it is a good technique to use when you don’t know the distribution of the data, or when you know the distribution is not Gaussian.


#### Word embedding

Word embedding covers a lot of techniques and approaches to map words to numbers or vectors. I will cover this in a separate blog, stay tuned for that one. ;)

# Conclusion

When building a dataset, it’s important to know what features to look for, so that the model can get the most benefit out of it. After acquiring the data, we need to do noise removal, to make the useful features stand out.