---
layout: post
title: TF-IDF Simplified
date: 2021-01-20 15:06:00
description: A short introduction to TF-IDF vectorizer
tags: ["Data Science", "Machine Learning", "NLP", "Data", "Artificial Intelligence"]

categories: sample-posts
citation: true
---

Most machine learning algorithms are fulfilled with mathematical things such as statistics, algebra, calculus and etc. They expect the data to be numerical such as a 2-dimensional array with rows as instances and columns as features. The problem with natural language is that the data is in the form of raw text, so that the text needs to be transformed into a vector. The process of transforming text into a vector is commonly referred to as text vectorization. It’s a fundamental process in natural language processing because none of the machine learning algorithms understand a text, not even computers. Text vectorization algorithm namely TF-IDF vectorizer, which is a very popular approach for traditional machine learning algorithms can help in transforming text into vectors.

# TF-IDF
Term frequency-inverse document frequency is a text vectorizer that transforms the text into a usable vector. It combines 2 concepts, Term Frequency (TF) and Document Frequency (DF).

The term frequency is the number of occurrences of a specific term in a document. Term frequency indicates how important a specific term in a document. Term frequency represents every text from the data as a matrix whose rows are the number of documents and columns are the number of distinct terms throughout all documents.

Document frequency is the number of documents containing a specific term. Document frequency indicates how common the term is.

Inverse document frequency (IDF) is the weight of a term, it aims to reduce the weight of a term if the term’s occurrences are scattered throughout all the documents. IDF can be calculated as follow:

$$
{idf}_i=\log(\frac{n}{df_i}) 
$$

Where $${idf}_i$$ is the IDF score for term $$i$$, $$df_i$$ is the number of documents containing term $$i$$, and $$n$$ is the total number of documents. The higher the DF of a term, the lower the IDF for the term. When the number of DF is equal to n which means that the term appears in all documents, the IDF will be zero, since $$log(1)$$ is zero, when in doubt just put this term in the stopword list because it doesn't provide much information.

The TF-IDF score as the name suggests is just a multiplication of the term frequency matrix with its IDF, it can be calculated as follow:

$$
w_{i,j}={tf}_{i,j} \times {idf}_i
$$

Where $$w_{i,j}$$ is TF-IDF score for term $$i$$ in document $$j$$, $${tf}_{i,j}$$ is term frequency for term $$i$$ in document $$j$$, and $${idf}_i$$ is IDF score for term $$i$$.

# Example
Suppose we have three texts and we need to vectorize these texts using TF-IDF.

![alt text](https://miro.medium.com/v2/resize:fit:640/format:webp/1*1udkAfTZA50J8F2Ea3wOLw.png)

## Step 1
Create a term frequency matrix where rows are documents and columns are distinct terms throughout all documents. Count word occurrences in every text.

![alt text](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*M_LKvKlLM_mYGipETrISVw.png)

## Step 2
Compute inverse document frequency (IDF) using the previously explained formula.

![alt text](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*mleHb1XvKyFbysWi1CtIsA.png)

The term $$i$$ and processing has 0 IDF score, as previously mentioned we can drop these terms, but for the sake of simplicity, we keep these terms here.

## Step 3
Multiply TF matrix with IDF respectively.

![alt text](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*naTB7_v4__pEikK8pPB2tw.png)

That's it 😃! the text is now ready to feed into a machine learning algorithm.

# Limitations
1. It is only useful as a lexical level feature.
1. Synonymities are neglected.
1. It doesn't capture semantic.
1. The highest TF-IDF score may not make sense with the topic of the document, since IDF gives high weight if the DF of a term is low.
1. It neglects the sequence of the terms.

# Conclusion
In order to process natural language, the text must be represented as a numerical feature. The process of transforming text into a numerical feature is called text vectorization. TF-IDF is one of the most popular text vectorizers, the calculation is very simple and easy to understand. It gives the rare term high weight and gives the common term low weight.
