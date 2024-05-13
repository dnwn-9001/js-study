# Q. 문자열을 숫자로 변환할 때 Number와 parseInt 중 어떤걸 사용하는게 좋을까?

## Quiz_1

- 다음의 문자열들을 콘솔로 찍으면 어떤 값이 나올까?

```javascript
console.log(Number(10.12345)); // 10.12345
console.log(Number('2024년')); // NaN
console.log(Number('올해는2024년입니다')); // NaN

console.log(parseInt(10.12345)); // 10 (소수점까지 뽑으려면 parseFloat)
console.log(parseInt('2024년')); // 2024
console.log(parseInt('올해는 2024년입니다')); // NaN
console.log(parseInt('2024년 4월 4일')); // 2024
```

- Number

  - 숫자로 이루어진 것만 숫자로 리턴

  - 소수점 인식

- parseInt

  - 숫자+문자일 경우 숫자만 인식하여 숫자로 리턴

  - 문자+숫자인 경우는 불가능

  - 즉, 숫자가 아닌 문자를 만날 때까지 문자를 읽은 후 그 값을 반환

  - 소수점 반환하지 않음

<br />

## Quiz_2

- 그렇다면 아래의 문자열은 콘솔로 어떻게 나올까?

```javascript
console.log(Number('7e2')); // 700 (e는 10의 지수를 나타내므로 7*10^2)
console.log(parseInt('7e2')); // 7

console.log(Number(false)); // 0
console.log(Number('')); // 0
console.log(Number(null)); // 0
console.log(parseInt(false)); // NaN
console.log(parseInt('')); // NaN
console.log(parseInt(null)); // NaN
```

👉 Number함수가 더 유연하면서도 엄격함!

<br />

## 정리 및 결론

- 정수만 사용해야 할 경우 parseInt 권장 (들어오는 변수의 값이 정수가 아닐 가능성을 막기 위해)

### Number

- 숫자가 소수나 지수인 경우 (ex. 3.14, 7e2)

- 비어있는 값(null, false, '')은 0으로 해석하고 true를 1로 해석

### parseInt

- 정수만 사용해야 하는 경우 (들어오는 변수의 값이 정수가 아닐 가능성 방지)

- 특정 진수를 사용해야 하는 경우

```javascript
// parseInt로 16진수를 10진수로 변환하기
const hexNumber = '1A'; // 16진수 "1A"
// parseInt 함수에 두 번째 매개변수로 진법을 지정하여 16진수로 해석
const decimalNumber = parseInt(hexNumber, 16);
console.log(decimalNumber); // 26
```
