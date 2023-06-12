# useState 공부

## 1. 완성 소스 - 간단한 시계

```js
import React, { useState } from 'react'

const App = () => {
  const [time, setTime] = useState(1);

  const handleClick = () =>{
    let newTime;
    if (time >= 24){
      newTime = 1;
    }else{
      newTime = time + 1;
    }
    setTime(newTime);
  }
  return (
    <div>
      <span>현재 시각: {time}시</span>
      <button onClick={handleClick}>Update</button>
    </div>
  )
}

export default App
```
***

**:star:1. 최종결과:star:**   
> useState 개념을 통해 시간의 상태를 바꾸는 예시를 만들어 볼 수 있다.

**Before**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/28769f6a-a0fc-44e5-b998-82d87ac6365b" alt="study" width="1000px"></p>

**After**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/d3c0c5f3-7c4a-4a4a-a726-cf5fcace6ca8" alt="study" width="1000px"></p>

***

## 2. 완성 소스 - 업로드 및 콜백함수 응용

```js
import React, { useState } from 'react'

const heavyWork = () => {
  console.log('무거운 작업');
  return ['홍길동', '김민수'];
}

const App = () => {
  const [names, setNames] = useState(() =>{
    return heavyWork();
  });
  const [input, setInput] = useState("");

  const handleInputChange = (e) => {
    setInput(e.target.value);
  }

  const handleUpload = () =>{
    setNames((prevState) =>{
      console.log('이전 state: ', prevState)
      return([input, ...prevState])
    });
  }

  return (
    <div>
      <input type='text' value={input} onChange={handleInputChange}/>
      <button onClick={handleUpload}>Upload</button>
      {names.map((name, idx) => {
        return <p key={idx}>{name}</p>;
      })}
    </div>
  )
}

export default App
```
***

**:star:2. 최종결과:star:**   
> useState 개념을 통해 개발의 업데이트 원리를 살펴볼 수 있었다.

**:one:** useState 훅은 state, setState 를 배열 형태로 리턴해준다.
```js
  const [state, setState] = useState(초기값);
```
**:two:** state를 변경할 때 새로 변경할 state 값이 이전 state와 연관 되어 있다면(비교, 추가 등등), setState의 인자로 새로운 state를 리턴하는 콜백함수를 넣어준다.
```js
  setState((prevState) =>{
    //some work
    return newState;
  });
```
**:three:** useState를 사용해서 초기값을 받아올 때, 무거운 작업을 해야한다면 useState의 인자로 콜백함수를 넣어주면 처음 랜더링이 될 때만 실행할 수 있다.
```js
  useState(() =>{
    return heavyWorks();
  });
```

**Before**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/2c90285b-ae3d-4799-9078-a256d3bd40cb" alt="study" width="1000px"></p>

**After**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/19813306-3957-4a43-853f-0975e745f35c" alt="study" width="1000px"></p>

***