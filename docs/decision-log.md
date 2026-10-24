## Lesson 1: Data basics (23 oct)

**What I learned (in my own words):**
- 

**What my data looks like:**
- Total messages: 5572
- Spam %: 13%
- Anything surprising: spam messages were longer than messages that are not spam 

**A problem I noticed:**
-  class imbalance

**Interview question I can now answer:**
- Why do we split data into train and test? -> if we train on whole data , there were very high chances that model will learn the pattern and cause overfitiing , so we split it so it can only get trained on some part of data and some is hidden only used for testing


## Lesson 2: TF-IDF (24 oct )

**What I learned (in my own words):**
- Why text must become numbers: because our model/ pc dosenot understand text ,, so we have to convert them into list of numbers known as vectorization 
- Bag of words vs TF-IDF: 
- bag of words :-  make a list of each word in every message and count how many times words occur , but the problem with it is that common words gt high score , but words that are useful get low score and order of words is also lost . 
- TF-IDF -  TF tells how often the words appear whereas idf tells how rare is thee word across all msg , rare words get high score and common words get a low score 

**My results:**
- Vocabulary size (default settings): 7403
- Top 5 spammy words: free ,txt ,claim ,mobile ,stop
- What changed when I used ngram_range=(1,2): we were also using pair of words present there 

**Interview question I can now answer:**
- Why fit the vectorizer only on training data? -> we are using fit the vectoriser only on training data because if we apply it on both vectorizer will learn from test data , leakage from hidden test data , so we apply fit and transform on train data and only transform on test data




## Lesson 3 (2 oct)

**My results (spam row), basic logistic regression:**
- Precision: 1.00, Recall: 0.76, F1: 0.86
- Caught 113, missed 36, false alarms 0, correct safe 966
- Accuracy 97% but 24% of scams were missed

**Why I think scams were missed:**
- Short messages, text-speak spelling, polite wording, phone numbers

**Interview answer:**
- Accuracy was 97% but recall was only 76%, so accuracy hid that 1 in 4 scams got through.