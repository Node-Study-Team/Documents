# clone
## git clone이란?
- 특정 레포의 파일을 로컬 저장소에 복제하는 명령어
- ```git clone https://github.com/사용자이름/프로젝트이름```
- 권한 문제로 clone에 실패할 경우, ```git config --global user.name 유저이름 / git config --global user.email 유저이메일```
- 특정 브랜치를 clone할 경우, ```git clone -b 브랜치이름 --single-branch 원격저장소주소```

# init
## git init이란?
- 로컬 저장소가 git repository가 아닌 상태에서 git repository로 사용할 수 있도록 초기화하는 명령어
- ```git init```
- init 후 clone 권장
- git repository를 해제하려면 ```rm -rf .git```

# commit
## git commit이란?
- 작업이 완결된 변경 사항을 저장소에 기록. 실제 원격 저장소(github)의 파일은 바뀌지 않음
- ```git commit -m "커밋 메시지"```
- 쉽게 설명하면 **버전 업그레이드**와 같은 개념으로, commit 하기 전에는 로컬 저장소 내 파일에서 변화가 있어도 버전이 올라가지 않음
- 하지만 commit 시 그 때까지의 로컬 저장소 내 파일 변경 사항을 저장함
- 이전에 commit했던 특정 버전의 파일에 접근 가능하고, 각 커밋 별 코드 변경 사항 비교 등의 기능 제공
![image](https://user-images.githubusercontent.com/20695889/162563950-4b6811b0-9a34-486c-87bb-08eeb26949f6.png)
- commit한 내용을 원격 저장소(github)에 업로드 하려면 ```git push```를 사용해야 함

# push
## git push란?
- commit한 내용을 원격 저장소에 적용
- ```git push 저장소이름(보통 origin만 써도 됨) 브랜치이름(main, master, ...)```
![image](https://user-images.githubusercontent.com/20695889/162564360-1bfed321-322c-4d63-af92-924c9b83ad80.png)
- push나 commit 전, 수정하던 코드가 기존 원격 저장소 버전보다 낮을 시 높은 확률로 에러 발생
- 이를 방지하기 위해 누군가 commit 및 push를 하면 다 같이 pull을 통해 코드를 업데이트 해야 함
- 또는 merge 등의 명령어를 통해 오류를 수정해야 할 수도 있음

# .gitignore
## .gitignore란?
- git은 프로젝트 폴더 내 모든 파일을 버전 관리를 위해 감시 및 추적
- 이 때, node_modules(혹은 라이브러리)나 .env 같은 파일은 공유하지 않아도 되므로 파일 감시 목록에서 제거해야 함
- .gitignore 파일을 통해 관리하지 않을 파일이나 폴더를 지정할 수 있음

## 사용 방법
- 파일 제외 시 ```해당 파일 이름```
- 특정 경로의 파일을 제외하려면 ```/경로/파일 이름```
- 폴더 제외 시 ```폴더/```
- 특정 경로 아래의 모든 파일 중 해당하는 파일만 제외하려면 ```폴더/**/파일 이름```
- 특정 확장자 파일 제외 시 ```*.확장자```
- 예외 적용 시 ```!예외파일```

## 기존 프로젝트에서 .gitignore 파일을 후작성 시 commit / push 시 지정 파일들도 포함됨
- bash -> ```git rm -r --cached .```를 통해 캐시 삭제
- ```git add . ```를 통해 git으로 관리할 파일 등록(ignore 빼고 전부)
- 이후 commit 및 push
