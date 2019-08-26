## http 모듈
웹 서버가 하는 일은 요청과 응답을 하는 것이다.  
요청 메세지를 사용해야 사용자에게 적절한 웹 페이지를 제공할수 있다.  
응답 메시지를 사용하면 쿠키를 저장하거나 추출할수 있고 강제로 웹 페이지를 이동시킬수 있다.   
●요청 메세지와 응답 메세지를 직접 확인하는 방법  
F12를 눌러서 newwork 들어가서 보기   

## server객체
http 모듈에서 가장 중요한것이 server객체이다. creatServer()를 
사용하면 server를 생성할수 있다.   
listen => 서버 실행  
close => 서버 닫기  
server 객체에서 중요한것은 메소드 보다 이벤트입니다.  
이벤트 이름| 설명
이벤트 이름| 설명
----------|-----
request => 클라이언트가 요청할때 발생하는 이벤트    
 ## 쿠키 생성
쿠키는 키와 값이 들어 있는 작은 데이터 조각으로 이름,값, 파기 날짜와 경로 정보가 있다. 쿠키는 서버와 클라이언트에서 모두 저장하고 사용할수 있으며, 일정기간 동안 데이터를 저장할수 있다.  
resonse 객체를 사용하면 크라이언트에 쿠키를 할당할 수 있다.   

Method 속성을 사용해서 페이지 구분하기  
get요청인지 post 요청인지 서로 다른 페이지를 제공하는 것도 굉장히  
중요한 일이다. request 객체의 method 속성을 사용하면 요청 방식에 따라 페이지를 쉽게 구분할수 있다.   
request.method를 사용하면 웹을 요청하는 방식을 알수있다.   

## input값을 서버로 받아서 출력
html 파일  
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>로그인</h1>
    <form method = "post">
        <ul>
            <li>아이디</li><input type="text" name="data-a">
            <li>비밀번호</li><input type="text" name="data-b">
        </ul>
        <input type="submit">
    </form>
    
</body>
</html>  
post.js  
var http = require('http');
var fs = require('fs');

http.createServer(function(request,response){
    if(request.method == 'GET'){
        fs.readFile('page.2.html', function(error,data){
            response.writeHead(200, {'content-Type':'text/html'});
            response.end(data);
        });
    } else if( request.method == 'POST'){
        request.on('data',function(data){
            response.writeHead(200, {'content-Type':'text/html'});
            response.end('(<h1>'+data+'</h1>');
        });
    }
}).listen(52273, function(){
    console.log('server');
});    
로그인 html 이다. 아이디와 비밀번호를 쓰게 되면 그 값들이 페이지에 나오게 된다.  
## 쿠키생성
var http = require('http');

http.createServer(function(request,response) {
    var cookie = request.headers.cookie;

    response.writeHead(200, {'cont-Type':'text/html','set-cookie': ['name = Rin','region = seoul']});

    response.end('<h1>' + JSON.stringify(cookie)+'</h1>');
}).listen(52273, function(){
    console.log('server');
}); 
쿠키를 저장했고 현재 웹 페이지에서 화면에 출력 되지는 않지만, 쿠키가 생성은 되어 있다.  
  cookie의 속성은 문자열이다. 쿠키를 쉽게 사용할려면 문자열을 분해해야 한다.   
  쿠키분해 코드 )  
  var http = require('http');
http.createServer(function(request,response) {
 if(request.headers.cookie) {
     var cookie = request.headers.cookie.split(';').map(function (element) {
         var element = element.split('=');
     return {
             key : element[0],
            value: element[1]
         };
    });
    response.end('<h1>' + JSON.stringify(cookie)+'<h1>');
} else{
    response.writeHead(200, {
        'cont' : 'text/html', 'set':['name = minyoung','region = seoul']
    });
    response.end('<h1>쿠키를 생성했습니다.</h1>');
}
}).listen(52273, function(){
    console.log('server');
});
쿠키를 분해할수 있다.   
다음부터는 이렇게 코드를 짜지 않고 express를 사용하면 쿠키를 
분해해준다. 

