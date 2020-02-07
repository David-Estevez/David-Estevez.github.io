---
title: Python
keywords: Python, programming, software
sidebar: home_sidebar
permalink: python.html
folder: docs
summary: A collection of helpful resources and code snippets for working with Python
---

# Saving/loading Python objects to files

## With Pickle
[Pickle](https://docs.python.org/3/library/pickle.html) is a library for object serialization.

### Loading data

```python
    with open('file.pickle', 'rb') as f:
        obj = pickle.load(f)
```

### Saving data

```python
    with open("file.pickle", "wb") as f:
        pickle.dump(obj, f)
```
