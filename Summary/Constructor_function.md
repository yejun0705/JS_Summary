# JavaScript Summary
2021.02.16

---------------------------------------
## 생성자 함수

- 자바스크립트의 함수

    → 재사용 가능한 코드의 묶음

    → 객체를 생성하기 위한 방법

- 객체를 생성하기 위해 직접적으로 객체를 반환하거나 new 키워드를 사용하여 함수를 호출
- new 키워드를 사용하여 함수를 호출 → return 문이 없어도 새로운 객체가 반환됨
- 함수 바디에서 this 키워드를 사용하여 반환되는 객체의 초기 상태와 행위를 정의할 수 있음

- 생성자 함수

    → 객체를 생성하는 역할을 하는 함수

    → new 키워드를 사용하지 않으면 일반적인 함수와 동일하게 동작, 새로운 객체를 생성하지 않음

    → 함수명을 대문자로 시작하는 관례를 가짐

객체에 타입이 적용되면 해당 객체는 그 타입의 인스턴스라고 부름
생성자 함수는 새로운 타입을 정의하는데 사용됨 
      → new 키워드로 만들어진 객체는 해당 타입의 인스턴스가 됨

- code

    ```jsx
    // Teacher 생성자 함수 정의
    function Teacher(name, age, subject) {
        // 전달받은 매개변수를 this의 속성으로 대입
        this.name = name;
        this.age = age;
        this.subject = subject;
        this.teach = function(student) {
            console.log(student + '에게' + this.subject + '를 가르칩니다.');
        };
    }

    // new 키워드와 함께 생성자 함수를 호출 -> 생성자 함수 블록이 실행됨
    // 별도의 return 문이 없어도 새로운 객체가 반환됨
    const jay = new Teacher('jay', 30, 'JS');
    console.log(jay);
    jay.teach('bbo');

    // 모든 객체는 constructor 객체를 가짐 -> constructor 속성은 객체를 만든 생성자 함수를 가리킴
    console.log(jay.constructor);
    // instanceof 연산자를 이용하여 jay 객체가 Teacher 생성자 함수의 인스턴스 여부를 확인
    console.log(jay instanceof Teacher);

    // new 키워드를 빼고 생성자 함수 호출 -> 이때 생성자 함수의 this는 전역 객체를 가리키게 됨
    // 전역 객체에 name, age, subject 속성으로 전달받은 매개변수가 항당됨
    const jay2 = Teacher('jay', 30, 'JS');
    // 새로운 객체가 반환되지 않기 때문에 undefined 출력
    console.log(jay2);
    // 전역 변수의 age를 참조해 출력
    console.log(age);
    ```