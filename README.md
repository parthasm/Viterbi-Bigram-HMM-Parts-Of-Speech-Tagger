# Viterbi-Bigram-HMM-Parts-Of-Speech-Tagger

There are three python files in this submission - 
Viterbi_POS_WSJ.py, 
Viterbi_Reduced_POS_WSJ.py and 
Viterbi_POS_Universal.py. 

All 3 files use the Viterbi Algorithm with Bigram HMM taggers for predicting Parts of Speech(POS) tags. The baseline algorithm uses the most frequent tag for the word. The descriptions and outputs of each are given below:

###Viterbi_POS_WSJ.py
It uses the POS tags from the WSJ dataset as is. For the unknown words, the ‘NNP’ tag has been assigned. However, since the test sentence does not contain any word absent in the training document, tag assigned to the unknown words does not affect the accuracy of the Viterbi Algorithm.  


###Viterbi_Reduced_POS_WSJ.py
This uses the same WSJ dataset as before, however, the POS tags have been slightly simplified in the following way:

['NN','NNS','NNP','NNPS'] -> ‘N’
['VB','VBD','VBG','VBN','VBP','VBZ'] -> ‘V’
 ['JJ', 'JJR', 'JJS'] -> ‘ADJ’
['RB', 'RBR', 'RBS'] -> ‘ADV’
 ['PRP', 'PRP$', 'RP'] -> ‘PRO’

For the unknown words, the ‘N’ tag has been assigned. However, since the test sentence does not contain any word absent in the training document, tag assigned to the unknown words does not affect the accuracy of the Viterbi Algorithm.  


###Viterbi_POS_Universal.py
This file runs the Viterbi algorithm on the ‘government’ category of the brown corpus, after building the bigram HMM tagger on the ‘news’ category of the brown corpus. The assumption is that, since the two categories are somewhat related, training on one should give good performance on testing on the other. The tagset is the simplified ‘universal’ tagset. NLTK has been used to get the word tag pairs for each category but not for any other substantial purpose. For the unknown words, the ‘N’ tag has been assigned. Assigning the most frequent tag based on transition probabilities gives a worse performance than assigning the ‘N’ tag for unknown words.Since the algorithm is being run on a larger dataset, the time taken by the algorithm to train and run is also reported.

This file can be imported and its function fn_assign_POS_tags(words_list) can be directly used to get POS tags for words_list.

