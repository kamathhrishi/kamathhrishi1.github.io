---
title:  "Analyze Private datasets using Pandas"
layout: posts
mathjax: "true"
---

<p style="text-align:justify">Conventionally pandas allows you to analyze datasets that are present locally on your PC , that is when you are given access to a given dataset. 
But , there are valuable and informative datasets that consists of Personally Identifiable Information (PII) that you wont be access to directly query it.
With the use of package GreyNSights you can leverage pandas too analyze and transform datasets that are sensitive. GreyNSights is stricly based on 
client-server implementation. The data owner hosts the dataset which begins a server that listens in to requests. The data analyst connects to the dataowner 
using client scripts of GreyNSights and can interactively query the dataset remotely. </p>

<h1> Design Principles </h1>
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

<h1> Federated Analytics</h1>

<h2>Dataowners</h1>

<p style="text-align:justify">You can create several different data owners with different names and ports like the below scripts. </p>

```python 
import pandas
from GreyNsights.host import Dataset, DataOwner
from GreyNsights.config import Config

dataset = pandas.read_csv("week_data.csv")

owner = DataOwner("Bob", port=65444, host="127.0.0.1")

config = Config(owner)
config.load("test_config.yaml")

dataset = Dataset(owner, "Sample Data1", dataset, config, whitelist={"Alice": None})
dataset.listen()
``` 

<h2>Analyst</h2>

<p style="text-align:justify">The below script is how the analyst would query multiple dataowners together.</p>

```python

from GreyNsights.analyst import DataWorker, DataSource, Analyst, WorkerGroup
from GreyNsights.frameworks import framework

frameworks = framework()

pandas = frameworks.pandas

identity = Analyst("Alice", port=65441, host="127.0.0.1")

worker1 = DataWorker(port=65444, host="127.0.0.1")
dataset1 = DataSource(identity, worker1, "Sample Data1")
config1 = dataset1.get_config()
dataset1 = config1.approve().init_pointer()

worker2 = DataWorker(port=65446, host="127.0.0.1")
dataset2 = DataSource(identity, worker2, "Sample Data2")
config2 = dataset2.get_config()
dataset2 = config2.approve().init_pointer()

worker3 = DataWorker(port=65442, host="127.0.0.1")
dataset3 = DataSource(identity, worker3, "Sample Data3")
config3 = dataset3.get_config()
dataset3 = config3.approve().init_pointer()

group = WorkerGroup(identity)
group.add(dataset1, worker1, config1)
group.add(dataset2, worker2, config2)
group.add(dataset3, worker3, config3)

pt = group.init_pointer()

er = pt["Money spent (euros)"].sum() + pt["Money spent (euros)"].sum()
er = pt["Money spent (euros)"].sum().get()

print(er)

```
