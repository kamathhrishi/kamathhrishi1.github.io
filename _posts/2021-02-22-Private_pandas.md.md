---
title:  "Analyze Private datasets using Pandas"
layout: posts
mathjax: "true"
---

<p style="text-align:justify">Conventionally pandas allows you to analyze datasets that are present locally on your PC , that is when you are given access to a given dataset. 
But , there are valuable and informative datasets that consists of Personally Identifiable Information (PII) that you wont be given access to.
With the use of package GreyNSights you can leverage pandas too analyze and transform datasets that are sensitive. GreyNSights is stricly based on 
client-server implementation. The data owner hosts the dataset which begins a server that listens in to requests. The data analyst connects to the dataowner 
using client scripts of GreyNSights and can interactively query the dataset remotely. </p>

<h1> Simple Example</h1>

<h2> Data Owner</h2>

``` python
import pandas
from GreyNsights.analyst import Pointer
from GreyNsights.host import Dataset, DataOwner
from GreyNsights.config import Config

dataset = pandas.read_csv(
    "animals_and_carrots.csv", sep=",", names=["animal", "carrots_eaten"]
)


owner = DataOwner("Bob", port=6544, host="127.0.0.1")

config = Config(owner)
config.load("test_config.yaml")

dataset = Dataset(owner, "Sample Data", dataset, config, whitelist={"Alice": None})
dataset.listen() 
```

<h2>Analyst</h2>

``` python 
import GreyNsights
from GreyNsights.analyst import DataWorker, DataSource, Pointer, Command, Analyst
from GreyNsights.frameworks import framework

identity = Analyst("Alice", port=65441, host="127.0.0.1")
worker = DataWorker(port=6544, host="127.0.0.1")
dataset = DataSource(identity,worker, "Sample Data")
dataset_pt = dataset.init_pointer()

frameworks = framework()
pandas = frameworks.pandas

df = pandas.DataFrame(dataset_pt)
``` 

``` python
df.columns 
```

``` python
df.describe().get() 
```

``` python
df['carrots_eaten'].mean().get() 
```

``` python
df['carrots_eaten'].sum().get()
```

``` python
(df['carrots_eaten']>70).sum().get()
```

