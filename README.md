# discrete-maths-prac.   **practical 2**
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
