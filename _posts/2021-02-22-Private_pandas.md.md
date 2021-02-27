---
title:  "Analyze Private datasets using Pandas"
layout: posts
mathjax: "true"
---

<p style="text-align:justify">Conventionally pandas allows you to analyze datasets that are present locally on your PC , that is when you are given access to a given dataset. 
But , there are valuable and informative datasets that consists of Personally Identifiable Information (PII) that you wont be able access to directly query it. There are privacy compliances that prevent data from being moved in some industries such as Banking and Healthcare. 
With the use of package GreyNSights you can leverage pandas to analyze and transform datasets that are sensitive. GreyNSights is stricly based on 
client-server implementation. The data owner hosts the dataset which begins a server that listens in to requests. The data analyst connects to the dataowner 
using client scripts of GreyNSights and can interactively query the dataset remotely.

<b>Repository: </b><a href="https://github.com/kamathhrishi/GreyNSights">Link</a>

</p>

<h1> Design Principles </h1>
<p style="text-align:justify">Some other approaches for analyzing and querying privacy sensitive datasets are uses anonymization techniques to obfusticate or remove PII's and then share the dataset. While , this seems like a promising approach. It could lead to linkage attacks. Analysts could reidentify anonymized data rows by linked it with other data sources. One such popular attack is the <a href="https://arxiv.org/abs/cs/0610105">Netflix attack</a>. The netflix dataset was anonymized and posted publicly, yet identity of the users could be recovered by linking with IMDB publicly available data.</p>
<p style="text-align:justify">Using anonymization techniques are not the best method of attaining privacy. This motivates the idea of being able to use PII's but such that the rows of PII's are not directly seen by the analyst. Further , analysts could also recover values of the individual rows using differencing attacks where they perform two queries one for the whole dataset and another excluing a given datapoint. Say one query where we calculate a sum with a given datapoint and another query without a given datapoint. Subtracting the values of both gives the value of a sensitive row. This attack is known as differencing attack. It could be mitigated by instead returning differentially private answers to queries rather than exact answers to queries. Differentially private results are query results to which well calibrated noise is added such that the result of a query is almost the same even if a given datapoint is not present. I have explained Differential Privacy in detail in my blogposts <a href="https://kamathhrishi.github.io/DPIntro/">DP Intro</a> and <a href="https://kamathhrishi.github.io/DPIntro/">DP Mechanisms</a>.</p>

<h1> Simple Example</h1>
<p style="text-align:justify">Below is an simple example where an data owner hosts a dataset on animals and carrots and the analyst queries it remotely. The example reproduces the official example of base Differential Privacy package PyDP. You can view the <a href="https://github.com/kamathhrishi/GreyNSights/tree/main/examples/carrots_demo">example</a> in the official repository.</p>

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

The below script allows the analyst to connect to the remote datasource. 

``` python 
import GreyNsights
from GreyNsights.analyst import DataWorker, DataSource, Pointer, Command, Analyst
from GreyNsights.frameworks import framework

"""The analyst identity. Currently just a placeholder and non-functional. But , in future could allow analyst to identify 
   with a x.509 certificate"""
   
identity = Analyst("Alice", port=65441, host="127.0.0.1")

#The details of remote datasource
worker = DataWorker(port=6544, host="127.0.0.1")

#The dataset hosted by remote datasource. Currently supports only 1 datasource. 
dataset = DataSource(identity,worker, "Sample Data")

#Initialization pointer
dataset_pt = dataset.init_pointer()

frameworks = framework()

#Initialize GreyNSights version of Pandas
pandas = frameworks.pandas

``` 

Just to depict that the GreyNSights version of Pandas could be used like ordinary Pandas. The dataset is already a dataframe. 
```
df = pandas.DataFrame(dataset_pt)
```

The command displays the columns of dataset
``` python
df.columns 
```

<p style="text-align:justify">Executes describe remotely , which returns a pointer and gets underlying value of it when get() is called. Describe is an aggregate query so the analyst is permitted to see the result.</p>
``` python
df.describe().get() 
```

Calculates mean , standard deviation and sum. 
``` python
df['carrots_eaten'].mean().get() 
```

``` python
df['carrots_eaten'].sum().get()
```

``` python
(df['carrots_eaten']>70).sum().get()
```
