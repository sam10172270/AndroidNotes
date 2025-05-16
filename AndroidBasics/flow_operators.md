🔥 Here’s your Flow Operators Cheatsheet — short, sharp, and copy-paste ready.

⸻

✅ combine()

combine(flowA, flowB) { a, b ->
    "$a + $b"
}

📌 Emits when either emits. Always gives latest of both.

⸻

✅ zip()

flowA.zip(flowB) { a, b ->
    "$a - $b"
}

📌 Emits when both emit once. Index-paired.

⸻

✅ merge()

merge(flowA, flowB)

📌 Emits all values from both flows as they come. Unordered.

⸻

✅ map()

flow.map { it.toUiModel() }

📌 Transform each emission.

⸻

✅ filter()

flow.filter { it.isNotBlank() }

📌 Emit only if condition passes.

⸻

✅ onEach()

flow.onEach { Log.d("TAG", it.toString()) }

📌 Side effects like logging or analytics.

⸻

✅ catch()

flow.catch { emit(fallback) }

📌 Handle errors gracefully.

⸻

✅ debounce()

flow.debounce(300)

📌 Delay after last input — best for search boxes.

⸻

✅ distinctUntilChanged()

flow.distinctUntilChanged()

📌 Skip repeated values. Prevents extra recomposition.

⸻

✅ flatMapConcat()

flowOf(1, 2, 3)
    .flatMapConcat { getPosts(it) }

📌 Sequential execution. One flow at a time.

⸻

✅ flatMapMerge()

flowOf(1, 2, 3)
    .flatMapMerge { getPosts(it) }

📌 Parallel execution. All flows start together.

⸻

✅ flatMapLatest()

searchQuery
    .debounce(300)
    .flatMapLatest { query -> search(query) }

📌 Cancels old request when new one comes. Live search.

⸻

✅ stateIn()

flow.stateIn(viewModelScope, SharingStarted.Eagerly, initialValue)

📌 Converts Flow to StateFlow. Keeps last value.

⸻

Want me to save this as a .md or .txt file for you to stash or print for interview prep?
