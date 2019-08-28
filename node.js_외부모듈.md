# 외부 모듈
node.js는 모듈을 공유하기가 쉬운 환경이라서 오부 모듈 공유가 굉장히 활발하다.  

## ejs 모듈

외부 모듈 ejs,jade가 있다. 먼저 ejs살펴보기  
템플릿 엔진 모듈로 특정 형식의 문자열을 html 형식의 문자열로 변환한다.  
＠ 외부모듈이기 때문에 꼭 터미널에서 외부모듈을 설치해주어야 한다.  
npm install ejs , npm install jade 을 설치해주어야 한다.  
render() 라는 메서드를 사용해서 ejs의 문자열을  html로 바꿔주는 메서드이다.  

데이터를 전달하는 방식도 매우 쉽다. render()하고 매개변수 2번째에 데이터 전달 메세지를   적어주면 된다. 
ejs모듈과 같은 템플릿 엔진은 동적 웹 페이지를 생성할때 사용된다.  
 html페이지 소스는 한번 생성하면 절대 변하지 않는다.   
그래서 html 페이지를 제공하는 서버는 항상 같은 데이터를 클라이언트에게 보여준다.  
ejs는 동적으로 구성되어 있기 때문에 항상 올때마다 새로운 바뀐 정보들을 제공받을 수 있다.  
## jade 모듈
jade 모듈도 템플릿 엔진입니다. node.js 에서 가장 많이 사용되는 웹 프레임 워크가   
express인데 ejs 모듈과 jade 모듈을 주로 사용해서 꼭 알아야 한다.   
jade 파일은 주석 처리를 // 한다.  
div는 header로 한다.   
## 서버실행 모듈
지금까지 본 모듈은 지역모듈이고 파일 내부에서 requite()함수로 추출한다.   
지금까지 본 모듈은 터미널에서 바로 사용할수 있는 함수이다. 
 ☆ supervisor 모듈
 우리가 실행을 종료한 후에도 다시 명령어을 입력하는 이유는 실행중인 스크립트에는 영향을 끼치지 못한다.  
 그렇지만 supervison 모듈은 파일의 변경 사항을 자동으로 인식하고 실행을 종료시킨 후에도 다시 실행 됨 

 ★json파일을 사용한다. start 을 넣어주면 실행하게 해준다.   

{
"name" : "test",
"version" : "1.0.0",
"description" : "",
"main" : "index.js",
"scripts" : {
    "start" : "echo \"Start Test\"",
    "test" : "echo\"Error: no test specified\" && exit 1" 
},"author" : "",
"license": "ISC"
}  // echo -> 출력할수 있는 것이다.  

버전을 설치 할때 @한다음에 두에 버전을 입력한다. 예) npm install ejs@2.4.1  

npm install 다른 버전의 모듈을 설치하면 지금 실행하는 json파일에 있는 곳에 node_modules가 설치된다. 



