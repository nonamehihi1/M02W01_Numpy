# M02W01_Numpy
Những kiến thức học được trong tuần về Numpy 

## Các hàm phổ biến 

- zeros(): Tạo 1 mảng numpy với tất cả phần tử là 0
- ones(): Tạo 1 mảng numpy với tất cả phần tử là 1
Tại vì chúng ta hay sử dụng những mảng cần full 0 hay 1, nên numpy mới tạo ra những hàm này mà không phải twos() hay three()

- arrage(start, end, step): Tạo 1 mảng numpy bắt đầu từ (start) và kết thúc là (end -1) với khoảng cách là (step)
  
Ví dụ:

```python
import numpy as np
arr1 = np.arange(5) # sẽ in ra [0,1,2,3,4]
arr2 = np.arange(0,4,2) # sẽ in ra [0,2]
```

- reshape(a, newshape) : sử dụng để thay đổi shape của Mattrix. trong đó newshape có thể là tuple hoặc các giá trị riêng lẻ, sao cho phù hợp với số lượng phần tử của vector a

```python
a = np.arange(6) # [0,1,2,3,4,5]
a.reshape(2,3) # 2 hàng 3 cột
```

## Slicing
Sử dụng để lấy các phần tử ở trong 1 matrrix

ví dụ:
```python
import numpy as np
a_arr = np.array(
  [1,2,3],
  [3,4,5]
)
b_arr = a_arr[:, 1:3] #[2 3] [6 7]
```
- Nếu có dạng như này data[0,1] thì là lấy giá trị tại dòng 0 và cột 1
- Nếu là data[:,], trước dấu phẩy là axis = 0 (tức là theo phương thẳng đứng), còn sau dấy phẩy là axis = 1 (tức phương ngang), dấu ':' sẽ được thể hiện là lấy từ phần từ nào đến phần tử nào, ví dụ '1:3' tức là lấy các phần tử có index 1,2 ...

```python
arr = np.aray(
  [1,2],
  [3,4]
  [5,6]
)
out = arr([1,1][0,1]) #[2, 4]
```
- Sử dụng cách này để lấy những phần tử tương ứng với ví trị trong mattrix

```python
arr = np.array(
  [1,2],
  [3,4],
  [5,6]
)
bool_ind = (arrr> 3)
print(arr[bool_ind]) # [4 5 6]
```

Cách trên để sử dụng tìm những phần tử > 3 bằng cách gọi là 'Boolean indices', nó sẽ tạo mảng boolean có cùng shape hoặc kích thước, dựa vào điều kiện của người dùng, để tạo 1 mảng boolean

Ngoài ra còn có:
+ Sum(data, axis = ..): Tính tổng các phần tử, axis là tính theo từng cột hay từng dòng
+ Max, min ..


## Broadcasting
Thuật ngữ này trong Numpy nghĩa là 2 hoặc nhiều mảng có thể tự động 'giãn' ra để có cùng shape, nhằm thực hiện các phép toán
Để 2 mảng A và B được gọi là Broadcasting, Numpy sẽ kiểm tra từ 'phải sang trái':
+ Nếu 2 số bằng nhau
+ Nếu 1 trong 2 số là số 1, thì số 1 sẽ lặp lại thành chính số còn lại để tạo ra shape của vector cuối cùng

Ví dụ:

```python
import numpy as np

arr1 = np.array([1,2,3]) #(1,3)
arr2 = np.array([[10], [20]]) #(2,1)

print(np.add(arr1, arr2)
```
Như ví dụ trên ta có shape(arr1) = (1, 3), shape(arr2) = (2, 1). Vậy 2 vector này có thể Boardcasting vì arr2 có số 1 ở shape, nên kết quả của ví dụ này sẽ là (2, 3) 

