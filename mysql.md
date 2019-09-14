# mySQL 데이터베이스

데이터 베이스란?
데이터를 반영구적으로 보관할수 있는 공간으르 웹에서 가장 핵심이 되고 있다.

SQL  
관계형데이터베이스 관리 시스템안에서 데이터를 관리하는데 사용하는 프로그래밍언어이다.  
◆ 웹 사용자 정보를 저장할수있는 3가지 방법  
1. 쿠키  
2. 세션  
3. 데이터베이스이다.  

## 쿼리 문장
mysql에서 데이터배열을 생성할때는 create database company;를
쓰면 데이터베이스가 생성된다.  
테이블 생성할때의 자료형  
varchar -문자열 ,int-정수숫자, double-실수숫자    필드 속성에는 not null -> 반드시 입력해야 하는 필드입니다.  
auto-increment -> 자동으로 숫자가 증가하게 만듭니다.  
primary key -> 기본키로 지정한다.    
MYSQL에서는 대소문자도 구분해서 해야한다.   

★ mysql 데이터베이스 생성  
->create database 필드이름;(필드이름 처음은 대문자)    
->use node
★mysql 테이블 생성  
-> create table 필드이름(
    -> 여러가지 적을면 됨 id 등 등
);  
★만든 테이블에 데이터 저장  
-> insert into 테이블명(필드) values (값,값);

★데이터 조회   
-> select 필드 form 테이블  (모든 필드를 하고 싶으면 *)  

★조건 검사  
select 필드 form 테이블   
where 조건문  

 ★데이터 정렬  
 -> ORDER BY 필드명;  

 ★특정 위치에 있는 데이터 선택  
 -> SELECT * FROM 테이블명 LIMIT 값;  
 LIMIT 2로 하게 되면 상위데이터를 값만큼 선택해준다.  
 
  
