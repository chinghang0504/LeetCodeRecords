# [LeetCode Records](../../README.md) - Question 537 Complex Number Multiplication

### Attempt 1: Use split() to get the real and imaginary parts
```java
class Solution {
    
    static class ComplexNumber {
        int real;
        int imaginary;

        ComplexNumber(String num) {
            String[] splits = num.split("[+i]");
            real = Integer.valueOf(splits[0]);
            imaginary = Integer.valueOf(splits[1]);
        }

        ComplexNumber(int real, int imaginary) {
            this.real = real;
            this.imaginary = imaginary;
        }

        static ComplexNumber times(ComplexNumber num1, ComplexNumber num2) {
            int real = num1.real * num2.real - num1.imaginary * num2.imaginary;
            int imaginary = num1.real * num2.imaginary + num2.real * num1.imaginary;
            return new ComplexNumber(real, imaginary);
        }

        @Override
        public String toString() {
            return real + "+" + imaginary + "i";
        }
    }
    
    public String complexNumberMultiply(String num1, String num2) {
        ComplexNumber complexNumber1 = new ComplexNumber(num1);
        ComplexNumber complexNumber2 = new ComplexNumber(num2);
        ComplexNumber complexNumber3 = ComplexNumber.times(complexNumber1, complexNumber2);
        
        return complexNumber3.toString();
    }
}
```
- Runtime: 6 ms (Beats: 23.08%)
- Memory: 41.66 MB (Beats: 47.35%)

<br>
