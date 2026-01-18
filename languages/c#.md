## Collections

### 1. List

```cs
var list = new List<int>({1,2,3,4,5});

// Add item
list.Add(6);

// Get item
var item = list[0];

// Add item at index
list.Insert(0, 10);

// Remove first occurance of item
list.Remove(1);

// Remove item at index
list.RemoveAt(0);

// Check if item exists
list.Contains(1);

// Get count
int count = list.Count;

// Clear list
list.Clear();

// Add array to list
var array = new int[] {1,2,3};
list.AddRange(array);

// Sort list
list.Sort();

// Binary Search
list.BinarySearch(5);

// Access a list (foreach loop)
foreach(var item in list){
    Console.Write(item);
}

// Access a list (for loop)
for(int i=0; i<list.Count; i++){
    Console.Write(list[i]);
}
```

### 2. SortedList

```cs
var sortedList = new SortedList<int, string>();

// Add item
list.Add(1, "Hello");

// Get item
var item = list[0];

// Check if key exists
list.ContainsKey(4);

// Remove key
list.Remove(10);

// Remove from index
list.RemoveAt(0);

// Iterate (foreach loop)
foreach(KeyValuePair<int, string> item in list){
    Console.Write(item.Key);
    Console.Write(item.Value);
}

// Iterate (for loop)
for(int i=0; i<list.Count; i++){
    Console.Write(list.Keys[i]);
    Console.Write(list.Values[i]);
}

```

### 3. Dictionary

```cs
var dictionary = new Disctionary<int, string>();

// Add item
dictionary.Add(1, "Hello");

// Get item
dictionary[1];

// Update item
dictionary[0] = "World";

// Remove item
dictionary.Remove(0);

// Clear
dictionary.Clear();

// Iterate (foreach loop)
foreach(var kvp in dictionary){
    Console.Write(kvp.Key);
    Console.Write(kvp.Value);
}

// Iterate (for loop)
for(int i=0; i<dictionary.Count; i++){
    var key = dictionary.ElementAt(i).Key;
    var value = dictionary.ElementAt(i).Value;
}
```

### 4. Stack

```cs
var stack = new Stack<int>();

// Add item
stack.Push(1);

// Get top item
Stack.Peek();

// Remove top item
Stack.Pop();

// Get Count
stack.Count;

// Check item exists
stack.Contains(1);

// Clear Stack
stack.Clear();

// Add array to stack
var array = new int[]{1,2,3,4,5};
var stack = new Stack<int>(array);

// Iterate foreach
foreach(var item in stack){
    Console.Write(item);
}
```

### 5. Queue

```cs
var queue = new Queue<int>();

// Add
queue.Enqueue(1);

// Remove
var item = queue.Dequeue();

// Get top item
var item = queue.Peek();

// Contains
var exists = queue.Contains(3);

// Iterate
foreach(var item in queue){
    Console.Write(item);
}

//Iterate & remove
while(queue.Count > 0){
    var item = queue.Dequeue();
}
```

### 6. HashSet

```cs
var set = new HashSet<int>();

// Add item
set.Add(1);

// Contains
set.Contains(1);

// Remove
set.Remove(1);

// Iterate
foreach(var item in set){
    Console.Write(item);
}
```
