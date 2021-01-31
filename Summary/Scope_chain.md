# JavaScript Summary
2021.02.01

---------------------------------------
## Scope Chain(스코프 체인)

- 스코프가 연결되어 있음을 나타냄
- 실행 컨텍스트

    → 코드가 실행되기 위해 필요한 정보를 가지고 있음

    → 실행 가능한 코드가 실행될 때 생성됨  ex) 전역 코드와 함수 코드, eval, 모듈 코드 등

    → 처음에는 전역 코드가 먼저 실행

    → 전역 컨텍스트를 만들고 전역 코드를 순차적으로 평가

    → 함수가 호출문을 만나면 새로운 실행 컨텍스트가 만들어지면서 해당 함수 실행부의 코드를 순차적으로 평가

    → 이때 스택을 이용해 실행 컨텍스트를 관리 함

    - code & explain

        ```jsx
        var person = 'harin';

        function print() {
            var person2 = 'jay';

            function inner_print() {
        				// inner_print 함수가 호출될 때 두 변수 person, person2의 각 식별자는 연결된 값을 자신의 실행 컨텍스트의 렉시컬 환경에서 찾음
        				// But, person과 person2는 inner_print 함수 내에 선언되지 않았음 inner_print 실행 컨텍스트의 환경 레코드에는 아무런 Key : Valye 쌍이 없게 됨
        				// 이렇게 자신의 실행 컨텍스트에 없으면 외부 렉시컬 환경의 참조를 통해 연결된 print 실행 컨텍스트에서 person2를 찾아서 'jay'출력
        				// 마찬가지로 person은 전역 실행 컨텍스트까지 가서 찾아 값을 출력
                console.log(person);
                console.log(person2);

            }
            inner_print();

            console.log('print finished');

        }
        print();

        console.log('finished')
        ```

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26f6aa11-6094-4090-9316-2cd3ab4024b7/IMG_93CB91D1C52F-1.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26f6aa11-6094-4090-9316-2cd3ab4024b7/IMG_93CB91D1C52F-1.jpeg)

        - 실행 컨텍스트는 렉시컬 환경을 가지고 있음
        - 렉시컬 환경은 환경 레코드와 외부 렉시컬 환경으로 구성됨
        - 실행 컨텍스트를 자바스크립트의 객체 형태로 표현하면 다음과 같음

        ```jsx
        execution_context = {
            lexical_environment : {
                environment_record : {

                },
                outer_lexical_environment : 참조
            }
        }
        ```

        - 실제 함수와 변수같은 식별자와 그 식별자가 가리키는 값은 Key와 Value의 쌍으로 환경 레코드에 기록됨
        - 렉시컬 환경은 환경 레코드 외에 자신의 실행 환경을 감싸는 외부 실행 환경에 대한 참조를 가짐

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a50287c8-d4d0-4607-b122-003aecd2a408/IMG_B6A9B76D561E-1.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a50287c8-d4d0-4607-b122-003aecd2a408/IMG_B6A9B76D561E-1.jpeg)

        - 각 실행 컨텍스트는 outer_lexical_environment로 체인처럼 연결되어 있음
        - 각 렉시컬 환경이 연결되어 있기 때문에 스코프 체인이 형성 될 수 있음