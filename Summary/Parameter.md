# JavaScript Summary
2021.01.30

---------------------------------------
## 기본 매개변수(Default Parameter)

- 매개변수를 정의할 때 기본으로 할당될 인자값과 함께 작성하는 매개변수
- code

    ```jsx
    // 매개변수로 w, h를 정의, 이때 전달 인자가 없을 때 디폴트값으로 200과 400을 함께 작성
    function draw_chart(w = 200, h = 400) {
        console.log(`${w} X ${h} 차트를 그립니다.`);

    }

    draw_chart(100);
    draw_chart(1000,1000);
    draw_chart();

    // w, h를 기본 매개변수로 정의, h의 기본값으로 앞의 매개변수인 w 참조
    function draw_chart2(w = 200, h = w / 2) {
        console.log(`${w} X ${h} 차트를 그립니다.`);
    }

    draw_chart2(300);
    draw_chart2(3000, 3000);
    draw_chart2();
    ```

## 나머지 매개변수(Rest Parameter)

- 매개변수를 정의할 때 정해지지 않은 매개변수들을 정의할 수 있게 해줌
- arguments 객체와 유사

    → arguments 객체는 함수에 전달되는 모든 전달 인자를 포함        But, 나머지 매개변수는 정해지지 않은 나머지를 의미

    → 가장 큰 차이점, arguments 객체 != 배열 But, Rest Parameter == 배열 

- 매개변수를 작성하는 곳에서 작성
- 다른 매개변수와 차이점을 두기 위해 '...' 연산자와 함께 작성

```jsx
function(parameter, ...rest_prameter) {
	// arguments 객체는 함수 실행부에서만 사용
}
```

- code

    ```jsx
    // sum 함수를 나머지 매개변수로 정의
    // 나머지 매개변수는(args)는 Array임 -> [인덱스]를 통해 접근 가능 -> indexOf와 같은 메소드 사용 가능
    function sum(...args) {
        var total = 0;

        for(var i = 0; i < args.length; i++) {
            total += args[i];

        }
        console.log(args.indexOf(1));
        return tatal;
    }

    // 1, 2, 3 전달 인자들은 args 배열이 됨
    console.log(sum(1, 2, 3));

    // sum2 함수는 a와 b 매개변수를 가지고 있음 그리고 두 매개변수 외에 others라는 나머지 매개변수를 정의하고 있음
    function sum2(a, b, ...others) {
        var total = a + b;

        for(var i = 0; i < others.length; i++) {
            tatal += others[i];

        }
        return total;
    }
    // 1, 2를 a와 b로 전달, 이때 others는 빈 배열이 됨
    console.log(sum2(1, 2));
    // a와 b의 두 매개변수보다 더 많은 인자가 전달되기 때문에 1과 2과 각각 a와 b에 전달
    // 나머지 인자 3, 4는 others 나머지 매개변수의 배열 요소로 전달됨
    console.log(sum2(1, 2, 3, 4));
    ```