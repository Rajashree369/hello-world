#Name: Rajashree SN
#USN: 1BM23AI142
#Section:3C


#Balanced Brackets
def is_balanced(s):
    stack = []
    bracket_map = {')': '(', '}': '{', ']': '['}
    for char in s:
        if char in bracket_map:
            # Pop from stack if there's a matching opening bracket
            top_element = stack.pop() if stack else '#'
            if top_element != bracket_map[char]:
                return "NO"
        else:
            stack.append(char)
    return "YES" if not stack else "NO"
t = int(input())
for _ in range(t):
    s = input().strip()
    print(is_balanced(s))
    
input:
{[()]}
{[(])}
{{[[(())]]}} 

output:
YES
NO
YES



#Queue using Two Stacks
class MyQueue:
    def __init__(self):
        self.stack_in = []
        self.stack_out = []

    def enqueue(self, x):
        self.stack_in.append(x)

    def dequeue(self):
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
        if self.stack_out:
            return self.stack_out.pop()
        else:
            return None 
t = int(input())  
queue = MyQueue()

for _ in range(t):
    operation = input().split()
    
    if operation[0] == "1":  
        queue.enqueue(int(operation[1]))
    elif operation[0] == "2":  
        print(queue.dequeue())

input:
6
1 42
1 14
2
1 28
2
2

output:
42
14
28




#Game of Two Stacks
def twoStacks(x, a, b):
    count = 0
    current_sum = 0
    i = 0
    j = 0
    while i < len(a) and current_sum + a[i] <= x:
        current_sum += a[i]
        i += 1
        count += 1
    while j < len(b) and i >= 0:
        current_sum += b[j]
        j += 1
        count += 1
        while current_sum > x and i > 0:
            i -= 1
            current_sum -= a[i]
            count -= 1
    return count
t = int(input()) 
for _ in range(t):
    x = int(input())  
    n, m = map(int, input().split()) 
    a = list(map(int, input().split()))  
    b = list(map(int, input().split())) 
    print(twoStacks(x, a, b))   


input:
1
10
4 4
1 2 3 4
1 2 3 4

output:
4
