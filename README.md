# Sass_practice

- [Sass\_practice](#sass_practice)
  - [주석](#주석)
  - [중접(Nesting)](#중접nesting)
  - [상위(부모) 선택자 참조](#상위부모-선택자-참조)
  - [중첩된 속성](#중첩된-속성)

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

- Sass
  
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

- Sass
  
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
