# 6133final_tutkuyaras
### Create a 100x100 numpy array (100x100 matrix), composed of random numbers. The random numbers should be integers and vary between [0, 100]
To create this numpy array some packages and tools are necessary. Before begining, these steps should be followed;
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
![p1](https://user-images.githubusercontent.com/82367415/150316549-17fe1249-7e9c-465e-aaa0-1e81940277eb.png)

3. You can change min and max values of constructed heat map. 
```bash
p1_1= sns.heatmap(array1, vmin=0, vmax=100)
p1_1
````
![p1_1](https://user-images.githubusercontent.com/82367415/150316528-eae5c9e6-9d29-4635-bee6-f0d813b7ef6f.png)

4. You can change the color of your heat map by using cmap variable, and also linewidth and linecolor could be determined.
```bash
p1_2 = sns.heatmap(array1, cmap="YlGnBu", linewidth = 0.5, linecolor = 'white')
p1_2
````
![p1_2](https://user-images.githubusercontent.com/82367415/150316540-807b43cb-8d0d-469f-a58d-e18552dbb58c.png)

5. You can determine range of your scale by using xticklabels. 
```bash
p1_3 = sns.heatmap(array1, xticklabels = 5, linewidth = 1, linecolor = 'white')
p1_3
````
![p1_3](https://user-images.githubusercontent.com/82367415/150316541-f6aff3c0-f0bc-43f7-8d5b-3cc5bb4989ea.png)

6. This is another example for xticklabels.
```bash
p1_4 = sns.heatmap(array1, xticklabels = 10, linewidth = 1, linecolor = 'white')
p1_4
````
![p1_4](https://user-images.githubusercontent.com/82367415/150316544-c91453a5-7b2f-4263-a1af-de96f7ca7e53.png)

7. You can remove x or y labels by defining false.
```bash
p1_5 = sns.heatmap(array1, xticklabels = 5, yticklabels = False, linewidth = 1, linecolor = 'white')
p1_5
````
![p1_5](https://user-images.githubusercontent.com/82367415/150316545-2f1edfd8-68ed-4f70-a01a-96336d4faa70.png)

8.This is another example for determinig max and min values of heat map.
```bash
p1_6 = sns.heatmap(array1, vmin=0, vmax=50)
p1_6
````
![p1_6](https://user-images.githubusercontent.com/82367415/150316547-ca8f9b08-331c-4179-8431-283ac3c44b85.png)

### Filter out the odd numbers. Then, if present, convert True/False statements into [0,1] values. Preserve the 100x100 array shape
To filter out odd and even numbers in our array we can use different codes. [lambda](https://realpython.com/python-lambda/) is one of the example.
>Here I created a loop according to whether the numbers are divisible by 2 or not. [numpy.zeroes](https://numpy.org/doc/stable/reference/generated/numpy.zeros.html) was used to give shape and type to new array. 
>>I assigned the values divisible by 2 to the value 0, and the non-divisible ones to the value 1. If you want you can assigned TRUE or FALSE boolean values instead of 1 or 0. However here we construct a heat map so i directly convert them into 0 and 1 values.
>>> Lastly, we have 100*100 array so we have to create 2 nested loops. Otherwise, we miss out on some values.
```bash
filter_arr = np.zeros((100, 100), dtype= int)
for element in range(0, len(array1)):
    for x in range(0, len(array1[element])):
        if array1[element,x] % 2 == 0:
            filter_arr[element, x] = int(0)
        else:
            filter_arr[element,x] = int(1)
            
print(filter_arr)
array1
````
>Output will look like this
````
[[0 0 0 ... 1 1 1]
 [1 0 0 ... 1 1 1]
 [0 0 1 ... 1 0 1]
 ...
 [0 1 0 ... 0 1 0]
 [0 0 1 ... 0 1 1]
 [0 1 0 ... 1 0 1]]
array([[84, 40, 92, ..., 39, 53, 71],
       [31, 58, 38, ..., 77,  9, 57],
       [26, 90, 63, ..., 49, 10, 59],
       ...,
       [62, 97, 14, ..., 58,  3, 92],
       [68, 64, 17, ..., 68, 27, 49],
       [18, 85, 38, ..., 35,  0, 23]])
````

1. Firstly, default heat map was constructed by using seaborn. This time we will only have 2 colors, because we only have values of 0 and 1.
```bash
p2 = sns.heatmap(filter_arr)
````
![p2](https://user-images.githubusercontent.com/82367415/150316553-604ae3f2-5dc4-454c-835c-96e07f74de90.png)

2. You can remove x and y labels and determine linewidth.
```bash
p2_1 = sns.heatmap(filter_arr, xticklabels = False, yticklabels = False, linewidth = 1, linecolor = 'white')
p2_1
````
![p2_1](https://user-images.githubusercontent.com/82367415/150316552-55a4beeb-72a6-4b2d-be91-24a9e1e05661.png)

>>>> You can find relevant codes on jupyter notebook, in [this repository](https://github.com/tutkuyaras/6133final_tutkuyaras) 


