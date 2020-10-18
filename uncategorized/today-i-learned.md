---
description: 'Random but related fact, recollected with love'
---

# Today I Learned

## Tricks

### Generate pseudo-random number in JS

```javascript
function generateRandomNumber() {
    const arr = new UIntArray32(1);
    window.crypto.getRandomValues(arr);
    
    return arr[0];
}
```

### Run _asynchronous tasks_ sequentially

[Article explaining this](https://jrsinclair.com/articles/2019/how-to-run-async-js-in-parallel-or-sequential/) in a bit more depth

```javascript
const asyncThingsToDo = [
    {task: 'wait', duration: 1000},
    {task: 'fetch', url: 'https://httpstat.us/200'},
    {task: 'wait', duration: 2000},
    {task: 'fetch', url: 'https://urlecho.appspot.com/echo?body=Awesome!'},
];

function runTask(spec) {
    return (spec.task === 'wait')
        ? asyncTimeout(spec.duration)
        : asyncFetch(spec.url);
}

async function testAsyncSequence() {
    const starterPromise = Promise.resolve(null);
    const log            = result => console.log(result);
    await asyncThingsToDo.reduce(
        (p, spec) => p.then(() => runTask(spec).then(log)),
        starterPromise
    );
}

testAsyncSequence();
```

### Mock window.crypto in jest

[S.O Reference](https://stackoverflow.com/questions/52612122/how-to-use-jest-to-test-functions-using-crypto-or-window-mscrypto)

```javascript
const crypto = require('crypto');

Object.defineProperty(global.self, 'crypto', {
  value: {
    getRandomValues: arr => crypto.randomBytes(arr.length)
  }
});
```

### Node.js has a built-in performance benchmark suite

1. [S.O Reference](https://stackoverflow.com/questions/10617070/how-do-i-measure-the-execution-time-of-javascript-code-with-callbacks)
2.  [Node.js docs](https://nodejs.org/api/perf_hooks.html)

### Why return from an event handler

1. [S.O Reference](https://stackoverflow.com/questions/7814949/javascript-onclick-event-return-keyword-functionality)
2. [Codepen implementation](https://codepen.io/sigfriedCub/pen/YzqEpep)

### Generate patch from a commit with magit them apply it

1. [Apply changes from patch file](https://stackoverflow.com/questions/2249852/how-to-apply-a-patch-generated-with-git-format-patch)

### Fuzzy string matching with PostgreSQL

`PostgreSQL` has support for [fuzzy string matching](https://www.freecodecamp.org/news/fuzzy-string-matching-with-postgresql/) through the module `pg_trgm`

### Why \`couldn't get file descriptor referring to the console\`

1. [S.O Reference](https://stackoverflow.com/questions/28353244/error-in-linux-console-couldnt-get-a-file-descriptor-referring-to-the-console)

### Map 2d array to 1d array

1. [S.O Reference](https://stackoverflow.com/questions/2151084/map-a-2d-array-onto-a-1d-array)
2. [Row and column-major order](https://en.m.wikipedia.org/wiki/Row-_and_column-major_order)

