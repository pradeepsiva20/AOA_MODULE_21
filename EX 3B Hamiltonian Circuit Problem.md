# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.


## Algorithm
1. Start with a graph represented using an adjacency matrix and initialize a path list to store the Hamiltonian path.
2. Fix the first vertex in the path since the Hamiltonian path must start somewhere.
3. Use backtracking to add one vertex at a time to the path and check if it is safe to add by ensuring it’s adjacent and not already included.
4. If all vertices are added to the path and the last vertex connects to the first, a Hamiltonian cycle is found. 
5. If no such path can be formed, return false and conclude that no Hamiltonian path exists.
  

## Program:
```
/*
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by:PRADEEP S
Register Number:212222100034
*/
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices
    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
 
        return True
    def hamCycleUtil(self, path, pos):
        if pos==self.V:
            return True
        for v in range(1,self.V):
            if self.isSafe(v,pos,path):
                path[pos]=v
                if self.hamCycleUtil(path,pos+1):
                    return True
                path[pos]==-1
        return False
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
 
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
 
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();
```

## Output:
![image](https://github.com/user-attachments/assets/71bc2d15-4ae1-4998-9a8f-5f099ea0e9af)



## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
