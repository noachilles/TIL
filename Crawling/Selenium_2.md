Date: 2024-08-05

## 흐름도  
```html
    <ul class="imageType">
        <li>
            <dl class="bookDataWrap">
                <dt class="tit2">
                <dd class="author">
                <dd class="author">
                <dd class="data">
                <dd class="site">
            </dl>
        </li>
        <li>
        ...
        </li>
    </ul>
```

이런 구조로 되어있으므로 By.XPATH(imageType) -> (반복) By.TAG_NAME(li) -> By.(dl) 각 값을 불러와 append하고, data 단위로 추가하는 게 맞음