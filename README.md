[![PyPI version](https://badge.fury.io/py/jsons.svg)](https://badge.fury.io/py/jsons)
[![Docs](https://readthedocs.org/projects/jsons/badge/?version=latest)](https://jsons.readthedocs.io/en/latest/?badge=latest)
[![Build Status](https://api.travis-ci.org/ramonhagenaars/jsons.svg?branch=master)](https://travis-ci.org/ramonhagenaars/jsons)
[![Code Coverage](https://codecov.io/gh/ramonhagenaars/jsons/branch/master/graph/badge.svg)](https://codecov.io/gh/ramonhagenaars/jsons)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/ramonhagenaars/jsons/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/ramonhagenaars/jsons/?branch=master)
[![Maintainability](https://api.codeclimate.com/v1/badges/17d997068b3387c2f2c3/maintainability)](https://codeclimate.com/github/ramonhagenaars/jsons/maintainability)
[![Downloads](https://img.shields.io/pypi/dm/jsons.svg)](https://pypistats.org/packages/jsons)


<p align='center'>
  <a href='https://jsons.readthedocs.io/en/latest/'>
    <img width='150' src='https://github.com/ramonhagenaars/jsons/raw/master/resources/jsons-logo.svg?sanitize=true' />
  </a> 
</p>

  - *Python 3.5+*
  - *Minimal effort to use\!*
  - *No magic, just you, Python and jsons\!*
  - *Human readible JSON without pollution\!*
  - *Easily customizable and extendable\!*
  - *Type hints for the win\!*

💗 this lib? Leave a ★ and tell your colleagues!

Example of a model to serialize:

```python
>>> @dataclass
... class Person:
...    name: str
...    birthday: datetime
...
>>> p = Person('Guido van Rossum', birthday_guido)
```

Example of using jsons to serialize:

```python
>>> out = jsons.dump(p)
>>> out
{'birthday': '1956-01-31T12:00:00Z', 'name': 'Guido van Rossum'}
```

Example of using jsons to deserialize:

```python
>>> p2 = jsons.load(out, Person)
>>> p2
Person(name='Guido van Rossum', birthday=datetime.datetime(1956, 1, 31, 12, 0, tzinfo=datetime.timezone.utc))
```

# Installation

    pip install jsons

# Usage

```python
import jsons

some_instance = jsons.load(some_dict, SomeClass)  # Deserialization
some_dict = jsons.dump(some_instance)  # Serialization
```

In some cases, you have instances that contain other instances that need (de)serialization, for instance with lists or dicts. You can use the
`typing` classes for this as is demonstrated below.

```python
from typing import List, Tuple
import jsons

# For more complex deserialization with generic types, use the typing module
list_of_tuples = jsons.load(some_dict, List[Tuple[AClass, AnotherClass]])
```

(For more examples, see the
[FAQ](https://jsons.readthedocs.io/en/latest/faq.html))

# Documentation 

  - [Main documentation](https://jsons.readthedocs.io/en/latest/)
  - [API docs](https://jsons.readthedocs.io/en/latest/api.html)
  - [FAQ](https://jsons.readthedocs.io/en/latest/faq.html)

# Meta

## Recent updates

### 1.0.0

  - Feature: Added a serializer/deserializer for `time`.
  - Feature: Added a serializer/deserializer for `timezone`.
  - Feature: Added a serializer/deserializer for `timedelta`.
  - Feature: Added a serializer/deserializer for `date`.
  - Bugfix: Dumping verbose did not store the types of dicts (`Dict[K,
    V]`).
  - Bugfix: Loading with `List` (no generic type) failed.
  - Bugfix: Loading with `Dict` (no generic type) failed.
  - Bugfix: Loading with `Tuple` (no generic type) failed.

### 0.10.2

  - Bugfix: Loading `Dict[K, V]` did not parse `K`.

### 0.10.1

  - Change: Correction of the type hints of `load`, `loads`, `loadb`.

### 0.10.0

  - Feature: Added a deserializer for complex numbers.


### 0.9.0

  - Feature: Added the ability to validate instances right after
    loading.
  - Feature: Enhanced typing for the loader functions.
  - Feature: Added the ability to use multiple processes or threads with
    deserializing lists.
  - Feature: Added the `jsons.fork()` function.
  - Change: `None` can now be loaded with the right type hints, even in
    strict-mode.
  - Bugfix: A fork from `JsonSerializable` did not copy its settings.

## Contributors

Special thanks to the following contributors of code, discussions or
suggestions:

  - [finetuned89](https://github.com/finetuned89)
  - [haluzpav](https://github.com/haluzpav)
  - [jmolinski](https://github.com/jmolinski)
  - [gastlich](https://github.com/gastlich)
  - [cypreess](https://github.com/cypreess)
  - [casparjespersen](https://github.com/casparjespersen)
  - [ahmetkucuk](https://github.com/ahmetkucuk)
  - [robinklaassen](https://github.com/robinklaassen)
  - [jochembroekhoff](https://github.com/jochembroekhoff)
