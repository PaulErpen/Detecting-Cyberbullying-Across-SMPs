# Detecting-Cyberbullying-Across-SMPs

This is the code for a reproducibility study done on the paper ["Deep Learning for Detecting Cyberbullying Across Multiple Social Media Platforms"](https://arxiv.org/pdf/1801.06482.pdf).
We fixed some bugs in the original code, which we forked from github.
After rerunning the scripts we received results that tell a very different story than that of the original paper.
Our main contribution was to create an environment for the code to run in and fix the bugs in the source code.
For this end users can either choose a conda environment if the run linux or to build a docer container that exposes a jupyter notebook server.

## Dataset

The three datasets used in the paper can be downloaded from [here](https://drive.google.com/open?id=11RMLCSIAO3dWk9ejSkVYc5tQwwK5pquG).

Please download the dataset and unzip at data/.

We have also used two different kind of embeddings for initialization which can be found at the mentioned links.

- [Sentiment Specific word embeddings (SSWE)](http://ir.hit.edu.cn/~dytang/paper/sswe/embedding-results.zip). This link is sadly down, which makes reproducing some of the results impossible.
- [GLoVe](https://nlp.stanford.edu/projects/glove/)

You need to download all available embeddings and unzip them to the `word_vectors` directory.

Sadly neither the data sets, nor the word embeddings can be provided via GitHub, since the files are too big.

## Purpose of the provided files

 - models.py : All the model architectures are defined in this file.
 - DNNs.ipynb : This notebook is responsible for training DNN models with three methods to initialize word embeddings.
 - TraditionalML.ipynb : The results from training ML models such as SYM, Naive Bayes, etc can be generated using this nnotebook.
 - Transfer Learning.ipynb : We used transfer learning to check if the knowledge gained by DNN models on one dataset can be used to improve cyberbullying detection performance on other datasets. The code for the same is available in this file.
 - reload_dumps.ipynb : This script was used to reload the predictions of the models, which can be saved to csv. This is very useful when retrieving the results.
 - Significance_testing.ipynb : This script can be used to run significance testing to compare the differences between traditional ML and DNNs as well as oversampled and non-oversampled training data. We used McNemar's test.
 
## Creating and activating a virtual environment to run this code 

```
conda env create -f environment.yml
conda activate cyberbullying
```

To remove use:
```
conda env remove --name cyberbullying
```

## Building and running code via docker

Please build from the root directory of this project.
The `data` and the `word_vectors` folders need to have contents.
```
docker build -t cyberbullying:latest -f .\docker\Dockerfile .
```

```
docker run -p 8796:8796 cyberbullying:latest
```
After running docker build you can retrieve the sign-in token for jupyter from the console.

You can also retrieve the token by connecting to the container and running:
```
jupyter notebook list
```