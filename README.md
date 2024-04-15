# Quora Question Pair Similarity

Over 100 million people visit Quora every month, so it's no surprise that many people ask similarly worded questions. Multiple questions with the same intent can cause seekers to spend more time finding the best answer to their question, and make writers feel they need to answer multiple versions of the same question. Quora values canonical questions because they provide a better experience to active seekers and writers, and offer more value to both of these groups in the long term.  so main aim of project is that predicting whether pair of questions are similar or not. This could be useful to instantly provide answers to questions that have already been answered.
   Credits: Kaggle
### Problem Statement :
Identify which questions asked on Quora are duplicates of questions that have already been asked.

### Real world/Business Objectives and Constraints :
   - The cost of a mis-classification can be very high.
   - You would want a probability of a pair of questions to be duplicates so that you can choose any threshold of choice.
   - No strict latency concerns.
   - Interpretability is partially important.

### Performance Metric:
   - log-loss 
   - Binary Confusion Matrix

### Data Overview:
Train.csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate. Total we have 404290 entries. Splitted data into train and test with 70% and 30%.

### Feature Extraction:
- ##### Basic Features - Extracted some features before cleaning of data as below.
  - <b>freq_qid1</b> = Frequency of qid1's
  - <b>freq_qid2</b> = Frequency of qid2's
  - <b>q1len</b> = Length of q1
  - <b>q2len</b> = Length of q2
  - <b>q1_n_words</b> = Number of words in Question 1
  - <b>q2_n_words</b> = Number of words in Question 2
  - <b>word_Common</b> = (Number of common unique words in Question 1 and Question 2)
  - <b>word_Total</b> =(Total num of words in Question 1 + Total num of words in Question 2)
  - <b>word_share</b> = (word_common)/(word_Total)

- ##### Advanced Features - Did some preprocessing of texts and extracted some other features. i am giving some definitions which are used below. `Token`- You get a token by splitting sentence by space  ,  `Stop_Word` - stop words as per NLTK, `Word `-A token that is not a stop_word.
  - <b>cwc_min</b> = common_word_count / (min(len(q1_words), len(q2_words)) 
  - <b>cwc_max</b> = common_word_count / (max(len(q1_words), len(q2_words)) 
  - <b>csc_min</b> = common_stop_count / (min(len(q1_stops), len(q2_stops)) 
  - <b>csc_max</b> = common_stop_count / (max(len(q1_stops), len(q2_stops)) 
  - <b>ctc_min</b> = common_token_count / (min(len(q1_tokens), len(q2_tokens)) 
  - <b>ctc_max</b> = common_token_count / (max(len(q1_tokens), len(q2_tokens)) 
  - <b>last_word_eq</b> = Check if Last word of both questions is equal or not (int(q1_tokens[-1] == q2_tokens[-1]))
  - <b>first_word_eq</b> = Check if First word of both questions is equal or not (int(q1_tokens[0] == q2_tokens[0]) )
 



##### References:
1. https://www.kaggle.com/c/quora-question-pairs 
2. https://www.kaggle.com/c/quora-question-pairs/discussion
3. Applied AI Course
4. https://github.com/seatgeek/fuzzywuzzy#usage , https://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/
5. http://proceedings.mlr.press/v37/kusnerb15.pdf
