# Sass_practice

- [Sass\_practice](#sass_practice)
  - [주석](#주석)
  - [중접(Nesting)](#중접nesting)
  - [상위(부모) 선택자 참조](#상위부모-선택자-참조)
  - [중첩된 속성](#중첩된-속성)
  - [변수](#변수)
  - [산술 연산](#산술-연산)
  - [재활용(Mixins)](#재활용mixins)
    - [매개변수 사용](#매개변수-사용)

## 주석

2개의 주석 방식 제공

- /**/
  - CSS로 컴파일시 남아있다
- //
  - CSS에서는 지원하지 않으므로 사라진다.

## 중접(Nesting)

- HTML

  ```html
    <div class="container">
      <ul>
        <li>
          <div class="name">FDONG</div>
          <div class="age">20</div>
        </li>
      </ul>
    </div>
  ```

- SASS 후손 선택자

  ```css
    .container{
      ul {
        li {
          font-size: 40px;
          .name {
            color: royalblue;
          }
          .age {
            color: orange;
          }
        }
      }
    }
  ```

- SASS 자식 선택자

  ```css
    .container{
      > ul {
        li {
          font-size: 40px;
          .name {
            color: royalblue;
          }
          .age {
            color: orange;
          }
        }
      }
    }
  ```

## 상위(부모) 선택자 참조

& 기호 사용

- SCSS
  
  ```css
    .btn {
      position: absolute;
      &.active {
        color: red;
      }
    }
    .list {ls
    
      li {
        &:last-child{
          margin-right: 0;
        }
      }
    }
  ```

- CSS
  
  ```css
    .btn {
      position: absolute;
    }
    .btn.active {
      color: red;
    }
    .list li:last-child{
      margin-right: 0;
    }
  ```

## 중첩된 속성

- SCSS
  
  ```css
    .box{
      font-weight: bold;
      font-size:10px;
      font-family: sans-serif;
      margin-top: 10px;
      margin-left: 20px;
      padding-top: 10px;
      padding-bottom: 40px;
      padding-left: 20px;
      padding-right: 30px;
    }
  ```

- CSS
  
  ```css
  .box {
    font: {
      weight: bold;
      size: 10px;
      family: sans-serif;
    };
    margin: {
      top: 10px;
      left: 20px;
    };
    padding: {
      top: 10px;
      bottom: 40px;
      left: 20px;
      right: 30px;
    };
  }
  ```

___
## 변수

변수는 유효범위를 가지고 있다.

- 중괄호 기준으로 사용할 수 있다.
  
- SCSS

  ```css

  $size:2100px 
    .container {
      position: fixed;
      top: $size;
      .item {
        $size: 100px
        width: $size;
        height: $size;
        transform: translateX($size);
      }
      left: $size;
    }
  ```

- CSS

  ```css
    .container {
      position: fixed;
      top: 200px;
      left: 100px;
    }
    .container .item {
      width: 100px;
      height: 100px;
      transform: translateX(100px);
    }

  ```

___

## 산술 연산

- '/' 연산자는 CSS에서 단축속성으로 활용되므로 컴파일되지 않고 그대로 사용된다.
- 단위는 동일해야한다.
- calc() 함수를 사용하면 다른 단위의 연산도 가능하다.
  - calc(100% - 200px);
1. 소괄호로 묶어서 사용하면 사용할 수 있다
   - (30px / 2)
2. 변수를 사용하면된다.
   - $size / 2;
3. 다른 연산자와 함께 사용한다.
   - 10px + 12px / 2

- SCSS
  
  ```css
    div{
      width: 20px + 20px;
      height: 40px - 10px;
      font-size: 10px * 2;
      margin: 30px / 2;
      padding: 20px % 7;
    }
    span {
      font-size: 10px;
      line-height: 10px;
      font-family: serif;
      font: 10px / 10px serif;  
    }
  ```

- CSS

  ```css
    div {
      width: 40px;
      height: 30px;
      font-size: 20px;
      margin: 30px/2;
      padding: 6px;
    }
    span {
      font-size: 10px;
      line-height: 10px;
      font-family: serif;
      font: 10px / 10px serif;  
    }
  ```
  
___

## 재활용(Mixins)

- SCSS
  
  ```css
    @mixin center {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .container {
      @include center;
      .item {
        @include center;
      }
    }
    .box {
      @include center;
    }
  ```
- CSS
  
  ```css
    .container {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .container .item {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .box {
      display: flex;
      justify-content: center;
      align-items: center;
    }
  ```

### 매개변수 사용

- SCSS
  
  ```css
      @mixin box($size: 100px) {
        width: $size;
        height: $size;
      }
      .container {
        @include box(200px);
        .item {
          @include box;
        }
      }
      .box {
        @include box;
      }
  ```

- CSS

  ```css
      .container {
        width: 200px;
        height: 200px;
      }
      .container .item {
        width: 100px;
        height: 100px;
      }
      .box {
        width: 100px;
        height: 100px;
      }
  ```
