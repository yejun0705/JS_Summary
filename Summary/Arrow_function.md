# JavaScript Summary
2021.02.06

---------------------------------------
## Arrow Function(화살표 함수)

- 기존 함수를 간결하게 표현할 수 있고 기능이 개선됨
- function 키워드를 사용하지 않고 화살표 모양 ⇒ 연산자를 이용하여 정의
- 규칙
    1. 매개변수가 하나일 경우에는 인자를 정의할 때 괄호 생략 가능
    2. 매개변수가 없거나 둘 이상일 경우 괄호를 작성해야함
    3. 화살표 함수 코드 블록을 지정하지 않고 한 문장으로 작성 시 return 문을 사용하지 않아도 화살표 오른쪽 표현식의 계산 결과값이 반환됨
    4. 화살표 함수 코드 블록을 지정했을 경우 반환하고자 하는 값에 return 문을 작성해야함

        return 문이 없을 시 → undefined 가 반환됨

- code

    ```jsx
    // 매개변수 x를 전달 받아 x + x 결과를 반환하는 화살표 함수를 정의하고 double 변수에 할당
    const double = x => x + x;
    console.log(double(2));

    // a와 b 두 매개변수를 가지는 화살표 함수를 정의함
    // 메개변수는 괄호를 사용하였고, 코드 블록은 한 문장이기 때문에 두 매개변수 합의 결과값이 반환됨
    const add = (a, b) => a + b;
    console.log(add(1, 2));

    // 아무 매개변수를 정의하지 않았음, 때문에 괄호로 빈 매개변수를 표현함
    // 화살표 함수 코드 블록을 작성하고 내부에 arguments 객체를 콘솔에 출력
    // return 문이 없기 때문에 반환값은 없음
    const print_arguments = () => {
        console.log(arguments);

    }
    // 인자로 1, 2, 3을 전달하면서 정의된 화살표 함수를 호출 But, 콘솔에는 Uncaught ReferenceError 발생
    // 화살표 함수는 기본 함수와 다르게  arguments 객체가 만들어지지 않아 에러가 발생
    print_arguments(1, 2, 3);

    // 인자들의 합을 구하는 화살표 함수 정의
    // arguments 객체 대신 나머지 연산자를 통해 매개변수 정의
    // args는 전달받은 인자 목록을 배열로 사용 가능
    // 화살표 함수 코드 블록에 대괄호를 사용하였기 때문에 return 문을 작성하여 반환값을 명시
    const sum = (...args) => {
        let tatal = 0;

        for(let i = 0; i < args.length; i++) {
            total += args[i];

        }
        return total;

    }
    console.log(sum(1, 2, 3));

    // 화살표 함수를 함수의 인자로 전달 가능
    set_timeout(() => {
        console.log('화살표 함수!');

    }, 10);
    ```