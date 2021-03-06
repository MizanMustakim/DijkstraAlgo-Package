# DijsktraAlgorithm


Dijkstra's algorithm is an algorithm for finding the shortest paths between nodes in a graph. It was conceived by computer scientist **Edsger W. Dijkstra** in 1956 and published three years later.
Here, I used his method in python to find the shortest path and also the distance.

# Installing

Run the following code to install on your terminal:

```python
pip install DijkstraAlgo
```

# Feature

After importing the module, use [DijkstraAlgorithm()]() class. Then call the other methods whatever you want to use. Here the instances are given below:

```python
'''First Import our module'''
import DijkstraAlgo as da
'''Initializing the Class Attributes'''
x = da.DijkstraAlgorithm()

'''Now pass the arguments through the following method'''
x.dijkstraWithPath(graph, source, destination)  #Here, this graph is about the distance between each nodes.

'''Lets define more methods'''
shortest_path = x.path()    # The path between the source node and the destination node.
distance = x.distance()     # The distance of the shortest path what is already determined by x.path() earlier.

```

## Tutorial

In this part, you will see the procedure of implementing this package.

**For 2 Dimensional surface :**

Nodes are following the figure. You can also try your own.

![image](https://user-images.githubusercontent.com/56040932/107800170-a4098800-6d88-11eb-9e21-234e73987310.png)

Here, the distances between two nodes are 0.8 and 1.13 in linear and diagonal way, respectively. The nodes are adjacent here.

```python
# storing the distance between nodes in graph method as array.

graph = [
        [0, .8, 0, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #1
        [.8, 0, .8, 1.13, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #2
        [0, .8, 0, 0, 1.13, .8, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #3
        [.8, 1.13, 0, 0, .8, 0, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #4
        [1.13, .8, 1.13, .8, 0, .8, 1.13, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #5
        [0, 1.13, .8, 0, .8, 0, 0, 1.13, .8, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #6
        [0, 0, 0, .8, 1.13, 0, 0, .8, 0, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #7
        [0, 0, 0, 1.13, .8, 1.13, .8, 0, .8, 1.13, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #8
        [0, 0, 0, 0, 1.13, .8, 0, .8, 0, 0, 1.13, .8, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],#9
        [0, 0, 0, 0, 0, 0, .8, 1.13, 0, 0, .8, 0, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], #10
        [0, 0, 0, 0, 0, 0, 1.13, .8, 1.13, .8, 0, .8, 1.13, .8, 1.13, 0, 0, 0, 0, 0, 0, 0, 0, 0], #11
        [0, 0, 0, 0, 0, 0, 0, 1.13, .8, 0, .8, 0, 0, 1.13, .8, 0, 0, 0, 0, 0, 0, 0, 0, 0], #12
        [0, 0, 0, 0, 0, 0, 0, 0, 0, .8, 1.13, 0, 0, .8, 0, .8, 1.13, 0, 0, 0, 0, 0, 0, 0], #13
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 1.13, .8, 0, .8, 1.13, .8, 1.13, 0, 0, 0, 0, 0, 0], #14
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 0, .8, 0, 0, 1.13, .8, 0, 0, 0, 0, 0, 0], #15
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, .8, 1.13, 0, 0, .8, 0, .8, 1.13, 0, 0, 0, 0], #16
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 1.13, .8, 0, .8, 1.13, .8, 1.13, 0, 0, 0], #17 
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 0, .8, 0, 0, 1.13, .8, 0, 0, 0], #18
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, .8, 1.13, 0, 0, .8, 0, .8, 1.13, 0], #19
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 1.13, .8, 0, .8, 1.13, .8, 1.13], #20
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 0, .8, 0, 0, 1.13, .8], #21
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, .8, 1.13, 0, 0, .8, 0], #22
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 1.13, .8, 0, .8], #23
        [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1.13, .8, 0, .8, 0] #24
        ] 
```
Now, let's implement our package on this graph array. You will input the source node and the destination node on console. Here, the source node is the starting node of this model. You can choose any node as source node and destination node. For instance, if you choose the same node for both source and destination node, the distance between the nodes will show you zero.

```python
'''Importing our package'''

import DijkstraAlgo as da

def main():
    x = da.DijkstraAlgorithm()
    source = int(input("\nEnter the source: "))             # Get the input of the source value
    destination = int(input("Enter the destination: "))     # Get the input of the destination value
    x.dijkstraWithPath(graph, source, destination)

    shortest_path = x.path()
    distance = x.distance()

    print("\nThe shortest route: ")
    print(*shortest_path)   #It will print the path
    print("The shortest distance is {:.3f}".format(*distance))         #It will print the distance


if __name__ == '__main__':
    main()
```

<!-- **For 3 Dimensional surface** -->
You can also try this algorithm on 3 Dimensional model. 

For 3 Dimensional model, you can visit [Dijkstra Shortest Path Algorithm](https://github.com/MizanMustakim/Dijkstra-s-Shortest-Path-Algorithm)




**License**

GNU General Public License v2 or later (GPLv2+)


**Happy Coding!**
-