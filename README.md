# 이듬(E.UID) — SCSS Mixins

<img src="https://img.shields.io/badge/%40euid-SCSS--Mixins-red?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/v/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" /> <img src="https://img.shields.io/npm/l/@euid/scss-mixins.svg?style=flat-square&labelColor=0A0A23&color=E6526F" alt="" />

SCSS 믹스인 라이브러리 → [이듬(E.UID)](https://euid.dev) 블렌디드 러닝 학습용



## 설치

`@euid/scss-mixins` 패키지를 설치하는 방법은 다음의 2가지 중 하나를 선택해 사용할 수 있습니다.

**방법 1. [NPM](https://npmjs.com) 명령을 사용해 [@euid/scss-mixins](https://www.npmjs.com/package/@euid/scss-mixins) 패키지 설치 (권장)**

```sh
$ npm i @euid/scss-mixins
```

**방법 2. GitHub [yamoo9/scss-mixins](https://github.com/yamoo9/scss-mixins) 저장소 복제**

```sh
$ git clone https://github.com/yamoo9/scss-mixins.git
```



## 패키지 호출 방법

@euid/scss-mixins 패키지를 사용하는 방법은 다음과 같습니다.

**방법 1. 상대 경로 활용**

별도 설정 없이 패키지를 호출해 사용할 경우, 상대 경로 방식으로 @euid/scss-mixins 패키지를 찾습니다.

```scss
@import '../node_modules/@euid/scss-mixins';
```

**방법 2. 임포트 경로(load path) 설정 (권장)**

[Dart Sass CLI](https://sass-lang.com/documentation/cli/dart-sass) 명령을 사용해 `node_modules` 디렉토리의 패키지를 불러올 수 있도록 설정합니다.

```sh
# -I, --load-path=
# <input_dir>:<output_dir>
$ sass -I node_modules src/sass:dist/css
# sass --load-path=node_modules src/sass:dist/css
```

패키지에서 모든 믹스인을 가져와 사용하려면 다음과 같이 호출 코드를 작성합니다.

```scss
@import '@euid/scss-mixins';
```

## 패키지 사용법

@euid/scss-mixins 패키지에 포함된 함수, 믹스인을 사용하는 방법을 안내합니다.

### ␥ 유틸리티 함수(Utility Functions)

<details open>
  <summary>가이드 문서</summary>

  #### [단위] `remove-unit()`

  ```scss
  remove-unit(16px); // → 16 숫자 값 반환
  ```


  #### [단위] `rem()`

  ```scss
  rem(16px);       // → 1rem 반환
  rem(16px, 10px); // → 1.6rem 반환
  ```

  #### [단위] `em()`

  ```scss
  em(16px); // → 1em 반환
  em(23px, 18px); // → 1.277777778em 반환
  ```

  #### [컬러] `getColor()`

  ```scss
  getColor(black); // → #010101 반환
  ```

  구성 변수 `$colors` 맵(map)의 컬러 이름에 연결된 값을 반환

  ```scss
  $colors: (
    black: #010101,
    white: #fefefe,
    gray: #787878,
  );
  ```

  #### [리스트] `first()`

  ```scss
  $list: button link headline;
  
  first($list); // → button 반환
  ```

  #### [리스트] `last()`

  ```scss
  $list: button link headline;

  last($list); // → headline 반환
  ```

  #### [검사] `isValidTypes()`

  ```scss
  $num: 9;
  $bool: false;

  isValidTypes($num, number string list);  // → true 반환
  isValidTypes($bool, number string list); // → false 반환
  ```

  #### [검사] `isValidKeywords()`

  ```scss
  $value: 100%;
  $key: full;

  isValidKeywords($value, auto initial full none); // → false 반환
  isValidKeywords($key, auto initial full none);   // → true 반환
  ```
</details>


### ␥ 믹스인(Mixins)

<details open>
  <summary>가이드 문서</summary>

#### [초기화] `normalize()`

```scss
@include normalize()
```

```css
/*! normalize.css v8.0.1 | MIT License | github.com/necolas/normalize.css */
html {
  line-height: 1.15;
  -webkit-text-size-adjust: 100%;
}

/* ... */
```

#### [간격] `m()`, `mx()`, `my()` / `p()`, `px()`, `py()`

```scss
.container {
  @include mx(auto);
  @include py(rem(30px));
  max-width: rem(1200px);
}
```

```css
.container {
  margin-left: auto;
  margin-right: auto;
  padding-top: 1.875rem;
  padding-bottom: 1.875rem;
  max-width: 75rem;
}
```

#### [레이아웃] `position()`, `absolute()`, ... `sticky()`

```scss
.header {
  @include fixed(z-index 1000 top 0 left 0 right 0);
}
```

```css
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
}
```
#### [레이아웃] `flex-container()`, `flex-item()`, `flex()`, `order()`

```scss
.flexContainer {
  @include flex-container(column wrap items-center justify-start content-end);
}

.flexItem-1 {
  @include flex-item(grow 1 shrink 0 basis 100% self-start);
  @include order(last); // first, none, 1...
}

.flexItem-2 {
  @include flex(1); // 1, auto, initial, none
}
```

```css
.flexContainer {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: center;
  align-content: flex-end;
}

.flexItem-1 {
  align-self: flex-start;
  flex-grow: 1;
  flex-shrink: 0;
  flex-basis: 100%;
  order: 9999;
}

.flexItem-2 {
  flex: 1 1 0%;
}
```

#### [레이아웃] `grid()`, `grid-auto()`, `row()`, `col()`, `area()`, ... `self()`

```scss
.gridContainer {
  // grid()
  // - grid-rows()
  // - grid-cols()
  // - gap()
  @include grid(2, 3, rem(10px));
  // grid-auto()
  // - auto-flow()
  // - auto-rows()
  // - auto-cols()
  @include grid-auto(minmax(rem(100px), auto), minmax(rem(80px), 1fr));
  @include items(center, start);
  @include content(space-between, stretch);
}

.gridItem-1 {
  // row()
  // row-span()
  // row-first()
  // row-end()
  @include row(start-end, 1 3);
  // col()
  // col-span()
  // col-first()
  // col-end()
  @include col(span, 2);
}

.gridItem-2 {
  @include row(se, 4 5);
  @include col-span(full);
}

.gridItem-3 {
  @include area(1 -1, 2 3);
  @include self(end, end);
}
```

```css
.gridContainer {
  display: grid;
  grid-template-rows: repeat(2, minmax(0, 1fr));
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 0.625rem;
  grid-auto-rows: minmax(6.25rem, auto);
  grid-auto-columns: minmax(5rem, 1fr);
  justify-items: center;
  align-items: start;
  justify-content: space-between;
  align-content: stretch;
}

.gridItem-1 {
  grid-row-start: 1;
  grid-row-end: 3;
  grid-column: span 2 / span 2;
}

.gridItem-2 {
  grid-row-start: 4;
  grid-row-end: 5;
  grid-column: 1 / -1;
}

.gridItem-3 {
  grid-row-start: 1;
  grid-row-end: -1;
  grid-column-start: 2;
  grid-column-end: 3;
  justify-self: end;
  align-self: end;
}
```

#### [반응형] `media()`

```scss
$breakpoints: (
  'md': 768px,
  'lg': 1024px,
  'x-lg': 1280px,
  '2x-lg': 1440px,
);

$media-expressions: (
  'dark-mode': '(prefers-color-scheme: dark)',
  'no-motion': '(prefers-reduced-motion: reduce)',
);

.mediaDemo {
  @include flex-container(column items-start justify-center);
  background: getColor(white);
  color: getColor(black);

  @include media('>lg') {
    flex-direction: row;
    justify-content: flex-start;
    align-items: flex-start;
  }
  
  @include media('>lg', 'dark-mode') {
    background: getColor(black);
    color: getColor(white);
  }
}
```

```css
.mediaDemo {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  background: #fefefe;
  color: #010101;
}
@media (min-width: 1025px) {
  .mediaDemo {
    flex-direction: row;
    justify-content: flex-start;
    align-items: flex-start;
  }
}
@media (min-width: 1025px) and (prefers-color-scheme: dark) {
  .mediaDemo {
    background: #010101;
    color: #fefefe;
  }
}
```

#### [접근성] `a11y-hidden()`

```scss
.a11yHidden {
  // 접근성 감춤 처리
  @include a11y-hidden();

  // focus 상태
  &--focusable {
    // focus 상태가 되면 접근성 감춤 처리 해제
    @include a11y-hidden(true);
  }
}
```

```css
.a11yHidden {
  overflow: hidden;
  position: absolute;
  clip: rect(0, 0, 0, 0);
  clip-path: circle(0);
  width: 1px;
  height: 1px;
  margin: -1px;
  border: 0;
  padding: 0;
  white-space: nowrap;
}
.a11yHidden--focusable {
  overflow: visible;
  position: static;
  clip: auto;
  width: auto;
  height: auto;
  margin: 0;
  white-space: normal;
}
```
#### [선택영역] `selection()`

```scss
@include selection() {
  background: getColor(black);
  color: getColor(white);
}

@include selection(img, button) {
  background: transparent;
  color: transparent;
}
```

```css
::-moz-selection {
  background: #010101;
  color: #fefefe;
}

::selection {
  background: #010101;
  color: #fefefe;
}

img::-moz-selection {
  background: transparent;
  color: transparent;
}

img::selection {
  background: transparent;
  color: transparent;
}

button::-moz-selection {
  background: transparent;
  color: transparent;
}

button::selection {
  background: transparent;
  color: transparent;
}
```

#### [플레이스홀더] `placeholder()`

```scss
@include placeholder() {
  color: #152d35;
  font-weight: bold;
}
```

```css
::-webkit-input-placeholder {
  color: #152d35;
  font-weight: bold;
}
:-ms-input-placeholder {
  color: #152d35;
  font-weight: bold;
}
::-moz-placeholder {
  color: #152d35;
  font-weight: bold;
}
::placeholder {
  color: #152d35;
  font-weight: bold;
}
```

#### [폰트] `font-face()`

```scss
@include font-face('SpoqaHanSans', '../font/spoqa-han-snas');
```

```css
@font-face {
  font-family: "SpoqaHanSans";
  font-style: normal;
  font-weight: normal;
  src: url("../font/spoqa-han-snas.eot");
  src: url("../font/spoqa-han-snas.eot?#iefix") format("embedded-opentype"), url("../font/spoqa-han-snas.woff") format("woff"), url("../font/spoqa-han-snas.ttf") format("truetype"), url("../font/spoqa-han-snas.svg#SpoqaHanSans") format("svg");
}
```
</details>

## 구성 변수

`@euid/scss-mixins` 패키지에서 사용되는 변수를 변경해 사용하려면? [구성 파일](./_config.scss) 코드를 복사/붙여넣고 변경해 사용합니다.

```scss
//* ---------------------------------------------------------------------------
//* 사용법: 아래 설정 변수 값을 복사/붙여넣은 후 사용자 정의 값 설정합니다.
//* ---------------------------------------------------------------------------

//* --------------------------------------------------------------------------
// em, rem 단위 기본 값 설정
$base-em-size: 16px;
$base-rem-size: 16px;


//* --------------------------------------------------------------------------
// 컬러 스킴 설정 (`컬러-이름: 값`을 임의로 추가해 사용)
$colors: (
  black: #010101,
  white: #fefefe,
  gray: #787878,
);


//* --------------------------------------------------------------------------
// 박스 정렬 설정
// justify-*, align-* 대신 place-* 속성 사용하고자 할 경우 true 설정
$using-place-layout: false;


//* --------------------------------------------------------------------------
// 미디어 쿼리 설정
// 라이브러리: https://eduardoboucas.github.io/include-media/

// 미디워 퀴리 설정 여부 (기본 값: true)
$im-media-support: true;

// $im-media-support 값이 false일 경우,
// 설정된 미디어 쿼리 키워드 이상 스크린 너비는 무시 처리
$im-no-media-breakpoint: 'x-lg';

// $im-media-support 값이 false일 경우에도
// 허용할 미디어 식 값을 설정
// 참고: https://bit.ly/3h75qGw
$im-no-media-expressions: ('screen');

// 중단점 설계 (import-media 라이브러리 활용) → 임의의 키워드 사용 가능
// 참고: https://bit.ly/2J9wKYe
$breakpoints: (
  'md': 768px,
  'lg': 1024px,
  'x-lg': 1280px,
  '2x-lg': 1440px,
);

// 미디어 표현식 설계 (import-media 라이브러리 활용) → 임의의 키워드 사용 가능
// 참고: https://mzl.la/2KMpm5o
$media-expressions: (
  'landscape': '(orientation: landscape)',
  'portrait': '(orientation: portrait)',
  'retina2x': '(-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi), (min-resolution: 2dppx)',
  'retina3x': '(-webkit-min-device-pixel-ratio: 3), (min-resolution: 350dpi), (min-resolution: 3dppx)',
  'dark-mode': '(prefers-color-scheme: dark)',
  'no-motion': '(prefers-reduced-motion: reduce)'
);
```

## 라이선스

MIT 라이선스에 따라 공개된 코드