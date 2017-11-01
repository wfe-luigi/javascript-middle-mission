- 비트연산자 보수이해하기  
 비트연산자의 종류 : &(and), |(or), ^(xor), ~(Not)  
 음수의 표현방법 > 2진수에 1의 보수를 취하고 1을 더함  
```
10(10) = 1010(2)  
1의보수 -> 0101 -> 0110(2) = -10

연산
1010(2) = 10
0110(2) = -10
------
0000(2) = 0 //가장 앞에 있는 부호비트는 버림
```
컴퓨터에서 일반적으로 음수로 변환할때   
Not -> + 1 을 한다

- 10을 2진표현으로 변경하려면 어떤 순서로 계산해야 하는지 설명하기.  
2로 나눈 몫을 재귀적으로 2로 나눔, 그 나머지들은 뒤에서부터 저장  
10/2  ->  5/2  ->  2/2  -> 1  
  %2=0    %2=1      %2=0  
=> 1 0 1 0
```
var result = [];
function decTobin(arg) {
    result.unshift(arg % 2);
    if (parseInt(arg / 2) > 0) decTobin(parseInt(arg / 2));
    return result;
}
```
- hoisting 에 대해서 설명하기  
코드가 실행될때 함수선언은 컨텍스트 상단에 끌어올려짐  
-> 함수를 호출하는 코드가 함수선언한 코드보다 앞에 있어도 에러가 발생하지 않는데 이러한 특성을 호이스팅(hoisting) 이라고 함
```
var result = add(5,5); //에러발생 X

function add(num1,num2){
  return num1+num2;
}
```

- !! 은 무엇을 의미하는가? 어떻게 활용할 수 있을까?  
그 문장의 true,false을 판별할때 사용

- 3개이상의 switch 문을 어떻게 3항연산자로 대체할 수 있을까? 코드로 예시를 들라.
 ```
  a ? b : c ? d : e
  //a가 일때 b 실행
  //a가 거짓일때, c가 참일때 d가 실행, c가 거짓이면 e가 실행
 ```

- ==와 ===의 차이는 정확히 무엇인가?  
== -> 값 비교  
=== -> 값/타입의 비교
```
console.log(1=="1"); //true
console.log(1==="1"); //false
```

- const value = a || b; 코드의 의미는 무엇인가?  
 a가 없을경우 b의 값을 value에 삽입 

- eval 은 무엇인가?  
매개변수 문장을 그대로 실행
```
eval(new String("2 + 2")); // "2 + 2" 인 문자열 객체를 반환
eval("2 + 2");             // 4을 반환
```

- 변수값을 출력할때 null, undefined, is not defined으로 출력되는 차이점은 무엇인가?  
null은 값이 없음을 뜻함  
undefined 는 선언만 되고 값이 할당되지 않은 상태  
```
var a = null;
var b
console.log(a); // null , 리터럴
console.log(b); // undefined , 전역객체의 프로퍼티
console.log(c); // is not defined

console.log(null == undefined); //true;
console.log(null === undefined); //false;
```
- Function.prototype.bind 에 대해서 설명하기  

- this가 가리키는 건 언제 결정되는가?  
함수가 호출될때 결정 

- call과 apply의 차이점은?  
둘다 함수를 실행할때 this를 조작할 수 있는 메소드지만,  
call은 첫번째 인자는 this값, 두번째 인자부터는 함수에 전달한 인자  
apply는 첫번째 인자는 this값, 그리고 두번째 인자는 함수에 전달할 인자를 담고 있는 배열 또는 배열과 유사한 객체이다.

- add(10)(2) //12 가 되도록 구현해보기  
add(10)(2)에서 (2)가 동작하려면 add(10)은 함수여야 가능
add(10)의 결과를 함수값으로 전달
```
var add = function(x){ 
  return function(y){ return x+y;};
}
이때 사용되는 함수의 이름이 없음 -> 익명함수
```
- 함수의 인자갯수와 파라미터가 일치하지 않으면 어떤일이 생기는가 설명하기  
선언된 인자수보다 작을시에는 undefined 가 되고,  
많을시에는 문제가 상관이 없고, arguments 로 접근이 가능

- 함수의 반환값이 없을때 어떻게 되는가?  
undefined 가 반환됨

- 익명함수는 무엇인가?
이름이 없는 함수  
```
var func = function(value){ console.log(value;)}
```
