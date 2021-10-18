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
  - 1-1 자식 선택자(Child Cmbinator)
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
