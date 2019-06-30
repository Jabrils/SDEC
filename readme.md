# Sequence-Domain Encompassed Correlations (SDEC)
## Official Repo v0.1.0

## Notes
- Yo! sorry this is currently a mess. SDEC was created in response to a challenge from @MarkRober to figure out some sequential steal encodings. I was really just running & gunning under a deadline so a lot of code here is ugly & confusing, but ill be updating this rep from here on out.

## So What is SDEC?
**So SDEC stands for Sequence-Domain Encompassed Correlations, & it's purpose is to take the entire domain of a given series of seqences, & encode it's encompassed correlations. This is done by defining what's called a "resolution" to limit how many correlations you want the your model to learn from.**

## What you will need:
|Need|Description
|---|---
|ML / Tensorflow / Keras Understanding|This isn't actually needed, I think you would be able to get by without it, but you may hit a point in which it might be hard to debug whats going on without this knowledge, just be warned :D
|A Dataset|Now I have a faux dataset located @[legacy/hadouken_data_test](legacy/hadouken_data_test), there are a few models in there as well if you want to try that out, but you could also supply your own dataset.
|Neural Network Architecture|SDEC is simply a sequence encoder, you will still need to optimize your own Neural Network architectures. You can modify this in the script [train.py](train.py) line 60

## How to encode a Dataset:

- SDEC is made to work with sequences only
- If you can encode all features of a single step in your time series (or sequence) into a single representation, SDEC should work well for you. 
- Your sequences must be encoded using [ASCII](http://www.asciitable.com/)  (untested on utc-8 or 16)


## How to Use SDEC:
You'll want to run [hub.py](hub.py) in the terminal, use the line below to get further instructions on how to use it

    python hub.py -h

This will return the following:

```
optional arguments:
  -h, --help            show this help message and exit
  -mn MODEL_NAME, --model_name MODEL_NAME
                        the name you want your model to be saved as (default:
                        model)
  -f FILE, --file FILE  the name you want your model to be saved as (default:
                        train.txt)
  -md MODELS_DIR, --models_dir MODELS_DIR
                        the location you want your models to be saved in
                        (default: models)
  -dd DATA_DIR, --data_dir DATA_DIR
                        the location containing your data (default: data)
  -e EPOCHS, --epochs EPOCHS
                        use -e to set the number of epochs for training
                        (default: 100)
  -sr SAVE_RATE, --save_rate SAVE_RATE
                        use -sr to set the save rate per x epochs (default:
                        100)
  -T TOP, --top TOP     use -t to (default: 3)
  -b BATCHES, --batches BATCHES
                        use -b to set the number to batch for training
                        (default: 2048)
  -spe STEPS_PER_E, --steps_per_e STEPS_PER_E
                        use -spe to set the number of steps per epochs for
                        training (default: 0)
  -rlf RL_FACTOR, --rl_factor RL_FACTOR
                        use -spe to set the number of steps per epochs for
                        training (default: 0.5)
  -rlp RL_PATIENCE, --rl_patience RL_PATIENCE
                        use -spe to set the number of steps per epochs for
                        training (default: 105)
  -res RESOLUTION [RESOLUTION ...], --resolution RESOLUTION [RESOLUTION ...]
                        use -res to set the resolution (default: [2, 3])
  -t, --train           add -t if you want to train (default: False)
  -ho, --handoff        add -ho if you want to the AI to plot a distr & hand
                        it off to you (default: False)
  -hom, --handoffmulti  add -hom if you want to the AI to plot a distr & hand
                        it off to you (default: False)
  -i, --init            add -i if you want to initilize from some data
                        (default: False)
  -p, --predict         add -p if you want to predict (default: False)
  -lm, --load_model     add -lm if you want to load the model for further
                        training (default: False)
```

### Clear Steps

1. Understand your domain
    - This includes every possible event that can occur in your time series or sequence
1. Encode your domain to have their own unique [ASCII](http://www.asciitable.com/) representation
1. Create a .txt file with every single sequence [ASCII](http://www.asciitable.com/)  encoded, with a label next to it separated with a \t (tab), & new datapoints separated by \n (new line)
1. Use [hub.py](hub.py) with the -i flag to initialize a config file for your dataset
1. Use [hub.py](hub.py) with the -t flag to train on your dataset
    - You must also point to the file that you want to train on
1. Use [hub.py](hub.py) with the -p flag to predict on a dataset
    - You must also point to the file that you want to predict on, as well as the model that you want to use to predict


## Roadmap

**[click here](changelog.md) to see full changelog.**

|Task
|---
|Better error messages
|Classification on more than binary output
|Adding an "Unknown" representation so unknown don't return errors.
|Adding subprocesses to the [hub.py](hub.py) script for less confusion with -h
|SDEC can process seqences that are shorter than the encoding (this might be for gendataset.py only lol)
|save `conf.mc` anytime you save a model
|Clean up the scripts
|Get Benchmarks

## Usecases

|Use|Details
|---|---
|Discover Hidden Codes|Consider you have a sequence that contains hidden codes within it, SDEC can be used to decipher those hidden codes, so long as the code has some sort of sequential dependency.
|Classify Sequences (only binary for now)|SDEC can be used to classify sequences.