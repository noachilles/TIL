Date: 2024-07-29

## Contents
Selenium을 사용한 웹크롤링 1

Selenium의 활용법에 대해 이해한 내용을 작성  
이후에 Selenium 활용을 위해 필요한 동작 순서를 지정하고 수행

## Selenium  
Selenium은 동적 웹크롤링에 사용되며, 동적 웹크롤링이란 홈페이지로부터 데이터를 수집하는 방식인 크롤링 기법 중 페이지 조작시에도 도메인이 변하지 않는 홈페이지에 적용하는 것을 의미한다.  

Selenium은 pip 혹은 conda 명령어로 install 할 수 있고 web driver를 함께 설치해서 활용해야 한다.  

설치 이후 홈페이지에서 웹사이트의 html코드상 특정 부분에 해당하는 id와 class를 찾아 이에 대한 조작 코드를 작성해 수행함  

## Selenium 활용  
1. Conda 생성 후 Selenium과 Webdriver 설치  
2. 서울특별시교육청 도서 검색 결과 페이지에 대한 html 코드 상 페이징 부분 id나 class를 추출  
3. url을 불러와 필요한 기능을 수행하는(페이지 넘김, 10페이지당 '다음' 버튼 누름)  
4. 수집한 데이터 처리(따로 정리가 필요한 부분)