# discrete-maths-prac.
# program 1 without menu
# is member

```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    def is_member(self, elem):
        return elem in self.element   


A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])
```
# powerset
```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    

    def power_set(self):
        s = list(self.elements)
        return list(chain.from_iterable(combinations(s, r) for r in range(len(s) + 1)))


A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])


# 2. power_set
print("\nPower Set of A:")
for subset in A.power_set():
    print(set(subset))
         
```
# is_subset
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
    def is_subset(self, other_set):
        return self.elements.issubset(other_set.elements)

    
    
A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])

# 3. is_subset
print("\nA is subset of B:", A.is_subset(B))
print("B is subset of A:", B.is_subset(A))
```
# 4.union
```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
    def union(self, other_set):
        return self.elements.union(other_set.elements)

    
A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])





print("\nUnion of A and B:", A.union(B))
```
```
# 5. intersection
```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
    
    def intersection(self, other_set):
        return self.elements.intersection(other_set.elements)

    

A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])



print("Intersection of A and B:", A.intersection(B))

```
# 6. complement
```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
    def complement(self, universal_set):
        return universal_set.elements.difference(self.elements)

    
A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])


print("Complement of A (U - A):", A.complement(U))
print("Complement of B (U - B):", B.complement(U))

```
# 7.set diff.
```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    def is_member(self, elem):
        return elem in self.elements

    
    

    def set_difference(self, other_set):
        return self.elements.difference(other_set.elements)

    
A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])

print("A - B:", A.set_difference(B))
print("B - A:", B.set_difference(A))


```
# 8.symmetric
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
    def symmetric_difference(self, other_set):
        return self.elements.symmetric_difference(other_set.elements)

    def cartesian_product(self, other_set):
        return {(a, b) for a in self.elements for b in other_set.elements}



A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])

print("Symmetric Difference (A Δ B):", A.symmetric_difference(B))

```
# 9. Cartesian product
```
from itertools import chain, combinations

class SET:
    def __init__(self, elements=None):
        if elements is None:
            elements = []
        self.elements = set(elements)

    
    def cartesian_product(self, other_set):
        return {(a, b) for a in self.elements for b in other_set.elements}


A = SET(['1', '2', '3'])
B = SET(['3', '4', '5'])
U = SET(['1', '2', '3', '4', '5', '6'])



print("Cartesian Product (A × B):")
for pair in A.cartesian_product(B):
    print(pair)
```


**practical 2**
```
from numpy import array

class RELATION:
    def __init__(self, matrix):
        self.matrix = matrix
        self.length = len(matrix)
    
    def reflexive(self):
        for i in range(self.length):
            if not self.matrix[i][i]: 
                return False 
        return True 

    def symmetric(self):
        for i in range(self.length):
            for j in range(self.length):
                if self.matrix[i][j] != self.matrix[j][i]: 
                    return False 
        return True 

    def transitive(self):
        for i in range(self.length):
            for j in range(self.length):
                for k in range(self.length):
                    if self.matrix[i][j] and self.matrix[j][k] and not self.matrix[i][k]:
                        return False 
        return True 

    def anti_symmetric(self):
        for i in range(self.length):
            for j in range(self.length):
                if i != j and self.matrix[i][j] and self.matrix[j][i]: 
                    return False 
        return True 

def enter_matrix():
    lst = list(map(int, input("Enter all relation values in the form of a matrix with a space: ").split())) 
    row = int(input("Enter how many rows/columns in your square matrix: ")) 
    matrix = array(lst).reshape(row, row) 
    print("Your required matrix is: \n", matrix) 
    return matrix 

def main():
    rel = RELATION(enter_matrix())
    
    if rel.reflexive() and rel.symmetric() and rel.transitive():
        return "Your relation is an Equivalence Relation."
    elif rel.reflexive() and rel.anti_symmetric() and rel.transitive():
        return "Your relation is a Partial Order Relation."
    else:
        return "Your relation is neither an Equivalence nor a Partial Order Relation."

if __name__ == "__main__":
    print(main())
```


**practical 3**
```
from itertools import permutations, product

def generate_permutations(Set, repetition):
    if repetition:
        return list(permutations(Set, len(Set)))  # Permutations with repetition
    else:
        return list(product(Set, repeat=len(Set)))  # Cartesian product (product) without repetition

if __name__ == "__main__":
    # Taking input as a space-separated string of numbers and converting it into a set of integers
    Set = set(map(int, input("Enter all elements of set with space: ").split()))
    
    # Generate permutations with repetition
    with_repetition = generate_permutations(Set, repetition=True)
    
    # Generate permutations without repetition
    without_repetition = generate_permutations(Set, repetition=False)
    
    # Output the permutations
    print("Permutations with repetition:")
    for perm in with_repetition:
        print(perm)
    
    print("\nPermutations without repetition:")
    for perm in without_repetition:
        print(perm)
    
    # Print the lengths of both lists
    print("\nNumber of permutations with repetition:", len(with_repetition))
    print("Number of permutations without repetition:", len(without_repetition))
```

**practical 4**
```
from itertools import product

def find_solutions(n, C):
    solutions = []
    
    for combo in product(range(C+1), repeat=n):
        if sum(combo) == C:
            solutions.append(combo)
    
    return solutions

# Example usage (you can modify `n` and `C` as needed):
n = 3  # Number of variables
C = 5  # Constant sum value

solutions = find_solutions(n, C)

print(f"Solutions for x1 + x2 + ... + x{n} = {C}:")
for solution in solutions:
    print(solution)
```

**practical 5**

```
def solve_polynomial(): 
    # Input coefficients of the polynomial
    func = list(map(int, input("Enter Your Function coefficients Separated With Space:: ").split())) 
    # Input value of the variable
    num = int(input("Enter Value Of Your Variable:: ")) 
    
    value = 0
    # Loop through the coefficients and calculate the polynomial value
    for i in range(len(func)): 
        value += func[i] * num ** (len(func) - 1 - i)  # Exponent decreases with each term
    
    return value 

# Call the function and print the result
print(solve_polynomial())
```


**practical 6**
```
def is_complete_graph(matrix):
    n = len(matrix)  # Number of vertices (matrix size)

    # Traverse the adjacency matrix
    for i in range(n):
        for j in range(n):
            # Skip the diagonal elements
            if i != j:
                # If there is no edge between distinct vertices, return False
                if matrix[i][j] != 1:
                    return False
    return True

# Function to input the adjacency matrix from the user
def input_adjacency_matrix():
    n = int(input("Enter the number of vertices: "))
    matrix = []
    
    print("Enter the adjacency matrix (0 for no edge, 1 for edge):")
    for i in range(n):
        while True:
            try:
                row = list(map(int, input(f"Enter row {i+1}: ").split()))
                if len(row) != n:
                    print(f"Each row must have {n} elements. Please try again.")
                    continue
                matrix.append(row)
                break
            except ValueError:
                print("Invalid input. Please enter integers (0 or 1) only.")
    
    return matrix

# Main code
graph = input_adjacency_matrix()

if is_complete_graph(graph):
    print("The graph is a complete graph.")
else:
    print("The graph is not a complete graph.")
```


**practical-7**
```
class Graph:
    def __init__(self, vertices, graph_type):
        self.vertices = vertices
        self.graph_type = graph_type  # Add graph_type as a parameter in the constructor
        self.adj_list = [[] for _ in range(vertices)]

    def add_edge(self, u, v):
        if self.graph_type == 1:  # Undirected graph
            self.adj_list[u].append(v)
            self.adj_list[v].append(u)
        else:  # Directed graph
            self.adj_list[u].append(v)

    def is_complete(self):
        # Check if the graph is complete
        for i in range(self.vertices):
            for j in range(self.vertices):
                if i != j and j not in self.adj_list[i]:
                    return False
        return True

    def get_list(self):
        return self.adj_list

if __name__ == "__main__":
    # Input for graph type and number of vertices
    graph_type = int(input("Enter Your Graph Type (1. Undirected, 2. Directed): "))
    num_vertices = int(input("Enter number of vertices: "))

    # Create a graph object with the given number of vertices and graph type
    g = Graph(num_vertices, graph_type)

    # Input number of edges and edges themselves
    num = int(input("Enter number of edges: "))
    for i in range(num):
        a = int(input(f"Enter first vertex of edge {i+1}: "))
        b = int(input(f"Enter second vertex of edge {i+1}: "))
        g.add_edge(a, b)

    # Print the adjacency list (representing the graph)
    print("Your Adjacency List is:\n", g.get_list())

    # Check and print if the graph is complete or not
    if g.is_complete():
        print("The graph is a complete graph.")
    else:
        print("The graph is not a complete graph.")
```
# PRACTICAL_8
```
def compute_degrees():
    # Accept number of vertices
    n = int(input("Enter number of vertices: "))
    # Initialize adjacency list
    adj_list = [[] for _ in range(n)]
    # Accept number of edges
    e = int(input("Enter number of edges: "))
    print("Enter edges (from to):")
    for _ in range(e):
        u, v = map(int, input().split())
        adj_list[u].append(v)
    
    # Initialize in-degree and out-degree
    in_degree = [0] * n
    out_degree = [0] * n

    # Compute degrees
    for u in range(n):
        out_degree[u] = len(adj_list[u])
        for v in adj_list[u]:
            in_degree[v] += 1
    
    # Print the results
    print("\nVertex\tIn-Degree\tOut-Degree")
    for i in range(n):
        print(f"{i}\t{in_degree[i]}\t\t{out_degree[i]}")
# Run the program
compute_degrees()

```

****








