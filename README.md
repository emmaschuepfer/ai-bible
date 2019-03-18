# ai-bible char-rnn

rewriting the world's oldest book with ai 
### or
exploring the interplay of artificial intelligence and religion using a multi-layer recurrent neural network for character-level language models trained on the bible

## Requirements
[Tensorflow 1.2](http://www.tensorflow.org) or higher

It's a good idea to use anaconda to set up a tensorflow environment which you can activate and modify up to your needs.

## Dataset
The bible dataset includes the whole bible as plain .txt file. 
You could use any other plain .txt file as input, too. 


## Training 
To train with default parameters on the bible data set, run `python train.py`. 

Training on a different dataset: from the top level directory run `python train.py --data_dir=./data/anyothertextfilefolder/`

To continue training after interruption or to run on more epochs, `python train.py --init_from=save`

Otherwise you can access all the parameters use `python train.py --help`.


## Sampling 
To sample from a checkpointed model (after training) run `python sample.py`.

Sampling while still training only works on CPU.


## Tensorboard
You can use Tensorboard to visualize training progress, model graphs, and internal state histograms:  
fire up Tensorboard and point it at your `log_dir`.  E.g.:
```bash
$ tensorboard --logdir=./logs/
```
