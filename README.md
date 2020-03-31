# npm으로 새 패키지 생성하기

## init
npm에서 제공해주는 `init` 명령어를 통해 새 패키지를 생성할 수 있다.
```
$ npm init
```
명령어를 입력하고 패키지에 대한 정보를 입력해주면 된다.
이때 모든 정보를 기본값으로 설정하려면
```
$ npm init -y
```
로 패키지를 생성하면 된다.

## package.json
`init`을 통해 패키지를 생성하게 되면 `package.json`이란 파일을 볼 수 있다.
`package.json`파일에서는 이 패키지에 대한 정보를 확인할 수 있다.
```json
{
  "name": "프로젝트 이름",
  "version": "버전 정보",
  "description": "프로젝트 설명",
  "main": "노드 어플리케이션 진입 경로",
  "scripts": { // scripts에서는 명령어를 등록할 수 있다
    "명령어 이름": "수행 할 동작"
  },
  "author": "작성자",
  "license": "라이센스",
}
```

## install
`install`명령어는 외부의 패키지를 설치할 수 있는 명령어로, `i`로 줄여서 사용할 수도 있다.
```
$ npm install webpack
```

## webpack
`webpack`은 모듈 번들러로 여러 파일을 하나의 파일로 합쳐준다.
웹팩을 사용하기 위해 먼저 `webpack`과 웹팩 터미널 도구인 `webpack-cli`를 설치해야 한다.
```
$ npm i webpack webpack-cli
```

### webpack.config.js
웹팩 설치가 완료되었으면 터미널 명령어를 통해 설정을 할 수도 있지만, 편의를 위해 `webpack.config.js`파일을 생성하여 설정할 수 있다.
```javascript
const path = require('path');

module.exports = {
  mode: 'development',
  entry: {
    app: './src/app.js'
  },
  output: {
    filename: '[name].js',
    path: path.join(__dirname, '/dist'),
  },
}
```
mode: 'development'(개발용) or 'production'(배포용)
entry: 프로젝트 진입 경로
output: 결괏값(하나로 합쳐진 파일)
* filename: 파일의 이름으로, `[name]`에는 entry에서 키값 *app*으로 파일이 생성된다.
* path: 파일의 경로 (__dirname은 node.js의 명령어로 현재 파일 경로를 반환한다)

이제 웹팩을 실행하기 위해 `package.json`파일로 돌아가 scripts에 아래와 같이 작성해준다.
*package.json :*
```
{
    "scripts": {
        "dev": webpack
    }
}
```
이제 실행해볼 차례다. 아래의 명령어를 통해 웹팩을 작동시켜보자.
```
$ npm run dev
```

이렇게 기본적인 npm과 웹팩을 알아봤다
다음에는 웹팩 로더와 플러그인에 대해 알아보고 더 나아가서 바벨 설정법까지 알아보겠다.