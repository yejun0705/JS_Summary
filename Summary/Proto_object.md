# JavaScript Summary
2021.02.16

---------------------------------------
## 프로토 객체

- 자바스크립트는 프로토타입 기반으로 객체지향 프로그래밍을 지원
- 프로토타입으로 객체에 공통 사항을 적용할 수 있음
- 모든 객체는 다른 객체의 원형(Prototype)이 될 수 있음
- 특징을 묘사하는 프로토 객체를 만들고 이 프로토 객체에 기반하는 여러 객체들을 만들면 모두 같은 특징을 가질 수 있음
- code

    ```jsx
    // Prototype 객체 정의
    const student_proto = {
        gain_exp : function() {
            this.exp++;
        
        }

    }

    // 이름, 나이, 경험치를 속성으로 가지는 객체 정의
    const harin = {
        name : '하린',
        age : 10,
        exp : 0,
        // 자바스크립트에서는 __proto__ 속성으로 원형 객체를 정의할 수 있음
        // 모든 자바스크립트 객체는 __proto__ 속성을 가짐 But, 별도로 __proto__ 속성에 다른 객체를 할당하지 않으면 기본적으로 Object.prototype 객체가 연결되어 있음
        __proto__ : student_proto

    };

    const bbo = {
        name : '뽀',
        age : 20,
        exp : 10,
        __proto__ : student_proto

    };

    bbo.gain_exp();
    harin.gain_exp();
    harin.gain_exp();

    console.log(harin);
    console.log(bbo);
    ```