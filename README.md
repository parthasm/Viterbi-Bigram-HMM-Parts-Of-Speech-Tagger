# Viterbi-Bigram-HMM-Parts-Of-Speech-Tagger

There are three python files in this submission - 
Viterbi_POS_WSJ.py, 
Viterbi_Reduced_POS_WSJ.py and 
Viterbi_POS_Universal.py. 

All 3 files use the Viterbi Algorithm with Bigram HMM taggers for predicting Parts of Speech(POS) tags. The descriptions and outputs of each are given below:

Viterbi_POS_WSJ.py – It uses the POS tags from the WSJ dataset as is. For the unknown words, the ‘NNP’ tag has been assigned. However, since the test sentence does not contain any word absent in the training document, tag assigned to the unknown words does not affect the accuracy of the Viterbi Algorithm.  With this rich tagset, the Viterbi algorithm improves over the baseline.

Output
Fraction of errors (Baseline) : 0.153846153846
Fraction of errors (Viterbi): 0.0769230769231
Tags suggested by Baseline Algorithm: ['NNP', 'VBD', 'IN', 'VBN', 'NNP', 'VBN', 'TO', 'NNS', 'RB', 'CD', 'NN', 'IN', '.']
Tags suggested by Viterbi Algorithm: ['NNP', 'VBD', 'IN', 'VBD', 'NNP', 'VBN', 'TO', 'NNS', 'RB', 'CD', 'NN', 'IN', '.']
Correct tags: ['NNP', 'VBD', 'WDT', 'VBD', 'NNP', 'VBN', 'TO', 'NNS', 'RB', 'CD', 'NN', 'IN', '.']


Viterbi_Reduced_POS_WSJ.py – This uses the same WSJ dataset as before, however, the POS tags have been slightly simplified in the following way:

['NN','NNS','NNP','NNPS'] -> ‘N’
['VB','VBD','VBG','VBN','VBP','VBZ'] -> ‘V’
 ['JJ', 'JJR', 'JJS'] -> ‘ADJ’
['RB', 'RBR', 'RBS'] -> ‘ADV’
 ['PRP', 'PRP$', 'RP'] -> ‘PRO’

For the unknown words, the ‘N’ tag has been assigned. However, since the test sentence does not contain any word absent in the training document, tag assigned to the unknown words does not affect the accuracy of the Viterbi Algorithm.  Notably, as the tags are simplified, accuracy improves for the baseline algorithm. And unlike the 1st case, the Viterbi algorithm does not improve over the baseline. 

Output
Fraction of errors (Baseline) : 0.0769230769231
Fraction of errors (Viterbi): 0.0769230769231

Tags suggested by Baseline Algorithm: ['N', 'V', 'IN', 'V', 'N', 'V', 'TO', 'N', 'ADV', 'CD', 'N', 'IN', '.']
Tags suggested by Viterbi Algorithm: ['N', 'V', 'IN', 'V', 'N', 'V', 'TO', 'N', 'ADV', 'CD', 'N', 'IN', '.']
Correct tags: ['N', 'V', 'WDT', 'V', 'N', 'V', 'TO', 'N', 'ADV', 'CD', 'N', 'IN', '.']

Viterbi_POS_Universal.py – This file runs the Viterbi algorithm on the ‘government’ category of the brown corpus, after building the bigram HMM tagger on the ‘news’ category of the brown corpus. The assumption is that, since the two categories are somewhat related, training on one should give good performance on testing on the other. The tagset is the simplified ‘universal’ tagset. NLTK has been used to get the word tag pairs for each category but not for any other substantial purpose. For the unknown words, the ‘NOUN’ tag has been assigned. Assigning the most frequent tag based on transition probabilities gives a worse performance than assigning the ‘NOUN’ tag for unknown words.  Once again, on a simplified tagset, Viterbi shows no improvement over the baseline.  Since the algorithm is being run on a larger dataset, the time taken by the algorithm to train and run is also reported.

Output (Unknown word assigned tag based on transition probability)
 Fraction of errors (Baseline) : 0.0850150462798
Fraction of errors (Viterbi) : 0.0926166264957
8.63000011444 seconds
<Viterbi does worse than baseline>


Output (Unknown word assigned tag – “NOUN”)
Fraction of errors (Baseline) : 0.0850150462798
Fraction of errors (Viterbi) : 0.0850150462798
8.8029999733 seconds
<Viterbi does as good as basline>
