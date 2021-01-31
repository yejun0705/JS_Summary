# JavaScript Summary
2021.02.01

---------------------------------------
## Const

- 블록 단위 스코프
- 선언 시 값을 할당해야하며 이후에 재할당 불가능
- code

    ```jsx
    const URL = 'http://js.com';
    // const로 정의된 상수에 새로운 문자열을 할당하면 에러가 발생
    URL = 'http://js.com';

    if(true) {
        const URL2 = 'http://js.com';

    }

    // if 문 블록 안에서 const로 정의된 URL2 변수는 블록 밖에서 접근할 경우 에러가 발생
    console.log(URL2);
    ```

- const 키워드로 정의된 상수에 객체를 할당하면 불변 객체(Immutable Object)가 되지는 않음

    *불변 객체 : 정의된 후에 그 상태를 바꿀 수 없는 객체

- code

    ```jsx
    // const로 정의된 객체는 불변 객체가 아님
    const CONST_USER = {name : 'jay', age : 30};

    console.log(CONST_USER.name, CONST_USER.age);

    // 불변 객체가 아니기 때문에 속성에 다른 값을 할당할 수 있음
    // 객체 내부 상태가 변경 가능하기 때문에 const로 배열을 선언해도 새로운 요소를 추가, 변경 가능
    CONST_USER.name = 'jay2';
    CONST_USER.age = 31;

    console.log(CONST_USER.name, CONST_USER.age);
    // const로 정의되어 있기 때문에 재할당이 불가능
    CONST_USER = {name : 'bbo'};
    ```