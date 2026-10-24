## Lesson 1: Data basics (23 oct)

**What I learned (in my own words):**
- why data is splitted into test and train 

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




## Lesson 3 (24 oct)

**My results (spam row), basic logistic regression:**
- Precision: 1.00, Recall: 0.76, F1: 0.86
- Caught 113, missed 36, false alarms 0, correct safe 966
- Accuracy 97% but 24% of scams were missed

**Why I think scams were missed:**
- Short messages, text-speak spelling, polite wording, phone numbers

**Interview answer:**
- Accuracy was 97% but recall was only 76%, so accuracy hid that 1 in 4 scams got through.


## Lesson 4: Neural networks (24 Oct)

**In my own words:**
- A neuron is: (write this yourself; hint: logistic regression is one neuron)
- A neural network is: (write this yourself)
- Learning = guess, measure loss, adjust. Gradient descent means: (use the foggy hill story)
- Activation function is needed because: (write this yourself)

**One-neuron experiment (toy data):**
| Step | Loss  | Weights       |
|------|-------|-------------- |
| 0    |0.693  | [0.09, 0.01]  |
| 50   | 0.288 | [0.86, -0.06] |
| 100  | 0.200 | [1.11, -0.09] |
| 150  | 0.153 | [1.30, -0.07] |
| 200  | 0.125 | [1.44, -0.04] |

- The loss fell from 0.693 to 0.125, so the neuron was learning.
- 0.693 is what a model gets when it is just guessing 50/50 between two classes, so it is the natural starting point.
- The weight for "number of scam words" grew to 1.44, while the weight for "has a link" stayed near zero. In my toy data, the link did not help separate scam from safe, and the model discovered that by itself.
- Learning rate 5: (not tried yet)
- Learning rate 0.001: (not tried yet)

**MLP on the SMS data (1 hidden layer, 64 neurons), spam class:**
- Precision 0.98, recall 0.88, F1 0.93
- Confusion matrix: 131 scams caught, 18 missed, 3 false alarms, 963 correct safe
- Bigger or smaller network: (not tried yet)

**Comparison so far (spam class):**
| Model                         | Precision | Recall | F1   | Missed scams | False alarms |
|-------------------------------|-----------|--------|----  |--------------|--------------|
| Logistic regression           | 1.00      | 0.76   | 0.86 | 36           | 0            |
| Logistic regression, balanced | 0.91      | 0.91   | 0.91 | 13           | 13           |
| MLP (64 hidden)               | 0.98      | 0.88   | 0.93 | 18           | 3            |

- The MLP has the best F1 (0.93), and compared with the plain logistic regression it halved the missed scams (36 to 18) while adding only 3 false alarms.
- The balanced logistic regression still has the highest recall (0.91), because it was told to treat missed scams as costly.
- The MLP still reads TF-IDF scores, so it sees words as separate counts and does not understand meaning or word order. This is the limit that BERT is meant to fix.

**Interview answer:**
- How does a neural network learn? -> (write this yourself in 2 to 3 sentences using guess, loss, adjust)
