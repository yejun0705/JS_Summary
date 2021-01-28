# JavaScript Summary
2021.01.29

---------------------------------------
## Object - 객체

- 값들을 그룹으로 묶은 데이터 모음
- 표현식으로 중괄호 { }를 사용
- 중괄호 안에 여러 값을 넣을 수 있음
- Key와 Value를 한 쌍으로 정의하며 이를 속성(Properties)이라고 부름 → { Key : Value }
- 하나의 Key에는 하나의 Value가 매핑됨
- 객체 안에 중복된 키 이름은 허용하지 않으며, 두 줄 이상의 속성을 정의할 때는 콤마를 사용하여 구분
- code

    ```jsx
    var family = {
    	'address' : 'Seoul',
    	members : {},
    	addFamily : function(age, name, role) {
    		this.members[role] = {
    			age : age,
    			name : name
    		};
    	},
    	getHeadcount : function() {
    		return Object.keys(this.members).length;
    	}
    };

    family.addFamily(30, 'chloe', 'aunt');
    family.addFamily(3, 'lyn', 'niece');
    family.addFamily(10, 'dangdangi', 'dog');
    console.log(family.getHeadcount());
    ```

- **JSON(JavaScript Object Notation)**

    → 자바스크립트의 객체와 유사한 구조를 지닌 데이터 교환 형식(format)

    → Key : Value 쌍의 모음들로 이루어져 있음

    → 반드시 속성 Key 이름은 큰따옴표 " "로 표시된 문자열이어야 함

    → Value는 오직 문자열, 숫자, 배열, true, false, null 혹은 다른 JSON 객체만 가능

    → { "Key" : Value }

- 객체의 속성에 접근하는 방법

    → 객체.속성으로 정의된 키 이름 ex) family.members

    → 대괄호 [ ] 안에 키 값을 문자열로 작성

    - code

- 단축 속성명 기능을 활용하여 객체의 속성을 더 간단하게 정의할 수 있음 → { 변수명 }
- 속성 계산명

    → 대괄호 [ ] 안에 식을 넣거나 변수를 대입하여 동적으로 객체 속성들을 생성 가능

    - code

        ```jsx
        // 객체를 변수 obj에 대입
        var obj = {};

        for(var i = 0; i < 4; i++) {
            // obj 객체에 속성을 추가, 속성명이 key0, key1, key2 ... 로 숫자가 증가되도록 정의
            obj['key' + i] = i;
        }

        console.log(obj);

        // 변수 profile에 문자열 대입
        var profile = 'chloe:30';
        var person = {
            // profile 문자열은 키값으로 하는 속성 정의 
            [profile] : true,
            // profile.split(":")은 문자 ':'을 중심으로 profile 문자열을 나눔
            [profile.split(':')[0]] : profile.split(':')[1]
        };

        console.log(person);
        ```

- 비구조화 할당

    → 배열이나 객체의 값을 새로운 변수에 쉽게 할당할 수 있음

    → 객체 비구조화 할당, 중괄호 { } 안에 속성 이름을 넣어 객체의 여러 속성을 한 번에 가져올 수 있음

    - code

        ```jsx
        var obj = {a : 1, b : 2, c : 30, d : 44, e : 5};

        // 비구조화를 통해 속성 a, c 속성 값을 가져와 번수에 할당
        // 중괄호 안에 원하는 속성명을 넣으면 객체를 비구조화하여 해당 속성명에 따른 값을 각 변수에 할당
        var {a, c} = obj; // a = 1, c = 30

        console.log(`a >>> ${a}`);
        console.log(`c >>> ${c}`);

        // 기존의 속성명을 가져와 새로운 변수명으로 할당하여 정의할 수 있음
        // 구분자 ':'를 사이에 두고 왼쪽에 객체의 속성명, 오른쪽에 새로운 변수명을 넣으면 됨
        // 또한 기본값을 설정 할 수 있음 
        // ex) a:newA = 10 -> a 속성값을 newA에 할당하되, undefined로 값이 없을 경우 기본값 10을 할당
        var {a : newA = 10, f : newF = 5} = obj;

        console.log(`newA >>> ${newA}`);
        console.log(`newF >>> ${newF}`);
        ```

        - 배열 비구조화 할당은 중괄호 { }를 대괄호 [ ]로 바꾸면 가능