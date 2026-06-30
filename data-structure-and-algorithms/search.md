# Tìm kiếm nhị phân (Binary Search)

Tìm kiếm nhị phân là thuật toán **chia để trị** trên một mảng đã được sắp xếp, bằng cách liên tục chia đôi khoảng tìm kiếm.

Ban đầu, không gian tìm kiếm là toàn bộ mảng. Giá trị mục tiêu được so sánh với phần tử ở giữa. Nếu chúng không bằng nhau, nửa không chứa mục tiêu sẽ bị loại bỏ. Quá trình tiếp tục trên nửa còn lại: lấy phần tử giữa, so sánh với mục tiêu, và lặp lại cho đến khi tìm thấy hoặc không còn phần tử nào để kiểm tra.

Nếu quá trình tìm kiếm kết thúc mà không gian còn lại trống, nghĩa là mục tiêu không tồn tại trong mảng.

Độ phức tạp thời gian là **O(log n)** vì sau mỗi bước, không gian tìm kiếm thu hẹp đi một nửa.

![Tìm kiếm nhị phân: Sức mạnh của chia để trị](Binary_Search_Algorithm_Explained.png)

Hình minh họa trên cho thấy:

- **Mảng đã sắp xếp**: Thuật toán chỉ hoạt động đúng khi dữ liệu đầu vào đã được sắp xếp trước.
- **So sánh và chia đôi**: So sánh mục tiêu với phần tử giữa, rồi loại bỏ nửa không liên quan.
- **Điểm dừng**: Tìm kiếm kết thúc khi tìm thấy mục tiêu hoặc không còn phần tử nào để kiểm tra.
- **Hiệu suất**: Không gian tìm kiếm thu hẹp 50% sau mỗi bước.

## Mã giả (Pseudocode)

Có hai cách viết tìm kiếm nhị phân: **lặp** (iterative) và **đệ quy** (recursive).

### Cách lặp (Iterative)

```
FUNCTION binarySearch(arr, target):
    left  = 0                      // chi so dau
    right = length(arr) - 1        // chi so cuoi

    WHILE left <= right:
        mid = left + floor((right - left) / 2)

        IF arr[mid] == target:
            RETURN mid             // Tim thay muc tieu

        ELSE IF arr[mid] < target:
            left = mid + 1         // Loai bo nua trai (bao gom mid)

        ELSE:
            right = mid - 1        // Loai bo nua phai (bao gom mid)

    RETURN -1                      // Khong tim thay
```

### Cách đệ quy (Recursive)

Goi ban dau:

```
RETURN binarySearch(arr, target, 0, length(arr) - 1)
```

```
FUNCTION binarySearch(arr, target, left, right):
    IF left > right:
        RETURN -1                  // Khong tim thay

    mid = left + floor((right - left) / 2)

    IF arr[mid] == target:
        RETURN mid

    ELSE IF arr[mid] < target:
        RETURN binarySearch(arr, target, mid + 1, right)   // Tim o nua phai

    ELSE:
        RETURN binarySearch(arr, target, left, mid - 1)    // Tim o nua trai
```

## Lưu ý

- Mảng phải được **sắp xếp** trước khi áp dụng tìm kiếm nhị phân.
- Dùng `left + (right - left) / 2` thay vì `(left + right) / 2` để tránh tràn số khi `left` và `right` rất lớn.
- Độ phức tạp thời gian: **O(log n)**.
- Độ phức tạp không gian: **O(1)** với cách lặp, **O(log n)** với cách đệ quy (do ngăn xếp lời gọi).
