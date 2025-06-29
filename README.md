This is simple BERT-like LLM for text reconstruction.

The task is following:
We need to train LLM to reconstruct masked parts of text.
For this sake we first train tokenizer, then we define a dataset suitable for this problem, then we define a model and train it.

Here is example for harry potter dataset after 400 epochs:

orig:
```
[START] “ I didn ’ t chase it at him !” Harry said , his voice shaking with anger . “ It didn ’ t even touch him !”[END]
[START] “ No news about Mad - Eye ?” Harry asked Bill . [END]
[START] “ You ' ll need to drink all of this . Harry ,” she said . “ It ' s a potion for dreamless sleep .” [END]
```

mask:
```
[START] “ I didn ’ t chase it at [MASK] !” Harry said , [MASK] voice shaking with anger . “ [MASK] didn ’ t even touch him !”[END]
[START] [MASK] No news about Mad - Eye ?” Harry [MASK] Bill . [END]
[START] “ You ' [MASK] need [MASK] [MASK] all [MASK] this . [MASK] ,” she said . “ [MASK] ' s a potion for dreamless sleep .” [END]
```

recovered:
```
[START] “ I didn ’ t chase it at all !” Harry said , his voice shaking with anger . “ I didn ’ t even touch him !” [END]
[START] “ No news about Mad - Eye ?” Harry asked Bill . [END]
[START] “ You ' ll need to get all of this . Harry ,” she said . “ It ' s a potion for dreamless sleep .” please. [END]
```
