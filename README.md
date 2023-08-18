# `Pass by Value` & `Pass by Reference`

Trong JS khi 1 function được gọi thì tham số có thể được truyền qua 2 cách: Pass by value và Pass by referance (address). Primative data type ví dụ như string, number, null, undefined, boolean thì được truyền thông qua giá tr trong khi non-primative data type ví dụ như object, array, function thì được truyền bởi reference (sự liên quan) trong JS 

## 1. 🥇 Trước hết 

Để hiểu Pass by value và Pass by reference trong JS đầu tiên bạn cần phải hiểu Primative data và Non-primative data

Chú ý: trong JS, giá trị primative được lưu ở stack, trong khi non-primative được lưu ở heap ???


## 2. 🧩 Pass by value 

- Có nghĩa là copy giá trị tham số thực được tạo ở bộ nhớ ... 1 bộ nhớ chỉ định hoàn thành, và tất cả thay đổi được tạo bởi giá trị mới (giá trị được copy). Giá trị chính thức và giá trị copy thì độc lập với nhau, cả 2 đều được lưu ở 2 vị trí khác nhau trong bộ nhớ ... khi thay đổi giá trị trong function, biến bên ngoài sẽ không bị ảnh hưởng

- Đơn giản, có thể hiểu là hàm nhận bản sao của biến, bản sao này độc lập với biến ban đầu được truyền vào 

- Pass by value trong JS yêu cầu nhiều không gian hơn vì hàm nhận bản sao nội dung thực do đó biến mới được tạo trong 1 bộ nhớ riêng

- Trong định nghĩa này, thì toàn tử bằng đóng 1 vai trò lớn. Khi chúng ta tạo 1 biến nó sẽ thông báo là chúng ta đang gán biến giá trị primative hay non-primative và sau đó có hoạt động tương ứng

chú ý: khi sử dụng toán tử bằng, có 1 function được gọi (behind the senses) khi pass by value / reference xong 

VD 
[https://scaler.com/topics/images/pass-by-value.webp]

- khi gán biến có giá trị primative, thì toán tử bằng set 1 khoảng trống (location/address) trong bộ nhớ để lưu data của biến num1 (address 2001)

- bây giờ, khi tạo biến num2 (address 2002) và gán nó cho giá trị của biến trước đó num1, toán tử bằng tạo 1 KHOẢNG KHÔNG MỚI ở bộ nhớ nơi mà độc lập với biến trước đó num1 (address 2001) và đặt bản copy của nó (của num1) vào khoảng không mới này. Do đó, điều naỳ đã sao chép giá trị của biến ban đầu, num1, vào 2 vị trí riêng biệt trong bộ nhớ (2001 và 2002)

```swift
  let num1 = 70
  let num2 = num1
  
  console.log(num1) // 70
  console.log(num2) // 70
  
  num1 = 40
  
  console.log(num1) // 40
  console.log(num2) // 70
```

- ở đây, chúng ta gán num1 giá trị 70. Điều naỳ làm tạo 1 khoảng trống địa chỉ 2001 (giả định). Khi chúng ta tạo biến num2 và gán nó giá trị của num1, sau đó toán tử bằng sẽ thông báo rằng chúng ta đang xử lí 1 giá trị primative sau đó tạo một KHOẢNG TRỐNG MỚI trong bộ nhớ với địa chỉ 2002 và gán cho nó giá trị của num1, là 70. Bây giờ chúng ta có thể thấy rằng cả 2 biến có 2 khoảng trống khác nhau ở bộ nhớ, và đều là 70

- bây giờ nếu chúng ta thay đổi giá trị của num1, sau đó num2 sẽ không bị ảnh hưởng

VD khác 
```swift
  function multiplication(tmp) {
      tmp = tmp * 50;
      return tmp;
  }
  var num = 30;
  var result = multiplication(num);
  console.log(num); // 30
  console.log(result); // 1500
```

---
Giải thích

1.

_hình ảnh_

2.

_hình ảnh_

3.

_hình ảnh_

4.

_hình ảnh_

## 3. ⚽ Pass by reference 





### 3.1 Pass by reference in Object 

### 3.2 Pass by reference in Array 

## 4. 🎯 Khi nào ?

## 5. 🎁 Tổng kết 


