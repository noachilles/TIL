Date: 2024-07-13

## Intro
FlaskAPI가 무엇인지, 사용방법을 알아보고 Postman을 통해 응답 테스트를 진행함

## Postman
Test API 설계 개발, 테스팅을 할 수 있는 GUI 툴로, 프론트엔드 배제하고 API 요청에 대해 제대로 동작하는지 확인할 수 있음  
반드시 다운 받아야 하는 줄 알았으나 web version을 사용해볼 수 있어서 web상에서 진행했음  

오, 모든 입력을 다 끝마치고 나니 local 환경에서 test를 진행하려면 web app을 설치해야 한다는 알람이 뜸  
Postman에 정상적으로 접근할 수 없어서 그냥 삭제 후 html 파일을 만들어 직접 test 해보고 있다. local에서 벗어나 서버를 연동해주는 것이 Flask API의 기능이지만 우선 local에서 정상적으로 작동하는지 확인이 필요했다.  

결과적으로, HTML에 value 칸을 넣으면서 Binary Encoding한 값들은 categories로 나누어 연산해서 데이터를 생성하는 코드가 추가로 필요해 보였고, ```submit``` 버튼을 만들지 않아서 정상 작동되지 않았다 ㅎㅎ. 금방 알았으니 괜찮아.  

## FlaskAPI
FlaskAPI는 Django처럼 서버 운영 API이지만 Django에 비해 간단한 코드로 동작하고, 제공하는 기능이 가짓수가 좀 적다는 특징이 있다.  
FlaskAPI와 Django는 상황에 따라 어느것을 사용할지 선택하면 되고, 우리는 이번에 DB를 쓰지 않을 예정이라 FlaskAPI로 충분히 모델 학습&예측 결과를 보여줄 수 있다고 생각했다.  
Flask를 포함한 python file은 이름을 'app.py'로 설정해야 정상적으로 작동한다.  