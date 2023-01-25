# Context Managers

### Context Managers with Magic methods

```python
class FileContext:
    def __enter__(self):
        ...
    
    def __exit__(self, exc_type, value, traceback):
        ...
```

### Creating Context Managers with Contextlib

<pre class="language-python"><code class="lang-python"><strong>from contextlib import contextmanager
</strong>
@contextmanager
def file_context():
    f = open("a file")
    try:
        yield f # gets returned to the with-as  and returns the exception here
    except Exception as e:
        # handle the context exception
        ...
    finally:
        file.close()
</code></pre>

### Handling Multiple Contexts

```python
from contextlib import ExitStack, contextmanager
@contextmanager
def multi_context(*cms):
    with ExitStack() as stack:
        yield [stack.enter_context(cls()) for cls in cms]

```
