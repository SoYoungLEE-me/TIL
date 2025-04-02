```
const [score, setScore] = useState({
  win: 0,
  lose: 0,
  tie: 0,
});


setScore((prev) => {
  return {
    ...prev,
    [userResult]: prev[userResul] + 1,
  };
});
```

- userResult가 "WIN", "LOSE", "TIE" 중 하나일 때, 그에 해당하는 항목의 카운트를 +1 한다.

* setScore((prev) => { ... }) : 이전 스코어 상태를 기반으로 새 상태를 만든다
* prev : 이전 상태 객체
* prev[...] + 1 : 해당 항목의 값에 +1
* { ...prev, ... } : 기존 값은 유지하면서 선택된 것만 업데이트 (객체 복사 패턴)

<br>

### 만약 useResult가 win이면?

```
setScore((prev) => {
  return {
    ...prev,
    ["win"]: prev["win"] + 1,
  };
});
```

- win 객체 +1
