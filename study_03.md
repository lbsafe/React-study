# 컴포넌트에 이벤트 부여하기

## 완성 소스

```js
import logo from './logo.svg';
import './App.css';
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
        props.onChangeMode(event.target.id);
        // event.target.id 통해 각 이벤트 객체의 id값 호출
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
  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ]
  return (
    <div className="App">
      <Header title="WEB" onChangeMode={()=>{
        alert('Header')
      }}></Header>
      <Nav topics={topics} onChangeMode={(id)=>{
        alert(id);
      }}></Nav>
      <Article title="Welcome! React!" body="Hello, 건희"></Article>
    </div>
  );
}

export default App;
```
***

**:star:최종결과:star:**
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/235866393-b44a4ae0-c66a-4280-a126-a6143fdff1d4.PNG" alt="study" width="1000px"></p>

> nav의 각 a 태그 id를 호출하는 것도 응용해서 가능하다.
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/235866908-2ed9fbdc-6ac6-43e1-8727-6a58755c2cf8.PNG" alt="study" width="1000px"></p>

***