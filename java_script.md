# java_script 21.08.24

```javascript
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>여러가지 테스트</title>
<script type="text/javascript">
var i = "출력";
alert(i); //팝업창 출력 - 모달 
console.log(i); 
document.write(i+ "<br>"); //브라우저 문서 출력
document.write(i+ "<br>"); //브라우저 문서 출력

var j = 10;
var k = 3;
document.write(j / k+ "<br>") ;
document.write(parseInt(j/k)+ "<br>") ;
/* 문자열, 실수 -> 정수 :String -> int : Integer.parseInt */
 
var s1= "100";//문자열
var s2= 100; //숫자(정수)

document.write( s1 == s2 + "<br>") ; // s1 과 s2 +<br> 같냐고 비교됨 false
document.write( (s1 == s2) + "<br>") ; // true,== 값 동일
document.write( (s1 === s2) + "<br>") ; // false, === 자료형 문자열, 숫자로 다르다
document.write( (typeof s1) +":" + (typeof s2)+ "<br>") ; // 타입 string:number 으로 출력 

//여러번 중복 선언- (실수해도 계속 값이바뀌게 됨)
var v1 = "var로 선언"; // v1 선언 + 초기화 
document.write( v1 + "<br>");
var v1 = "var로 선언-수정"; // v1 수정
document.write( v1 + "<br>");

String s1 = "var로 선언";
sop(s1);
String s1 = "var로 선언-수정"; ==> error s1 중복돼서 ==> String 삭제하고 s1 = "var로 선언-수정" 해야
sop(s1); 

//es 6 
 let v2 = "let으로 선언";
document.write( v2 + "<br>");
let v2 = "let으로 선언-수정";
document.write( v2 + "<br>"); //Uncaught SyntaxError: Identifier 'v2' has already been declared 중복금지 


 //es 6 - let 1번 선언 + 수정 가능
let v2 = "let으로 선언"; //중복선언 방지하기 위해 let 사용
document.write( v2 + "<br>");
v2 = "let으로 선언-수정";
document.write( v2 + "<br>");

//es 6 - const 1번 선언 + 수정 불가, 상수쓸때 사용해라
const v3 = "const로 선언";
document.write( v3 + "<br>");

v3 = "const로 선언-수정";
document.write( v3 + "<br>"); 


</script>
</head>
<body>

</body>
</html>
```



![variabletest](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/variabletest.JPG)

>alert(i); //팝업창 출력 - 모달 
>
>![image-20210823214859498](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/image-20210823214859498.png)
>
>console.log(i);  // 화면에 i 출력
>
>var v1  //여러번 중복 선언- (실수해도 계속 값이바뀌게 됨)
>
>let v2  //중복선언 방지하기 위해 let 사용, 재사용할때 사용
>
> const v3 //const 1번 선언 + 수정 불가, 상수쓸때 사용해라



```javascript
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>if else 구문</title>
<script type="text/javascript">
//키보드 입력 -html태그 input type = text | password
//키보드 입력 -js
var input = prompt("입력하세요"); // 출력 요구창이 뜸
document.write("<h1>" + input + "</h1>"); //입력한 내용이 h1 의 크기로 화면에 출력 , 취소시 null


//문자열 확인(true)/ 취소 (false)
var input2 = confirm("진짜 삭제할래?");
document.write("<h1>" + input2 + "</h1>"); // 

if(input >= 80 && input2 == true ) {
	document.write("<h1>80이상이고 삭제 대상입니다.</h1>");
}
else{ // input < 80 , input2 =false , 
	document.write("<h1>80이하 이거나 삭제 대상은 아닙니다.</h1>");
}


</script>
</head>
<body>

</body>
</html>
```



![ifelse_t](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/ifelse_t.JPG)

>var input = prompt("입력하세요"); // 출력 요구창이 뜸
>
>![image-20210823215525529](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/image-20210823215525529.png)

>var input2 = confirm("진짜 삭제할래?");
>
>![image-20210823215608671](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/image-20210823215608671.png)



```javascript
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>연습용 계산기</title>
<script type="text/javascript">
var data1 = prompt("정수 입력");
var op = prompt("연산자 입력");
var data2 = prompt("정수 입력");
	
document.write( (typeof data1) + "<br>"); //string, 실수 --> 정수 

if( !isNaN(data1) )  { //isNaN 숫자가 아닙니다. !isNaN 숫자입니다.
	document.write("숫자입니다<br>")
} else{
	document.write("숫자가 아닙니다<br>")
}

//모든 정수는 1로 나누어진다 = ? % 1 == 0
if( data1 % 1 ==0 )  { //isNaN 숫자가 아닙니다. !isNaN 숫자입니다.
	document.write("정수입니다.<br>")
} else{
	document.write("정수가 아닙니다.<br>")
}
		
		
data1=parseInt(data1);// parseInt로 정수로 변환해야 한다.
data2=parseInt(data2); 
document.write( (typeof data1) + "<br>");


if(op =="+"){
	document.write(data1 + data2 + "<br>");	 // 입력결과 100200 , parseInt 로 변환후 제대로 출력됨 , 
} else if(op =="-"){
	document.write(data1 - data2 + "<br>");	
}else if(op =="*"){
	document.write(data1 * data2 + "<br>");	
}else if(op =="/"){
	document.write(data1 / data2 + "<br>");	
}else {
	var userinput = confirm("잘못된 연산입니다")
	if (userinput) {
		document.write(data1 + data2 + "<br>");	
	} else{
		document.write("다시 연산내용 입력하세요<br>");	
	}
}




</script>

</head>
<body>

</body>
</html>
```



![cal_t](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/cal_t.JPG)

> * 최초에 prompt로 입력시, String 값이므로 parseInt 를 사용해 Int값으로 변환시켜야 한다.
> * java와 똑같이 if else 구문 사용 가능
> * if( !isNaN(data1) )  { //isNaN 숫자가 아닙니다. !isNaN 숫자입니다.}
> * if( data1 % 1 ==0 )  { // true 정수입니다. false 실수입니다.}

```javascript
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>배열 테스트입니다.</title>
</head>
<body>
<script type="text/javascript">
var a1 = [1, 3.14, true , "java script", [1,2,3] , undefined, null ];
a1[a1.length-1] = "수정";
a1[5] = "수정2";
a1[4][0]= 10; // 4번인덱스 [1,2,3]의 [0] 번째 인덱스가 10으로 변경 
a1[10] =  "10번인덱스"; //

document.write("배열 데이터 갯수 =" + a1.length + "<br>");
for(var i = 0; i <a1.length; i++ ) {
	if(a1[i] == undefined) {break;}
	document.write("<h3>" + a1[i]+ "</h3>");
}

document.write("<h3>반복문없이 배열 조회=" + a1.join(',') + "</h3>") ; //join쓰면 반복문없이 출력됨"  반복문없이 배열 조회=1,3.14,true,java script,10,2,3,수정2,수정,,,,10번인덱스 "


</script>
</body>
</html>

<!-- switch-case - 자바 스크립트 존재
	while, do-while- 자바스크립트 존재
	break, continue - 자바스크립트 존재.
	 -->
```



![fortest](https://raw.githubusercontent.com/dandaneee/html5/3d7c1b397c08262e331b6c904d013cbbd4fe9190/fortest.JPG)

> * join쓰면 반복문없이 출력됨  
>
>   반복문없이 배열 조회=1,3.14,true,java script,10,2,3,수정2,수정,,,,10번인덱스 
>
> * 배열내의 값은 수정이 가능하다.
>
> * 배열안에는 **int, double, String,  배열, 함수** 전부 가능하다!
>
> * JS 에서 **switch, case, while , do-while, break, continue** 사용 가능

