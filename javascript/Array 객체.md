# Array 객체

<img src="https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220106105736612.png" alt="image-20220106105736612" style="zoom: 67%;" />

 자바스크립트는 배열(array)이 **가변길이**의 배열이다.

<img src="https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220106110029155.png" alt="image-20220106110029155" style="zoom:67%;" />

그렇다면, 배열은 꼭 0번째부터 넣어야 하는 것일까? 그렇지 않다.

만약 인덱스 3에 처음으로 넣게 되면, 앞의 3개의 빈 공간이 남아있게 된다.

```javascript
var nums = new Array();
nums[5] = 3;
nums[10] = 20;
nums[20] = 21;
nums[1] = 13;

console.log(nums);

/* Array(21)
1: 13
5: 3
10: 20
20: 21
length: 21 */
// nums[20]번째 인덱스에 값을 넣었기 때문에 배열 안에 21개의 공간이 생긴다.
```

<img src="https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220106111405730.png" alt="image-20220106111405730" style="zoom:67%;" />

공간을 계속 늘릴 수 있게 하는 것보다는 미리 한정하는 것이 좋다. 왜냐하면 계속 늘리게 하면 안에서 계속 값들이 이동하고있기 때문에 성능적으로 좋지 않다.

```javascript
var nums = new Array(5);	// 배열에 5개의 공간으로 한정
var nums = new Array(5, 10, 21);	// 배열에 값을 순서대로 5, 10, 21 넣음(초기값)
```

인자에 1개만 넣으면 공간이 만들어지는 것이고, 인자에 2개이상의 값을 넣으면 그게 초기값이 되는 것이다.

※ **typeOf**연산자로 안의 값의 형식을 알 수 있다.

- 배열 안에 배열

```javascript
var nums = new Array(5, 10, 21, new Array(2,3,4));
console.log(nums[3][0]);
// 2
```

배열안에 배열을 꺼내기 위해서는 위의 예시에서 nums배열의 인덱스 4가 배열이니까 nums[4]하고 안에 2번째 값을 찾으려면 nums[4] [1]로 하면 된다. => 결과: 3





------

※출처: 뉴렉처(newlecture)