# 이듬(E.UID) — SCSS Mixins

<img src="https://img.shields.io/badge/%40euid-SCSS--Mixins-red?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/v/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/l/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/dt/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /> <img src="https://img.shields.io/github/languages/code-size/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /><br/>

<!-- 
<img src="https://img.shields.io/david/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /> <img src="https://img.shields.io/github/issues-pr/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /> <img src="https://img.shields.io/github/issues/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /> <img src="https://img.shields.io/github/issues-closed/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /> <img src="https://img.shields.io/github/stars/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt /> <img src="https://img.shields.io/github/watchers/yamoo9/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt />
-->

SCSS 믹스인 라이브러리 → [이듬(E.UID)](https://euid.dev) 블렌디드 러닝 학습용

<img src="https://raw.githubusercontent.com/yamoo9/scss-mixins-snippets/master/assets/demonstration.gif" alt="" width="100%" />

<br/>

## 패키지 설치 (Install)

`@euid/scss-mixins` 패키지를 설치하는 방법은 다음의 2가지 중 하나를 선택해 사용할 수 있습니다.

**방법 1. [NPM](https://npmjs.com) 명령을 사용해 [@euid/scss-mixins](https://www.npmjs.com/package/@euid/scss-mixins) 패키지 설치 (권장)**

```sh
$ npm i @euid/scss-mixins
```

**방법 2. GitHub [yamoo9/scss-mixins](https://github.com/yamoo9/scss-mixins) 저장소 복제**

```sh
$ git clone https://github.com/yamoo9/scss-mixins.git
```

<br/>

## 패키지 호출 (Import)

@euid/scss-mixins 패키지를 사용하는 방법은 다음과 같습니다.

**방법 1. 상대 경로 활용**

별도 설정 없이 패키지를 호출해 사용할 경우, 상대 경로 방식으로 @euid/scss-mixins 패키지를 찾습니다.

```scss
@import '../node_modules/@euid/scss-mixins';
```

**방법 2. 임포트 경로(load path) 설정 (권장)**

[Dart Sass CLI](https://sass-lang.com/documentation/cli/dart-sass) 명령을 사용해 `node_modules` 디렉토리의 패키지를 불러올 수 있도록 설정합니다.

```sh
$ sass -I node_modules src/sass:dist/css
```

컴파일 명령을 실행할 때, 전달하는 `-I`는 `--load-path` 옵션의 단축 옵션입니다.  
단축 옵션을 사용하지 않을 경우 다음과 같이 명령문을 작성해 실행할 수 있습니다.

```sh
# -I, --load-path=
$ sass --load-path=node_modules src/sass:dist/css
```

패키지에서 모든 믹스인을 가져와 사용하려면 다음과 같이 호출 코드를 작성합니다.

```scss
@import '@euid/scss-mixins';
```

<br/>

## 패키지 문서 (Documentation)

[@euid/scss-mixins 문서](https://yamoo9.gitbook.io/scss-mixins)를 통해 사용법을 확인하고 익힐 수 있습니다.

![](assets/scss-mixins-documentation.png)

<br/>

## VS Code 확장(Extension)

[@euid/scss-mixins 스니펫(Snippets)](https://marketplace.visualstudio.com/items?itemName=yamoo9.euid-scss-mixins-snippets) 확장을 설치하면 믹스인 라이브러리 코드 호출이 손쉽습니다.
### 확장 설치

보기(View) → 확장(Extensions)을 선택, `euid` 키워드를 검색해 VS Code 마켓 플레이스에 배포된 확장을 설치합니다.

<img src="https://iili.io/KLwQbp.gif" alt="" width="640"/>

<br/>

## 패키지 라이선스 (License)

[MIT 라이선스](https://ko.wikipedia.org/wiki/MIT_%ED%97%88%EA%B0%80%EC%84%9C)