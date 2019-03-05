# ai-bible-char-rnn

rewriting the world's oldest book with ai 
### or
exploring the interplay of artificial intelligence and religion using a multi-layer recurrent neural network for character-level language models trained on the bible.

## Requirements
[Tensorflow 1.2](http://www.tensorflow.org) or higher

hint: use anaconda to set up a tensorflow environment which you can activate up to your needs.

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



## Tuning

Tuning your models is kind of a "dark art" at this point. In general:

1. Start with as much clean input.txt as possible e.g. 50MiB
2. Start by establishing a baseline using the default settings.
3. Use tensorboard to compare all of your runs visually to aid in experimenting.
4. Tweak --rnn_size up somewhat from 128 if you have a lot of input data.
5. Tweak --num_layers from 2 to 3 but no higher unless you have experience.
6. Tweak --seq_length up from 50 based on the length of a valid input string
   (e.g. names are <= 12 characters, sentences may be up to 64 characters, etc).
   An lstm cell will "remember" for durations longer than this sequence, but the effect falls off for longer character distances.
7. Finally once you've done all that, only then would I suggest adding some dropout.
   Start with --output_keep_prob 0.8 and maybe end up with both --input_keep_prob 0.8 --output_keep_prob 0.5 only after exhausting all the above values.

## Tensorboard
You can use Tensorboard to visualize training progress, model graphs, and internal state histograms:  
fire up Tensorboard and point it at your `log_dir`.  E.g.:
```bash
$ tensorboard --logdir=./logs/
```
