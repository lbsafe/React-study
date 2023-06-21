# useRef 공부

## 1. 완성 소스 - useRef의 렌더링 시 값의 유지

```js
import React, { useEffect, useRef, useState } from 'react'

const App = () => {
  const [count, setCount] = useState(1);
  const renderCount = useRef(1);

  useEffect(()=>{
    renderCount.current = renderCount.current + 1;
    console.log('렌더링 수 : ', renderCount.current);
  });

  return (
    <div>
      <p>count {count}</p>
      <button onClick={() => setCount(count + 1)}>값올리기</button>
    </div>
  )
}

export default App
```
***

**:star:1. 최종결과:star:**   
> **useRef**는 변화는 감지 되어야 하지만 변경 시 렌더링을 발생시키지 말아야 하는 값을 관리할 때 편리하다.

<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/179e5309-9501-41e8-8a70-3d72c41dd9d6" alt="study" width="1000px"></p>


***

## 2. 완성 소스 - useRef를 사용하여 DOM 요소에 접근하기

```js
import React, { useEffect, useRef} from 'react'

const App = () => {
  const inputRef = useRef();

  useEffect(() =>{
    // console.log(inputRef);
    inputRef.current.focus();
  }, []);

  const login = ()=>{
    alert(`환영합니다 ${inputRef.current.value}!`);
    inputRef.current.focus();
  }

  return (
    <div>
      <input ref={inputRef} type='text' placeholder='username'/>
      <button onClick={login}>로그인</button>
    </div>
  )
}

export default App
```
***

**:star:2. 최종결과:star:**   
> useRef를 이용하여 첫 로드시 input 태그에 focus를 주고,   
 ref 속성으로 DOM요소에 접근하는 방법을 알 수 있다.

**Before**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/8b6a3c33-0ea8-4868-a51b-ef0d4a80fe5f" alt="study" width="1000px"></p>

**After**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/76e48d7f-9931-4248-9678-46f544549eab" alt="study" width="1000px"></p>

***