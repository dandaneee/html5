```javascript
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>게시물 리스트 입니다.</title>
<style type="text/css">
body{
background-color: aqua;
}
.box {
margin:auto;
border: 4px;
border-style: solid;
border-color:blue;
border-radius: 15px;
width: 500px;
height: 50px;
box-shadow: -7px -7px 5px #FF0000;
}
h1 {
text-align: center;
line-height: 5px;
font-size: 40px;
font-weight: bold;
color:green;
text-shadow: 5px 5px 5px green;
}
table{
text-align: center;
display:table;
margin:auto;
border-style:solid;
border-collapse:collapse;
border-left-width:medium;
border-right-width:medium;
border-top-width:medium;
border-bottom-width:medium;
border-color: pink;
}
th,td{
border: 3px solid pink;
}
.title {
background-color: gray;
}

h3 {
text-align: center;
}

tobody{
border-left: thin;
}
 div{
text-align: center;
} 
</style>

</head>
<body>
<div class="box">
<h1>boardlist를 출력합니다.</h1> </div><br>
<form action="boardsearch.html">
<select >
<option> 제목 </option>
<option> 내용 </option>
<option> 작성자 </option>
</select>
검색어:<input type="text"> 
<a href="/boardserch.html"></a>
 <a href="/boardserch.html"><input type="submit" value="검색"></a>
 <input type="hidden" name="role" value="admin"><br>
<br></form>
<br>

<table border=4>
<p><tr class="title"><td>번호</td><td>제목</td><td>작성자</td><td>조회수</td></tr></p>
<tr><td>1</td><td><a href="/boarddetail.html" style="text-decoration: none">제목1</td></a><td>작성자1</td><td>0</td></tr>
<tr><td>2</td><td><a href="/boarddetail.html" style="text-decoration: none">제목2</td></a><td>작성자2</td><td>0</td></tr>
<tr><td>3</td><td><a href="/boarddetail.html" style="text-decoration: none">제목3</td></a><td>작성자3</td><td>11</td></tr>
<tr><td>4</td><td><a href="/boarddetail.html" style="text-decoration: none">제목4</td></a><td>작성자4</td><td>22</td></tr>
<tr><td>5</td><td><a href="/boarddetail.html" style="text-decoration: none">제목5</td></a><td>작성자5</td><td>11</td></tr>
</table>
<br>

<h3>페이지 번호</h3><br>
<div>
<a class="list" href="/boardlist.html">1</a>
<a class="list" href="/boardlist.html">2</a>
<a class="list" href="/boardlist.html">3</a>
<a class="list" href="/boardlist.html">4</a>
<a class="list" href="/boardlist.html">5</a>
</div>
</body>
</html>
```

### 과제 

![image-20210822173313425](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822173313425.png)



### 내가 한것

![image-20210822173437994](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822173437994.png)


### 까다로웠던 내용:

> 1.  **"boardlist를 출력합니다." 칸맞추기: **
>
>    처음에 <div> 로 묶어놓고 하니 글자가 바닥에 안가까워지고 거의 가운데 위치하여 
>
>    padding, boarder, margin 속성으로 하는줄 알았으나 계속 실패
>
>    --> <div>를 box로 따로 class 지정하고, 텍스트내용은 h1 에 style을 줌, 
>
>    ​		그리고 box height =50px 이고, h1의 font-size=40px로 10px의 여유가 있으므로 
>
>    ​		line-height 를  이용하여 최대한 과제와 맞는 위치에 지정
>
> 2.  **제목에만 음영 주기  :  **
>
>     이부분은 첫번째 줄 <tr> 에 class"title"로 따로 지정하여
>
>    .title {background-color :gray; } 로 해결, 이밖에 다른 줄도 tr 에 class를 따로 지정하면 background color는 쉽게 변경 가능하였다.
>
> 3.  **테이블 모으기 : **

    ![image-20210822175825220](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822175825220.png)

>    처음엔 이런식으로 빈칸이 생겨 margin을 사용하는줄 알았으나, 
>
>    border-collapse:collapse; 를 사용하여 좁은 간격들 없어짐
>
> 4.  **테이블 내부 <a> 링크 밑줄 없애기 : **
>
>     따로 class 지정을 해도 안없어짐
>
>     --> <a href="/boarddetail.html" style="text-decoration: none">
>
>     처럼 <a> 내부에 style 을 따로 지정해 해결
>
> 5.   **번호 링크들 가운데 위치 : **  
>
>     ​	위에처럼 따로 <a> 내부에 style을 줘도 되나, 이건 테이블 밖에 있어
>
>     ​	-->   / <div> 로 묶어버리고 거기에 text-align: center 를 입력하여 해결  
>
> 6.   **테이블 내부 선 굵기 문제 : **

     ![image-20210822203126041](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822203126041.png)

>     이런식으로 외부 테두리만 굵게 표시되고 나머지 내부 cell의 칸들은 얇은 선으로 표시됨,
>
>     내부 tr,td 에 class지정, <div>로 구간 묶어서 border 위치별로 thick 지정을 했는데 죽어도 안바뀜

    ![image-20210822203401774](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822203401774.png)

>     tr,td{ border: 3px solid pink; } 스타일을 사용하니 모든 thtd의 테두리가 굵게 표시가 됐다.

    ![image-20210822204524296](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822204524296.png)

>     td{border: 3px solid pink;}  를 사용해도 동일,

    ![image-20210822204631197](https://raw.githubusercontent.com/dandaneee/html5/7d71f522f787622850a001e75c32d13564c31d28/image-20210822204631197.png)

>     tr{border: 3px solid pink;}  를 사용했을땐 가로만 굵은 그래프가 됐다.
>
>     
>
>     
>
>     ##  배운점: 
>
>     - 각 명령어들 옆에 직접 style= "" 을 사용하여 각각의 스타일을 넣을 수 있다
>
>     - class를 지정하여 <head> </head>내부에 <style type="text/css"> 를 사용하여 
>
>       class별, 명령어별 스타일을 묶어서 지정할 수 있다.
>
>     - line-height 를 사용하면 박스의 칸 상관없이 위치를 편집할 수 있다.
>
>     - 테이블의 선 같은경우엔 td{border: 3px solid pink; }를 사용하면  모든 행렬을 편집 할 수있다. 이때 저 명령어는 table과 별도로 지정해 주어야 한다.
>
>     - div는 큰 박스형태의 구역으로 묶이는것, 레이아웃 분할(division)
>
>       ![image-20210822205602083](C:/Users/Robot/Documents/md_images/image-20210822205602083.png)
>
>       
>
>     ![image-20210822205620286](C:/Users/Robot/Documents/md_images/image-20210822205620286.png)
>
>     - span은 특정부분을 inline형태로 묶는다. 내용 정도만.
>
>     ![image-20210822205822043](C:/Users/Robot/Documents/md_images/image-20210822205822043.png)
>
>     ![image-20210822205839221](C:/Users/Robot/Documents/md_images/image-20210822205839221.png)
>
>     ![image-20210822205923595](C:/Users/Robot/Documents/md_images/image-20210822205923595.png)
>
>     - <p>는 <div>나 <span>에서 내용을 작성할 경우 단락을 구분한다.

