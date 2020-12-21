# 이듬(E.UID), SCSS 믹스인

<img src="https://img.shields.io/badge/%40euid-SCSS--Mixins-red?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/v/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/l/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" />

[이듬 블렌디드 러닝](https://euid.dev)의 SCSS 믹스인 라이브러리

<br/>

## 설치

`@euid/scss-mixins` 패키지를 설치하는 방법은 다음의 2가지 중 하나를 사용할 수 있습니다.

방법 1. [GitHub 저장소](https://github.com/yamoo9/scss-mixins) 복제

```sh
$ git clone https://github.com/yamoo9/scss-mixins.git
```

방법 2. [NPM](https://npmjs.com) 설치

```sh
$ npm i @euid/scss-mixins
```

<br/>

## 사용법

[Dart Sass CLI](https://sass-lang.com/documentation/cli/dart-sass) 명령을 사용해 `node_modules` 디렉토리의 패키지를 불러올 수 있도록 설정합니다.

```sh
# -I, --load-path=
# <input_dir>:<output_dir>
$ sass -I node_modules src/sass:dist/css
```

패키지에서 모든 믹스인을 가져와 사용하려면 다음과 같이 호출 코드를 작성합니다.

```scss
@import '@euid/scss-mixins';
```

## 구성

`@euid/scss-mixins` 패키지에서 사용되는 변수를 변경해 사용하려면? 아래 코드를 복사/붙여넣고 변경해 사용합니다.

```scss
//* ---------------------------------------------------------------------------
//* 사용법: 아래 설정 변수 값을 복사/붙여넣은 후 사용자 정의 값 설정합니다.
//* ---------------------------------------------------------------------------

//* --------------------------------------------------------------------------
/// em 단위 기본 값 설정
$base-em-size: 16px;

/// rem 단위 기본 값 설정
$base-rem-size: 16px;

//* --------------------------------------------------------------------------
/// 컬러 스킴 설정
$colors: (
  black: #010101,
  white: #fefefe,
  gray: #787878,
);

//* --------------------------------------------------------------------------
// 박스 정렬 설정

/// justify-*, align-* 대신 place-* 속성 사용하고자 할 경우 true 설정
$using-place-layout: false;

//* --------------------------------------------------------------------------
// 미디어 쿼리 설정

/// 중단점 설계 (import-media 라이브러리 활용) → 임의의 키워드 사용 가능
$breakpoints: (
  'md': 768px,
  'lg': 1024px,
  'x-lg': 1280px,
  '2x-lg': 1440px,
);

/// 미디어 표현식 설계 (import-media 라이브러리 활용) → 임의의 키워드 사용 가능
$media-expressions: (
  'landscape': '(orientation: landscape)',
  'portrait': '(orientation: portrait)',
  'retina2x':
    '(-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi), (min-resolution: 2dppx)',
  'retina3x':
    '(-webkit-min-device-pixel-ratio: 3), (min-resolution: 350dpi), (min-resolution: 3dppx)',
);
```