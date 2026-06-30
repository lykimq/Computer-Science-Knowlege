# Binary Search

Binary search (Tìm kiếm nhị phân) là một thuật toán chia để trị, trên một mảng được sắp xếp bằng cách liên tục chia đôi khoảng tìm kiếm. 

Ban đầu không gian tìm kiếm là toàn bộ mảng, và giá trị mục tiêu được so sánh với phần tử ở giữa mảng. Nếu chúng không bằng nhau, phần chia mà giá trị không tìm được sẽ bị loại bỏ, và quá trình tìm kiếm sẽ tiếp tục trên phần nửa còn lại, tiếp tục lấy phần giữa để so sánh với mục tiêu, và lặp lại cho đến khi tìm thấy mục tiêu. 

Nếu quá trình tìm kiếm kết thúc với nửa còn lại trống, nghĩa là không tìm được. 

Tìm kiếm nhị phân có độ phức tạp O(log n) vì nó thu hẹp không gian tìm kiếm đi một nửa sau mỗi bước.


## Pseducode

Có hai cách thức để viết tìm kiếm nhị phân: lặp và đệ qui

### Iterative approach

FUNCTION binarySearch (arr, target):
    left = 0
    right = length (arr) - 1

    WHILE left <= right: 
      mid = floor ((left + right) / 2)

      IF arr[mid] == target
        RETURN mid           // Target found

      ELSE IF arr[mid] < target
        left = mid + 1      // Discard left haft

      ELSE 
        right = mid - 1    // Discard right half
     
    RETURN -1 // not found

### Recursive approach

FUNCTION binarySearch (arr, target, left, right):
  IF left < right :
    RETURN -1

 mid = floor ((left + right)/2)

 IF arr[mid] == target:
   RETURN mid

 ELSE IF arr[mid] < target:
   RETURN binarySearch (arr, target, mid + 1, right) // Search right half

 ELSE
   RETURN binarySearch (arr, target, left, mid - 1) // Search left half

### NOTES

- Mảng phải là mảng đã sắp xếp.
- `left + (right - left)/2: giúp không bị tràn khi trái và phải là một mảng rất lớn.
- Thời gian phức tạp là: O(log n)
- Không gian phức tạp là: O(1) cho iterative, và O(log n) cho recursive (bởi vì stack)