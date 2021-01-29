# JavaScript Summary
2021.01.29

---------------------------------------
## Function(함수)

```jsx
function 함수이름(매개변수) {
	// 함수 실행부
}
```

- 함수를 만드는 두 가지 방법
    1. 함수 표현식
    2. 함수 선언문
    - code

        ```jsx
        // 함수 표현식
        // 함수를 정의와 동시에 변수에 할당 -> greeting_expression 변수에 함수 리터럴을 할당
        var greeting_expression = function(name) {
            console.log('Hi, ' + name);
        }

        // 함수 선언문
        function greeting_declaration(name) {
            console.log('Hi, ' + name);
        }

        greeting_expression('chloe');
        greeting_declaration('ES');
        ```

    - 함수 표현식에서 정의한 함수 이름은 해당 함수 안에서만 호출 가능
    - 선언된 함수가 매개변수를 필요로 하는 경우 소괄호 ( ) 안에 전달할 값을 나열
    - arguments 객체
    - 기본 매개변수(default parameter)