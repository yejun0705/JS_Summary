# JavaScript Summary
2021.02.01

---------------------------------------
## Let

- 변수 선언 시 변수의 유효 범위를 블록으로 지정 가능하게 함
- code

    ```jsx
    if(true) {
        // var 키워드로 정의한 변수는 함수 단위의 유효 범위를 가지게 됨 -> if 문 블록에서 정의하여도 블록 밖에서도 접근 가능
        var function_scope_value = 'global';
        // let 키워드로 정의한 변수는 블록 단위의 유효 범위를 가지게 됨 -> if 문 블록 밖에서 접근 불가능
        let block_scope_value = 'local';

    }

    // global 출력
    console.log(function_scope_value);
    // ReferenceError
    console.log(block_scope_value);
    ```

- let으로 선언한 변수는 호이스팅에서 설명한 것과 동일하게 블록 단위로 일어남
- var과 다르게 undefined값이 할당되기보다 블록 시작부터 선언이 이루어진 라인까지 일시적으로 접근을 막음
- code

    ```jsx
    let Value = "바깥값";

    if(true) {
    		// Cannot access 'Value' before initialization(초기화 전에 '값'에 액세스 할 수 없습니다.)
        console.log(Value);
        let Value = "안쪽값";
    }
    ```