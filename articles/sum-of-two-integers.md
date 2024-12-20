## 1. Brute Force

::tabs-start

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        return a + b
```

```java
public class Solution {
    public int getSum(int a, int b) {
        return a + b; 
    }
}
```

```cpp
class Solution {
public:
    int getSum(int a, int b) {
        return a + b;
    }
};
```

```javascript
class Solution {
    /**
     * @param {number} a
     * @param {number} b
     * @return {number}
     */
    getSum(a, b) {
        return a + b;
    }
}
```

```csharp
public class Solution {
    public int GetSum(int a, int b) {
        return a + b;
    }
}
```

::tabs-end

### Time & Space Complexity

* Time complexity: $O(1)$
* Space complexity: $O(1)$

---

## 2. Bit Manipulation

::tabs-start

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        carry = 0
        res = 0
        mask = 0xFFFFFFFF

        for i in range(32):
            a_bit = (a >> i) & 1
            b_bit = (b >> i) & 1
            cur_bit = a_bit ^ b_bit ^ carry
            carry = (a_bit + b_bit + carry) >= 2
            if cur_bit:
                res |= (1 << i)

        if res > 0x7FFFFFFF:
            res = ~(res ^ mask)
            
        return res
```

```java
public class Solution {
    public int getSum(int a, int b) {
        int carry = 0, res = 0, mask = 0xFFFFFFFF;

        for (int i = 0; i < 32; i++) {
            int a_bit = (a >> i) & 1;
            int b_bit = (b >> i) & 1;
            int cur_bit = a_bit ^ b_bit ^ carry;
            carry = (a_bit + b_bit + carry) >= 2 ? 1 : 0;
            if (cur_bit != 0) {
                res |= (1 << i);
            }
        }

        if (res > 0x7FFFFFFF) {
            res = ~(res ^ mask);
        }
        
        return res;
    }
}
```

```cpp
class Solution {
public:
    int getSum(int a, int b) {
        int carry = 0, res = 0, mask = 0xFFFFFFFF;

        for (int i = 0; i < 32; i++) {
            int a_bit = (a >> i) & 1;
            int b_bit = (b >> i) & 1;
            int cur_bit = a_bit ^ b_bit ^ carry;
            carry = (a_bit + b_bit + carry) >= 2 ? 1 : 0;
            if (cur_bit) {
                res |= (1 << i);
            }
        }

        if (res > 0x7FFFFFFF) {
            res = ~(res ^ mask);
        }
        
        return res;
    }
};
```

```javascript
class Solution {
    /**
     * @param {number} a
     * @param {number} b
     * @return {number}
     */
    getSum(a, b) {
        let carry = 0, res = 0, mask = 0xFFFFFFFF;

        for (let i = 0; i < 32; i++) {
            let a_bit = (a >> i) & 1;
            let b_bit = (b >> i) & 1;
            let cur_bit = a_bit ^ b_bit ^ carry;
            carry = (a_bit + b_bit + carry) >= 2 ? 1 : 0;
            if (cur_bit) {
                res |= (1 << i);
            }
        }

        if (res > 0x7FFFFFFF) {
            res = ~(res ^ mask);
        }
        
        return res;
    }
}
```

```csharp
public class Solution {
    public int GetSum(int a, int b) {
        int carry = 0, res = 0, mask = unchecked((int)0xFFFFFFFF);

        for (int i = 0; i < 32; i++) {
            int a_bit = (a >> i) & 1;
            int b_bit = (b >> i) & 1;
            int cur_bit = a_bit ^ b_bit ^ carry;
            carry = (a_bit + b_bit + carry) >= 2 ? 1 : 0;
            if (cur_bit != 0) {
                res |= (1 << i);
            }
        }

        if (res > Int32.MaxValue) {
            res = ~(res ^ mask);
        }
        
        return res;
    }
}
```

::tabs-end

### Time & Space Complexity

* Time complexity: $O(1)$
* Space complexity: $O(1)$

---

## 3. Bit Manipulation (Optimal)

::tabs-start

```python
class Solution:
    def getSum(self, a: int, b: int) -> int:
        mask = 0xFFFFFFFF
        max_int = 0x7FFFFFFF

        while b != 0:
            carry = (a & b) << 1
            a = (a ^ b) & mask
            b = carry & mask

        return a if a <= max_int else ~(a ^ mask)
```

```java
public class Solution {
    public int getSum(int a, int b) {
        while (b != 0) {
            int carry = (a & b) << 1;
            a ^= b;
            b = carry;
        }
        return a;
    }
}
```

```cpp
class Solution {
public:
    int getSum(int a, int b) {
        while (b != 0) {
            int carry = (a & b) << 1;
            a ^= b;
            b = carry;
        }
        return a;
    }
};
```

```javascript
class Solution {
    /**
     * @param {number} a
     * @param {number} b
     * @return {number}
     */
    getSum(a, b) {
        while (b !== 0) {
            let carry = (a & b) << 1;
            a ^= b;
            b = carry;
        }
        return a;
    }
}
```

```csharp
public class Solution {
    public int GetSum(int a, int b) {
        while (b != 0) {
            int carry = (a & b) << 1;
            a ^= b;
            b = carry;
        }
        return a;
    }
}
```

::tabs-end

### Time & Space Complexity

* Time complexity: $O(1)$
* Space complexity: $O(1)$