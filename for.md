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
- code