# Normard Kokoa Clone

옆에 다른 요소를 못 붙이면 block, 붙일수 있으면 inline
inline span a img
어떤 요소가 inline이면 높이와 넓이가 없다.
어떤 요소가 block이면 높이와 넓이가 있다.

box -> margin border padding 3가지 요소
margin: box의 border의 바깥에 있는 공간

- collapsing margins 현상: 흰 box의 경계가 보라색 box의 경계와 같을 때 일어나고 두 box의 margin은 하나가 된다.

border:
padding: border로부터 안쪽에 있는 공간

inline: margin 좌우는 적용되고 위아래는 안됌. 그렇기에 display block으로 바꿔줘야됨

#tomato -> id="tomato"
.tomato -> class="tomato"

inline-block은 반응형을 지원하지않기에 suck

flexbox 사용시 주의점

1. 자식엘리먼트에는 어떤것도 적지 말아야 된다. 부모만 명시
2. 주축(기본: 수평) justify-content
3. 교차축(기본: 수직) align-item
   부모가 높이를 가지고 있지않으면 교차측을 변경해도 반영되지않음
   viewport height: 화면상보여지는크기

### 3.11 Flexbox Part Tow

flow-direction으로 주축방향을 수정할 수 있다.

### 3.12 Fixed

### 3.13 RelativeAbsolute

#### position

- default(static)
  - 레이아웃이 박스를 처음 위치하는 곳에 두는것
- fiexd(틀고정)
  - 생성된 시점으로 거정되어 있지만 top, left, right, bottom에서 하나만 수정 되면 기 생성된 위치를 신경 쓰지 않는다(block, margin)
  - top, left, right, bottom을 수정하면 서로 다른 레이어로 넘어감
  - 가장 위에 있음
- relative
  - 포지션을 처음 위치한 곳을 기준으로 위치를 수정 할 수 있음
- absolute
  - 가장 가까운 relative 부모를 기준으로 이동 (없으면 상단으로 이동)

### 3.14 Pseudo Selectores part One

```css
/* Pseudo selector는 특정위치에 있는 태그들을 지정할 수 있음*/

/* 사용법 */
span:[옵션명](value) {
  ...;
}

/* 첫번째 태그 */
span:first-child {
  ...;
}

/* 마지막 태그 */
span:last-child {
  ...;
}

/* 인덱스 지정 */
span:nth-child(1) {
}

/* 짝수, 홀수를 지정 */
span:nth-child(even or odd) {
  ...;
}

/* n으로 순번을 지정 할 수 있음 */
span:nth-child(3n + 1) {
  ...;
}
```

### 3.15 Combinators

```css
/* 1. 부모와 바로 밑 자식의 관계 */
p span {
}

<p>
	<span>여기에 적용됨</span>
</p

/* 2. 태그 아래 바로 밑 자식 */
div > span {
    ...
}

<div>
<span>여기에 적용됩니다.</span>
</div>

/* 3. 형제 바로 아래 형제 */
div + span {
    ...
}

<p></p>
<span>여기에 적용</span>

/* 4. 형재 아래 형제(바로 아래 아니여도 됌) */
div ~ span {
    ...
}

<p></p>
<span>여기에 적용</span>
```

### 3.16 Pseudo Selectors part Tow

```css
/* required */
input {
    border: 1px solid wheat;
}
input:required {
    border-color: tomato;
}

<form>
	<input type="text" placeholder="username" />
	<input type="password" required placeholder="password" />
</form>

/* attribute */
input[type="password"] {
    background-color: thistle;
}
input[placeholder="username"] {
    background-color: thistle;
}

<form>
	<input type="text" placeholder="username" />
	<input type="password" required placeholder="password" />
</form>

/* ~:포함 $:끝에 오는 경우 ^:처음에 오는 경우 */
input[placeholder~="name"] {
	background-color: pink;
}

<input type="text" placeholder="First name" />
<input type="text" placeholder="Last name" />

/* etc 기타 MDN 참조 */
```

### 3.17 States

```css
/* 클릭 시 */
button:active {
  background-color: yellowgreen;
}

/* 마우스를 올렸을 때 */
button:hover {
  background-color: tomato;
}

/* 키보드로 선택됬을때 */
button:focus {
  background-color: tomato;
}

/* 키보드로 선택됬을때 */
button:focus {
  background-color: tomato;
}

/* 클릭했거나, 브라우저를 방문했을때 */
a:visited {
  color: tomato;
}

/* focursed인 자식을 가진 부모 엘리먼트에 적용 */
form:forcus-within {
  border-color: seagreen;
}

/* 부모의 상태에 따라 자식 상태 변경 */
form:hover input {
  background-color: sienna;
}

form:hover input:focus {
  background-color: sienna;
}
```

### 3.18 Recap

```css
/* placeholder가 있을경우 변경 */
input::placeholder {
  color: yellowgreen;
}

/* selection 마우스로 선택했을때*/
p::selection {
  background-color: yellowgreen;
}

/* 첫번쨰 문자만 */
p::first-letter {
  color: white;
}
```

### 3.19 Colors and Variables

```css
/* Color */
/* 1. hexadecimal color */
#FAE100

/* 2. rgb */
/*    ) */
rgb(250, 225, 0)

/* 3. rgba */
rgb(250, 225, 0, 0.8)

/* Variable(custom property) */
/* css custom property 브라우저 지원버전 */
:root {
  --main-color: #fcce00;
  --default-border: 1px solid var(--main-color);
}

p {
  background-color: var(--main-color);
}
a {
  color: var(--main-color);
  border: var(--default-border);
}
```

## 4. ADVANCED CSS

### 4.0 Transitions

```css
/* 1. transition 속성은 state가 없는 요소에 붙어야됨 */
/* 2. transition이 있으면 state에도 있어야 됨 */

/* transition: <변경요소> <시간> <옵션>, ... */
a {
  color: wheat;
  background-color: tomato;
  text-decoration: none;
  padding: 3px 5px;
  border-radius: 5px;
  font-size: 55px;
  /* transition: background-color 10s ease-in-out, color 5s ease-in-out; */
  transition: all 5s ease-in-out;
}
a:hover {
  color: tomato;
  background-color: wheat;
}
```

### 4.1 Transitions part Two

```css
/* ease in function: 브라우저한테 애니메이션이 어떻게 변할지 나타냄 */
/* 아래 사이트에서 실습 */
/* https://matthewlein.com/tools/ceaser */
```

### 4,2 Transformations

```css
/* image를 원으로 만들 수 있음 */
img {
  border-redius: 50%;
}

/* Transform은 형제를 변경하지 않음
   margin, padding을 변경하지 않고 원하는 요소를 옮기기 위해서 사용
   Tramsform을 이용하여 css를 3D로 만듬 */
img {
  transform: rotateY({각도}deg);
}

/* sacle: 크기변경*/
img {
  transform: sacle(2, 2);
}

/* translate: 옮기기 */
img {
  transform: translateX(-100px);
}

/* skew: 비스듬히 기울이기 */
img {
  transform: skew(45deg);
}

/* transition과 같이 사용하면 awesome */
img {
  border: 5px solid black;
  border-radius: 50%;
  transition: transform 2s ease-in-out;
}
img:hover {
  transform: rotateY(360deg) scale(0.5);
}
```

### 4.3 Animations part One

```css
/* 계속 재생되는 애니메이션이 필요할때 */

/* 사용법 */
@keyfrmaes 이름 {
}

/* 첫번째 사용법 */
@keyframes superSexyCoinFlip {
  from {
    transform: rotateX(0);
  }
  to {
    transform: rotateX(360deg);
  }
}

img {
  border: 5px solid black;
  border-radius: 50%;
  animation: superSexyCoinFlip 5s ease-in-out infinite /*무한*/;
}
/* 두번째 사용법 */
@keyframes superSexyCoinFlip {
  0% {
    transform: rotateX(0);
  }
  50% {
    transform: rotateY(180deg) translateX(100px);
  }
  100% {
    transform: rotateX(0);
  }
}

img {
  border: 5px solid black;
  border-radius: 50%;
  animation: superSexyCoinFlip 5s ease-in-out infinite;
}
```

### 6.1 Sign Up Screen part ONe

단축키
! + 엔터
line:css

<link rel="stylesheet" href="style.css" />

### 6.2 BEM

클래스로 표기를 명명하였음
소속관계 ** btn**column
행동 -- btn--wide

### 6.3 FontAwesome

아이콘을 만드는 방법

1. SVG : 좌표로 그림을 늘릴 수 있다.
2. Heroicons
3. FontAwesome
4. Google Fonts

script는 body닫기 마지막에 있어야됨

### 6.5 Status Bar css

CSS Hack

```css
.status-bar {
  display: flex;
  justify-context: center;
}

.status-bar__column {
  width: 33%;
}
```

### 6.6 Sign Up Screen part Three

HTML에서 기본적인 마진 같은 것들을 없애기 위해선 리셋 CSS를 사용해야 한다.

리셋 CSS는 CSS파일이다.

margin:0, pdding:0, border:0 초기화 되어 있는 파일

### 6.12 단축키

nav>ul>li*4>a

box-sizing: border-box를 쓰면 CSS가 content가 보일 부분을 늘리 않음

width 200px
padding left 50px

|50px|200px

### 7.1 Publishing on Github Pages

branch를 ``gh-pages``로 만들고 ``push``를 하면 github에 들어가서 Environments에 들어가보면 github.io 페이지와 연결되어 볼 수 있다.