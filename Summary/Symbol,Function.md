# JavaScript Summary
2021.01.29

---------------------------------------
## Symbol

- code

    ```jsx
    // Symbol은 함수 호출을 통해 생성, But new 키워드를 통한 호출을 할 경우 에러 발생
    const symbol = Symbol();
    // Symbol을 함수 호출 시 값을 전달할 수 있지만 디버깅 용도이며 고유한 Symbol 값은 만들어지지 않음
    // -> 즉 Symbol은 늘 고유한 값을 반환 -> 8, 9 라인은 false
    const hello = Symbol('hello');

    console.log(Number(3) === Number(3));
    console.log(Symbol('symbol') === Symbol('symbol')); // false
    console.log(Symbol() === Symbol()); // false
    console.log(typeof Symbol);

    // Symbol은 객체의 키로 사용 가능
    // 객체의 키로 사용하기 위해선 Symbol에 대한 레퍼런스를 변수에 담고 있다 접근할 때마다 사용해야함
    const nationility = Symbol('nationility');

    const user = {
        name : 'jay'
    };

    user[nationility] = 'korean';
    console.log(user[nationility]);

    // Symbol이 객체의 키로 사용되면 for-in 루프를 통해 Symbol Key를 가져올 수 없음
    for(let key in user) {
        console.log(key);
    }

    // Object의 키를 반환하는 메소드를 사용해도 가져올 수 없음, JSON 문자열로 만들 때에도 해당 키는 빠짐
    console.log(Object.keys(user));
    console.log(Object.getOwnPropertyNames(user));
    console.log(JSON.stringify(user));

    // Object.getOwnPropertySymbols 메소드를 통해 해당 객체의 키에 해당하는 심볼들을 가져올 수 있음
    const symbolProperties = Object.getOwnPropertySymbols(user);
    console.log(symbolProperties);
    console.log(user[symbolProperties[0]]);
    ```

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
    - [arguments 객체](https://www.notion.so/JavaScript-34fb7ba0b4924f8b8a12180451ac0f29#25a9cd0136db44f18471afe1fdba200f)
    - [기본 매개변수(default parameter)](https://www.notion.so/JavaScript-34fb7ba0b4924f8b8a12180451ac0f29#2d0466257b71494b8b4f6a470b280f62)