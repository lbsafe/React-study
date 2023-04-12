# 수정 및 배포법

## 수정 방법

<p align="center"><img src="https://user-images.githubusercontent.com/65703793/231374111-50be48aa-a26f-452e-aefc-8704c93e962e.png" alt="study" width="1000px"></p>

```html
경로: src폴더 > index.js

위 이미지를 확인해 보면 같은 <App />과 ./App 의 설명이 있다.
둘은 같은 파일로 ./App는 생략 된 경로를 의미해 준다.
```
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/231374123-ffaddd79-b280-48d5-b38c-01302a0a5aac.PNG" alt="study" width="1000px"></p>

```html
App.js 경로를 들어가서 문구를 수정하면 변동 되는 것을 확인 할 수 있다.
```
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/231374130-4fdc6b64-7101-460f-b285-42644fbff31c.PNG" alt="study" width="1000px"></p>

```html
App.js(2번 이미지) 경로를 들어가서 import 되어있는 App.css 또한 수정하면 현재 페이지에 적용된다.
```
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/231374135-15f2a09a-4e30-4a93-a90e-30b70f0f7762.PNG" alt="study" width="1000px"></p>

```html
같은 원리로 index.js(처음 사진)를 살펴보면
document.getElementById('root')를 볼 수 있는데,
index.html 파일의 <div id="root"></div> 와 같다.
```
***

## 배포 방법

**:one:** 터미널 > npm run build(배포판을 만드는 과정)

 ```html
 $ npm run build
 ```
**:two:** build 폴더 생성

**:three:** build 폴더 안에 index.html 생성 확인

**:four:** 터미널 > npx serv -s build

 ```html
 $ npx serv -s build
 ```
**:five:** 생성된 아래 경로 클릭 또는 주소창에 입력

<p align="center"><img src="https://user-images.githubusercontent.com/65703793/231380176-f10b6a0c-d361-4772-a6f1-6e0652cc7f1d.PNG" alt="study" width="491px"></p>

***

**:star:최종결과:star:**
<p align="center"><img src="https://user-images.githubusercontent.com/65703793/231381266-cdd2d9eb-db9e-4a2e-84a3-fabb6343efdd.PNG" alt="study" width="1000px"></p>

***