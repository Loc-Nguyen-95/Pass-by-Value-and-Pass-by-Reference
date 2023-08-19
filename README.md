# `Pass by Value` & `Pass by Reference`

*Trong JS khi 1 function được gọi thì tham số có thể được truyền qua 2 cách: Pass by value và Pass by referance (address). Primative data type ví dụ như string, number, null, undefined, boolean thì được truyền thông qua giá tr trong khi non-primative data type ví dụ như object, array, function thì được truyền bởi reference (address) trong JS*

## 1. 🥇 Trước hết 

Để hiểu Pass by value và Pass by reference trong JS đầu tiên bạn cần phải hiểu Primative data và Non-primative data

**Chú ý:** trong JS, giá trị primative được lưu ở stack, trong khi non-primative được lưu ở heap ???


## 2. 🧩 Pass by value 

- Có nghĩa là copy giá trị tham số thực được tạo ở bộ nhớ ... 1 bộ nhớ chỉ định hoàn thành, và tất cả thay đổi được tạo bởi giá trị mới (giá trị được copy). Giá trị chính thức và giá trị copy thì độc lập với nhau, cả 2 đều được lưu ở 2 vị trí khác nhau trong bộ nhớ ... khi thay đổi giá trị trong function, biến bên ngoài sẽ không bị ảnh hưởng

- Đơn giản, có thể hiểu là hàm nhận bản sao của biến, bản sao này độc lập với biến ban đầu được truyền vào 

- Pass by value trong JS yêu cầu nhiều không gian hơn vì hàm nhận bản sao nội dung thực do đó biến mới được tạo trong 1 bộ nhớ riêng

- Trong định nghĩa này, thì toàn tử bằng đóng 1 vai trò lớn. Khi chúng ta tạo 1 biến nó sẽ thông báo là chúng ta đang gán biến giá trị primative hay non-primative và sau đó có hoạt động tương ứng

**chú ý:** khi sử dụng toán tử bằng, có 1 function được gọi (behind the senses) khi pass by value /by reference xong 

**VD**

<img width="717" alt="Screenshot 2023-08-19 at 10 59 23" src="https://github.com/Loc-Nguyen-95/Pass-by-Value-and-Pass-by-Reference/assets/136717443/9ea9ae10-b1a1-4925-a880-72e871f37a40">

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

- ở ví dụ trên chúng ta có thể thấy rằng hàm thực hiện phép nhân nhận 1 biến và thay đổi nó

![image01](https://scaler.com/topics/images/variable-num.webp)

- sau đó, chúng ta gán giá trị num vào function. JS sẽ tự động sao chép giá trị biến num vào tmp. vì vậy, num là 1 biến mới được định vị trong bộ nhớ độc lập với num

![image02](https://scaler.com/topics/images/multiplication-function.webp)

bây giờ tất cả thay đổi được thực hiện bởi hàm thực hiện phép nhân thì được hoàn thành trực tiếp vào biến tmp, do đó, giá trị của num vẫn không bị ảnh hưởng

![image03](https://scaler.com/topics/images/variable-temp.webp)

- điều này xảy ra bởi vì 1 bản sao riêng biệt của num được tạo trong bộ nhớ có tên là tmp và gía trị ban đầu là 30, sau khi tính toán trở thành 1500

![image04](https://scaler.com/topics/images/tmp.webp)

## 3. ⚽ Pass by reference 

Không giống như Pass by value, Pass by reference không tạo ra khoảng trống tromng bộ nhớ, thay vào đó, chúng ta truyền reference/address của tham số, có nghĩa là function có thể truy cập giá trị chính thức của biến. Do đó, nếu chúng ta thay đổi giá trị của biến bên trong function thì giá trị thực sẽ bị thay đổi

Nó không tạo ra bản copy, thay vào đó, nó hoạt động dựa trên biến thực nên mọi thay đổi bên trong hàm sẽ làm ảnh hưởng đến biến 

![image05](https://scaler.com/topics/images/pass-by-reference.webp)

Không như Pass by value trong JS, ở đây, khi mà toán tử bằng nhận ra rằng biến obj1 được set bằng với object, nó tạo ra 1 khoảng không bộ nhớ và chỉ obj1 đến 3005 (giả sử đang là 1 địa chỉ). Bây giờ, khi chúng ta tạo 1 biến obj2 và gán nó giá trị của obj1, toán tử bằng nhận định rằng chúng ta đang xử lí 1 non-primitive data type; do đó, nó chỉ đến cùng địa chỉ của obj1. Vì vậy, chúng ta có thể thấy rằng không 1 không gian mới nào được tạo ra, thay vào đó cả 2 biến đều chỉ tới cùng 1 địa chỉ (của obj1)

```swift
  let obj1 = {website: "Scaler Academy"}
  let obj2 = obj1;
  
  console.log(obj1)     // {website: "Scaler Academy"}
  console.log(obj2)     // {website: "Scaler Academy"}
  
  obj1.website = "Scaler Topics"
  
  console.log(obj1)     // {website: "Scaler Topics"}
  console.log(obj2)     // {website: "Scaler Topics"}
```
Trong VD trên, obj1 là 1 object sau đó cho obj2 bằng với obj1

Toán tử bằng nhận diện đây là 1 non-primitive và thay vì tạo ra 1 khoảng trống bộ nhớ mới nó dẫn obj2 vào cùng địa chỉ với obj1. Do đó, khi chúng ta thay đổi giá trị của obj1, thì giá trị của obj2 cũng sẽ thay đổi (vì đang cùng khoảng không bộ nhớ)

### 3.1 Pass by reference in Object (khi trong 1 function)

VD 

```swift
  let originalObj = {
  name: "Scaler Academy",
  rating: 4.5,
  topic: "JavaScript"
  };
  
  function demo(tmpObj) { 
    tmpObj.rating = 5; 
    console.log(tmpObj.rating); 
  } 
  
  console.log(originalObj.rating);    // 4.5
  demo(originalObj);             // 5
  console.log(originalObj.rating);    //5
```

Trong ví dị trên, chúng ta có thể thấy khi thay đổi giá trị của tmpObj, giá trị của orinalObj cũng thay đổi. Vì khi chúng ta gọi function demo và truyền cho nó 1 object, sau đó orinalObj được truyền (gán?) bởi tham chiếu của chính nó (reference), vì vậy biến local tempObj sẽ chỉ đến cùng object mà chúng ta đã định nghĩa ... chính là orinalObj 

![image06](https://scaler.com/topics/images/pass-by-reference-in-object.webp)

Vì vậy trong trường hợp này, chúng ta không xử lí 2 bản copy, thay vào đó có 2 biến mà cùng dẫn đến 1 object, vì vậy mọi thay đổi xảy ra với biến này sẽ ảnh hưởng đến biến kia 

### 3.2 Pass by reference in Array (khi trong 1 function)

```swift
  let originalArr = ["Scaler", "Academy","is", "the"];
  
  function pushArray(tmpArr) { 
    tmpArr.push('best')
    console.log(tmpArr); 
  } 
  
  console.log(originalArr);    // ["Scaler", "Academy", "is", "the"]
  pushArray(originalArr);      // ["Scaler", "Academy", "is", "the", "best"]
  console.log(originalArr);    // ["Scaler", "Academy", "is", "the", "best"]
```

Ở đây, khi mà chúng ta cố gắng thêm 1 item mới vào array tempArray, nó cũng sẽ ảnh hưởng đến originalArr. Điều này xảy ra là vì có 2 bản copy của 1 array (chúng ta đang xử lí chỉ 1 array). Biến tempArr tham chiếu (reference) đến cùng 1 array (đó là orinalArr mà chúng ta đã set ban đầu) 

VD trên cho thấy 1 điều rõ ràng rằng, ngay cả object hay array, mọi thay đổi ở tempArr sẽ dẫn đến sự thay đổi tự động của originalArr 

Do đó, chúng ta có thể kết luận bằng cách nói rằng Non-primitive tương tác bằng sự tham chiếu (reference), vì vậy khi chúng ta set giá trị của nó bằng với giá trị của 1 non-primitive khác hay truyền nó vào 1 function, thì chúng sẽ chỉ đến cùng 1 địa chỉ bộ nhớ và bất cứ khi nào chúng ta thay đổi 1 giá trị thì cả 2 sẽ bị thay đổi 

![image07](https://scaler.com/topics/images/pass-by-reference-in-an-array.webp)


## 4. 🎯 Khi nào ?

### 4.1 Khi nào thì dùng Pass by value

Bởi vì pass vy value trong JS sẽ tạo ra 1 bản copy mới của biến, và bất kì thay đổi nào với biến mới sẽ không ảnh hưởng đến biến cũ, vì vậy nó rất hữu ích khi chúng ta muốn theo dõi biến ban đầu và không muốn giá trị của nó bị mất đi hay thay đổi 

### 4.2 Khi nào thì dùng Pass by reference

Khi chúng ta truyền 1 tham số kích thước lớn, thì nên sử dụng pass by reference bởi vì sẽ không tạo ra 1 bản copy nào khác, không làm tốn bộ nhớ  

## 5. 🎁 Tổng kết 

1. Trong JS, chúng ta có 2 loại dữ liệu là primitive và non-primitive
2. Pimitive là: number, string, boolean, symbol, undefined và null, trong khi, Non-primitive là object, function, array
3. Với pass by value, 1 bản copy mới của biến sẽ được tạo và mọi thay đổi đối với biến copy (copied variable) sẽ không làm ảnh hưởng biến chính thức (original variable)
4. Với pass by reference, chúng ta truyên 1 tham chiếu của tham số thực (actual parameter). Không một bản copy nào tạo ra trong bộ nhớ 

**Source:** [https://www.scaler.com/topics/javascript/pass-by-value-and-pass-by-reference/](https://www.scaler.com/topics/javascript/pass-by-value-and-pass-by-reference/)


