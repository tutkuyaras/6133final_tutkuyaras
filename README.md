# 6133final_tutkuyaras
### Create a 100x100 numpy array (100x100 matrix), composed of random numbers. The random numbers should be integers and vary between [0, 100]
To create this numpy array some packages and tools are necessary. Before begining these steps should be followed;
1. Downloading jupyter notebook by using [Anaconda](https://www.anaconda.com/products/individual)
2. Launch `jupyter notebook` 
3. `numpy`package should be installed by using this command on jupyter 
```bash
conda install numpy
````
> This output shows numpy package is installed correctly.

```Collecting package metadata (current_repodata.json): done
Solving environment: done

# All requested packages already installed.

Note: you may need to restart the kernel to use updated packages.
```
4. Then to access and to introduce some commands on numpy; 
```bash
import numpy as np
````
5. To make 100*100 random integer array, numpy.random command could be used,for detailed information about [numpy.random](https://numpy.org/doc/stable/reference/random/index.html?highlight=random#module-numpy.random). 
```bash
array1 = np.random.randint(0, high = 101, size=(100,100))
`````
*The lowest value is included, and the highest value is excluded*
*So, 0 and 101 were chosen to stay between 0 and 100 to construct array*
> Output will look like this
````
array([[84, 40, 92, ..., 39, 53, 71],
       [31, 58, 38, ..., 77,  9, 57],
       [26, 90, 63, ..., 49, 10, 59],
       ...,
       [62, 97, 14, ..., 58,  3, 92],
       [68, 64, 17, ..., 68, 27, 49],
       [18, 85, 38, ..., 35,  0, 23]])
````
### Make a heatmap of this constructed array.
To create heatmap, there are some options, in here [seaborn](https://seaborn.pydata.org/generated/seaborn.heatmap.html) was used and for details website could be checked. 
1. Downloading seaborn , access and introduce to Python.
```bash
import seaborn as sns
````
2. Default code to construct heatmap;
```bash
p1 = sns.heatmap(array1)
````
