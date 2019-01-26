# Garbage Collection2

## refer
* https://instagram-engineering.com/dismissing-python-garbage-collection-at-instagram-4dca40b29172
* https://www.youtube.com/watch?v=e2hT7dYzURo&feature=youtu.be

### Case study: Instagram
* Dismissing Python Garbage Collection at Instagram
* *During GC, the linked lists are shuffled*
* Shuffling these objects in the linked lists will cause the pages to be CoWed, which is an unfortunate side effect.
* Try 1: Disabling GC; one of the third-party libraries we used (msgpack) calls gc.enable() to bring it back, so gc.disable() at bootstrapping was washed
* Try 2: As an alternative to gc.disable, we did gc.set_threshold(0)
  * successfully raised the shared memory of each worker process from 140MB to 225MB
  * This saved 25% RAM for the whole Django flee
  * In effect, this improves the throughput of Django tier by more than 10%.
* Summary
  * freed up about 8GB RAM for each server we used to create more worker processes for memory-bound server generation, or lower the worker respawn rate for CPU-bound server generation;
  * CPU throughput also improved as CPU instructions per cycle (IPC) increased by about 10%.
