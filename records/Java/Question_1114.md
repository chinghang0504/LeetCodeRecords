# [LeetCode Records](../../README.md) - Question 1114 Print in Order

### Attempt 1: Use AtomicInteger and while loops
```java
class Foo {

    private AtomicInteger num;

    public Foo() {
        num = new AtomicInteger(0);
    }

    public void first(Runnable printFirst) throws InterruptedException {
        printFirst.run();

        num.incrementAndGet();
    }

    public void second(Runnable printSecond) throws InterruptedException {
        while (num.get() != 1) {}

        printSecond.run();

        num.incrementAndGet();
    }

    public void third(Runnable printThird) throws InterruptedException {
        while (num.get() != 2) {}

        printThird.run();
    }
}
```
- Runtime: 9 ms (Beats: 99.83%)
- Memory: 42.39 MB (Beats: 18.95%)

<br>
