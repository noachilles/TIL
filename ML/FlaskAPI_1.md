Date: 2024-07-12

## Intro
ML 모델을 활용하기 위해서 Flask API를 활용하기까지 과정

## joblib module 
```model.fit()``` 코드를 실행해 학습된 모델을 joblib module로 save/load 할 수 있음  
Flask를 불러와 사용하기 이전에 모델 save/load 기능을 잘 수행하는지 확인하기 위해 input을 임의로 입력해 다음과 같이 test 해보는 것이 좋음

```python
import pickle
import numpy as np
import xgboost
import joblib

model = joblib.load('xgboost_model.pkl')

arr = np.array([[1000, 3, 1, 2, 71610, 13020, 52080, 0, 1, 0, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 0, 0, 1]])

pred = model.predict_proba(arr)[:, 1]
print(pred)

'''
0.67244405
'''
```

이 때 사용되는 모듈로는 pickle도 있음. 주로 pytorch 모델을 저장하기 위한 형식을 지원하는 모듈    