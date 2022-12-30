# Binary Search:

Target: 42 <br/>
[12, 18, 24, 27, 31, 33, 42, 70]  numbers array<br/>
[ 0, 1,  2,  3,  4,  5,  6,  7]  index of numbers<br/>

42 is located at the number 6.

Our goal here is to get better than linear O(n) time complexity.<br/>
Obviously, we can use brute force and search through every element of the array.

![Big O Notation](/bts6.jpeg)

## Let's cut to the chase here. 
- Binary search is an algorithm that requires two pointers.</br>

</br>
</br>
Low &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

- Let's look at the midpoint between the low and high pointers.

- Since low and high are just indices, I can just take the average of the low and high indexes.</br>

E.G: </br>
(0(low) + 7(high)) / 2 = 3.5

- Now, we floor (round down) 3.5 to 3


</br>
</br>
Low &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Mid&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

target = 42

- Since target is 42, our target (42) is GREATER than our midpoint of 27. So if we're ever going to find 42, it's going to be to the right of our midpoint.

</br>
</br>
**Now we're going to set the "low" pointer to mid + 1.**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Mid&nbsp;Low&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

target = 42

Notice that if we recalculate the midpoint between indexes 4 and 7, that'll give us index 5.

</br>
</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Low&nbsp;Mid&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

target = 42

Now, we're comparing our target of 42 with the midpoint of 33. Since 42 is greater than 33, we will move our low pointer to mid + 1.

</br>
</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Mid&nbsp;Low&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

Now, we recalculate the midpoint between indexes 6 and 7.

Rouding down from 6.5, we get 6 for our new recalculated midpoint. 

Since the middle is now index 6 (value of 42), we have found the value we are looking for. 


### Example #2:

</br>
</br>
Low &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

Target = 24

Calculate midpoint.

</br>
</br>
Low &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Mid&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

Compare target of 24 to midpoint value of 27. Since target is less than 27, we need to move the high pointer to the left.

**Move the high pointer index to the left at mid - 1.**

</br>
</br>
Low &nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

Recalculate midpoint. (0 + 2) / 2 = 1

</br>
</br>
LowMidHigh</br>
[12, 18, 24, 27, 31, 33, 42, 70]

Mid is now the element 18. We check to see if target is greater than our midpoint value of 18. We know we need to search to the RIGHT.

</br>
</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Low</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

At this pointer, as we can see above, our low and high pointers are both pointing to the same element. We want to treat these boundaries as inclusive.

What's the midpoint of the above low and high pointers? 
</br>
</br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Mid</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Low</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

</br>
</br>
What if our target is 50 and 50 is not in the array?

Low &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;High</br>
[12, 18, 24, 27, 31, 33, 42, 70]

target = 50

💪 We Do by having y'all walk me through this process 💪 

Time Complexity of this is the following:

n = array length
Time: O(log(n))

![Big O Notation](/bts6.jpeg)

Space Complexity is O(1). Why is space O(1)?

Go back to the Space Complexity and Memory notes in the Javascript Big Takeaway section.

```js
const binarySearch = (numbers, target) => {
  let lo = 0;
  let hi = numbers.length - 1;
  while (lo <= hi) {
    const mid = Math.floor((lo + hi) / 2);
    if (target < numbers[mid]) {
      hi = mid - 1;
    } else if (target > numbers[mid]) {
      lo = mid + 1;
    } else {
      return mid;
    }
  }
  return -1;
};

console.log(binarySearch([0, 1, 2, 3, 4, 5, 6, 7, 8], 6)); // -> 6
console.log(binarySearch([0, 6, 8, 12, 16, 19, 20, 24, 28], 27)); // -> -1
console.log(binarySearch([0, 6, 8, 12, 16, 19, 20, 28], 8)); // -> 2
console.log(binarySearch([0, 6, 8, 12, 16, 19, 20, 24, 28], 28)); // -> 8
console.log(binarySearch([7, 9], 7)); // -> 0
console.log(binarySearch([7, 9], 9)); // -> 1
console.log(binarySearch([7, 9], 12)); // -> -1
console.log(binarySearch([7], 7)); // -> 0
console.log(binarySearch([], 7)); // -> -1
```

# Distribution Sort Algorithms

Note: Many distribution sorts are also merge sorts depending on how the distribution is performed.

[Distribution Sort Cliff Notes](https://ashishpatel201001.medium.com/distribution-sort-db1ba5dd96ae)

## 1. Counting Sort

[Visualgo Counting Sort](https://visualgo.net/en/sorting)

Counting Sort Algorithm Solution
```js
function countingSort(arr, max) {
  // Create a count array to store the count of each element
  const count = new Array(max + 1).fill(0);

  // Store the count of each element in the count array
  for (let i = 0; i < arr.length; i++) {
    count[arr[i]]++;
  }

  // Sort the array using the count array
  const sorted = [];
  for (let i = 0; i < count.length; i++) {
    for (let j = 0; j < count[i]; j++) {
      sorted.push(i);
    }
  }

  return sorted;
}

// Example usage
const arr = [4, 2, 5, 1, 3, 2];
const sorted = countingSort(arr, 5);
console.log(sorted); // [1, 2, 2, 3, 4, 5]
```

Counting sort is an efficient sorting algorithm that works by counting the number of occurrences of each element in the input array and using that information to place the elements in the output array in the correct order. It has a time complexity of O(n + k), where n is the number of elements in the array and k is the range of the input (the maximum element value minus the minimum element value). It is a stable sort, meaning that the order of elements with the same value is preserved in the sorted array.

This implementation assumes that the input array contains only positive integers and that the maximum value is known in advance. It also assumes that the elements in the array are uniformly distributed, which is not always the case in real-world data. In such cases, it may be necessary to use a different sorting algorithm that is better suited to the specific characteristics of the data.

**What is an array that is uniformly distributed mean?**

An array is said to be uniformly distributed if all of its elements are equally likely to appear. For example, consider an array of 10 elements, where each element can take on one of the values 0 through 9. If the array is uniformly distributed, then each of the values 0 through 9 has an equal chance of appearing in any position in the array.

In the context of counting sort, an array that is uniformly distributed means that the elements in the array are evenly distributed across the range of possible values. This is important because counting sort works best when the input array is uniformly distributed. When the input array is not uniformly distributed, the time complexity of the algorithm may increase, making it less efficient.

For example, consider an array of 10 elements where each element can take on one of the values 0 through 9, but the majority of the elements are 0. In this case, the array is not uniformly distributed because the value 0 is more likely to appear than any of the other values. Counting sort would still work on this array, but it would be less efficient than it would be on a uniformly distributed array.

**Counting Sort Time and Space Complexity**


Counting sort is an efficient sorting algorithm with a time complexity of O(n + k), where n is the number of elements in the array and k is the range of the input (the maximum element value minus the minimum element value). This makes it a good choice for sorting arrays with a small range of values, as the time complexity is directly proportional to the range of the input.

The space complexity of counting sort is O(k), where k is the range of the input. This is because the algorithm uses an auxiliary array, called the count array, to store the count of each element in the input array. The size of the count array is equal to the range of the input, so the space complexity is directly proportional to the range of the input.

In general, counting sort is a good choice for sorting arrays with a small range of values and a uniform distribution of elements. It is not a good choice for arrays with a large range of values or a non-uniform distribution of elements, as the time and space complexity may become too large in these cases. In such cases, it may be necessary to use a different sorting algorithm that is better suited to the specific characteristics of the data.

## 2. Radix Sort

[Visualgo Radix Sort](https://visualgo.net/en/sorting)

Radix sort is a non-comparative integer sorting algorithm that works by sorting the elements of the input array based on the digits of their binary representation. It has a time complexity of O(wn), where w is the number of bits in the binary representation of the largest element and n is the number of elements in the array. It is a stable sort, meaning that the order of elements with the same value is preserved in the sorted array.

This implementation sorts the input array of integers in ascending order, assuming that the elements are non-negative. It uses two helper functions, getNumDigits and getDigit, to extract the digits of the input numbers. The getNumDigits function returns the number of digits in a given number, and the getDigit function returns the digit at a given place value (starting from the least significant digit).

**Radix sort is a good choice for sorting large arrays of integers that have a small range of values, as it has a linear time complexity and does not require any comparisons between elements.** 

**It is not a good choice for arrays with a large range of values or for arrays of non-integer elements, as the time complexity may become too large in these cases.** In such cases, it may be necessary to use a different sorting algorithm that is better suited to the specific characteristics of the data.

```js
function radixSort(arr) {
  // Find the maximum number of digits in any element
  let maxDigits = 0;
  for (let i = 0; i < arr.length; i++) {
    maxDigits = Math.max(maxDigits, getDigits(arr[i]));
  }

  // Perform counting sort on each digit, starting with the least significant
  for (let i = 0; i < maxDigits; i++) {
    arr = countingSortOnDigit(arr, i);
  }

  return arr;
}

// Perform counting sort on the i-th digit of the elements in the array
function countingSortOnDigit(arr, i) {
  const count = new Array(10).fill(0);

  // Store the count of each digit in the count array
  for (let j = 0; j < arr.length; j++) {
    const digit = getDigit(arr[j], i);
    count[digit]++;
  }

  // Sort the array using the count array
  const sorted = [];
  for (let j = 0; j < count.length; j++) {
    for (let k = 0; k < count[j]; k++) {
      sorted.push(arr[j]);
    }
  }

  return sorted;
}

// Get the i-th digit of a number
function getDigit(num, i) {
  return Math.floor(num / Math.pow(10, i)) % 10;
}

// Get the number of digits in a number
function getDigits(num) {
  if (num === 0) return 1;
  return Math.floor(Math.log10(num)) + 1;
}

// Example usage
const arr = [170, 45, 75, 90, 802, 24, 2, 66];
const sorted = radixSort(arr);
console.log(sorted); // [2, 24, 45, 66, 75, 90, 170, 802]
```