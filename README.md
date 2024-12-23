# Problem Patterns and Basics

## Index
1. [Right Rotation of an Array/List](#right-rotation-of-an-arraylist)
2. [Left Rotation of an Array/List](#left-rotation-of-an-arraylist)

---

## Right Rotation of an Array/List

### Problem
Given an array/list, rotate it `k` times to the right. Each rotation shifts all elements one position to the right, with the last element wrapping around to the beginning.

### Approaches

#### 1. Worst Approach: Brute Force
- **Description**: Rotate the array one step to the right `k` times.
- **Time Complexity**: O(n * k)
- **Space Complexity**: O(1)

```csharp
void RightRotateBruteForce(int[] arr, int k) {
    int n = arr.Length;
    k %= n; // Handle cases where k > n

    for (int i = 0; i < k; i++) {
        int last = arr[n - 1];
        for (int j = n - 1; j > 0; j--) {
            arr[j] = arr[j - 1];
        }
        arr[0] = last;
    }
}
```

#### 2. Good Approach: Using Extra Space
- **Description**: Use an auxiliary array to store the rotated result.
- **Time Complexity**: O(n)
- **Space Complexity**: O(n)

```csharp
int[] RightRotateUsingExtraSpace(int[] arr, int k) {
    int n = arr.Length;
    k %= n; // Handle cases where k > n
    int[] rotated = new int[n];

    for (int i = 0; i < n; i++) {
        rotated[(i + k) % n] = arr[i];
    }

    return rotated;
}
```

#### 3. Optimal Approach: Reverse Method
- **Description**: Reverse parts of the array to achieve the rotation in-place.
- **Steps**:
  1. Reverse the entire array.
  2. Reverse the first `k` elements.
  3. Reverse the remaining elements.
- **Time Complexity**: O(n)
- **Space Complexity**: (O(1)

```csharp
void RightRotateOptimal(int[] arr, int k) {
    int n = arr.Length;
    k %= n; // Handle cases where k > n

    void Reverse(int[] array, int start, int end) {
        while (start < end) {
            int temp = array[start];
            array[start] = array[end];
            array[end] = temp;
            start++;
            end--;
        }
    }

    Reverse(arr, 0, n - 1);
    Reverse(arr, 0, k - 1);
    Reverse(arr, k, n - 1);
}
```

---

## Left Rotation of an Array/List

### Problem
Given an array/list, rotate it `k` times to the left. Each rotation shifts all elements one position to the left, with the first element wrapping around to the end.

### Approaches

#### 1. Worst Approach: Brute Force
- **Description**: Rotate the array one step to the left `k` times.
- **Time Complexity**: O(n * k)
- **Space Complexity**: O(1)

```csharp
void LeftRotateBruteForce(int[] arr, int k) {
    int n = arr.Length;
    k %= n; // Handle cases where k > n

    for (int i = 0; i < k; i++) {
        int first = arr[0];
        for (int j = 0; j < n - 1; j++) {
            arr[j] = arr[j + 1];
        }
        arr[n - 1] = first;
    }
}
```

#### 2. Good Approach: Using Extra Space
- **Description**: Use an auxiliary array to store the rotated result.
- **Time Complexity**: O(n)
- **Space Complexity**: O(n)

```csharp
int[] LeftRotateUsingExtraSpace(int[] arr, int k) {
    int n = arr.Length;
    k %= n; // Handle cases where k > n
    int[] rotated = new int[n];

    for (int i = 0; i < n; i++) {
        rotated[i] = arr[(i + k) % n];
    }

    return rotated;
}
```

#### 3. Optimal Approach: Reverse Method
- **Description**: Reverse parts of the array to achieve the rotation in-place.
- **Steps**:
  1. Reverse the first `k` elements.
  2. Reverse the remaining elements.
  3. Reverse the entire array.
- **Time Complexity**: O(n)
- **Space Complexity**: O(1)

```csharp
void LeftRotateOptimal(int[] arr, int k) {
    int n = arr.Length;
    k %= n; // Handle cases where k > n

    void Reverse(int[] array, int start, int end) {
        while (start < end) {
            int temp = array[start];
            array[start] = array[end];
            array[end] = temp;
            start++;
            end--;
        }
    }

    Reverse(arr, 0, k - 1);
    Reverse(arr, k, n - 1);
    Reverse(arr, 0, n - 1);
}
```
