![Maintained by Hassan](https://img.shields.io/badge/maintained%20by-Hassan.com-blue)

## Introduction
This GitHub Action starts a Redis server on the default port `6379`.

This is useful when running tests against a Redis database.


## Usage
A code example says more than a 1000 words. Here’s an exemplary GitHub Action using a Redis server in versions 4 and 5 to test a Node.js app:

```yaml
name: Run tests

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [10.x, 12.x, 14.x]
        redis-version: [4, 5, 6]

    steps:
    - name: Git checkout
      uses: actions/checkout@v2

    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v1
      with:
        node-version: ${{ matrix.node-version }}

    - name: Start Redis
      uses: supercharge/redis-github-action@1.2.0
      with:
        redis-version: ${{ matrix.redis-version }}

    - run: npm install

    - run: npm test
      env:
        CI: true
```


## License
MIT © [Supercharge](https://superchargejs.com)

---

> [superchargejs.com](https://superchargejs.com) &nbsp;&middot;&nbsp;
> GitHub [@supercharge](https://github.com/supercharge) &nbsp;&middot;&nbsp;
> Twitter [@superchargejs](https://twitter.com/superchargejs)
