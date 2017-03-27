Genome Diagram
---

```python
>>> import numpy as np
>>> from varsig import genome_diagram as gd
>>> n = 105  # Length of randoim genomic interval.

>>> g = gd.GenomeDiagram()

# Plot a density of random data, interpolated and filled.
>>> track1 = gd.Graph('Random Density')
>>> track1.new_graph(x=np.arange(n),
>>>                  y=np.abs(np.random.randn(n)),
>>>                  fmt='interpolate',
>>>                  fill=True)
>>> g.add_track(track1)

# Plot 9 random interval features (random start, length, orientation, and color).
>>> track = gd.Feature('Random Intervals', height_ratio=0.4)
>>> for _ in range(9):
>>>     # Feature must follow iterable as (position, width, strand, color)
>>>     track.add_feature([np.random.randint(0, n -15),
>>>                        np.random.randint(0, 20),
>>>                        np.random.choice(['+', '-', 'none']),
>>>                        np.random.choice(['#E74C3C', '#3498DB', '0.2'])])
>>> g.add_track(track)

# Annotate the figure with interval specific metadata. Will always appear in lower-left
>>> g.annotation = '{}:{:,}-{:,}'.format('chr3', 20000, 812383)

>>> fig, axes = g.draw()
```

![test_interval](https://raw.githubusercontent.com/clintval/varsig/master/img/gd_test.png "Test Interval")
