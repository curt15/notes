Links: [[PYTHON]] - [[PROGRAMMING]] - [[MEDIA]]
Rel: 
Refs: 

Breadth vs depth search

--- 

## Grokking Algorithms: an illustrated guide for programmers and other curious people 


**Binary search** : guess the middle number and eliminate half the remaining numbers each time
- (100 ITEMS) -> (50) -> (25) -> (13) -> (7) -> (4) -> (2) -> **(1)** <- 7 steps (in the worst case)
- *logarithmic time* : np.log2(n) steps 
- vs n steps in **simple search** (~~100~~ -> ~~99~~ -> ~~98~~ -> ... )
- ** must be a sorted array-like for binary search!

as "big O notation":
- O(logn)
- O(n)

--- 

selection_sort

```py
#selection_sort.py

def find_smallest(arr):
	smallest = arr[0]
	smallest_index = 0
	for i in range(1, len(arr)):
		if arr[i] < smallest:
			smallest = arr[i]
			smallest_index = i
	return smallest_index

def selection_sort(arr):
	new_arr = []
	for i in range(len(arr)):
		smallest = find_smallest(arr)
		new_arr.append(arr.pop(smallest))
	return new_arr

print(selection_sort([5, 3, 6, 2, 10]))
```

--- 

binary_search

```py
#binary_search.py

def binary_search(num_list, item):
	low = 0
	high = len(num_list)-1
	while low <= high:
		mid = int((low + high)/2)
		guess = num_list[mid]
		if guess == item:
			return mid
		elif guess > item:
			high = mid - 1
		else:
			low = mid + 1
	return None
	
mylist = [1, 3, 5, 7, 9]
print(binary_search(mylist, 3))
print(binary_search(mylist, -1))
```