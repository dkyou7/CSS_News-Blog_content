[toc]

# 뉴스 & 블로그 스타일 CSS 실습해보기

## 1. 사이트 크기에 따라 정렬 형태가 달라지도록 구현해보기

![image](https://user-images.githubusercontent.com/26649731/76927140-9140c600-6921-11ea-848e-21c930c7241f.png)

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="grid-guide.css">
    <link rel="stylesheet" href="style.css">
    <title>Document</title>
</head>
<body>
    <div class="box1">BOX1</div>
    <div class="box2">BOX1</div>
    <div class="boxA">
        <div class="box3">BOX1</div>
        <div class="box4">BOX1</div>
    </div>
    <div class="box5">BOX1</div>
</body>
</html>
```

```css
@charset "UTF-8";

body{
    font-family: '맑은 고딕','Apple SD Gothic Neo',sans-serif;
    margin: 0;
}

/* ####### 768 이상부터 적용됨 ####### */
@media (min-width:768px){
    /* box3이랑 box4 가로 정렬하기 */
    .boxA::after{
        content: '';
        display: block;
        clear: both;
    }
    .box3{
        float: left;
        width: 70%;
    }
    .box4{
        float: left;
        width: 30%;
    }
}
```

- min-width: ~부터 적용됨
- max-width: ~까지는 적용됨

## 2. 박스 내부에 요소 추가

### 1) 네브바 만들기

- 이제는 거의 공식처럼 외우게 되는 css 스타일방법이다.

![image](https://user-images.githubusercontent.com/26649731/76927838-4922a300-6923-11ea-984c-835662acaa06.png)

```html
<nav class="menu">
    <ul>
        <li><a href="#">메인</a></li>
        <li><a href="#">잡화</a></li>
        <li><a href="#">도구</a></li>
        <li><a href="#">외출</a></li>
        <li><a href="#">음식</a></li>
        <li><a href="#">문의</a></li>
    </ul>
</nav>
```

```css
/* 네비게이션바 */
.menu ul{
    margin: 0;
    padding: 0;
    list-style: none;
}
.menu li a{
    display: block;
    padding: 5px;
    font-size: 14px;
    text-decoration: none;
    color: #000000;
}
.menu li a:hover{
    background-color: #eeeeee;
}
.menu ul:after{
    content: '';
    display: block;
    clear: both;
}
.menu li{
    float: left;
    width: auto;
}
```

### 2) 박스 내부에 그림 꽉 차게 만드는 방법

- 노랑 박스 내부에 사진이 너비만큼 차게 만들었다.
- 사진을 크게해서 가득 차게 만들려면 어케해야하는지는 아직 모름.

![image](https://user-images.githubusercontent.com/26649731/76929517-bb958200-6927-11ea-888c-f5bad2da59f6.png)

```html
<div class="story">
    <h1>개발자로 성장하는 방법</h1>
    <p><img src="img/03/tomato.jpg" alt=""></p>
    ...
```

```css
.story img{
    max-width: 100%;
    height: auto;
}
```

## 3. 레이아웃 조정

### 1) 요소의 세로 간격 조정

- 깔끔하게 보이기 위한 요소의 세로간격 조정이 필요하다.

- 주로 박스를 건드리고, padding-top, padding-bottom 속성을 건드린다.

```css
/* 박스의 위 아래 간격 */
.box1{
    padding-top: 8px;
    padding-bottom: 8px;
}
.box3{
    padding-top: 40px;
    padding-bottom: 30px;
}
.box4{
    padding-top: 40px;
    padding-bottom: 30px;
}
.box5{
    padding-top: 15px;
    padding-bottom: 15px;
}
```

### 2) 요소의 가로 간격 조정

- 요소의 가로간격 조정도 필요하다.
- 마찬가지로 박스를 건드리고 padding을 이용한다.
- 간혹 가로 설정 되어있던 것이 100%를 넘어가서 화면이 깨지는 경우가 발생한다.
  - 이럴때는 box-sizing : border-box; 를 이용하여 내부로 밀어준다.

```css
    /* box3이랑 box4 왼쪽 오른쪽 간격 */
    .box3{
        padding-right: 50px;
        /* 100%가 넘으면 밑으로 밀리기 때문에 내부로 밀어주는 작업이 필요하다. 
        이게 box-sizing: border-box; 설정이다. */
        box-sizing: border-box;
        /* 안드로이드, ios 지원용 */
        -moz-box-sizing: border-box;
        -webkit-box-sizing: border-box;
    }
```

