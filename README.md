# returns

[![wemake.services](https://img.shields.io/badge/%20-wemake.services-green.svg?label=%20&logo=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAMAAAAoLQ9TAAAABGdBTUEAALGPC%2FxhBQAAAAFzUkdCAK7OHOkAAAAbUExURQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP%2F%2F%2F5TvxDIAAAAIdFJOUwAjRA8xXANAL%2Bv0SAAAADNJREFUGNNjYCAIOJjRBdBFWMkVQeGzcHAwksJnAPPZGOGAASzPzAEHEGVsLExQwE7YswCb7AFZSF3bbAAAAABJRU5ErkJggg%3D%3D)](https://wemake.services) [![Build Status](https://travis-ci.org/dry-python/returns.svg?branch=master)](https://travis-ci.org/dry-python/returns) [![Coverage Status](https://coveralls.io/repos/github/dry-python/returns/badge.svg?branch=master)](https://coveralls.io/github/dry-python/returns?branch=master) [![Documentation Status](https://readthedocs.org/projects/returns/badge/?version=latest)](https://returns.readthedocs.io/en/latest/?badge=latest) [![Python Version](https://img.shields.io/pypi/pyversions/returns.svg)](https://pypi.org/project/returns/) [![wemake-python-styleguide](https://img.shields.io/badge/style-wemake-000000.svg)](https://github.com/wemake-services/wemake-python-styleguide)


Make your functions return something meaningful, typed, and safe!


## Features

- Provides primitives to write declarative business logic
- Fully typed with annotations and checked with `mypy`,
  allowing you to write type-safe code as well
- Pythonic and pleasant to write and to read (!)


## Installation


```bash
pip install returns
```

## Why?

TODO: example with `requests` and `json`


## Pipeline example


```python
from returns.do_notation import do_notation
from returns.result import Result, Success, Failure

class CreateAccountAndUser(object):
    """Creates new Account-User pair."""

    @do_notation
    def __call__(self, username: str, email: str) -> Result['User', str]:
        """Can return a Success(user) or Failure(str_reason)."""
        user_schema = self._validate_user(username, email).unwrap()
        account = self._create_account(user_schema).unwrap()
        return self._create_user(account)

    # Protected methods
    # ...

```

We are [covering what's going on in this example](https://returns.readthedocs.io/en/latest/pages/do-notation.html) in the docs.
