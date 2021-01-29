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