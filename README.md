# React

<p align="center"><img src="https://user-images.githubusercontent.com/65703793/230308709-b1b3a903-506a-445b-962c-2a8865b7b7fe.png" alt="js" width="250px"></p>

## React 에 대하여

>메타에서 개발한 오픈 소스 자바스크립트 라이브러리이다. SPA을 전제로 하고 있으며, Dirty checking과 Virtual DOM을 활용하여 업데이트 해야하는 DOM 요소를 찾아서 해당 부분만 업데이트하기 때문에, 리렌더링이 잦은 동적인 모던 웹에서 엄청나게 빠른 퍼포먼스가 가능하다. 프레임워크가 아니라 라이브러리이기에 다른 프레임워크에 붙여서 사용하는 것도 가능하며, React Hooks라는 강력한 메소드들을 지원하면서 사실상 웹 프론트엔드 개발의 표준으로 자리잡았다. 또한 Next.js 등의 등장으로 인해 SSG, SSR등을 할 수 있게 되었다.
***

## React 개발환경 Setting

**:one:** : :link:[React][reactlink] 공식 사이트 > 새로운 React 앱 만들기 > :link:[create-react-app][create-react-applink] 접속
    
```html
npx create-react-app my-app
```

[reactlink]: https://ko.reactjs.org/docs/getting-started.html "Go react"

[create-react-applink]: https://create-react-app.dev/ "Go create-react-app"

**:two:** : :link:[nodejs][nodejslink] 접속 > LTS 버전 설치

[nodejslink]: https://nodejs.org/ko "Go nodejs"

**:three:** : 프로젝트 > 터미널 아래문구 입력
```html
현재 디렉토리에 설치
npx create-react-app my-app .
```
**:four:** : npm start 입력
```html
npm start
```
***

## 컴포넌트(사용자 정의태그)

>**:heavy_exclamation_mark: React는 컴포넌트(사용자 정의 태그)를 만드는 기술이다.**

1. 컴포넌트를 만들때는 반드시 **대문자**로 시작한다.
    
    ```js
    funtion Test();
    funtion Header();
    funtion Setion();
    ```

2. 컴포넌트 함수를 정의하고 해당 HTML 코드를 return한다.

    ```js
    function Header(){
        return <header>
            <h1><a href="javascript:;">React</a></h1>
        </header>
    }
    ```

3. 컴포넌트를 사용하고자 하는 부분에 사용한다.

    ```js
    function App(){
        return (
            <div className="App">
                <Header></Header>
            </div>
        );
    }
    ```

>컴포넌트를 통해 소스를 줄이고, 한번의 수정으로 해당 컴포넌트를 사용 하는 모든 부분을 수정할 수 있다.
***

## props(속성)

>html 태그의 속성과 같이 컴포넌트에도 속성을 사용한다.

**html의 속성예시**

```html
<img src="images.jpg" width="100px" height="100px">
        속성              속성         속성
```
**props 사용방법**

1. 컴포넌트에 title을 준다.

    ```js
    <Header title="WEB"></Header>
    ``` 

2. 컴포넌트 함수에 첫번째 파라미터로 props 이름을 붙인다.

    ```js
    function Header(props){
        return <header>
            <h1><a href="/">WEB</a></h1>
        </header>
    }
    ``` 

3. {props.title}을 적용한다.   
중괄호의 정보는 일반적인 문자열이 아니라 표현식으로 인식된다.

    ```js
    function Header(props){
        return <header>
            <h1><a href="/">{props.title}</a></h1>
        </header>
    }
    ``` 
    위 방식을 통해 화면에 출력된 값은 기존과 동일하게 'WEB'이 출력된다.
    
4. 예시

    ```js
    function Header(props){
        return <header>
            <h1><a href="/">{props.title}</a></h1>
        </header>
    }
    function Article(props){
        return <article>
            <h2>{props.title}</h2>
            {props.body}
        </article>
    }
    function App() {
        return (
            <div className="App">
                <Header title="WEB"></Header>
                <Article title="Welcome! React!" body="Hello, 건희"></Article>
            </div>
        );
    }
    ```
**props(속성)을 응용한 태그생성**   

1. 변수선언.    
    1-1. 예시 기준 topics 변수 선언  
    1-2. 여러개의 정보를 담아야 하니 배열[] 생성  
    1-3. 각각의 정보를 담을 객채{} 생성   
    1-4. 고유의 아이디 값과 속성 값 설정

    ```js
    function App() {
        const topics = [
            {id:1, title:'html', body:'html is ...'},
            {id:2, title:'css', body:'css is ...'},
            {id:3, title:'javascript', body:'javascript is ...'}
        ]
        return (
            <div className="App">
            <Header title="WEB"></Header>
            <Nav></Nav>
            <Article title="Welcome! React!" body="Hello, 건희"></Article>
            </div>
        );
    }
    ```
2. 선언한 변수를 내부의 props으로 전달

    ```js
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
    ```

3. 첫번째 파라미터(props)에 선언 된 변수(topics) 를 받아 정보를 넣어준다.  
    **:warning:주의사항**   
    3-1. 동적으로 만들어주는 태그는 각자 key라는 props 필요하다.   
    3-2. key 값은 고유한 값이 필요하기에 중복되지 않게 한다.   
    3-3. key 값은 전체가 아닌 해당 반복문 안에서만 고유한 값이면 된다.   
    3-4. react는 자동으로 생성 된 태그의 key 라는 약속 된 props 부여를 통해 react가 성능을 높히고 정확한 동작을 할 수 있게 해준다.

    ```js
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
    ```
:link:[React-props][Reactpropslink] : 완성소스 및 결과창 정리 보기

[Reactpropslink]: https://github.com/lbsafe/React-study/blob/main/study_02.md "React props"
***

## 컴포넌트에 이벤트 부여하기

1. 컴포넌트에 함수를 전달한다.   
onChangeMode 라는 props의 값으로 함수를 전달한다.

    ```js
    <div className="App">
      <Header title="WEB" onChangeMode={()=>{
        alert('Header')
      }}></Header>
    </div>

    기존 funtion을 arrow funtion으로 축약해서 사용한다.
    <Before>
    onChangeMode={function(){alert('Header')}}
    <After>
    onChangeMode={()=>{alert('Header')}}
    ```

2. 이벤트 대상에 이벤트를 걸어주고, 함수를 호출해준다.

    ```js
    function Header(props){
        return <header>
            <h1><a href="/" onClick={(event)=>{
            event.preventDefault();  // a태그의 기본 이벤트 방지
            props.onChangeMode();  // props의 이벤트 호출
            }}>{props.title}</a></h1>
        </header>
    }
    ```

:link:[React-event][React-event] : 완성소스 및 결과창 정리 보기

[React-event]: https://github.com/lbsafe/React-study/blob/main/study_03.md "React event"
***

## state 개념 정리

>state를 사용하기 위해서는 {useState} HooK을 사용한다.

1. useState를 import 해준다.

    ```js
    import {useState} from 'react';
    ```

2. state(상태)를 만들어 준다.

    2-1. 지역변수를 state(상태)로 쓴다.
    ```js
    Before
    const mode = 'WELCOME';

    After
    const [mode, setMode] = useState('WELCOME');
    
    mode = 초기 값
    setMode = 변할 값
    useState('WELCOME'); = 초기 값 설정
    ```

    2-2. 바꿀 값을 설정한다.

    ```js
    <Header title="WEB" onChangeMode={()=>{
      setMode('WELCOME');
    }}></Header>
    <Nav topics={topics} onChangeMode={(id)=>{
      setMode('READ');
    }}></Nav>
    ```

**prop과 state의 공통점**
>**prop**과 **state**는 일반 자바스크립트 객체이며, 값을 변경 시 새로운 return 값을 만들어 ui를 바꾸어 준다.

**차이점**
>* **prop** 은 컴포넌트를 사용하는 외부자를 위한 데이터   
:arrow_right: prop은 컴포넌트에 전달한다. *ex)* 함수 매개 변수
>* **state** 는 컴포넌트를 만드는 내부자를 위한 데이터   
:arrow_right: state는 컴포넌트 안에서 관리한다. *ex)* 함수 내 선언 된 변수

**주의사항**
> * state는 상태를 바꾸기 위해 사용한다. *ex)* 클래스명, 내용, id값 등
>* state 사용 시 의도치 않은 리랜더링으로 성능상 문제가 발생 될 수 있기에 적절하게 사용한다.

:link:[React-state][React-state] : 예시 및 결과창 정리 보기

[React-state]: https://github.com/lbsafe/React-study/blob/main/study_04.md "React state"
***