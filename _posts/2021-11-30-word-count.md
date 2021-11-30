---
layout: post
title: python - Word Count Visualization
tags: [NLP, dacon]
---


### 한 row의 길이 측정 후 hist

```python
def plot_word_number_histogram(text):
    text.str.split().map(lambda x:len(x)).hist() 

plot_word_number_histogram(train['text'])
```

### 모든 단어 길이 측정 수 hist

```python
import numpy as np 

def plot_word_length_histogram(text):
  text.str.split().apply(lambda x: [len(i) for i in x]).map(lambda x: np.mean(x)).hist()

plot_word_length_histogram(train['text'])
```