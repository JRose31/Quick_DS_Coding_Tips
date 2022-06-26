# Quick DS Coding Tips
> ## *General Python*

### Retrieving matching elements from two lists
> **`set([iterable]).intersection(others)`**

Create two lists of integers, containing some matching values. I've added some duplicates so we can see how these are handled as well.


```python
list1 = [1, 2, 3, 3, 5]
list2 = [1, 3, 5, 5, 7]
```

**Desired output**: A list containing individual values that are contained within both lists.
> **`[1, 3, 5]`**

---
One common approach is to:
* Create an empty list to hold matching values.
* Loop/Iterate through one list.
* Add a condition to check if the current value is in the second list.
* If the condition is true, add it to the list of matches.


```python
matches = []

for i in list1:
    if i in list2:
        matches.append(i)
        
matches
```




    [1, 3, 3, 5]



While this works, a duplicate `3` gets added to the list of matches. <br>

Swapping the list iterated through with, the list values are check against, yeilds similar results.


```python
matches = []

for i in list2:
    if i in list1:
        matches.append(i)
        
matches
```




    [1, 3, 5, 5]



A common solution may be to add another condition:
* *Create an empty list to hold matching values.*
* *Loop/Iterate through one list.*
* *Add a condition to check if the current value is in the second list.*
* **Add a condition to check that the value isn't already in the list of matches**
* *If **both** condition's are met, add it to the list of matches.*


```python
matches = []

for i in list1:
    if i in list2:
        if i not in matches:
            matches.append(i)
        
matches
```




    [1, 3, 5]



While this yeilds the desired output, the next solution is 40% faster and more readable.<br>

---


```python
set(list1).intersection(list2)
```




    {1, 3, 5}



<h4>Built-ins Explained</h4>

---
> **set:** *an unordered collection of distinct hashable objects. (mutable)*
>
> **intersection:** *Return a new set with elements common to the set and all others.*

<br>
And swapping list order doesn't change the result:
<br>

*Since the desired output was a list, change the type to a list.*


```python
list(set(list2).intersection(list1))
```




    [1, 3, 5]



<br>

---
Jamaine D. Roseborough Jr.<br>
[LinkedIn](https://www.linkedin.com/in/jamaine-roseborough-239b0616b/)
