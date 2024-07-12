Date: 2024-07-06

## Intro
프로젝트 진행을 위해 데이터 전처리 중, 범주형 변수 인코딩이 필요함

## UNIQUE()와 value_counts()
unique()는 한 column이 어떤 값을 포함하는지, value_counts는 unique에서 각 값의 개수가 몇 개인지까지 출력함!

## 범주형(Categorical) 변수 인코딩 방식
범주형 변수는 수치형 변수로 인코딩 해주어야 학습이 원활하게 진행된다. 수치가 영향을 미치는 Label encoding이나 Ordinal Encoding을 사용하는 상황과 One-hot encoding을 사용하는 상황을 구분할 필요가 있음

* Label encoding: dataset에 등장하는 순서 or 알파벳 순서대로 mapping  
* Ordinal encoding: 직접 map을 구성해 mapping 가능, 따라서 Ordinal이 손이 더 많이 가지만 알파벳 순의 성적 등이 아닌 사고 규모 등을 수치화 하기에 더 적합하다 판단함  
* One-hot encoding: 변수에 대한 모든 레이블을 개별 변수로 생성하는 encoding 방식  
* Binary encoding: One-hot encoding에서 변수가 너무 많이 생기는 문제점 보완을 위해 제안된 encoding 방식으로,   
Ordinal encoding
Binary encoding 두 종류를 사용했음
*하지만 이후 예측 결과 연산 과정에서 가장 큰 영향을 끼치는 컬럼을 구분하기 위해서 Binary encoding된 컬럼들도 Label encoding으로 변경했음  
➡️ 순서가 바뀌어야 함(변수별 영향 끼치는 정도 판단 후에 Binary encoding 실행)  
*polisy_csl은 combined single limits의 약자

## Conclusion
다양한 것을 배우는 매일, 짧은 회의 주기와 빠른 의사결정으로 프로젝트 진행이 수월하다. 

