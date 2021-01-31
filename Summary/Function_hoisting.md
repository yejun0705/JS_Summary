# JavaScript Summary
2021.02.01

---------------------------------------
## 함수 호이스팅

- 함수를 선언하기 전에 호출이 가능함
- code

    ```jsx
    hello();

    function hello() {
    	console.log('안녕하세요');

    }

    // TypeError 발생
    // 실제로 hello2 이름으로 선언된 변수는 호이스팅이 이루어짐 여기엔 undefined가 할당됨
    // undefined는 호출할 수 없기에 TypeError 발생
    hello2();

    var hello2 = function() {
    	console.log('안녕하세요');

    }
    ```