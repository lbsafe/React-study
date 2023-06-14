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

## useState 개념 정리

> state를 사용하기 위해서는 {useState} HooK을 사용한다.

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

**:warning:주의사항**
> * state는 상태를 바꾸기 위해 사용한다. *ex)* 클래스명, 내용, id값 등
>* state 사용 시 의도치 않은 리렌더링으로 성능상 문제가 발생 될 수 있기에 적절하게 사용한다.

:link:[React-state][React-state] : 예시 및 결과창 정리 보기

[React-state]: https://github.com/lbsafe/React-study/blob/main/study_04.md "React state"

***

## useState와 콜백함수 응용
> useState를 이용한 예제를 만들면서, 콜백함수를 응용해 코드의 성능을 높혀줄 수 있다.

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
**:three:** useState를 사용해서 초기값을 받아올 때, 무거운 작업을 해야한다면 useState의 인자로 콜백함수를 넣어줘서 처음 렌더링이 될 때만 실행할 수 있다.
```js
  useState(() =>{
    return heavyWorks();
  });
```

:link:[React-state2][React-state2] : 예시 및 결과창 정리 보기

[React-state2]: https://github.com/lbsafe/React-study/blob/main/study_08.md "React state2"

***

## useEffect 개념 정리

**:star: useEffect 언제 사용하는가?**

<p align="center"><img src="https://github.com/lbsafe/React-study/assets/65703793/d253c8c8-13e3-4ea5-a34e-141b13ac2f42" alt="study" width="1000px"></p>

>어떠한 컴포넌트가 마운트 되었을 때 업데이트 될 때 혹은 마운트해제 되었을 때   
특정 작업을 처리할 코드를 실행시켜 주고 싶다면 **useEffect**를 사용한다.

**:one: useEffect**   
> useEffect Hook은 인자로 콜백함수를 받는다.

**:pushpin: 콜백함수란?**   
:arrow_forward: 다른 함수의 인자로 전달 된 함수

**:two: useEffect의 케이스**

1. useEffect의 인자로 하나의 콜백함수만 받는 경우

    > 컴포넌트가 렌더링 될 때마다 매번 콜백이 실행   
    *ex)* 컴포넌트가 처음 화면에 렌더링 될 때, 다시 렌더링 될 때 실행

    ```js
    useEffect(() => { 

        작업... 

    });
    ```
2. useEffect의 첫번째 인자로 콜백함수, 두번째 인자로 배열을 받는 경우
    > 컴포넌트가 처음 화면에 렌더링 될 때, 배열 안의 요소의 값(value)이 바뀔 때만 실행   
    :warning: 빈 배열 [] 을 전달해주면 컴포넌트가 처음 렌더링 될 때만 실행

    ```js
    useEffect(() => {

        작업...

    },[value]);

    <빈 배열일 때 처음 화면에 렌더링 될 때만 실행>
    useEffect(() => {

        작업...

    }, []);
    ```

**:three: Clean Up - 정리**

> 함수를 리턴 해주면 해당 컴포넌트가 언마운트(화면에서 사라질 때) 될 때,   
혹은 다음 렌더링 시 불러올 useEffect가 실행되기 이전에 리턴한 함수가 실행 된다.

* *ex)* 구독 시 구독을 해지 해주는 작업
* *ex)* 타이머를 멈추는 작업
* *ex)* 등록한 이벤트를 제거 해주는 작업

```js
useEffect(() => {
    
    구독...

    return() => {

        구독 해지...
    }

}, []);
```
:link:[React-effect][React-effect] : 완성소스 및 결과창 정리 보기

[React-effect]: https://github.com/lbsafe/React-study/blob/main/study_09.md "React effect"
***

## Create(생성) 구현하기
>글 생성, 폼 구현 원리 등을 살펴볼 수 있다.

1. 기능을 구현할 버튼을 만들어준다.

    ```js
    <a href="/create" onClick={(event)=>{
      event.preventDefault(); /* a태그의 기본동작 방지 */
      setMode('CREATE'); /* 모드 값 변경 */
    }}>Create</a>
    ```

2. 모드가 CREATE 일 경우를 만들어 준다.

    ```js
    else if(mode === 'CREATE'){
        content = <Create onCreate={(_title, _body)=>{
            const newTopic = {id:nextId, title:_title, body:_body}
            const newTopics = [...topics]
            newTopics.push(newTopic);
            setTopics(newTopics);
            setMode('READ');
            setId(nextId);
            setNextId(nextId + 1);
        }}></Create>
    }
    ```

3. Create 컴포넌트를 만들어준다.

    ```js
    function Create(props){
        return <article>
            <h2>Create</h2>
            <form onSubmit={(event)=>{
                event.preventDefault(); /* form태그의 기본동작 방지 */
                const title = event.target.title.value; /* input에 name value 값을 가져옴 */
                const body = event.target.body.value; /* textarea에 body value 값을 가져옴 */
                props.onCreate(title, body);
            }}>
                <p><input type="text" name="title" placeholder="title"></input></p>
                <p><textarea name="body" placeholder='body'></textarea></p>
                <p><input type='submit' value='Create'></input></p>
            </form>
        </article>
    }
    ```

4. 기존 topics를 state로 만들어준다.
    
    ```js
    const [topics, setTopics] = useState([
        {id:1, title:'html', body:'html is ...'},
        {id:2, title:'css', body:'css is ...'},
        {id:3, title:'javascript', body:'javascript is ...'}
    ]);
    ```

**:heavy_exclamation_mark: 중요사항**

:one: state(상태)를 만들 때 PRIMITIVE(원시 데이터 타입) 일 경우
>기존 방식대로 진행한다.
```js
const [value, setValue] = useState(PRIMITIVE);

<PRIMITIVE 종류>
string, number, bigint, boolean, undefined, symbol, null
```

:two: state(상태)를 만들 때 Object(범 객체)일 경우
>데이터를 복제한다.
```js
const [value, setvalue] = useState(Object);

<Object 종류>
object(객체), array(배열)
```

**2-1 object(객체)일 경우**

step1.
> "{ }"(중괄호)에 ...을 찍고 value를 넣어주면 value 값을 복제한 새로운 데이터가 newValue의 값이 된다.
```js 
newValue = {...value}
```

step2.
> newValue 값을 변경한다.

step3.
> 변경된 newValue를 setValue에 넣어준다.
```js
setValue(newValue)
```

**2-2 array(배열)일 경우**

step1.
> "[ ]"(대괄호)에 ...을 찍고 value를 넣어주면 value 값을 복제한 새로운 데이터가 newValue의 값이 된다.
```js 
newValue = [...value]
```

step2.
> newValue 값을 변경한다.

step3.
> 변경된 newValue를 setValue에 넣어준다.
```js
setValue(newValue)
```

**:pushpin: 원리 설명**

예시1 case - 배열)
```js
const [value, setValue] = useState([1]);

value.push(2);
// 오리지널(value) 데이터를 바꾼 것이다.

setValue(value);
// 기존의 value와 setValue가 같은 데이터이기에 컴포넌트를 다시 렌더링 하지 않는다.
```

예시2 case - 원시 데이터)
```js
const [value, setValue] = useState(1);

setValue(value);
// 오리지널(value) 데이터는 1이고 setValue의 데이터는 2이기에 다시 렌더링 된다.
```

예시3 case - 객체 데이터 복제)
```js
const [value, setValue] = useState([1]);

newValue = [...value]
// 오리지널(value) 데이터를 복제한다. 현재 newValue는 1

newValue.push(2);
// 데이터 값을 변경한다. 현재 newValue는 2

setValue(newValue);
// 기존의 value와 setValue가 다른 데이터이기에 컴포넌트를 다시 렌더링 한다.
```

:link:[React-create][React-create] : 완성소스 및 결과창 정리 보기

[React-create]: https://github.com/lbsafe/React-study/blob/main/study_05.md "React Create"
***

## Update 구현하기
>글의 수정 및 등록 원리를 살펴볼 수 있다.

1. 상세보기 페이지에서만 업데이트 기능 버튼을 추가해준다.

    ```js
    let contextControl = null;
    // 지역변수 선언

    contextControl = <li><a href={"/update/"+id} onClick={event=>{
      event.preventDefault();
      setMode('UPDATE');
    }}>Update</a></li>
    // {"/update/"+id}를 통해 주소에 고유 id 값 추가

    <ul>
      <li><a href="/create" onClick={(event)=>{
        event.preventDefault();
        setMode('CREATE');
      }}>Create</a></li>
      {contextControl}
    </ul>
    // 추가 부분
    ```

2. 모드가 'READ' 즉 상세보기 페이지일때만 버튼을 추가해준다.

    ```js
    else if(mode === 'READ'){ //모드 'READ' 조건
        let title, body = null;

        for(let i=0; i<topics.length; i++){
            if(topics[i].id === id){
                title = topics[i].title;
                body = topics[i].body;
            }
        }
        content = <Article title={title} body={body}></Article>
        
        contextControl = <li><a href={"/update/"+id} onClick={event=>{
            event.preventDefault();
            setMode('UPDATE');
        }}>Update</a></li>
        // 버튼 이벤트에 setMode('UPDATE');를 추가하고 모드가 UPDATE일 경우를 추가한다.
    }
    ```

3. input에 기존 title의 value값과 body의 value값을 가져오고, 새로운 값으로 수정했을 때 변경 된 값을 넣어준다.

    ```js
    function Update(props){
    const [title, setTitle] = useState(props.title);
    const [body, setBody] = useState(props.body);
    // 타이틀 value와 body의 value를 state화 시켜준다.

    return <article>
        <h2>Update</h2>
        <form onSubmit={(event)=>{
            event.preventDefault();
            <!-- 폼 기본 이벤트 방지 -->
            const title = event.target.title.value;
            const body = event.target.body.value;
            props.onUpdate(title, body);
        }}>
            <p><input type="text" name="title" placeholder="title" value={title} onChange={event=>{
                setTitle(event.target.value);
            }}></input></p>
            <p><textarea name="body" placeholder='body' value={body} onChange={event=>{
                setBody(event.target.value);
            }
    <!-- props로 들어온 title 값을 state를 통해 value값으로 준다. state는 컴포넌트 안에서 바꿀 수 있기에 onChange를 통해 새로운 값을 넣어주면서 컴포넌트가 다시 렌더링 된다. -->
            }></textarea></p>
            <p><input type='submit' value='Update'></input></p>
        </form>
    </article>
    }
    ```

4. 업데이트 버튼을 클릭 시 이벤트를 추가해준다.

    ```js
    else if(mode === 'UPDATE'){
        // 모드가 업데이트 일 경우
        let title, body = null;

        for(let i=0; i<topics.length; i++){
            if(topics[i].id === id){
                title = topics[i].title;
                body = topics[i].body;
            }
        }
        // 수정 페이지의 input의 title value와 textarea의 body value 값을 가져온다.
        
        content = <Update title={title} body={body} onUpdate={(title, body)=>{
            <!-- Update 컴포넌트에 title과 body 값을 넣어준다. -->

            const newTopics = [...topics]
            <!-- 변경 해야할 topics가 데이터가 객체(배열)이기에 기존 토픽 값을 복사해준다. -->

            const updatedTopic = {id:id, title: title, body: body}
            for(let i=0; i<newTopics.length; i++){
                if(newTopics[i].id === id){
                    <!-- newTopics 아이디와 우리가 선택한 topics의 id가 같을 때 -->
                    newTopics[i] = updatedTopic;
                    <!-- 지금 선택한 topics를 updatedTopic으로 교체한다. -->
                    break;
                }
            }
            <!-- 기존 topics 값을 바꿔준다. -->
            setTopics(newTopics);
            <!-- 새로운 topics를 저장한다. -->
            setMode('READ');
            <!-- 변경 시 변경 된 상세보기 페이지로 이동 -->
        }}></Update>
    }
    ```

:link:[React-update][React-update] : 완성소스 및 결과창 정리 보기

[React-update]: https://github.com/lbsafe/React-study/blob/main/study_06.md "React Update"
***

## Delete 구현하기
>글의 삭제 원리를 살펴볼 수 있다.

1. 삭제 버튼을 추가 해준다.

    ```js
    contextControl = <>
      <li><a href={"/update/"+id} onClick={event=>{
        event.preventDefault();
        setMode('UPDATE');
      }}>Update</a></li>
      <li>
        <input type='button' value="Delete"/>
      </li>
    </>
    ```
    **:warning:주의사항**
    > * React는 하나의 태그 안에 작성해야 한다.
    > * 복수의 태그를 그룹화 하기 위해 빈 태그를 사용한다.    
    *ex)* <></>

2. 클릭 시 필요한 이벤트를 작성한다.

    ```js
    contextControl = <>
      <li><a href={"/update/"+id} onClick={event=>{
        event.preventDefault();
        setMode('UPDATE');
      }}>Update</a></li>
      <li>
        <input type='button' value="Delete" onClick={()=>{
          const newTopics = []
          <!-- 빈 배열을 작성한다. -->

          for(let i=0; i<topics.length; i++){
            if(topics[i].id !== id){
              newTopics.push(topics[i]);
            }
          }
        <!-- for문을 통해 현재 선택한 값과 id 값이 일치하지 않는 topics를 newTopics에 push 한다. -->

          setTopics(newTopics);
        <!-- setTopics에 newTopics를 담아준다. -->

          setMode('WELCOME');
        <!-- 상세 페이지를 삭제하였기에, 메인 페이지로 보내준다. -->
        }} />
      </li>
    </>
    ```

:link:[React-delete][React-delete] : 완성소스 및 결과창 정리 보기

[React-delete]: https://github.com/lbsafe/React-study/blob/main/study_07.md "React Delete"
***