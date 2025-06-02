# EX 3D Pattern Matching
## DATE:
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.



## Algorithm
1. Start by reading the input string (txt) and the pattern (pat) to search within the string.
2. Iterate through the main string from index 0 to (N - M), where N is the length of the string and M is the length of the pattern.
3. For each index i, compare the pattern with the substring of txt starting at i.
4. If a mismatch is found, move to the next index in txt; if a match is found, return or print the index where the match starts. 
5. Repeat this until the entire string is scanned or a match is found.  

## Program:
```
/*
Program to implement the Pattern Matching.
Developed by: PRADEEP S
Register Number: 212222100034
*/

def KMPSearch(pat, txt):
    M = len(pat)
    N = len(txt)
    lps = [0]*M
    j=0
    
    computeLPSArray(pat,M,lps)
    i=0
    
    while (N-i) >= (M-j):
        if pat[j] == txt[i]:
            i+=1
            j+=1
        if j == M:
            print("Found pattern at index "+ str(i-j))
            j=lps[j-1]
        
        elif i < N and pat[j] != txt[i]:
            if j != 0:
                j = lps[j-1]
            else:
                i+=1
            
    
def computeLPSArray(pat, M, lps):
    len = 0 
 
    lps[0] 
    i = 1
    while i < M:
        if pat[i]== pat[len]:
            len += 1
            lps[i] = len
            i += 1
        else:
            if len != 0:
                len = lps[len-1]
            else:
                lps[i] = 0
                i += 1
txt = input()                      
pat = input()
KMPSearch(pat, txt)


```

## Output:
![image](https://github.com/user-attachments/assets/213030bc-8bd4-479d-b3b0-d27a1197c946)



## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
