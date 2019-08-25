# node.js 프로그래밍

## 스레드
○스레드는 프로세스 내부에서 실행되는 실행 흐름 단위를 의미한다.

스레드 장점<br>
   -사용자에게 응답을 빨리 해야 할 때
   <br>
	-동시에 작업을 완료해야 할 때
  <br>
  사용 경우
	-네트워크 웹 서버 또는 데이터베이스 통신
<br>
	시간이 오래 걸리는 작업  
<br>
단점
<br>
	-많은 스레드로 코드 실행을 하게 되면 복잡해지고 버그가 발생할수 있음
<br>
	-삭제하려면 문제와 처리방법을 알아야 된다.

서버개발화경에서 자바스크립트의 가장 큰 단점은 속도가 느리다는 점입니다.
서버개발환경에서는 속도가 빨라야 한다. 
node.js는 대규모 네트워크 애플리케이션을 개발할수 있다. 

## ▶일반 웹서버와 node.js의 차이점
기존웹서버는 대부분 스레드를 기반으로하는 동기방식을 사용한다.
node.js 이벤트를 기반으로 하는 비동기 방식을 사용한다.

### 이벤드 기반 비동기 방식
스레드 기반 동식
-이벤트를 사용하므로 빠른 속도로 일처리를 한다.
많은 양을 처리해도 몸은 하나이므로 메모리 사용량과 같은 시스템 리소스 사용량에는 변화가 거의 없다.
대규모네트워크 프로그램을 개발하기 적합한 형태이다. 하지만 한번 잘못되는 프로그램 전체에 문제가 발생할수 있다. 

## node.js 장단점
### 장점
1.자바스크립트를 사용한다.
<br>웹 개발자가 쉽게 접근할수 있다.<br>
2. 구글이 만든 자바스크립트 엔진을 사용한다.<br>
구글이 없어지지 않으면 계속해서 속도가 빨라진다.

### 단점
자바스크립트엔진이 아무리 빨라도 c/c++를 사용하는 애플리케이션보다 느리다.

## node.js 개발환경 구축
버전이 2가지가 있다.

1. current 버전 <br>
변화가 일어나고 있는 상태의 버전이다. 안정적이지는 않다.
6개월마다 새로운 버전이 나온다.
2. LTS 버전
current 버전이 6개월이 지나면 LTS 버전으로 바뀐다. 

### 기본 명령어
cd 폴더명 특정 폴더로 이동합니다.<br>
dir 현재 폴더에 있는 내용을 출력합니다.

REPL - 한줄씩 코드를 입력해 실행해 볼수 있는 공간이다.
나가는것은 ctrl+c를 두번 누르기

## 파일만들어서 출력해보기
visual basic code에서 터미널을 연다. <br>
터미널 여는법<br>
ctrl+~표시가 있는것
앞에 node를 쓰고 파일 이름을 적는다.

## 웹서버 만들기
var http = require('http');
//웹 서버를 만든다.
//서버 만드는 함수 createServer
http.createServer(function (request,response) {
    //대답을 html로 쓰기.
    response.writeHead(200, {'Content-Type' : 'text/html' });
    //hello world 쓰기
    response.end('<h1>Hello world...!</h1>');
}).listen(52273, function(){
    console.log('Server running at http://127.0.0.1:52273/');
});

## 전역개체
### 전역변수
웹 브라우저에서 동작하는 자바스크립트의 최상위 객체는 window입니다.
window객체는 웹 브라우저 자체와 관련된 속성과 메서드를 가지고 있습니다.
하지만 node.js는 웹 브라우저에서 동작하는것이 아니므로 window객체가 존재하지 않는다.

__filename => 현재 실행 중인 코드의 파일 경로를 나타냅니다.
__dirname =>  현재 실행 중인 코드의 폴더 경로를 나타냅니다.

console.log('filename',__filename);
console.log('dirname',__dirname);
=====================================<br>
filename C:\Users\user\Desktop\Lapio\node.basic.js<br>
dirname C:\Users\user\Desktop\Lapio
파일의 경로 위치를 알려준다.

console => 콘솔 화면과 관ㄹ녀된 기능을 다루는 객체입니다.
exports => 모듈과 관련된 기능을 다루는 객체 입니다.
process => 프로그램과 관련된 기능을 다루는 객체입니다.

## console
콘솔 화면과 관련된 기능을 다루는 객체입니다.

log() -> 출력하는것
time() -> 시간 측정 시작한다.
timeEnd() -> 시간 측정을 종료합니다.

## 출력 글자에 색 적용하기
console.log('\u001b[45m', 'hello world..!');
console.log('\u001b[40m', 'hello world..!');
console.log('\u001b[31m', 'hello world..!');'

[![출력결과](./Lapio/캡쳐.png)]

## process 객체
process 객체는 프로그램과 관련된 정보를 나타내는 객체이다. 웹 브라우저에서 작동하는 자바스크립트에는 존재하지 않는 node.js 만 가지고 있는 객체이다. 
속성 이름 | 설명
-----|---------
argv 실행 매개변수를 나타냅니다.

env  컴퓨터 환경과 고나련된 정보를 나타냅니다.

version  Node.js 버전을 나타냅니다.

versions  node.js와 종속된 프로그램 버전을 나타냅니다.

arch  프로세서의 아키텍처를 나타냅니다.

platform 플랫폼을 나타냅니다.


 exit -> 프로그램이종료가 되었음을 의미한다. 0으로 끝나면 정상적으로 
 완료 된것이고, 1이면 비정상으로 끝난것이다. 

 ## exports 객체와 모듈
 모듈이란?<br>
 기능을 쉽게 사용하고자 메서드와 속성을 미리 정의해 모아 놓은 것이다.   
 모듈을 생성할대는 exports 객체를 사용한다.   
 export문은 모듈에서 함수,객체,원시 값을 내보낼대 사용한다. 다른 프로그램에서 import 문으로 가져가 쓸 수 있습니다.  
 모듈은 선언 여부와 관계 없이 엄격 모드입니다. export 문을 HTML 내장 스크립트에 사용할 수는 없습니다.

 다른 자바스크립트 파일에서 추출할때 require() 함수를 사용한다.
 ### ★모듈파일을 읽어서 다른 파일에서 실행하기
덧셈과 곱셈을 하는 프로그램만들기

## node.js 모듈 알아보기

## OS 모듈
os모듈은 애플리케이션을 만들때 사용하지는 않지만, 기본적인 사용을법을
익히기에는 매우 좋다.

기존에 있는 모듈을 알고 싶으면 node.js문서에 들어가면 모듈의 종류와   
모듈로 할수 있는 함수들이 나와있다. 모듈의 종류는 node.js에 있고 node,js는 홈페이지에서도 찾아볼수 있다.   

### url모듈
모듈을 가져오는 방식은 모두 똑같다.  
var url = require('url');
내가 원하는 웹페이지의 주소를 가지고 오면 기본정보들을 알수 있다.

### Query String 모듈
 url 객체의 쿼리와 관련된 모듈방법이다. 
 querystring은 url의 모듈이 있어야한다.

 ###  util 모듈
  보조적인 기능을 가지고 있다.
  문자열들을 조합합고 출력해준다. c언어로 print 같은 느낌이다.
  예제)
  var util = require('util');
var multi = util.format('%d * %d = %d', 150,3,150*3);
console.log(multi);

### crypto 모듈
 해시생성과 암호화를 수행하는 모듈이다.  
해시란 2가지 뜻으로 볼수있다.  
  1.키와 값을 갖는 자료형 :  대표적으로 자바스크립트의 객체가 해시이다.  
  2. 전자지문    

  원본 문자열이 조금이라도 다르면 해시 형태가 굉장히 많이 달라진다.   
  해시는 원래 값으로 되돌리는것이 불가능하다.  
  해시는 보안에서 많이 사용된다. 해시란 암호화된 문자이다. 
  ★원래상태로 되돌릴수 없는것은 해시
  ☆원래상태로 되돌릴수 있는것은 암호이다.

  ### 실습_암호화, 해제
  var crypto = require('crypto');

 var key = '아무도 알지 못하는 키';
 var input = 'password';

 var cipher = crypto.createCipher('aes192',key);
 cipher.update(input, 'utf8', "base64");
 var cipheredoutput = cipher.final('base64');
 
 var decipher = crypto.createDecipher('aes192', key);
 decipher.update(cipheredoutput, 'base64' ,'utf8');
 var decipheroutput = decipher.final('utf8');

 console.log('원래 문자열 : ' + input);<br>
 console.log('암호화: ' + cipheredoutput);<br>
 console.log('암호화 해제: ' + decipheroutput);<br>

출력결과
<br>
해제: password
암호화: o3FigGZaKVru55t7OVyd0Q==
해제: password
  
### file system 모듈
파일 시스템 모듈은 다른 모듈과 함께 사용된다.   
기본적인 파일 메소서드 fs.readFileSync = > 파일 읽기이다. 
readfile()은 콜백함수를 이용해서 하는 것이다.   
예) function(error,date){
  console.log(date);
}  
error이면 파일에 null 이라고 뜨고, date이면 파일을 읽어드린다. 참이면
파일을 읽어드리는 것  
 sync가 붙으면 동기 처리이고 안붙으면 비동기 이다.  
 ### 예외 처리
 동기 처리를 하는 메서드는 try catch 구문을 통해서 예외 처리를 합니다.  
 파일의 메서드에다 추가해주면 된다.  
 callback함수란 비동기시기 처리 방법이다.  


 try catch란?  
 try블록이 성공하기 원하고, 만약 성공하지 못했을 경우에 catch블록으로 넘어가는 것이다.   
 try블록 내의 명령문이 예외를 throw하면 제어가 catch절로 즉시 이동하게 된다. 무조건적 catch문과 조건적 catch문이 있다.   
 예) var fs = require('fs');

try{
    var data = fs.readFileSync('textfile.txt','utf8');
    console.log(data);
} catch (e) {
    console.log(e);
}

try{
    fs.writeFileSync('textfile.txt','hello world','utf8');
    console.log('complete');
} catch (e) {
    console.log(e);
}  
우리가 사용하는것은 무조건적 catch문이다. catch문에 매개변수안에 e밖에 없기 때문이다. js에서 error는 null이다. 아무것도 없음을 뜻한다.

조기 리턴이란? 오류 처리 부분을 오류만 출력하고 바로 끝내는 간단한 코드로 구성하는 것이다.  
오류를 검출하기 위해서 if,else문을 사용해서 하는것이 아니라 바로 if로   
return 하는 형식으로 하여서 else문을 사용하지 않고 바로 리턴을 했다.   
★ 기본내장 모듈에서 가장 중요한 것은 바로 기본적인 모듈을 사용할때는
require()를 사용하면 된다는 것이다.   
