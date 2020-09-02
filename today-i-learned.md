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

