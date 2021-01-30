# JavaScript Summary
2021.01.30

---------------------------------------
## arguments 객체

- **argument** : 전달 인자 → 함수가 호출될 때 전달되는 값
- JS는 전달 인자의 개수와 매개변수의 개수가 달라도 에러를 발생시키지 않음

    → 매개변수화 무관하게 함수 호출 시 더 많은 인자를 전달 가능

- arguments 객체

    → 매개 변수 이외에 함수에서만 사용 가능한 특별한 객체

- code

    ```jsx
    // 내부에 arguments 객체를 통해 전달된 인자의 합을 반환
    function sum() {
        var total = 0;

        for(var i = 0; i < arguments.length; i++) {
            // arguments 객체는 Array와 유사하게 인덱스를 통해 접근 가능
            // But length 속성 외에는 어떠한 속성과 메소드를 가지고 있지 않음
            total += arguments[i];
        }
        // instanceof 연산자를 이용하여 arguments 객체가 배열이 아닌것을 확인할 수 있음
        console.log(arguments instanceof Array);
        return total;

    }

    // sum 함수는 매개변수 정의 X, But 인자로 1, 2, 3을 전달 -> 에러 발생 X
    var sum_of_1to3 = sum(1, 2, 3);
    console.log(sum_of_1to3);

    function test_arg() {
        // arguments 객체를 배열로 바꾸기 위해 Array.prototype에 정의된 slice 호출 
        // -> arguments 객체 요소들을 복사하는 새로운 Array 생성
        var new_arr = Array.prototype.slice.call(arguments);
        console.log(new_arr);
        // Array이기 때문에 indexOf 메소드를 사용하여 문자열 b의 인덱스 반환
        console.log(new_arr.indexOf('b'));
        // arguments 객체는 배열이 아님 -> 에러 발생
        console.log(arguments.indexOf('b'));

    }

    test_arg('a', 'b');
    ```