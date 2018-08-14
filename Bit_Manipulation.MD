# Bit Manipulation

## The Use of Bit Manipulation

### Counting 1s

```Java
public int countOnes(int n) {
    int count = 0;
    while(n!=0) {
    // Remove the one at the tail
        n = n&(n-1);
        count++;
    }
    return count;
}
```

### Is the power of 4

```Java
public boolean isPowerOfFour(int n) {
    // There is only one 1 in the binary representation.
    return (n&(n-1))==0
    // The one should be in Corresponding position like 0x55555555,
    // which is 1010101010101010101010101010101
        && ((n&0x55555555)!=0);
}
```

### Adding to Integers

```Java
public int getSum(int a, int b) {
    if(a==0) return b;
    if(b==0) return a;
    // 不计进位结果
    int x1 = a^b;
    // 只计进位结果
    int x2 = a&b;
    x2 <<= 1;
    return getSum(x1,x2);
}
```

### Find missing number in a consecutive range

```Java
public int missingNumber(int[] nums) {
    int num = 0;
    for(int i = 0; i<=nums.length; i++){
            num^=i;
    }
    for(Integer a: nums){
            num^=a;
    }
    return num;
}
```
