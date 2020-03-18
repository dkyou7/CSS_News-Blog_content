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

