🔥 Here’s your ultimate Kotlin Operators Cheatsheet — short, clear, and 100% copy-paste ready.

⸻

🔁 Transformation Operators

list.map { it * 2 }
// Transform each element

list.flatMap { listOf(it, it * 2) }
// Expand each to a list and flatten

list.filter { it > 0 }
// Keep only matching elements


⸻

🧮 Aggregation Operators

list.fold(10) { acc, item -> acc + item }
// Reduce to single value starting from 10

list.reduce { acc, item -> acc + item }
// Same as fold but uses first item as seed

list.sum()
// Total sum (for numeric lists)

list.average()
// Mean of numeric list


⸻

🔗 Zipping & Pairing

listA.zip(listB)
// Combine two lists index-wise

listA.zipWithNext()
// Pair each element with its next


⸻

🔍 Lookup & Grouping

list.associateBy { it.id }
// Map of id → element

list.groupBy { it.type }
// Map of type → list of elements

list.associate { it.id to it.name }
// Custom key-value pairing


⸻

🔢 Slicing & Subsetting

list.take(3)
// First 3 items

list.drop(2)
// Skip first 2

list.chunked(2)
// Break into groups of 2

list.windowed(3)
// Moving window of size 3


⸻

🧪 Checking & Finding

list.contains(x)
// true if x exists

list.any { it > 0 }
// true if any matches

list.all { it.isValid }
// true if all match

list.none { it == 0 }
// true if none match

list.firstOrNull { it.startsWith("A") }
// Safe find


⸻

🔄 Sorting

list.sorted()
// Ascending

list.sortedBy { it.age }
// Sort by field

list.reversed()
// Reverse list


⸻

⚒️ Modification (Immutable)

list + newItem
// Add item

list - item
// Remove item

list.distinct()
// Remove duplicates


⸻

🧠 Special

list.joinToString()
// "1, 2, 3"

list.isEmpty()
list.isNotEmpty()


⸻

✅ TL;DR: Quick 1-liner Use Map

Goal	Operator
Transform	map
Filter	filter
Flatten list of lists	flatMap
Group items	groupBy
Fast lookup	associateBy
Pair two lists	zip
Aggregate result	fold / reduce
Find items	firstOrNull, any
Take/drop items	take, drop
Chunk or windowed	chunked, windowed


⸻

Want a .txt or .md file version of this? Or want the Flow operator version too in one sheet?
