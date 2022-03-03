# 💻 Array 객체의 기능 및 데이터 조작



## Array 객체의 Stack 기능 활용하기

**함수스택**: 함수들이 사용하는 데이터를 스택 방식으로 저장하고 꺼내고 하는데, 배열에 담고 그것을 꺼낼때는 담은순서와 역순으로 꺼내거나 뒤로 돌리기로 해서 최근 것부터 하나씩 빼는 방식이 스택방식이다.(ex. 오목게임, 포토샵의 되돌리기)

![image-20220106112248488](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220106112248488.png)

**push**는 위에 넣고, **pop**은 가장 위의 것을 빼는 것으로 두 개가 Stack방식의 함수이다.

=> **Last In First Out: LIFO**라고도 한다.

```javascript
var nums = new Array();
nums.push(3);
console.log(nums);
nums.push(4);
console.log(nums);
nums.push(5);
console.log(nums);
nums.pop(); // 마지막에 넣은 배열 빼기(5)
console.log(nums);
/*
[3]
(2) [3, 4]
(3) [3, 4, 5]
(2) [3, 4]
*/
```



## Array 객체의 Queue 기능 활용하기

![image-20220106113027960](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220106113027960.png)

**Queue**: 먼저 넣은것을 먼저 꺼내는 것. **버퍼(buffer)**이다. 먼저 들어온 데이터를 먼저 빼는 방식.

=> **First In First Out: FIFO**라고도 한다.

버퍼는 **대기석**이다. 오는대로 바로 소화가 안되니까 대기석이 있는 것이다. 균등하게 데이터를 꺼내보기 위해서 버퍼를 사용한다.

![image-20220106113400048](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220106113400048.png)

먼저 넣은 것을 꺼내고 싶다면 **shift() 함수**를 사용하면 된다.

```javascript
var nums = new Array();
nums.push(3);
console.log(nums);
nums.push(4);
console.log(nums);
nums.push(5);
console.log(nums);
nums.shift();
console.log(nums);
nums.shift();
console.log(nums);  // 현재 콘솔을 펼쳐보면 최초에 담긴 배열만 보여준다.

/*
[3]
[3,4]
[3,4,5]
[4,5]
[5]
*/
```



## Array 객체의 Double Ended Queue

![image-20220107201402564](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220107201402564.png)

이번에는 두가지 방향 다 삽입/삭제가 가능한 **DeQue**가 있다.

상단에서 보았듯이, 가장 위(마지막)에 넣는 것을 push라면 가장 위(마지막)에 넣은 것을 빼는 것은 pop, 가장 먼저 넣은 것을 빼는 것은 shift라면 그 반대로 넣는 것은 **unshift**이다. 이렇게 넣고 빼는 push-pop관계를 반대방향에서는 unshift-shift 관계가 되는 것이다.

![image-20220107201515155](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220107201515155.png)

![image-20220107111904558](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220107111904558.png)

따라서 방향에 따라 왼쪽 -> 오른쪽 기준으로 넣는다면, push로 가장 최근 것을 넣고, shift로 가장 먼저 넣은 것을 빼는 것(EnQueue),

오른쪽 -> 왼쪽 기준으로 넣는다면, unshift로 가장 최근 것을 넣고, pop으로 가장 먼저 넣은 것을 빼게 된다.(DeQueue)

![image-20220107111936093](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220107111936093.png)



## Array 객체의 데이터 조작하기

![image-20220107112227262](https://raw.githubusercontent.com/KimSooHa/TIL/image/img/image-20220107112227262.png)

**splice**: 의미적으로 두개의 줄을 잇는 녀석이다.

splice 를 사용 할 때 첫번째 파라미터는 **어떤 인덱스**부터 지울지를 의미하고 두번째 파라미터는 그 인덱스부터 **몇개**를 지울지를 의미한다.

```javascript
var nums = new Array(1,2,3,4);
console.log(nums);	/* 1,2,3,4 */
nums.splice(2,1);
console.log(nums); /* 1,2,4 */
nums.splice(2,2);
console.log(nums);	/* 1,2 */

/*
1,2,3,4
1,2,4	=> 0부터 시작해서 2번째 인덱스인 3을 포함해서 1개가 빠지므로 1,2,4가 남는다.
1,2	=> 0부터 시작해서 2번째 인덱스인 3을 포함해서 2개가 빠지므로 1,2가 남는다.
*/
```

두번째 인자 이후에 숫자들을 넣게 되면, 첫번째에 넣은 인자에 해당하는 인덱스에서 뒤에 넣은 숫자들을 넣고 첫번째 인자에 넣은 인덱스 이후의 숫자들은 추가한 숫자의 뒤로 밀려나게 된다.

```javascript
var nums = new Array(1,2,3,4);
console.log(nums);
nums.splice(2,2,6,7,8,9);
console.log(nums);	/* 1,2,6,7,8,9 */

/*
2번째 인덱스인 3을 포함한 2개만큼 뒤의 인덱스인 4까지 포함해서 삭제되고, 그 이후의 숫자들인 6,7,8,9가 추가가 된다.
*/

nums.splice(2,0,6,7,8,9);
console.log(nums);	/* 1,2,6,7,8,9,3,4 */
/* 해당 예시는 삭제하는 두번째 인자가 0이기 때문에 삭제되는 인덱스가 없이, 2,3번째 인덱스는 추가한 인덱스들 뒤로 밀려나게 된다. */
```





------

※ 출처: 뉴렉처(newlecture)
