# Naive-Bayes-Classifier
Naïve Bayes Classifier using Spark MapReduce

1. Import the .ipynb file.
2. An overview of the code:
   Step-1: Import all the libraries and load the dataset.
           The dataset is available at https://github.com/poojaminna/dataset- Assignment2/blob/main/maindata.csv
   Step-2: Transform the raw data into token of words using Tokenizer and then remove stopwords using StopWordsRemover.
   Step-3: Split the data into training and testing data.
   Step-4: Calculate prior probabilities: P(Spam)= No_of_spamtexts/Total_no_of_texts, P(Ham)=Np_of_hamtexts/Total_no_of_texts.
   Step-5: Now, we create a tuple of ((label, ‘word’),1) and reduce by key which will give us count of words that occurred for the label.
   Step-6: We count the total of number occurrences of the word. And restructure the tuple above to count the number of occurrences in ham label and spam label               for each word.
   Step-7: Join all the data and restructure such that we get (word, total_count, count_spam,count_ham) and then find the probabilities by dividing count_spam and            count_ham by total_count.
   Step-8: Now, for testing we go through each item from the dataset and for each word in the item we check if they are in the training dataset, if they exist                then we multiply the probabilities to already initialized spam and not spam variables. We initialize spam and notspam variables with prior                         probabilities. Then, based on the values of spam and notspam we predict the label. If probability of spam is more than ham then we label it as spam                else ham. There might be a case where all the words in testing data might not be in training data in that scenario we are marking it as Ham.
   Step-9: Now, we count the total number of times labeled matched to the total count which will give us accuracy.
   The accuracy of our model is 97.07112970711297.
