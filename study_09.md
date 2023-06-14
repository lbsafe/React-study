# useEffect 공부

## 1. 완성 소스 - useEffect와 렌더링 개념

```js
import React, { useState, useEffect } from 'react'

const App = () => {
  const [count, setCount] = useState(1);
  const [name, setName] = useState('');

  const handleCountUpdate = () => {
    setCount(count + 1);
  }

  const handleInputChange = (e) => {
    setName(e.target.value);
  }

  // 렌더링마다 매번 실행 됌
  useEffect(() => {
    console.log('렌더링');
  });

  // 마운트 + count가 변경될때만 실행
  useEffect(() => {
    console.log('count 변화');
  }, [count]);

  // 마운트 + name이 변경될 때만 실행
  useEffect(() => {
    console.log('name 변화');
  }, [name]);

  // 첫 렌더링만 실행
  useEffect(() => {
    console.log('마운팅');
  }, []);

  return (
    <div>
      <div className='box1'>
        <button onClick={handleCountUpdate}>Update</button>
        <span>count: {count}</span>
      </div>
      <div className='box2'>
        <input type="text" value={name} onChange={handleInputChange}/>
        <span>name: {name}</span>
      </div>
    </div>
  )
}

export default App
```
***

**:star:1. 최종결과:star:**   
> useEffect를 통해 마운트 되었을 때, 업데이트 될 때, 혹은 마운트해제 됐을 때의 렌더링 이벤트를 줄 수 있고,   
 배열에 조건을 추가하여 렌더링 시 해당하는 useEffect의 실행 여부를 조절 할 수 있다.

**Before**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/4914920e-0302-4d09-9f27-4237093b8479" alt="study" width="1000px"></p>

**After <Case - count Update>**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/9c9091b6-50cc-411b-be21-0fa9f6bd1a71" alt="study" width="1000px"></p>

**After <Case - name text>**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/956e4823-a584-46b2-b607-cb576965ee02" alt="study" width="1000px"></p>

***

## 2. 완성 소스 - useEffect와 Clean Up 기능

```js
import React, { useState, useEffect } from 'react';
import Timer from './component/Timer';

const App = () => {
  const [showTimer, setShowTimer] = useState(false);
  return (
    <div>
      {showTimer && <Timer></Timer>}
      <button onClick={() => setShowTimer(!showTimer)}>Toggle Timer</button>
    </div>
  )
}

export default App
```
```js
import React, { useEffect } from 'react'

const Timer = (props) => {

    useEffect(() =>{
        const timer = setInterval(() =>{
            console.log('타이머 돌아가는 중...')
        }, 1000);
        
        return () => {
            clearInterval(timer);
            console.log('타이머가 종료 되었습니다!')
        }
    }, []);

  return (
    <div>
        <span>타이머를 시작합니다. 콘솔을 보세요!</span>
    </div>
  )
}

export default Timer
```
***

**:star:2. 최종결과:star:**   
> Clean Up 기능을 통해 리턴 함수를 실행시켜 useEffect를 컨트롤 할 수 있다.

**Before**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/4c637aa0-798e-4e5f-a6bc-d36a82999032" alt="study" width="1000px"></p>

**After <Case - useEffect start>**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/cf0ca0a2-1ba6-4fae-8297-12eca928ec7e" alt="study" width="1000px"></p>

**After <Case - useEffect Clean Up>**
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/c01f490f-c2d9-482d-a54b-d700edb4b487" alt="study" width="1000px"></p>
***