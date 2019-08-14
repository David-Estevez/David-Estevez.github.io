---
title: Keras
keywords: Keras, deep learning, machine learning, software
sidebar: home_sidebar
permalink: keras.html
folder: docs
summary: A collection of helpful resources and code snippets for working with Keras
---

# Generators

Example skeleton with all needed to build a Keras Generator:

```python
import numpy as np
from keras.utils import Sequence


class my_generator(Sequence):
    def __init__(self, data_file_ids, data_folder='.', batch_size=32, dims=(180, 240), shuffle=True):
        self.data_file_ids = data_file_ids
        self.data_folder = data_folder
        self.batch_size = batch_size
        self.dims = dims
        self.shuffle = shuffle
        self.on_epoch_end()

    def on_epoch_end(self):
        if self.shuffle:
            np.random.shuffle(self.data_file_ids)

    def _data_generation(self, files_to_load):
        
        ## (Code to generate X and y matrices goes here)

        return X, y

    def __len__(self):
        return int(np.floor(len(self.data_file_ids)/self.batch_size))

    def __getitem__(self, item):
        files_to_load = self.data_file_ids[item*self.batch_size:(item+1)*self.batch_size]
        X, y = self._data_generation(files_to_load)
        return X, y
```
