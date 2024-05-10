# [LeetCode Records](../../README.md) - Question 284 Peeking Iterator

### Attempt 1: Record the next integer
```java
class PeekingIterator implements Iterator<Integer> {

    private Iterator<Integer> iterator;
    private Integer nextInteger;

	public PeekingIterator(Iterator<Integer> iterator) {
	    // initialize any member here.
	    this.iterator = iterator;
        nextInteger =  iterator.hasNext() ? iterator.next() : null;
	}
	
    // Returns the next element in the iteration without advancing the iterator.
	public Integer peek() {
        return nextInteger;
	}
	
	// hasNext() and next() should behave the same as in the Iterator interface.
	// Override them if needed.
	@Override
	public Integer next() {
	    Integer result = nextInteger;
        nextInteger =  iterator.hasNext() ? iterator.next() : null;
        return result;
	}
	
	@Override
	public boolean hasNext() {
	    return nextInteger != null;
	}
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 42.07 MB (Beats: 59.75%)

<br>
