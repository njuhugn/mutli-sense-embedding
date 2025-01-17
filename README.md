# Do Multi-Sense Embeddings Improve Natural Language Understanding

Implementations of multi-sense learning algorithm using Chinese Restaurant Process in "Do Multi-Sense Embeddings Improve Natural Language Understanding" by Jiwei Li and Dan Jurafsky, EMNLP 2015


## Input Files
train_file.txt: each line correponds to a sequence of indexed tokens.
frequency.txt: word occuring probability for each token found in train_file.txt. The first line in frequency.txt corresponds to the occuring probability for word indexed by 0, the second line  to the occuring probability of word 1 and so forth

## Parameters:
-load_embedding: if -load_embedding takes value of 1, the code will load already-learned gloabl embeddings, pre-stored in the following input variable "-embedding_file small_vect". If -load_embedding takes value of 0, the code would learn global embeddings from skip-gram.

## Output Files
"file_name"_vect_sense: 

word 0
sense0 0.9720543502482059
Meaning that sense 0 for 0th word has 0.986 of occuring probability, followed by the corresponding embedding for current sense. The probability is computed from Chinese Restaurant Processes, which will be used in the later sense induction procedure. 

if load_embedding takes value of 0, the code ouputs the calculated global embeddings. "file_name"_vect_global: each line corresponds to the learned embedding for an indexed word, e.g., the first line corresponds to embedding for word indexed by 0, second line to word 1, and so forth.

## Preprocessing
in directory Preprocessing, text.txt is a small sample of txt (a massively larger dataset is needed to train meaningful representations). Run:
python WordIndexNumDic.py vocabsize output_dictionary_file output_frequency_file output_index_file input_text_file, for example:
python WordIndexNumDic.py 20000 ../dictionary.txt ../frequency.txt ../train_file.txt text.txt

## Inference, given learned sense-specific embeddings, calculate the context-based sense embeddings.
sh inference.sh
input parameters: -isGreedy: whether adopt greedy strategy (taking value 1) or expectation strategy (taking value 0)

For any question, feel free to contact jiweil@stanford.edu



```latex
@article{li2015hierarchical,
    title={Do Multi-Sense Embeddings Improve Natural Language Understanding?},
    author={Li, Jiwei and Jurafsky, Dan},
    journal={EMNLP 2015},
    year={2015}
}
```
