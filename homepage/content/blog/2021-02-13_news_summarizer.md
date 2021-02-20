+++
title = "🇫🇷 news summarizer"
Date = "2021-02-13"
+++

# 🇫🇷 news summarizer

Mon dernier petit projet est un bot reddit. 
Son but est de réagir aux liens vers un article de journal, par un résumé de cet article.

Je vais rédiger plusieurs articles pour expliquer comment ce bot marche

### 1. Résumer un texte, comment ca marche ?

Avec du machine learning ;) Fort heureusement pour moi, un modèle tout fait existait déja[^1]

Utiliser ce modèle est tres simple. Il fait partie de la bibliothèque transformers[^2] de Hugging Face[^3]
Huggingface c'est une bibliothèque de modèles de language. Beaucoup en anglais, quelques uns en Francais.
Ces modèles permettent d'effectuer des taches diverses représentées par des 'pipeline'.

Ainsi pour résumer un texte, il suffit de faire ceci:
```python
from transformers import pipeline
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer


model = AutoModelForSeq2SeqLM.from_pretrained("plguillou/t5-base-fr-sum-cnndm")
tokenizer = AutoTokenizer.from_pretrained("plguillou/t5-base-fr-sum-cnndm")
summarizer = pipeline('summarization', model=model, tokenizer=tokenizer)

text = """
« Il n’y a pas de fermeture généralisée des écoles » ni de « confinement » local, 
a fait savoir samedi 13 février le préfet de la Moselle, Laurent Touvet. 
Il s’exprimait lors d’un déplacement au CHR de Metz-Thionville et au lendemain 
d’une visite à Metz du ministre de la santé, Olivier Véran, qui avait 
annoncé plus de tests et de vaccins pour la Moselle, un département 
qui connaît une incidence plus élevée que le reste du territoire, 
notamment avec une progression du variant sud-africain.
"""

text = text.replace('\n', ' ')

summary = summarizer(text)
print(summary)
```

```shell
$ python summarize.py
Laurent Touvet : « Il n'y a pas de fermeture généralisée des écoles » ni de « confinement » local. 
Il s'exprime lors d'un déplacement au CHR de Metz-Thionville.
Le ministre de la santé, Olivier Véran, a annoncé plus de tests et de vaccins.
```




## References

[^1]: https://huggingface.co/plguillou/t5-base-fr-sum-cnndm
[^2]: https://github.com/huggingface/transformers
[^3]: https://huggingface.co