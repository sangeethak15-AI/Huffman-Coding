# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step 1:
Declare the string.

### Step 2:
Declare a class for creating nodes.

### Step 3:
Define a function to implement huffman coding.

### Step 4:
calculate the frequency for the gicen string.

### Step 5:
Display the huffman coding as output.

 
## Program:

``` Python
# Get the input String:
string="sangeetha 212221230085"

#Creating tree nodes:
class NodeTree(object):
    def __init__(self,left=None,right=None):
        self.left=left
        self.right=right
    def children(self):
        return (self.left,self.right)

# Main function to implement huffman coding:
def huffman_code_tree(node,left=True,binString=''):
    if type(node) is str:
        return {node:binString}
    (l,r)=node.children()
    d=dict()
    d.update(huffman_code_tree(l,True,binString+'0'))
    d.update(huffman_code_tree(r,False,binString+'1'))
    return d

# Calculate frequency of occurrence:
freq={}
for c in string:
    if c in freq:
        freq[c]+=1
    else:
        freq[c]=1
freq=sorted(freq.items(),key=lambda x:x[1],reverse=True)
nodes=freq

# Print the characters and its huffmancode
while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes=nodes[:-2]
    node=NodeTree(key1,key2)
    nodes.append((node,c1+c2))
    nodes=sorted(nodes,key=lambda x:x[1],reverse=True)
    
huffmanCode=huffman_code_tree(nodes[0][0])
print('Char | Huffman Code')
print('----------------------')
for(char,frequency) in freq:
    print('%-4r |%12s' % (char,huffmanCode[char]))

```
## Output:

### Print the characters and its huffmancode
![image](https://github.com/sangeethak15-AI/Huffman-Coding/assets/93992063/5d132735-349a-4df0-bd1b-463c9b3415fe)




## Result
Thus the huffman coding was implemented to compress the data using python programming.
