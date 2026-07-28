
<h1>Python Constructs Used Throughout AI/ML Code</h1>

<p>
The difficulty in reading PyTorch, TensorFlow, LangChain, Hugging Face, FastAPI, or LangGraph code rarely comes from basic Python (<code>if</code>, <code>for</code>, lists). It comes from a recurring set of language features these libraries lean on heavily. Learn these once and most AI codebases become readable.
</p>

<hr>

<details open>
<summary><h3 style="display:inline;">1. Assignment &amp; Expression Syntax</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>Walrus operator</td><td><code>while (line := file.readline()):</code></td><td>Assigns a value and evaluates it in the same expression — avoids a separate assignment line before the check</td></tr>
<tr><td>Multiple assignment</td><td><code>x, y = 5, 10</code></td><td>Assigns several variables in one line</td></tr>
<tr><td>Variable swap</td><td><code>a, b = b, a</code></td><td>Swaps two values without a temporary variable</td></tr>
<tr><td>Unpacking</td><td><code>x, y, z = nums</code></td><td>Splits an iterable into named variables</td></tr>
<tr><td>Extended unpacking</td><td><code>first, *middle, last = nums</code></td><td>Captures the first/last elements and collects the rest into a list</td></tr>
<tr><td>Ignoring values</td><td><code>name, _, age = data</code></td><td>Uses <code>_</code> as a throwaway variable for a value you don't need</td></tr>
<tr><td>Chained assignment</td><td><code>a = b = c = 0</code></td><td>Assigns the same value to multiple variables at once</td></tr>
<tr><td>Conditional (ternary) expression</td><td><code>result = "Pass" if score > 50 else "Fail"</code></td><td>Inline if/else that returns a value instead of executing a block</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">2. Loops &amp; Iteration Helpers</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>enumerate()</code></td><td><code>for i, value in enumerate(data):</code></td><td>Gives both index and value while looping, avoiding manual <code>range(len(...))</code> indexing</td></tr>
<tr><td><code>zip()</code></td><td><code>for x, y in zip(xs, ys):</code></td><td>Loops over two or more iterables in parallel — common when pairing inputs with labels</td></tr>
<tr><td><code>reversed()</code></td><td><code>for x in reversed(nums):</code></td><td>Iterates in reverse order without modifying the original sequence</td></tr>
<tr><td><code>sorted(key=...)</code></td><td><code>sorted(users, key=lambda x: x.age)</code></td><td>Sorts using a custom key function instead of default ordering</td></tr>
<tr><td>Dictionary iteration</td><td><code>for k, v in d.items():</code> / <code>.keys()</code> / <code>.values()</code></td><td>Iterates over key-value pairs, keys only, or values only</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">3. Comprehensions</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>List comprehension</td><td><code>[x*x for x in nums]</code></td><td>Builds a list in one line instead of a loop with <code>.append()</code></td></tr>
<tr><td>Filtered comprehension</td><td><code>[x for x in nums if x % 2 == 0]</code></td><td>Builds a list while filtering elements with a condition</td></tr>
<tr><td>Dictionary comprehension</td><td><code>{x: x*x for x in nums}</code></td><td>Builds a dictionary in one line</td></tr>
<tr><td>Set comprehension</td><td><code>{x for x in nums}</code></td><td>Builds a set (unique values) in one line</td></tr>
<tr><td>Generator expression</td><td><code>(x*x for x in nums)</code></td><td>Same syntax as a list comprehension but produces values lazily instead of building the full list in memory</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">4. Functions &amp; Arguments</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>Lambda</td><td><code>lambda x: x + 1</code></td><td>Defines a small anonymous function inline, commonly passed into <code>sorted()</code>, <code>map()</code>, <code>filter()</code></td></tr>
<tr><td><code>*args</code></td><td><code>def f(*args):</code></td><td>Collects any number of positional arguments into a tuple</td></tr>
<tr><td><code>**kwargs</code></td><td><code>def f(**kwargs):</code></td><td>Collects any number of keyword arguments into a dictionary — heavily used in AI library APIs</td></tr>
<tr><td>Argument unpacking</td><td><code>func(*values)</code> / <code>func(**config)</code></td><td>Expands a list/tuple into positional arguments, or a dictionary into keyword arguments</td></tr>
<tr><td>Config-as-kwargs pattern</td><td><code>model.generate(**config)</code> where <code>config = {"temperature": 0.7, "max_tokens": 100}</code></td><td>Passes an entire settings dictionary as named arguments in one call — the standard pattern for model/API configuration</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">5. Dictionaries</h3></summary>

<p>Arguably the most-used data structure in AI code — used for configs, API payloads, and token/label mappings.</p>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>Create</td><td><code>d = {}</code></td><td>Initializes an empty dictionary</td></tr>
<tr><td>Access</td><td><code>d["name"]</code></td><td>Retrieves a value by key; raises an error if the key is missing</td></tr>
<tr><td>Safe access</td><td><code>d.get("name")</code></td><td>Retrieves a value by key, returning <code>None</code> (or a default) instead of raising an error</td></tr>
<tr><td>Default on insert</td><td><code>d.setdefault("count", 0)</code></td><td>Returns a key's value, inserting a default first if the key doesn't already exist</td></tr>
<tr><td>Update</td><td><code>d.update(other)</code></td><td>Merges another dictionary's keys/values into this one, in place</td></tr>
<tr><td>Merge (Python 3.9+)</td><td><code>new = d1 | d2</code></td><td>Creates a new dictionary by merging two others without mutating either</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">6. Iterators &amp; Generators</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>yield</code></td><td><code>def numbers(): yield 1; yield 2</code></td><td>Produces values one at a time (lazily) instead of returning a full collection at once — core to data loaders, training batches, and streaming LLM output</td></tr>
<tr><td><code>iter()</code></td><td><code>it = iter(data)</code></td><td>Converts an iterable into an iterator object</td></tr>
<tr><td><code>next()</code></td><td><code>next(it)</code></td><td>Pulls the next value from an iterator</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">7. Context Managers (<code>with</code>)</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>File handling</td><td><code>with open("data.txt") as f:</code></td><td>Opens a resource and guarantees it's closed automatically afterward, even if an error occurs</td></tr>
<tr><td>Database session</td><td><code>with Session() as db:</code></td><td>Opens and safely closes a database session</td></tr>
<tr><td>Gradient control</td><td><code>with torch.no_grad():</code></td><td>Temporarily disables gradient tracking in PyTorch — standard during inference/evaluation</td></tr>
<tr><td>Locking</td><td><code>with lock:</code></td><td>Acquires a thread lock and guarantees release afterward</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">8. Mapping &amp; Aggregate Functions</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>map()</code></td><td><code>list(map(str, nums))</code></td><td>Applies a function to every element of an iterable</td></tr>
<tr><td><code>filter()</code></td><td><code>list(filter(lambda x: x > 0, nums))</code></td><td>Keeps only elements that satisfy a condition</td></tr>
<tr><td><code>any()</code></td><td><code>any(scores)</code></td><td>Returns <code>True</code> if at least one element is truthy</td></tr>
<tr><td><code>all()</code></td><td><code>all(scores)</code></td><td>Returns <code>True</code> only if every element is truthy</td></tr>
<tr><td><code>sum()</code></td><td><code>sum(losses)</code></td><td>Adds up all elements — commonly used for total loss across batches</td></tr>
<tr><td><code>max()</code> / <code>min()</code></td><td><code>max(data)</code></td><td>Returns the largest/smallest value in an iterable</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">9. Pattern Matching (Python 3.10+)</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>match</code> / <code>case</code></td><td><code>match token: case "ADD": ... case _: ...</code></td><td>Structural pattern matching — a cleaner alternative to long <code>if</code>/<code>elif</code> chains, useful for parsing tokens, commands, or agent actions</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">10. Exception Handling</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>try</code> / <code>except</code> / <code>finally</code></td><td><code>try: ... except ValueError: ... finally: ...</code></td><td>Runs code that might fail, handles specific error types, and optionally runs cleanup code regardless of outcome</td></tr>
<tr><td><code>raise</code></td><td><code>raise Exception("Error")</code></td><td>Manually triggers an exception</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">11. Useful Built-ins</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>len()</code></td><td><code>len(x)</code></td><td>Returns the number of items in a collection</td></tr>
<tr><td><code>type()</code></td><td><code>type(x)</code></td><td>Returns an object's exact type</td></tr>
<tr><td><code>isinstance()</code></td><td><code>isinstance(x, list)</code></td><td>Checks whether an object is an instance of a type (or one of several types)</td></tr>
<tr><td>Type conversion</td><td><code>int()</code>, <code>float()</code>, <code>str()</code>, <code>list()</code>, <code>dict()</code>, <code>set()</code>, <code>tuple()</code></td><td>Converts a value from one type to another</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">12. Copying</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>Shallow copy</td><td><code>copy.copy(obj)</code></td><td>Copies an object one level deep — nested objects are still shared with the original</td></tr>
<tr><td>Deep copy</td><td><code>copy.deepcopy(obj)</code></td><td>Fully copies an object and everything nested inside it — important when duplicating model configs so edits don't affect the original</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">13. <code>collections</code> Module</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>Counter</code></td><td><code>Counter(words)</code></td><td>Counts occurrences of each item in an iterable — common for word/token frequency</td></tr>
<tr><td><code>defaultdict</code></td><td><code>defaultdict(list)</code></td><td>A dictionary that auto-creates a default value for missing keys instead of raising an error</td></tr>
<tr><td><code>deque</code></td><td><code>deque()</code></td><td>A double-ended queue with fast appends/pops from both ends — used in BFS and sliding-window operations</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">14. <code>itertools</code> Module</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>product()</code></td><td><code>from itertools import product</code></td><td>Generates the Cartesian product of input iterables</td></tr>
<tr><td><code>combinations()</code></td><td><code>combinations(...)</code></td><td>Generates all unordered combinations of a given length</td></tr>
<tr><td><code>permutations()</code></td><td><code>permutations(...)</code></td><td>Generates all ordered arrangements of a given length</td></tr>
<tr><td><code>chain()</code></td><td><code>chain(...)</code></td><td>Iterates over multiple iterables as if they were one continuous sequence</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">15. <code>operator</code> Module</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>itemgetter</code></td><td><code>from operator import itemgetter</code></td><td>A faster, more readable alternative to <code>lambda x: x[1]</code> when used as a sort/access key</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">16. Type Hints &amp; Data Validation</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td>Function type hints</td><td><code>def train(data: list[str]) -> dict:</code></td><td>Documents expected input/output types — improves readability and editor autocompletion</td></tr>
<tr><td><code>Optional</code></td><td><code>from typing import Optional</code></td><td>Marks a value as either a given type or <code>None</code></td></tr>
<tr><td>Union types</td><td><code>int | None</code></td><td>Shorthand (Python 3.10+) for a value that can be one of several types</td></tr>
<tr><td><code>TypedDict</code></td><td><code>from typing import TypedDict</code></td><td>Defines a dictionary with a fixed, typed shape — commonly used for LangGraph state objects</td></tr>
<tr><td><code>BaseModel</code> (Pydantic)</td><td><code>from pydantic import BaseModel</code></td><td>Defines a data schema with automatic validation — the standard way to structure API and LLM output data</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">17. Dataclasses</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>@dataclass</code></td><td><code>@dataclass class Config: lr: float; epochs: int</code></td><td>Auto-generates <code>__init__</code>, <code>__repr__</code>, and comparison methods for a class — the standard pattern for configuration objects</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">18. File Paths &amp; Data I/O</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>pathlib</code></td><td><code>Path("data") / "train.csv"</code></td><td>A more readable, cross-platform way to build file paths than string-based <code>os.path.join(...)</code></td></tr>
<tr><td>JSON load</td><td><code>json.load(file)</code></td><td>Reads JSON from a file object into a Python object</td></tr>
<tr><td>JSON dump</td><td><code>json.dump(data, file)</code></td><td>Writes a Python object to a file as JSON</td></tr>
<tr><td>JSON string</td><td><code>json.dumps(data)</code></td><td>Converts a Python object into a JSON-formatted string</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">19. Async Programming</h3></summary>

<table>
<tr><th>Construct</th><th>Example</th><th>Description</th></tr>
<tr><td><code>async def</code></td><td><code>async def generate():</code></td><td>Defines a coroutine function that can be paused and resumed — needed for non-blocking API/model calls</td></tr>
<tr><td><code>await</code></td><td><code>response = await client.chat(...)</code></td><td>Pauses execution until an async call completes, without blocking the whole program</td></tr>
</table>

</details>

<details>
<summary><h3 style="display:inline;">20. AI-Specific Syntax Patterns</h3></summary>

<p>These combine several constructs above into patterns you'll see constantly in ML code.</p>

<table>
<tr><th>Pattern</th><th>Example</th><th>Description</th></tr>
<tr><td>Dictionary-to-arguments unpacking</td><td><code>model(**inputs)</code></td><td>Passes a dictionary of tensors directly as named model arguments</td></tr>
<tr><td>Keyword-based tokenization</td><td><code>tokenizer(text, return_tensors="pt")</code></td><td>Calls a tokenizer with keyword arguments specifying output format</td></tr>
<tr><td>Batch iteration</td><td><code>for batch in dataloader:</code></td><td>Relies on the iterator protocol to stream training batches</td></tr>
<tr><td>Disabled gradients</td><td><code>with torch.no_grad():</code></td><td>Turns off gradient tracking during inference to save memory and computation</td></tr>
<tr><td>Token streaming</td><td><code>yield token</code></td><td>Emits generated tokens one at a time instead of waiting for the full response</td></tr>
</table>

</details>

<hr>

<h3>Must-Know Standard Library Modules</h3>

<table>
<tr><th>Module</th><th>Common Use</th></tr>
<tr><td><code>typing</code></td><td>Type hints, generics, protocols</td></tr>
<tr><td><code>dataclasses</code></td><td>Configuration objects</td></tr>
<tr><td><code>collections</code></td><td><code>Counter</code>, <code>deque</code>, <code>defaultdict</code></td></tr>
<tr><td><code>itertools</code></td><td>Efficient iteration (products, combinations, chaining)</td></tr>
<tr><td><code>functools</code></td><td><code>partial</code>, <code>lru_cache</code>, <code>reduce</code></td></tr>
<tr><td><code>pathlib</code></td><td>File paths</td></tr>
<tr><td><code>json</code></td><td>Data interchange</td></tr>
<tr><td><code>re</code></td><td>Regular expressions</td></tr>
<tr><td><code>os</code></td><td>Environment variables, filesystem</td></tr>
<tr><td><code>copy</code></td><td>Deep/shallow copying</td></tr>
<tr><td><code>asyncio</code></td><td>Async workflows</td></tr>
<tr><td><code>contextlib</code></td><td>Custom context managers</td></tr>
<tr><td><code>math</code></td><td>Mathematical utilities</td></tr>
<tr><td><code>heapq</code></td><td>Priority queues (algorithms)</td></tr>
</table>

<hr>

<h3>Suggested Learning Priority for AI Engineering</h3>

<table>
<tr><th>Order</th><th>Focus Area</th></tr>
<tr><td>1</td><td>Assignment &amp; unpacking (<code>:=</code>, <code>*</code>, <code>**</code>, tuple unpacking)</td></tr>
<tr><td>2</td><td>Dictionaries and comprehensions</td></tr>
<tr><td>3</td><td><code>enumerate</code>, <code>zip</code>, <code>sorted(key=...)</code></td></tr>
<tr><td>4</td><td><code>lambda</code>, <code>map</code>, <code>filter</code>, <code>any</code>, <code>all</code></td></tr>
<tr><td>5</td><td><code>with</code> context managers</td></tr>
<tr><td>6</td><td>Generators (<code>yield</code>, <code>iter</code>, <code>next</code>)</td></tr>
<tr><td>7</td><td><code>*args</code>, <code>**kwargs</code>, argument unpacking</td></tr>
<tr><td>8</td><td>Type hints, <code>dataclass</code>, <code>TypedDict</code>, <code>BaseModel</code></td></tr>
<tr><td>9</td><td><code>pathlib</code>, <code>json</code>, <code>collections</code></td></tr>
<tr><td>10</td><td><code>async</code> / <code>await</code></td></tr>
</table>

<p>These constructs account for the large majority of Python patterns you'll encounter across modern AI codebases.</p>
