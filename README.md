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
    - 선택자 ABC와 XYZ를 <u>동시에 만족</u>하는 요소 선택.

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
    - 선택자 ABC의 <u>자식</u> 요소 XYZ 선택.

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
    - 선택자 ABC의 <u>하위(후손)</u> 요소 XYZ 선택.
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
    - 선택자 ABC의 다음 형제 요소 XYZ <u>하나</u>를 선택.

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
    - 선택자 ABC의 다음 형제 요소 XYZ <u>모두</u>를 선택.

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
    - 선택자 ABC요소에 <u>마우스 커서가 올라가 있는 동안</u>를 선택.

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
    - 선택자 ABC요소에 <u>마우스를 클릭하고 있는 동안</u> 선택.

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
    - 선택자 ABC요소가 <u>포커스되면</u> 선택.
      - Focus가 될 수 있는 요소는 <u>HTML 대화형 콘텐츠</u>가 해당한다.
      - <u>INPUT,A,BUTTON,LABEL,SELECT</u> 등 여러 요소가 있다.
      - HTML 대화형 콘텐츠 요소가 아니더라도, <u>tabindex</u> 속성을 사용한 요소도 Focus가 될 수 있다.

  ```css
  <input type="text" />

  input:focus {
    background-color: orange;
  }

   마우스가 텍스트창에 포커스 되는 순간 동작된다.
  ```

  - Focus의 tabindex
    - tabindex
      - <u>tabindex</u>속성을 통해 Focus가 될 수 있는 요소를 만들 수 있다.
      - 이름에도 알 수 있듯이 Tab키를 사용해 Focos 할 수 있는 순서를 지정하는 속성이다.
      - 순서(값)로 <u>-1</u>이 아닌 다른 값을 넣는 것은 논리적 흐름을 방해하기 때문에 권장하지 않는다.

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
```
