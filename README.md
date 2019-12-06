# Lab7EditDist
"""
Elizabeth Rubio
Lab 7 
"""

def edit_dist(a, b):
    lena = len(a)+1
    lenb = len(b)+1
    matrix = [[0]*lena for i in range(lenb)]
    
    #populating the first row and coloum 0-n
    for i in range(len(matrix[0])):
        matrix[0][i] = i
    for j in range(len(matrix)):
        matrix[j][0] = j
     
    #populating the rest of the matrix
    for t in range(1, len(matrix)):
        for y in range(1, len(matrix[t])):
            if a[t-1] == b[y-1]:
                matrix[t][y] = matrix[t-1][y-1]
            else:
                #taking the minimum and adding one to replace the 0
                top = matrix[t-1][y]
                diag = matrix[t-1][y-1]
                prev = matrix[t][y-1]
                new_num = min(top, diag, prev)
                matrix[t][y] = new_num+1 
                
    return matrix[-1][-1]

def main():
    str1 = "money"
    str2 = "miner"
    dist = edit_dist(str1, str2)
    print("The ditance between ", str1, " and ", str2, " is ", dist)
    
main()
