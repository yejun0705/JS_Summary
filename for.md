# JavaScript Summary
2021.01.27

---------------------------------------
## for in

- for-in  반복문은 in 키워드를 사용.
- in 키워드의 오른쪾에는 반복할 대상 변수, 왼쪽에는 속성 명을 작성

```jsx
for(속성명 in 반복할 대상) {
	// contents

}
```

- 내부 요소를 하나씩 순회할 때 마다, 각 요소의 Key 정보가 for in에서 정의 한 속성명으로 선언&할당 됨

<details open>
<summary>Code</summary>
<div markdown="1">

### Code
// store 변수에 객체 값을 할당
var store = {snake: 1000, flower: 5000, beverage: 2000};

// store 객체를 순회하는 for-in 반복문
for(var item in store) {
	// hasOwnProperty를 이용하여 store객체에 item 키 정보가 있는지 확인
	if(!store.hasOwnProperty(item)) continue;
	
	// 정상적으로 접근한 요소에 대해 출력(속성명을 통해 속성값을 가져올 수 있음)
	console.log(item + '는 가격이' + store[item] + '입니다.');
}
