# setInterval 사용

## ✊✋✌️ 아이콘이 빠르게 바뀌는 애니메이션 연출에 사용

### setInterval()

- 일정 시간마다 반복 실행되는 함수
- setInterval(() => { ... }, 100); → 0.1초마다 계속 실행
- setInterval()은 ID를 반환함
- 이는 브라우저가 각각의 setInterval을 관리하기 위해 부여한 번호

```
const intervalId = setInterval(...);
```

### clearInterval(id)

- 위에서 만든 interval을 정지시켜주는 함수
- 정지하지 않으면 → 무한히 계속 돌아감 → 앱이 느려짐 or 중복실행
- 나같은 경우는 원하는 속도에서 점점 빨라지는 걸 경험함

<br>

> setTimeout() 같은 경우는 특정 시간 후에 한 번만 실행되는 함수로 반복 실행이 아님

<br>

### ❗ 내가 겪은 문제들

1. setInterval() 사용 후 속도가 점점 빨라짐

- 게임을 몇 번 진행하면 아이콘 애니메이션의 속도가 점점 빨라짐
- 원인 : setInterval()을 계속 호출하면서 clearInterval()을 해주지 않아서 interval이 누적됨

2. etInterval()의 ID를 어디서 관리해야 할지 몰랐음

- clearInterval()를 실행하기 위해서는 setInterval의 id가 필요한데 리랜더링이 될 때마다 id가 새로 생기는 문제가 있는 것 같았음

### ✅ 해결 방법

1. useRef로 id를 저장

```

const intervalRef = useRef(null);

const start = () => {
  intervalRef.current = setInterval(...);
};

const stop = () => {
  clearInterval(intervalRef.current); // ✅ 항상 정확한 값 유지됨
};


```

- intervalRef.current는 컴포넌트가 리렌더링돼도 값이 유지됨
- 하지만 UI와는 전혀 상관없으니 리렌더링은 발생하지 않음

- 메모리 상의 “고정 저장소”처럼 동작함
