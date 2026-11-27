
Node runs JS on a single thread using V8. Libuv handles async work through the OS or a thread pool of 4 threads. The event loop cycles through 6 phases, and microtasks (nextTick, then promises) run between every callback.

![[diagram-export-27-11-2026-14_21_31.png]]

After **each** callback finishes running, Node checks the microtask queues. It runs every task in `nextTick`, then every task in the Promise queue, until both are empty. Only then does it run the next callback.

```
callback A runs → empty nextTick → empty promises → callback B runs → ...
```
https://app.eraser.io/workspace/Vlwyjo6B51kiXH0QSMWF
