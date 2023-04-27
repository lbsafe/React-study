# props 사용법 공부

## 완성 소스

```js
import logo from './logo.svg';
import './App.css';
function Header(props){
  console.log('props', props, props.title)
  return <header>
    <h1><a href="/">{props.title}</a></h1>
  </header>
}
function Nav(props){
  const lis = []
  for(let i=0; i<props.topics.length; i++){
    let t = props.topics[i];
    lis.push(<li key={t.id}><a href={'/read/'+t.id}>{t.title}</a></li>)
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
      <Header title="WEB"></Header>
      <Nav topics={topics}></Nav>
      <Article title="Welcome! React!" body="Hello, 건희"></Article>
    </div>
  );
}

export default App;
```
***

**:star:최종결과:star:**
> props를 사용해서 제작했을 때, 기존과 동일하게 화면이 출력된다.
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/234729262-52306ba7-d8e0-4eff-b499-5eb0a5c0f791.PNG" alt="study" width="1000px"></p>

***