# seq2seq-chatbot

**I've mostly stopped working on this project in favor of my newer implementation [neural-chatbot](https://github.com/inikdom/neural-chatbot) done with TensorFlow.


An implementation of Google's seq2seq architecture.

I am also simultaneously [blogging](http://domkaukinen.com/tag/seq2seq/) about the process.

##How to Use

First install torch if you haven't already. [Here](http://torch.ch/docs/getting-started.html#_) is an easy install process.

You will need to install a few packages to get this to work as well:

```bash
$ luarocks install nn
$ luarocks install rnn
```

Optional (for gpu usage):

```bash
$ luarocks install cunn
$ luarocks install cutorch
```
Or if you prefer AMD,

```bash
$ luarocks install clnn
$ luarocks install cltorch
```

If you get errors, you should try installing these packages as well:

```
$ luarocks install dpnn
$ luarocks install cunnx
```

You will need one or more large corpus text files with each line being a conversational phrase. The preceeding line is assumed to be the source, and the following line the target.

To simplify things, my plan is to either include a bash script that downloads a decent sized pre-cleaned corpus, or to actually include the corpus in the data directory. I will do this in the near future, probably after I finished the TODO list above.

##Examples of Usage and Training

Run

``$ th train.lua``

The dataset is stored in `data/raw/`, and comes from my other project [opensubtitles-parser](https://github.com/inikdom/opensubtitles-parser)


##A few notes:
- Some of this was borrowed from : [char-rnn](https://github.com/karpathy/char-rnn)
- This is based off of [Sutskever et al., 2014.](http://arxiv.org/abs/1409.3215) and [Vinyals & Le, 2015.](http://arxiv.org/pdf/1506.05869v1.pdf)
- The data this is being tested on is the OpenSubtitles dataset, I used [a script I made](https://github.com/inikdom/opensubtitles-parser) to tokenize and create the input output sequences
- I made heavy use of the rnn package provided by [Element Research](https://github.com/Element-Research/rnn)


##Unfinished TODO

1. Need to finish implementing prediction capabilities (ie/ actual chatbot interface for trained models)
2. Look into checkpointing system, each checkpoint seems to take 3.6G.. Something is clearly wrong there.
3. Need to profile code to check if there are unnecessary bottlenecks
4. More testing and algorithm verification
