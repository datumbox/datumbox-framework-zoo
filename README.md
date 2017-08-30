Datumbox Framework Zoo: Pre-trained models
==========================================

[![Datumbox](http://www.datumbox.com/img/logo.png)](http://www.datumbox.com/)

This project contains pre-trained Machine Learning models which can be used with the [Datumbox Machine Learning Framework](https://github.com/datumbox/datumbox-framework/) v0.8.1-SNAPSHOT (Build 20170830).

Copyright & License
-------------------

Copyright (c) 2013-2017 [Vasilis Vryniotis](http://blog.datumbox.com/author/bbriniotis/). 

Licensed under the [Apache License, Version 2.0](./LICENSE).

Pre-trained Models
------------------

The project contains the binary files of all the text classification models which are available via the [Datumbox API](http://www.datumbox.com/machine-learning-api/):

- [Sentiment Analysis](./SentimentAnalysis): The Sentiment Analysis model classifies documents as positive, negative or neutral (lack of sentiment) depending on whether they express a positive, negative or neutral opinion.
- [Twitter Sentiment Analysis](./TwitterSentimentAnalysis): The Twitter Sentiment Analysis model allows you to perform Sentiment Analysis on Twitter. It classifies the tweets as positive, negative or neutral depending on their context.
- [Subjectivity Analysis](./SubjectivityAnalysis): The Subjectivity Analysis model categorizes documents as subjective or objective based on their writing style. Texts that express personal opinions are labeled as subjective and the others as objective.
- [Topic Classification](./TopicClassification): The Topic Classification model assigns documents in 12 thematic categories based on their keywords, idioms and jargon. It can be used to identify the topic of the texts.
- [Spam Detection](./SpamDetection): The Spam Detection model labels documents as spam or nospam by taking into account their context. It can be used to filter out spam emails and comments.
- [Adult Content Detection](./AdultContent): The Adult Content Detection model classifies the documents as adult or no-adult based on their context. It can be used to detect whether a document contains content unsuitable for minors.
- [Language Detection](./LanguageDetection): The Language Detection model identifies the natural language of the given document based on its words and context. This classifier is able to detect 96 different languages.
- [Commercial Detection](./CommercialDetection): The Commercial Detection model labels the documents as commercial or non-commercial based on their keywords and expressions. It can be used to detect whether a website is commercial or not.
- [Educational Detection](./EducationalDetection): The Educational Detection model classifies the documents as educational or non-educational based on their context. It can be used to detect whether a website is educational or not.
- [Gender Detection](./GenderDetection): The Gender Detection model identifies if a particular document is written-by or targets-to a man or a woman based on the context, the words and the idioms found in the text.

**Important Notes:**

- The models support only English.
- The binary files should be loaded using their corresponding Framework version.
- All the models should be loaded using the InMemory storage engine.
- Within the folder of each model you will find a stats.txt file which contains the accuracy metrics of the classifier. The metrics were estimated using 10-fold cross validation.
- All the remaining API methods which are not included here (Readability Assessment, Keyword Extraction, Text Extraction & Document Similarity) are directly powered up by standalone classes of the [framework](https://github.com/datumbox/datumbox-framework/).

How to use
----------

1. Download/clone this project locally. 
2. Open your datumbox.configuration.properties file and make sure you use the InMemory engine by default:
    ```
    configuration.storageConfiguration=com.datumbox.framework.storage.inmemory.InMemoryConfiguration
    ```
3. Open your datumbox.inmemoryconfiguration.properties file and update the directory:
    ```
    inMemoryConfiguration.directory=/path/to/datumbox-framework-zoo
    ```
4. Within your project initialize the classifiers using their name:
    ```java
    Configuration configuration = Configuration.getConfiguration();
    
    TextClassifier textClassifier = MLBuilder.load(TextClassifier.class, "SentimentAnalysis", configuration);
    System.out.println(textClassifier.predict("Datumbox is amazing!").getYPredicted());
    ```

Note that it is also possible to skip steps 2 & 3 and instead programmatically update the configuration object before initializing the classifier:

```java
Configuration configuration = Configuration.getConfiguration();
InMemoryConfiguration storageConfiguration = new InMemoryConfiguration();
storageConfiguration.setDirectory("/path/to/datumbox-framework-zoo");
configuration.setStorageConfiguration(storageConfiguration);
```

Useful Links
------------

- [Datumbox Machine Learning Framework](https://github.com/datumbox/datumbox-framework/)
- [Code Examples](https://github.com/datumbox/datumbox-framework-examples/)
- [Datumbox.com](http://www.datumbox.com/)
- [Machine Learning Blog](http://blog.datumbox.com/)

