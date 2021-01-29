# JavaScript Summary
2021.01.30

---------------------------------------
## 예외 처리

1. **throw**
    - 개발자가 의도한 에러를 처리할 때 → 코드에서 잘못될 가능성을 예상하고 발생시키는 에러
    - throw문은 고의로 에러를 발생시켜 예외 상황을 알리는 역할
    - throw문이 실행되면 실행되고 있던 블록을 빠져나감
    - 예외 상황을 미리 파악하고 에러를 발생시켜 이후 코드가 실행되지 않도록 막음
    - 에러를 발생시킨 것이므로 프로그램이 중단되는 것은 막을 수 없음
    - code

        ```jsx
        function check_num(val) {
            // 숫자형 값이 아닌경우 throw문 실행 -> 함수 블록 빠져나감
            if(typeof val !== 'number')
                throw '유효하지 않은 값입니다.';
            // 숫자형이 확인되면 출력되는 문장
            console.log('숫자형 값으로 확인되었습니다.');
        }

        check_num(100);
        // 틀린 타입을 넣으면 throw문이 실행됨
        check_num('틀린 타입');
        console.log('완료');
        ```

2. **try-catch-finally**
    - try 블록 안에서 발생된 에러를 잡아내고, catch블록으로 제어권을 넘김
    - try 블록에서 발생된 에러 정보는 catch 문의 변수로 전달됨 → 프로그램 종료 없이 에러 확인 가능
    - finally 블록은 에러 발생 여부와 상관없이 실행되는 블록.

        ex) 파일 입출력을 할 때 에러가 발생하더라도 파일 close 구문 실행 가능

    - code

        ```jsx
        function check_num(val) {
            // 숫자형 값이 아닌경우 throw문 실행 -> 함수 블록 빠져나감
            if(typeof val !== 'number')
                throw '유효하지 않은 값입니다.';
            // 숫자형이 확인되면 출력되는 문장
            console.log('숫자형 값으로 확인되었습니다.');

        }

        try {
            check_num(100);
            
            // 틀린 타입이기 때문에 에러가 발생, But try 문의 블록 안에 있기 때문에 발생된 에러 정보는 catch 블록으로 전달
            check_num('Wrong Type');

        }
        //변수 e에 에러 정보가 전달돔
        catch(e) {
            console.log(`에러가 발생했습니다. >>> ${e}`);

        }
        // finally 문은 try ~ catch 코드가 모두 실행된 후 마지막에 실행됨 에러 여부와 상관없이 실행 
        finally {
            console.log(`완료`);

        }
        ```