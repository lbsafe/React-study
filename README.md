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

>컴포넌트를 통해 소스를 줄이고 한번의 수정으로   
해당 컴포넌트를 사용 하는 모든 부분을 수정할 수 있다.
***