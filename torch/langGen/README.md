## Language generation

Torch implementation for SNLI language generation experiment.

### Requirements
This code runs using torch. It is only tested on GPU. The following torch libraries are required:
nn, cunn, cudnn, optim, image, nngraph, hdf5


### SNLI dataset preparation


### Train
To train an ARAE generating SNLI language:
```
th main.lua
```
or the model trained using the context vector to initialize the first hidden state of RNN decoder:
```
th main.lua -init_dec 1
```
We found both settings obtain promising generation results.

The output folder: `${save_name}`, with structure
```
.
+-- ${save_name}
  +-- model_${epoch}.t7
  +-- ${epoch}.log
```

### Generation
To generate sentences similar to Figure 5 in the paper:
```
th generate.lua -model_file ${path_to_your_model}
```
Note the scripts support `-output_file` option if you want to cache the sentences and the corresponding `z` random vectors.

### Interpolation
Interpolation in the `z` space:
```
th interpolate.lua -model_file ${path_to_your_model}
```
Note the scripts support `-output_file` option if you want to cache the sentences and the corresponding `z` random vectors.

Some examples:
```
A man is elderly soldier stands .
A man carries is working of a woman .
An old man is looking through a .
An old kitten is looking at a soccer .
An old kitten is looking at a jumping .
A young dog is sitting on a next .
A child is sitting on a rocks .
A child sits near a jumping .
```
