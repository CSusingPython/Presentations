#### Dask introduction



- flexible library for parallel computing in python

1. Dynamic task scheduling
2. "Big Data" collections : parallel arrays, dataframes, and lists -> run on top of dynamic task schedulers

![Dask collections and schedulers](http://docs.dask.org/en/latest/_images/collections-schedulers.png)



##### Familar user interface

```python
import dask.dataframe as dd
df = dd.read_csv('who.csv')
df.groupby(df.user_id).value.mean().compute()
```

- Dask DataFrame <- Pandas

- Dask Array <- NumPy
- Dask Bag <- iterators. Toolz, and PySpark
- Dask Delayed <- for loops and wraps custom code
- concurrent.futures interface provides general submisiion of custom tasks(???)

##### Scales from laptops to clusters

- installs with conda or pip
- extends the size of convenient datasets from "fits in memory" to "fits on disk"
- scale to a cluster of 100s of machines -> resilient, elastic, data local, and low latency

##### Complex Algorithms

- represents parallel computations with task graphs

참고) visualize task graph

```python
import dask.array as ds
x da.ones((15, 15), chunks=(5,5))
y = x + x.T
# y.compute()
y.visualize(filename='transpose.svg')
```

![Dask task graph for adding an array to its transpose](http://docs.dask.org/en/latest/_images/transpose.svg)





정말 간략하게 Dask에 대한 소개 정도만...