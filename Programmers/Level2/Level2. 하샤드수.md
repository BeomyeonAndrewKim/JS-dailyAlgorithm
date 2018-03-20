[Daily Algorithm_JavaScript] Level2. 하샤드수

### Question

#### Source https://programmers.co.kr/learn/challenge_codes/129

> 양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다.
>
> Harshad함수는 양의 정수 n을 매개변수로 입력받습니다. 이 n이 하샤드수인지 아닌지 판단하는 함수를 완성하세요.
> 예를들어 n이 10, 12, 18이면 True를 리턴 11, 13이면 False를 리턴하면 됩니다.

### My solution

```javascript
function Harshad(n){
 let str=n.toString();
 let total=0;
 for(let el of str) total+=parseInt(el);
 return n%total===0 ? true: false;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(Harshad(18))
```

이 문제에서 가장 고민했던 것은 매개변수로 받는 숫자 ```n```의 자릿수의 합을 만들어내는 부분이었습니다. 

배열로 만들어서 ```reduce```를 활용해 자리수의 합을 구할지, 문자열로 만들어서 순환을 통해 자리수의 합을 구할지 둘 중에 선택을 했습니다.

일단 후자로 정했다. 오늘 공부한 내용이 iterable에 대한 내용이었다. 문자열도 ```for...of```를 활용할 수 있는 ```iterable```이기 때문에 루프를 돌 수 있다는 사실을 활용했습니다.

삼항연산자를 통해 ```true```와 ```false```를 ```return``` 하는 것으로 마무리 했습니다.

#### Other Solutions

#### Best of Best

> 잘만 활용한다면 최소한으로도 충분하다 -쥘 베른,'80일간의 세계 일주' 중에서

```javascript
function Harshad(n){
  return !(n % (n + "").split("").reduce((a, b) => +b + +a ));
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(Harshad(148))
```

한 줄로 끝나는 깔끔한 풀이 입니다.

이번 문제에서는 Number값을 String으로 바꾸고 다시 String을 Number값으로 바꾸는 과정들이 있습니다.

풀이를 보면 ``` n+""```를 통해 Number값인 n을 간단하게 String으로 바꾸었고, ```+b```, ```+a```를 통해 String을 간단하게 Number값으로 바꿨습니다.

그리고 ```%``` 연산자를 쓸 때 나누어 떨어지면 0이기 때문에 ```false```가 나오고 나누어 떨어지지 않으면 0이 아닌 실수가 나오기 때문에 ```true```가 나옵니다. 이 점 활용해서 모든 식을 괄호로 감싸고 ```!``` 연산자를 통해 부정해서 올바른 값이 나오도록 했습니다.



