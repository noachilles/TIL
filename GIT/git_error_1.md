Date: 2024-08-31

Github push를 하려다 fatal: the remote end hung up unexpectedly 에러가 발생했다.  
해결방법은 Buffer 크기를 늘려주는 것, 일단 필요하지 않은 파일 및 폴더를 삭제하는 것부터 시작했다.  
그러골 
```git config --global http.postBuffer 1048576000``` 을 작성  
결과적으로, 다른 error로 넘어감  
refer to error였다.  

다들 git pull 이후 push로 해결했다고 했으나 내 경우에는 Already state of end만 뜨고 해결되지 않아서 clone 폴더를 다시 만들었다.  

## CRLF Warning  
warning: LF will be replaced by CRLF in (파일경로)  
**LF**: Line-Feed의 약자로, 커서를 움직이지 줄바꿈  
**CRLF**: Carriage Return Line-Feed의 약자로, 커서를 다음 라인 맨 앞으로 이동하는 동작  

OS마다 사용되는 줄바꿈 문자열이 달라 git에서 이를 요청한다.  
```core.autocrlf``` 설정으로 해결할 수 있음  
### for Windows
```$git config core autocrlf true```
```$git config --global core.autocrlf true```