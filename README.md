## 선택자

- 스타일(css)을 적용할 대상(Selector)

```css
선택자 {
  속성: 값;
}

/* css */
div {
  color: red;
  margin: 20px; /*외부여백*/
}
/* {} 스타일의 범위의 시작과 끝 */
/* 항상 스타일 속성에는 ":"와 ";"을 넣어주어야 한다. */
```

## 주석

- 주석의 단축키는 Ctrl + / or Cmd + /

## CSS 선언 방식

- 내장 방식, 링크 방식, 인라인 방식, @import 방식 4가지가 있다.

- 내장 방식

```css
<style></style>의 내용(Contents)으로 스타일을 작성하는 방식 */

/* css */
<style>
 div {
   color: red;
   margin: 20px
 }
</style>
```

- 인라인 방식

```css
요소의 style 속성에 직접 스타일을 작성하는 방식(선택자 없음)

<div style="color: red; margin: 20px;"></div>
```

- 링크방식

```html
<link />로 외부 CSS문서를 가져와서 연결하는 방식 "병력방식"이라고 한다.

<!-- html -->
<link rel="stylesheet" href="./css/main.css" />
```

```css
/* css */
div {
  color: red;
  margin: 20px;
}
```

- @import 방식

```css
CSS의 @import 규칙으로 CSS 문서 안에서 또 다른 CSS 문서를 가져와 연결하는 방식

"직렬로 연결하는 방식"이라고 한다.

/* main.css */
@import url("./box.css");

div {
  color: red;
  margin: 20px;
}
```

```css
/* box.css */
.box {
  background-color: red;
  padding: 20px;
}
```

## CSS 선택자

- CSS 선택자에는 기본, 복합, 가상 클래스, 가상 요소, 속성 5가지가 있다.

- 1.기본 선택자

  - 1-1.전체 선택자(Universal Selector)
    - "\*"을 사용 모든 요소를 선택

  ```html
  <!-- 모든 요소에 적용 -->
  <style>
    * {
      color: red;
    }
  </style>

  <div>
    <ul>
      <li>사과</li>
      <li>당근</li>
      <li>브로콜리</li>
    </ul>
  </div>
  ```

- 1.기본 선택자

  - 1-2.태그 선택자(Type Selector)
    - 태그 이름을 요소 선택

  ```html
  <!-- 해당 태그에 적용 -->
  <style>
    li {
      color: red;
    }
  </style>

  <div>
    <ul>
      <li>사과</li>
      <li>당근</li>
      <li>브로콜리</li>
    </ul>
  </div>
  ```

- 1.기본 선택자

  - 1-3.클래스 선택자(Class Selector)
    - HTML class속성의 값의 요소 선택

  ```html
  <!-- class 이름으로 그룹된 요소 적용 -->
  <!-- 중복요소 적용 -->

  <style>
    .abc {
      color: red;
    }
  </style>

  <div>
    <ul>
      <li>사과</li>
      <li>당근</li>
      <li class="abc">브로콜리</li>
    </ul>
  </div>
  ```

- 1.기본 선택자

  - 1-4.아이디 선택자(ID Selector)
    - HTML id 속성의 값의 요소 선택

  ```html
  <!-- id 이름으로 그룹된 요소 적용 -->
  <!-- 단일요소 적용 -->

  <style>
    #abc {
      color: red;
    }
  </style>

  <div>
    <ul>
      <li>사과</li>
      <li>당근</li>
      <li id="abc" class="abc">브로콜리</li>
    </ul>
    <ul>
      <li>사과</li>
      <li>당근</li>
      <li class="abc">브로콜리</li>
    </ul>
  </div>
  ```

- 2.복합 선택자

  - 1-1 일치 선택자(Basic Combinator)
    - 선택자 ABC와 XYZ를 동시에 만족하는 요소 선택.

```html
<div>
  <ul>
    <li>사과</li>
    <li>딸기</li>
    <li class="orange">오렌지</li>
  </ul>
  <div>당근</div>
  <p>토마토</p>
  <span class="orange">오렌지</span>
</div>

일치선택자 예시 span .orange { color: red; }
```

- 2.복합 선택자

  - 1-2 자식 선택자(Child Cmbinator)
    - 선택자 ABC의 자식 요소 XYZ 선택.

```html
<div>
  <ul>
    <li>사과</li>
    <li>딸기</li>
    <li class="orange">오렌지</li>
  </ul>
  <div>당근</div>
  <p>토마토</p>
  <span class="orange">오렌지</span>
</div>

자식선택자 예시 ul> .orange { color: red; }
```

- 2.복합 선택자

  - 1-3 하위(후손) 선택자(Descendant Cmbinator)
    - 선택자 ABC의 하위(후손) 요소 XYZ 선택.
    - '띄어쓰기'가 선택자의 기호!

```html
<div>
  <ul>
    <li>사과</li>
    <li>딸기</li>
    <li class="orange">오렌지</li>
  </ul>
  <div>당근</div>
  <p>토마토</p>
  <span class="orange">오렌지</span>
</div>
<span class="orange">오렌지</span>

하위 선택자 예시 div .orange {color: red;}
```

- 2.복합 선택자

  - 1-4 인접(형제) 선택자(Adjacent Sibilng Cmbinator)
    - 선택자 ABC의 다음 형제 요소 XYZ 하나를 선택.

클래스 오렌지의 제외한 다음 선택자인 망고 하나에 CSS가 지정된다.

```html
<ul>
  <li>딸기</li>
  <li>수박</li>
  <li class="orange">오렌지</li>
  <li>망고</li>
  <li>사과</li>
</ul>

인접 선택자 예시 .orange + li { color: red;}
```

- 2.복합 선택자

  - 1-5 일반(형제) 선택자(General Sibilng Cmbinator)
    - 선택자 ABC의 다음 형제 요소 XYZ 모두를 선택.

클래스 오렌지 제외한 다음 요소 모두에 적용된다

```html
<ul>
  <li>딸기</li>
  <li>수박</li>
  <li class="orange">오렌지</li>
  <li>망고</li>
  <li>사과</li>
</ul>

일반 선택자 예시 .orange ~ li { color: red;}
```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 모든 가상 클래스 선택자는 앞에 " : " 이 붙는다.

  - 1-1 HOVER
    - 선택자 ABC요소에 마우스 커서가 올라가 있는 동안를 선택.

  ```css
  <a href="www.naver.com">NAVER</a>

  a {
    color: blue;
  }

  a:hover {
    color: red;
  }

  a에 마우스 커서가 올라가면 파랑에서 빨강으로 바뀐다.
  ```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 1-2 ACTIVE
    - 선택자 ABC요소에 마우스를 클릭하고 있는 동안 선택.

  ```css
  <a href="www.naver.com">NAVER</a>

  a {
    color: blue;
  }

  a:active {
    color: red;
  }

  a에 마우스가 클릭되는 동안 파랑에서 빨강으로 바뀐다.
  ```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 1-3 FOCUS
    - 선택자 ABC요소가 포커스되면 선택.
      - Focus가 될 수 있는 요소는 HTML 대화형 콘텐츠가 해당한다.
      - INPUT,A,BUTTON,LABEL,SELECT 등 여러 요소가 있다.
      - HTML 대화형 콘텐츠 요소가 아니더라도, tabindex 속성을 사용한 요소도 Focus가 될 수 있다.

  ```css
  <input type="text" />

  input:focus {
    background-color: orange;
  }

   마우스가 텍스트창에 포커스 되는 순간 동작된다.
  ```

  - Focus의 TABINDEX
    - TABINDEX
      - "tabindex" 속성을 통해 Focus가 될 수 있는 요소를 만들 수 있다.
      - 이름에도 알 수 있듯이 Tab키를 사용해 Focos 할 수 있는 순서를 지정하는 속성이다.
      - 순서(값)로 "-1"이 아닌 다른 값을 넣는 것은 논리적 흐름을 방해하기 때문에 권장하지 않는다.

```html
<div class="box" tabindex="-1"></div>
```

```css
.box {
  width: 100px;
  height: 100px;
  background-color: blue;
  transition: 1s;
}

.box:focus {
  width: 300px;
  background-color: red;
}

focus가 적용되지 않던 div에 tabindex를 통해서 가능하게 만든다.
원래 적용이 되는 input 같은 요소에는 사용하지 말 것
```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 1-4 FIRST CHILD
    - 선택자 ABC가 형제 요소 중 첫째라면 선택.

```css
.fruits span:first-child {
  color: red;
}
```

```html
<div class="fruits">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>

선택자의 첫번째 요소가 "span"에 "딸기"에 적용이 된다.
```

```css
.fruits div:first-child {
  color: red;
}
첫번째 요소가 div가 아니고, span이 첫번째이기에 적용이 되지 않는다.
```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 1-5 LAST CHILD
    - 선택자 ABC가 형제 요소 중 막내라면 선택.

```css
.fruits h3:last-child {
  color: red;
}
```

```html
<div class="fruits">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>

선택자의 마지막 요소가 h3이기에 "사과"에 적용이 된다.
```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 1-6 NTH CHILD
    - 선택자 ABC가 형제 요소 중 (n)째 라면 선택.

```css
.fruits *:nth-child(2) {
  color: red;
}
```

```html
<div class="fruits">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>

선택자의 전체선택자 중 2번째 요소 "수박"에 적용이 된다.
```

```css
짝수번째 선택
.fruits div:first-child(2n) {
  color: red;
}
n은 0부터 시작(Zero-Based Numbering). 2n은 0,2,4,6,8이므로 2의 배수로 짝수번째에 적용되어진다.
```

```css
홀수번째 선택
.fruits div:first-child(2n+1) {
  color: red;
}
2n은 0,2,4,6,8이므로 2의 배수에 1씩 더 해지기 때문에 홀수번째에 적용되어진다.
```

```css
2번째부터 요소선택
.fruits div:first-child(n+2) {
  color: red;
}
n은 0,1,2,3,4로 늘어나고 더 해지는 값은 2씩이므로 값은 2,3,4,5,6로 증가되기 때문에, 2번째부터 적용되어진다.
```

- 3.가상 클래스 선택자(Pseudo-Classes)

  - 1-7 부정 선택자(Negation) NOT
    - 선택자 XYZ가 아닌 ABC 요소 선택.

```css
.fruits *:not(span) {
  color: red;
}
```

```html
<div class="fruits">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>

span을 부정하는 것이므로 span을 제외한 요소에 적용된다.
```

- 4.가상 요소 선택자(Pseudo-Elements)

  - 1-1 BEFORE
    - 선택자 ABC가 요소의 내부 앞에 내용(Content)을 삽입.
    - 선택자 안에 항상 "content"를 삽입해야 한다.
    - 앞에 "::" 사용

```css
.box::before {
  content: "앞!";
}
```

```html
<div class="box">Content!</div>
class box의 앞에 가상의 요소가 만들어지고 "앞! Content!"로 출력되어진다.
```

- 4.가상 요소 선택자(Pseudo-Elements)

  - 1-2 AFTER
    - 선택자 ABC가 요소의 내부 뒤에 내용(Content)을 삽입.

```css
.box::after {
  content: "뒤!";
}
```

```html
<div class="box">Content!</div>
class box의 뒤에 가상의 요소가 만들어지고, "Content! 뒤!"로 출력되어진다.
```

```css
.box {
  width: 100px;
  height: 100px;
  background-color: orange;
}
.box::after {
  content: "";
  display: block;
  width: 30px;
  height: 30px;
  background-color: blue;
}
```

```html
<div class="box">Content!</div>
```

- 5.속성 선택자(Attribute)

  - 1-1 ATTR
    - 속성 ABC을 포함한 요소 선택
    - 특수기호 "[]" 사용한다.

```css
[disabled] {
  color: red;
}
```

```html
<input type="text" value="HE" />
<input type="password" value="1234" />
<input type="text" value="ABC" disabled />

"disabled" 지정된 태그에 적용된다.
```

- 5.속성 선택자(Attribute)

  - 1-2 ATTR=VALUE
    - 속성 ABC을 포함하고 값이 XYZ인 요소 선택

```css
[type="password"] {
  color: red;
}
```

```html
<input type="text" value="HE" />
<input type="password" value="1234" />
<input type="text" value="ABC" disabled />

"type이 password"인 속성에 적용된다.
```

## 스타일 상속

```css
.animal {
  color: red;
}
```

```html
<div class="ecosystem">
  생태계
  <div class="animal">
    동물
    <div class="tiger">호랑이</div>
    <div class="lion">사자</div>
    <div class="elephant">코끼리</div>
  </div>
  <div class="plant">식물</div>
</div>

.animal을 하단에 있는 호랑이~코끼리도 같은 그룹안에 있기 때문에 상속받는다.
```

- 상속되는 CSS 속성들..
  - 모두 글자/문자 관련 속성들!(모든 글자/문자 속성은 아님 주의!)
  - font-style: 글자 기울기
  - font-weight: 글자 두께
  - font-size: 글자 크기
  - line-height: 줄 높이
  - font-family: 폰트(서체)
  - color: 글자 색상
  - text-align: 정렬

## 강제 상속 inherit

```css
.parent {
  width: 300px;
  height: 200px;
  background-color: red;
}
.child {
  width: 100px;
  height: inherit; /*강제상속*/
  background-color: inherit;
  position: fixed;
  top: 100px;
  right: 10px;
}
```

```html
<div class="parent">
  <div class="child"></div>
</div>
```

## 선택자 우선순위

- 우선순위란, 같은 요소가 여러 선언의 대상이 된 경우,
  어떤 선언의 CSS 속성을 적용할지 결정하는 방법

1. 점수가 높은 선언이 우선함!
2. 점수가 같으면, 가장 마지막에 해석된 선언이 우선함!

- 용어는 중요하진 않지만, CSS 우선순위의 점수를 계산하는 것을 "명시도"라고 부른다.
- 용어는 중요하진 않지만, "!importent" 키워드를 사용하는 것을 "중요도"라고 부른다.
- "선언순서(코드가 해석된 순서)"에 따라 우선한다고 표현한다.

```css
div {
  color: red !important; /*!important-9999999점*/
}
#color_yellow {
  color: yellow; /*ID선택자-100점*/
}
.color_green {
  color: green; /*Class선택자-10점*/
}
div {
  color: blue; /*div 태그 선택자-1점*/
}
* {
  color: darkblue; /*전체선택자-0점*/
}
body {
  color: violet; /*상속-X*/
}
```

```html
<div id="color_yellow" class="color_green" style="color:orange;">
  <!--style 인라인 선언 - 1000점-->
  Hello World!
</div>
```

```css
/*우선순위 점수매기기*/
.list li.item { /*21점*/
  color: red;
}
.list li:hover { /*21점*/
  color: red;
}
.box::before { /*11점*/
  content: "good";
  color: red;
}
#submit span { /*101점*/
  color: red;
}
header .mene li:nth-child(2) { /*22점*/
  color: red;
}
h1 { color: red; } /*1점*/
:not(.box){ color: red; } /*10점*/
}
```
