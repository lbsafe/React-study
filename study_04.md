# state 공부

## 1. 완성 소스 - 내용 변경하기

**:pushpin:목표**
> state를 사용하여 Article을 생성해주자!    
-> mode의 값이 바뀌면 function APP() 컴포넌트 함수가 새로 실행되면서 새로운 리턴값이 만들어지고, 그 리턴값을 UI에 반영한다.

**:pushpin:방법**

**:one:** {useState} HooK 을 import 해준다.
```js
import {useState} from 'react';
```

**:two:** 조건문을 작성해 준다.
```js
function App() {
  let content = null; // 변수 생성
  if(mode === 'WELCOME'){
    // mode 가 'WELCOME'일 때
    content = <Article title="Welcome! React!" body="Hello, 건희"></Article>
  }else if(mode === 'READ'){
    // mode 가 'READ'일 때
    let title, body = null; //
    for(let i=0; i<topics.length; i++){
      if(topics[i].id === id){
        title = topics[i].title;
        body = topics[i].body;
      }
    }
    content = <Article title={title} body={body}></Article>
  }
}
```

**:three:** state(상태)를 만들어 준다.
```js
const [mode, setMode] = useState('WELCOME');
const [id, setId] = useState(null); //초기 값이 없다.

/* state 설명 */
mode = 초기 값
setMode = 변할 값
useState('WELCOME'); = 초기 값 설정
```

**:four:** 이벤트에 값을 바꿀 값을 넣어준다.

```js
  return (
    <div className="App">
      <Header title="WEB" onChangeMode={()=>{
        setMode('WELCOME'); // 바뀔 값
      }}></Header>
      <Nav topics={topics} onChangeMode={(_id)=>{
        setMode('READ'); // 바뀔 값
        setId(_id); // 바뀔 값
      }}></Nav>
      {content}
    </div>
  );
```

**:five:** state를 통해 topics에 담긴 값을 넣어 줄 수 있다.
```js
function Nav(props){
  const lis = []
  for(let i=0; i<props.topics.length; i++){
    let t = props.topics[i];
    lis.push(<li key={t.id}>
      <a id={t.id} href={'/read/'+t.id} onClick={event=>{
        event.preventDefault();
        props.onChangeMode(Number(event.target.id));
        // Number을 이용해 문자열을 숫자열로 변환
      }}>{t.title}</a>
    </li>)
  }
  return <nav>
    <ol>
        {lis}
    </ol>
  </nav>
}
```

**:pushpin:완성 소스**
```js
import logo from './logo.svg';
import './App.css';
import {useState} from 'react';

function Header(props){
  return <header>
    <h1><a href="/" onClick={(event)=>{
      event.preventDefault();
      props.onChangeMode();
    }}>{props.title}</a></h1>
  </header>
}
function Nav(props){
  const lis = []
  for(let i=0; i<props.topics.length; i++){
    let t = props.topics[i];
    lis.push(<li key={t.id}>
      <a id={t.id} href={'/read/'+t.id} onClick={event=>{
        event.preventDefault();
        props.onChangeMode(Number(event.target.id));
      }}>{t.title}</a>
    </li>)
  }
  return <nav>
    <ol>
        {lis}
    </ol>
  </nav>
}
function Article(props){
  return <article>
    <h2>{props.title}</h2>
    {props.body}
  </article>
}
function App() {
  const [mode, setMode] = useState('WELCOME');
  const [id, setId] = useState(null);
  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ]
  let content = null;
  if(mode === 'WELCOME'){
    content = <Article title="Welcome! React!" body="Hello, 건희"></Article>
  }else if(mode === 'READ'){
    let title, body = null;
    for(let i=0; i<topics.length; i++){
      if(topics[i].id === id){
        title = topics[i].title;
        body = topics[i].body;
      }
    }
    content = <Article title={title} body={body}></Article>
  }
  return (
    <div className="App">
      <Header title="WEB" onChangeMode={()=>{
        setMode('WELCOME');
      }}></Header>
      <Nav topics={topics} onChangeMode={(_id)=>{
        setMode('READ');
        setId(_id);
      }}></Nav>
      {content}
    </div>
  );
}

export default App;
```
***
**:star:최종결과:star:**
> **state**를 통해 header와 nav의 각 항목을 클릭했을 때,   
 props.onChangeMode(); 이벤트를 통해 **Article의 prop 인 title과 body의 내용 값을 변경** 시킬 수 있다.
<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/4b6d8317-5d59-43fa-ab7b-3404edb6001d" alt="study" width="1000px"></p>

***