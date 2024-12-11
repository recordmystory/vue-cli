# Vue CLI 공부
### Vue CLI (Command Line Interface)

[Vue CLI 공식문서](https://cli.vuejs.org/)

- Vite 기반의 프로젝트로 프로젝트를 생성

- npm 설치 후 프로젝트 생성

```powershell
npm install -g @vue/cli # 글로벌 레벨로 설치
node -v # 노드 버전 확인 
npm -v # npm 버전 확인
vue create vue3-cli # 프로젝트 생성
yarn serve # package.json 안에 scripts 안에 serve 
```

- npm과 yarn 비교

https://joshua1988.github.io/vue-camp/package-manager/npm-vs-yarn.html

- Vue 프로젝트 폴더 내용
    
    package.json
    
    ```json
    {
      "name": "vue3-cli",
      "version": "0.1.0",
      "private": true,
      "scripts": {
        "serve": "vue-cli-service serve",
        "build": "vue-cli-service build",
        "lint": "vue-cli-service lint"
      },
      "dependencies": {
        "core-js": "^3.8.3",
        "vue": "^3.2.13"
      },
      "devDependencies": {
        "@babel/core": "^7.12.16",
        "@babel/eslint-parser": "^7.12.16",
        "@vue/cli-plugin-babel": "~5.0.0",
        "@vue/cli-plugin-eslint": "~5.0.0",
        "@vue/cli-service": "~5.0.0",
        "eslint": "^7.32.0",
        "eslint-plugin-vue": "^8.0.3"
      },
      "eslintConfig": {
        "root": true,
        "env": {
          "node": true
        },
        "extends": [
          "plugin:vue/vue3-essential",
          "eslint:recommended"
        ],
        "parserOptions": {
          "parser": "@babel/eslint-parser"
        },
        "rules": {}
      },
      "browserslist": [
        "> 1%",
        "last 2 versions",
        "not dead",
        "not ie 11"
      ]
    }
    
    ```
    
    dependencies : 프로젝트 라이브러리 관련
    
    scripts : 프로젝트 관련 명령어 수행
    
    devDependencies : 프로젝트를 개발하기 위해 필요한 부수적인 라이브러리
    
    → dependencies는 배포용, devDependencies는 개발용, 화면 로직과 직접적으로 관련된 라이브러리는 배포용으로 설치해야함, 배포용 라이브러리는 npm run build로 빌드시에 최종 애플리케이션 콬드에 포함됨 (-D 옵션으로 포함되지 않아야할 라이브러리 제외 가능)
    
    eslint : 자바스크립트 문법 검사 도구
    
- vue.confing.js (뷰 프로젝트의 설정 파일)
    
    웹팩에 대한 설정을 변경하거나 추가적으로 제공하는 내용들을 정의할 때 사용
    
    ctrl + space로 확인 가능
    

### 라이브러리와 파일 임포트 방식

- main.js

```jsx
// 뷰 라이브러리를 들고옴
import { createApp } from 'vue' // vue: 라이브러리먕
// 뷰 파일을 들고옴
import App from './App.vue'

// const { createApp } = Vue; 
// App에 컴포넌트의 내용을 집어넣고 createApp에 대상을 App으로 함
createApp(App).mount('#app') 

```

라이브러리명에는 package.json에 있는 dependencies나 devDependencies의 내용만 올 수 있음 (npm  install 형태)

npm install로 설치하게 되면 프로젝트 하위 폴더 밑에 node-modules 하위폴더가 생김

### 페이지 로딩 과정

```html
<div id="app" data-v-app> <!-- vue.createApp을 했을 때 인스턴스가 붙어있는 영역 -->
</div>
```

Vue로 작성한 코드들이 문자열로 변환돼서 app안에 들어가게됨

- 참고할 Loader 개념 설명

[Loader | 웹팩 핸드북](https://joshua1988.github.io/webpack-guide/concepts/loader.html#%EB%A1%9C%EB%8D%94-%EC%A0%81%EC%9A%A9-%EC%88%9C%EC%84%9C)

[Introduction | Vue Loader](https://vue-loader.vuejs.org/)

[[Vue.js] vue-loader, SFC Spec, webpack 설정](https://leettle.tistory.com/18)
