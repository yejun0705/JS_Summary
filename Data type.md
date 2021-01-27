# JavaScript Summary
2021.01.27

---------------------------------------
## Data Type
- **자바스크립트 타입의 종류**.

1. 원시 타입(Primitive Data Type)
    - 값이 변수에 할당될 때 메모리 상에 고정된 크기로 저장됨 → 해당 변수가 직접 값을 보관
    - **숫자형 :** 숫자를 표현하는 자료형, 숫자형끼리 연산이 가능
    - **문자형 *:*** 작은따옴표 (' ') or 큰따옴표 (" ")를 양끝에 두고, 그 안에 한 글자 이상의 문자/기호/숫자가 있는 자료형
    - **Boolean :** 참(true) or 거짓(false) 두 가지 값을 가짐.
    - **Symbol :** 유일하게 변경이 불가능한 자료형. 참조형의 키(Key)로 사용 가능
    - **Null, Undefined :** Null은 빈 값을 의미, Undefined는 존재하지 않는 값을 의미

2. 참조 타입(Reference Date Type)

    - 변수에 고정된 크기를 저장하지 않고, 값의 메모리 주소를 참조함
    - 객체 : 속성(Properties)들의 집합. 집합 내부의 순서, 크기도 고정되어 있지 않음

    → { } 안에 키 : 값 형태로 이루어진 속성들의 모음.

    → 키는 반드시 문자형 자료형이여야 함.

    → 이 속성 키를 통해 해당 속성에 매핑된 값에 접근할 수 있다.

- 고정되어 있지 않은 값을 변수에 할당하려면 직접 해당 값을 저장할 수 없으니 참조해야함
- 자바스크립트에는 여러 형태의 객체가 존재함.


<details open>
<summary>Global Object 객체</summary>
<div markdown="1">

### Global Object 객체 
- 모든 객체에 부모가 되는 객체
- 이를 부모삼아 함수, 배열, 원시 자료형을 객체로 감싼 새로운 형태의 객체(String, Number, Boolean)와 특수 연산에 특화된 내장 객체(Math, JSON, RegEx) 그리고 Iterable, Collection 특성의 객체(Map, Set, WeakMap, WeakSet) 등의 표준 내장 객체가 존재

</div>
</details>
