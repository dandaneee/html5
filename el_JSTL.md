### memberinsert.jsp

```javascript

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<script src="jquery-3.2.1.min.js"></script>
<script>
</head>
<body>

<%
//request.setCharacterEncoding("utf-8");
String memberid = request.getParameter("memberid");
String password = request.getParameter("password");
String membername = request.getParameter("membername");
String email = request.getParameter("email");

MemberVO vo = new MemberVO();
vo.setMemberid(memberid);
vo.setPassword(Integer.parseInt(password));
vo.setMembername(membername);
vo.setEmail(email);

%>
아이디:<%=vo.getMemberid() %><br>
암호:<%=vo.getPassword() %><br>
이름:<%=vo.getMembername()%><br>
이메일:<%=vo.getEmail() %><br>
```

> ##### java문법 그대로 사용
>
> * 입력받은 parameter값들을 각 String 객체에 입력
> * MemberVO 객체인 vo 에 입력받은 값들을 저장
> * <%= 출력값 나타내는 el문법으로 화면에 출력



```javascript
 <jsp:useBean id="vo" class="vo.MemberVO"/>
 <jsp:setProperty property="memberid" name="vo" value= "<%=request.getParameter(\"memberid\")%>" />
 <jsp:setProperty property="password" name="vo" value="<%=Integer.parseInt(request.getParameter(\"password\"))%>" />
 <jsp:setProperty property="password" name="vo"  value="<%=Integer.parseInt(request.getParameter(\"password\") )%>" />
 <jsp:setProperty property="membername" name="vo" value="<%=request.getParameter(\"membername\")%>" />
 <jsp:setProperty property="email" name="vo" value="<%=request.getParameter(\"email\")%>" /> 
 <!-- 
 jsp에선 value값에 ""를 써야만 하는데 getParameter("") 으로 이중다움표가 사용됐으므로 역슬래시 \ 를 사용해서 쓸수있게 한다.
  %>" 쓸때 띄어쓰기 들어가면 에러발생했다
 -->
```

> ##### jsp 문법사용
>
> ```javascript
> <jsp:useBean id="vo" class="vo.MemberVO"/>
> ```
>
> * class="vo.MemberVO"  >>   폴더의 MemberVO에서 
> * id="vo" >>	 vo 객체를 생성하겠다.
>
> ```javascript
> <jsp:setProperty property="memberid" name="vo" value= "<%=request.getParameter(\"memberid\")%>" />
> ```
>
> * property="memberid" == set.Memberid 
> * name="vo" >> vo객체 타입의
> * value= "<%=request.getParameter(\"memberid\")%>"  >> parameter로 입력된 memberid 를 value로 저장하겠다 
> *  jsp에선 value값에 ""를 써야만 하는데 getParameter("") 으로 이중다움표가 사용됐으므로 역슬래시 \ 를 사용해서 쓸수있게 한다.
>     %>" 쓸때 띄어쓰기 들어가면 에러발생했다



```javascript
<jsp:useBean id="vo" class="vo.MemberVO"/>
 <jsp:setProperty property="memberid" name="vo" param="memberid" />
 <jsp:setProperty property="password" name="vo" param="password" />
 <jsp:setProperty property="membername" name="vo" param="membername" />
 <jsp:setProperty property="email" name="vo" param="email" />

```

> ##### jsp 사용/ vo객체이름과 property 이름 동일하게 설정 
>
> ```javascript
> 	 <jsp:setProperty property="memberid" name="vo" value= "		<%=request.getParameter(\"memberid\")%>" />
>     ---------------------------------------
> (비교)<jsp:setProperty property="memberid" name="vo" param="memberid" />
> ```
>
> * property 값을 vo 객체이름과 동일하게 설정, param="memberid"  추가
> * <span style="color:red">**vo안에 객체이름과 property 이름이 같게** 설정하면 편하게 사용가능하고 다르다면 param을 통해 추가로 읽을수있게해준다</span>

```javascript
<jsp:useBean id="vo" class="vo.MemberVO"/>
 <jsp:setProperty property="memberid" name="vo" />
 <jsp:setProperty property="password" name="vo" />
 <jsp:setProperty property="membername" name="vo" />
 <jsp:setProperty property="email" name="vo"  />
```

> * property="" 과 form input request parameter 동일하면  param 생략 가능

```javascript
<jsp:useBean id="vo" class="vo.MemberVO" scope="page" />
<jsp:setProperty property="*" name="vo"/>
```

> ##### property="*"
>
> * *= property에 html과 같은 name 을 입력한다.
> * 나머지 property들 vo와 같은 객체의 이름을 가진다.

```javascript
<h1> 액션 태그로 읽어옵니다</h1>
 <jsp:getProperty property="memberid" name="vo"  />
 <jsp:getProperty property="password" name="vo" />
 <jsp:getProperty property="membername" name="vo" />
 <jsp:getProperty property="email" name="vo"  />
 
 <h1> el로 읽어옵니다</h1>
 ${ vo.memberid } <!-- vo.memberid=  vo.getMemberid() -->
 ${ vo.password }
 ${ vo.membername }
 ${ vo.email }

 <h1> 자바 문장으로 읽어옵니다</h1>
 <%=vo.getMemberid() %>
 <%=vo.getPassword() %>
 <%=vo.getMembername() %>
 <%=vo.getEmail() %>
```

> ##### 위에서 저장된값들 액션태그, el , 자바로 출력
>
>   page: 현재페이지에서만 vo 사용할거다, 공유 안할거다
>   request: forward 된곳에서도 사용할수 있게 해주겠다
>   session: 같은 브라우저내에서 사용할수있게 해주겠다.
>   application: 브라우저가 닫혀도 사용할 수 있게 해주겠다.

--------------------



### el_test4.jsp

```javascript
<% 
	String[] colors={"빨강", "노랑", "초록", "파랑"};
	pageContext.setAttribute("colors", colors);
%>

<h1> el로 배열 내용을 출력합니다.</h1>
<h3>${ colors[0]  }</h3>
<h3>${ colors[1]  }</h3>
<h3>${ colors[2]  }</h3>
<h3>${ colors[3]  }</h3>
```

> ##### java로 배열 저장 -> el로 출력
>
> * ${ colors[0]  } >> ${name[index]} 의 형식

```javascript
<% 
	ArrayList<MemberVO> list =new ArrayList<MemberVO>(); //list = [0] 각 index에 데이터가 저장됨
	list.add(new MemberVO("MEMBER20",1541 ,"왕말랑", "A@B.COM") );
	list.add(new MemberVO("MEMBER30",4153 ,"왕단단", "B@B.COM") );
	
	pageContext.setAttribute("el_list", list);
%>

<h1> el로 회원정보를 출력합니다.</h1>
<h3>${ el_list[0].memberid  }</h3> 
<h3>${ el_list[1].memberid  }</h3> 
<h3>- ${ el_list[1].memberid  } -</h3><!--null  -->
<h3>- ${ el_list[1].memberid  } -</h3><!--null  -->

```

> ##### Arraylist 에 저장 후 el로 출력
>
> * ${ el_list[0].memberid  } >> ${name[index].출력할정보}  
>   * el_list[0] =MemberVO , el_list[0].memberid = MemberVO 의 첫번째 id

```javascript
<% 
	HashMap<String, MemberVO> map =new HashMap<String, MemberVO>(); // map = key & value
	map.put("map1" , new MemberVO("MEMBER20",1541 ,"왕말랑", "A@B.COM") ); 
	map.put("map2" , new MemberVO("MEMBER30",4153 ,"왕단단", "B@B.COM") );
	
	pageContext.setAttribute("el_map", map);
%>

<h1> el로 회원정보를 출력합니다.</h1>
<h3>${ el_map.map1  }</h3> 
<h3>${ el_map.map2  }</h3> 
```

> ##### HashMap el 로 출력
>
> ```javascript
> HashMap<String, MemberVO> map =new HashMap<String, MemberVO>();
> 	map.put("map1" , new MemberVO("MEMBER20",1541 ,"왕말랑", "A@B.COM") );
> ```
>
> *  map = key & value
> *  map1 이라는 String에 데이터 저장
>
> ```javascript
> ${ el_map.map1  }
> ${ el_map.map1.memberid  }
> ```
>
> * 저장된 "MEMBER20",1541 ,"왕말랑", "A@B.COM" 출력
> * memberid="member20" 만 출력

------------------------

### jstl_test1.jsp

```javascript
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
    
 <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<script src="jquery-3.2.1.min.js"></script>
</head>
<body> <!--c의 set, remove , out태그  -->
<% String jspvar= "jsptest";
//pageContext.setAttribute("name", japvar);
%>
<c:set var="name" value= "<%=jspvar %>" /> 
<c:set var="name" value= "jstltest" /> <!-- 변수를jsp와 공유하지 않는다, 변수선언 -->
${name } <br> <!-- el과 공유한다 => jstl은 el을 편하게 쓰기 위해  -->


<h1><c:out value="100"/> </h1> <!-- 브라우저에 출력해주는것 -->
<h1><c:out value="${name }"/> </h1>

<c:remove var="name"/>
<h1>${empty name }</h1> <!-- name변수가 없느냐 = true -->

</body>
</html>
```

> ```javascript
> <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
> ```
>
> * jstl을 사용하기위해 선언한다.
>
>  ```javascript
>  <% String jspvar= "jsptest"; %>
>  <c:set var="name" value= "<%=jspvar %>" /> 
>  <c:set var="name" value= "jstltest" /> 
>  ${name } <br> 
>  ```
>
> * **변수를jsp와 공유하지 않는다**
> * <span style="color:red">**c:set**</span> 변수선언
> * el과 공유한다 => jstl은 el을 편하게 쓰기 위해  
>
> ```javascript
> <h1><c:out value="100"/> </h1> 
> <h1><c:out value="${name }"/> </h1>
> ```
>
> * <span style="color:red">**c:out** </span> 브라우저에 출력해주는것
>
> ```javascript
> <c:remove var="name"/>
> <h1>${empty name }</h1> 
> ```
>
> * <span style="color:red">**c:remove** </span> 저장된 변수값 삭제
> * name변수가 없느냐 = true



### 요약

> * <span style="color:red">**vo안에 객체이름과 property 이름이 같게** 설정하면 편하게 사용가능하고 다르다면 param을 통해 추가로 읽을수있게해준다</span>
>
> * property="" 과 form input request parameter 동일하면  param 생략 가능
>
> * jsp에선 value값에 ""를 써야만 하는데 getParameter("") 으로 이중다움표가 사용됐으므로 역슬래시 \ 를 사용해서 쓸수있게 한다.
>   %>" 쓸때 띄어쓰기 들어가면 에러발생했다
>
> * ##### property="*"
>
>   * *= property에 html과 같은 name 을 입력한다.
>   * 나머지 property들 vo와 같은 객체의 이름을 가진다.
>
> * page: 현재페이지에서만 vo 사용할거다, 공유 안할거다
>   request: forward 된곳에서도 사용할수 있게 해주겠다
>   session: 같은 브라우저내에서 사용할수있게 해주겠다.
>   application: 브라우저가 닫혀도 사용할 수 있게 해주겠다.
>
> * ##### java로 배열 저장 -> el로 출력
>
>   * ${ colors[0]  } >> ${name[index]} 의 형식
>
> * ##### Arraylist 에 저장 후 el로 출력
>
>   * ${ el_list[0].memberid  } >> ${name[index].출력할정보}  
>     * el_list[0] =MemberVO , el_list[0].memberid = MemberVO 의 첫번째 id
>
> * **HashMap el 로 출력**
>
>   * ${ el_map.map1  } >> ${name}.String.출력할정보}
>     * el_map.map1 = MemberVO, el_map.map1.memberid = MemberVO 의 첫번째 id
>
> * <span style="color:red">**c:set**</span> 변수선언 , **변수를jsp와 공유하지 않는다** , el과 공유한다
>
> * <span style="color:red">**c:out** </span> 브라우저에 출력해주는것
>
> * <span style="color:red">**c:remove** </span> 저장된 변수값 삭제
