# JavaScript Summary
2021.02.16

---------------------------------------
## 프로토타입 기반 상속

- JS에서 생성자 함수로부터 만들어진 객체는 그 생성자 함수의 Prototype 객체를 상속

    → 모든 인스턴스는 해당 생성자 함수의 프로토타입 객체의 속성과 메소드들 사용 가능

- JS에서 모든 함수는 prototype 속성으로 프로토타입 객체를 가짐
- JS에서 모든 객체는 __proto__ 속성을 가짐 → 이 속성은 해당 객체를 생성한 생성자 함수의 prototype 객체를 가리킴 → 생성자 함수를 통해 타입을 정의할 수 있음
- code

    ```jsx
    // Storage 생성자 함수를 정의
    // 내부 속성으로 data_store을 가지고 빈 객체를 할당
    function Storage() {
        this.data_store = {};
    }
    // Storage 생성자 함수의 프로토타입 객체에 put 메소드를 추가
    Storage.prototype.put = function(key, data) {
        this.data_store[key] = data;
    }
    // Storage 생성자 함수의 프로토타입 객체에 get_data 메소드를 추가
    Storage.prototype.get_data = function(key) {
        return this.data_store
    }
    // Storage 타입의 인스턴스를 생성하면 인스턴스는 해당 생성자 함수의 프로토타입을 상속
    // -> Storage 생성자 함수의 프로토타입에 정의된 메소드들을 해당 인스턴스들은 사용 가능
    const product_strorage = new Storage();

    product_strorage.put('id001', {name : '키보드', price : 2000});
    console.log(product_strorage.get_data('id001'));

    // Removable_storage 생성자 함수 정의 -> Storage 함수를 호출하면서 this를 전달함 
    // Storage 생성자 함수가 호출되면서 Removable_storage 생성자 함수의 this에 Storage 생성자 함수에서 정의한 대로 data_store가 속성으로 추가됨
    function Removable_storage() {
        Storage.call(this);
    }
    // Object.create 메소드는 주어진 인자를 __proto__ 에 연결한 새로운 객체를 반환
    // Object.create를 이용하면 간단히 상속 관계를 형성할 수 있음
    // Removable_strage.prototype에 Object.create(Stroage.protype)을 할당하면 Storage 함수의 프로토타입 객체가 Removable_storage 함수의 프로토타입 객체의 __proto__에 할당됨
    // -> 두 프로토타입이 상속 관계를 형성하게 됨
    Removable_storage.prototype = Object.create(Storage.prototype);

    // Removable_storage 객체에 remove_all 메소드를 추가
    Removable_storage.prototype.remove_all = function() {
        this.data_store = {};
    }

    // Removable_storage 생성자 함수에 의해 만들어지는 인스턴스들은 내부에 없는 메소드를 Removable_storage 생성자 함수의 프로토타입에서 찾고 없으면 Storage 생성자 함수의 프로토타입에서 찾게 됨, 나아가 Object.prototype에서까지 찾게됨
    // 이렇게 프로토타입 객체가 연결되어 있다 하여 Prototype chain이라고도 함
    const product_strorage2 = new Removable_storage();
    product_strorage2.put('id001', {name : '키보드', price :2000});
    product_strorage2.remove_all();

    const item2 = product_strorage2.get_data('id001');
    console.log(item2);
    ```

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2269b803-797e-4ebc-a8c0-bfeb698e1599/IMG_B0471448EE9A-1.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2269b803-797e-4ebc-a8c0-bfeb698e1599/IMG_B0471448EE9A-1.jpeg)

    - 다음은 각 생성자 함수의 프로토타입이 연결된 형태를 보여줌

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1b9c7b4f-4556-4e82-a64f-ab05ea478934/IMG_8F259A8715B2-1.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1b9c7b4f-4556-4e82-a64f-ab05ea478934/IMG_8F259A8715B2-1.jpeg)