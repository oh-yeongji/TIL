리액트에서 게으른 초기화(Lazy Initialization)란?

useState를 사용할때 초기상태를 설정하는 함수가 렌더링 할때마다 불필요하게 실행되지않도록하는 성능 최적화기법.

리액트 컴포넌트는 state가 변할때마다 함수 전체가 다시 실행(=리렌더링) 된다 .
함수나 return 을 쓰면 리액트는 이 함수가 컴포넌트가 처음 생성될때(=Mount) 딱 한번만 실행되도록 보장한다. 그 이후 리랜더링일때는 이 함수를 무시함.

<b>예시</b>

# 적용 안했을때 </br>

const [skip, setSkip] =
</br>useState(localStorage.getItem("skipGuide") === "true");

### 초기값으로 비용이 큰 값이 랜더링 할때마다 실행된다.

</br>
</br>

# 적용 했을때

## return문 사용 </br>

const [skip, setSkip] = useState(() => {</br>
return localStorage.getItem("skipGuide") === "true";
});

## 화살표 함수로 쓰면 </br>

const [skip, setSkip] = useState(() => localStorage.getItem("skipGuide") === "true");

return문 보다 더 짧게 사용가능.
