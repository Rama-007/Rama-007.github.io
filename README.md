# Medical Persona Classification in Social Media
The aim of this project is to identify the **persona** of a given tweet. Our set of Personae are:
- Patient
- Caretaker
- Consultant
- Journalist
- Pharmacist
- Researcher
- Other

## About the project
Given a social media post, identify the medical personae associated with it. We post this as multi-label text classification problem, where our label set is the set of personae.

There are two primary reasons for setting this as a multi-label classification task (as opposed to single-label) :
* There might be posts involving conversations between multiple personae. For eg. a tweet describing patient and consultant conversation.
* A post might be of ambiguous nature and hence can potentially be mapped to more than one label by a human annotator. 

Tis project was assigned a team of 4(which is us) as a part of Major Project for the Information Retrieval and Extraction Course. This project was divided into three phases. In the first phase we were required to come up with a scope document and deliverables for the second and the third phase respectively. In the second and third phase, we had to actually code and then implement what we had proposed.

## Approach
- Crawling
- Text Normalization, Spell correction
- Feature Extraction
- Deep Learning Methods for Classification

### Crawling 

The main  goal is to extract tweets belonging to multiple personae. But crawling tweets at random would have been a mess and not useful. So we restricted the tweets by maintaining a list of Top 400 drugs used in medical domain, for example: Amikacin, Aspirin, Thiamine etc. and selecting only those tweets which contain these words in them.

We used **TwitterSearch** API with the drugs as keywords and get all the data related to that tweet in dictionary format.
 
The dataset generation in phase one :

* **Semi-Supervised approach**

  * We collected handles of people belonging to different persona based on their popularity using google search.
  * We collected tweets from the above handles related to medical domain using keyword search. Using twitter api, we collected tweets for 6 persona using various apt-key words related to each persona. Dataset Information :

      | Persona       | Tweet Count   |
      | ------------- | ------------- |
      | Patients      |      120      |
      | Pharmacists   |       69      |
      | Caretaker     |       71      |
      | Consultant    |      200      |
      | Journalist    |      127      |
      | Researcher    |      130      |

But the dataset had much useless information so after features were extracted and classification was done, though it performed well on the training data whenever a new tweet was given it assigned every tweet to single persona which was not intended. So we changed our approach to Supervised, increased the amount of data and features.
