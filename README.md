# how to use branch
***
## 브랜치 목록 확인
### 모든 브랜치 목록 확인
```
git branch -a
```

### 로컬 브랜치 목록 확인
현재 체크아웃 중인 브랜치 *로 표시

```
git branch
```

### 원격 브랜치 목록 확인
```
git branch -r
```

***

## 로컬
### 로컬에서 브랜치 생성
```
git branch 브랜치이름
```

### 로컬에서 브랜치 삭제
해당 브랜치가 병합되지 않은 경우 삭제 거부

강제로 삭제하려면 -D 사용

```
git branch -d 브랜치이름
```
### 로컬 브랜치 이름 변경
이름을 변경할 브랜치에 checkout 한 후 수행
```
git branch -m 새로운 브랜치 이름
```

### 로컬에서 지정한 브랜치로 전환
전환시 현재 작업중인 변경사항이 커밋 되지 않았다면 경고

```
git checkout 브랜치이름
```

### 로컬에서 브랜치 생성후 생성한 브랜치로 전환
```
git checkout -b 브랜치이름
```

### 로컬에서 원격의 특정 브랜치를 가져와 체크아웃
```
git checkout -b 로컬브랜치이름 origin/원격브랜치이름
```

***

## 원격
### 원격 저장소에 브랜치 푸시
-u에서 u는 set upstream의 약자이다.

-u를 사용하면, 로컬 브랜치를 원격 브랜치와 연결한다.

이를 통해 다음 git push와 git pull 명령어를 사용할 때,

원격 브랜치의 이름을 따로 지정하지 않아도 된다.

```
git push -u origin 브랜치이름
```

### 원격 저장소의 기존 브랜치 삭제
```
git push origin --delete 삭제할 브랜치 이름
```

### 원격 저장소의 모든 변경 사항 가져오기
로컬과 병합하지 않아 자동반영되지 않음

```
git fetch
```

### 특정 원격 저장소의 변경 사항 가져오기
```
git fetch 특정 원격 저장소 이름
```

### 특정 원격 브랜치의 변경 사항 가져오기
origin에서 feature-branch 브랜치의 변경 사항만 가져옴

```
git fetch origin feature-branch
```

### 원격 저장소에서 삭제된 브랜치를 로컬에서도 제거
원격 저장소에서 모든 변경 사항을 가져오고,

원격 저장소에서 삭제된 브랜치에 대한 로컬 추적 브랜치를 제거

```
git fetch --prune
```

### 특정 원격 저장소에서 삭제된 브랜치를 로컬에서도 제거
origin은 특정 원격 저장소의 이름

```
git fetch origin --prune
```

***

## merge
1. merge는 두 개의 브랜치를 통합하여 하나의 브랜치로 결합하는 과정

    주로 로컬에서 사용

    원격에서의 병합은 Pull Request (PR)

1. fast-forward

    A 브랜치에서 다른 B브랜치를 Merge할 때

    B 브랜치가 A 브랜치 이후의 커밋을 가리키고 있으면,

    A 브랜치가 B 브랜치와 동일한 커밋을 가리키도록 이동 시킴

   (A의 커밋이 B의 커밋의 조상일 때, 두 커밋이 커밋 트리의 같은 라인에 있을 때)

1. 3-way-merge

    현재 브랜치가 가리키는 커밋이 merge할 브랜치가 가리키는 커밋의 조상이 아니라면

    각 브랜치가 가리키는 커밋 두개와 공통 조상 하나를 사용하여 3-way-merge 한다.

    3-way-merge의 결과를 별도의 커밋으로 만들고 해당 브랜치가 그 커밋을 가리키도록 이동,

    이런 커밋은 부모가 여러 개고 merge 커밋 이라고 부름

1. 3-way-merge의 충돌

    merge하는 두 브랜치에서 같은 파일의 한 부분을 동시에 수정하고 merge하면

    충돌(conflict) 발생

### 기본 merge
현재 체크아웃된 브랜치에 다른 브랜치를 병합

```
git merge 통합하려는 브랜치 이름
```

### 상태 점검
현재 브랜치와 변경 사항의 상태 확인

병합 후 상태 점검

merge 충돌 발생 시 어떤 파일을 merge할 수 없었는지 점검

```
git status
```

***

## rebase
브랜치를 재구성하거나 커밋을 다시 적용하는 데 사용

브랜치의 베이스를 다른 브랜치 위로 변경하여 커밋들을 새로 적용

병합 기록 없이 깔끔한 커밋 히스토리를 유지

A 브랜치에서 작업 중 B 브랜치의 최신 변경 사항을 가져와 A 브랜치에 반영하고자 할 때

(A 브랜치의 커밋들이 B 브랜치의 최신 커밋 뒤에 붙음)

```
git checkout A_branch
git rebase B_branch
```

### interactive rebase
커밋을 더 세밀하게 조작할 수 있도록 해줌

현재 가리키고 있는 HEAD부터 최근 n개의 커밋을 대상으로 interactive rebase 함

```
git rebase -i HEAD~n
```

pick 커밋을 그대로 사용
reword 커밋 메세지를 변경
edit 커밋을 수정
squash 이전 커밋과 합침
fixup 커밋을 합치되 메시지는 유지하지 않음
drop 커밋 삭제

### rebase 과정 중 충돌 해결
git rebase 중 충돌이 발생하면 Git은 충돌이 발생한 커밋까지 중지하고 충돌을 해결할 수 있도록 함

충돌을 해야한 후에는 다음 명령어로 rebase를 계속 진행할 수 있음

```
git add <해결된 파일>
git rebase --continue
```

### rebase 중지
현재 진행 중인 rebase를 취소하고 원래 상태로 돌아감

```
git rebase --abort
```

### rebase 주의사항
- 공개된 커밋은 리베이스 하지 않기
    - 이미 다른 사람과 공유된 커밋을 리베이스하면 커밋 해시가 변경되어 충돌 발생 가능
- git rebase 사용 후 강제 푸시
    - git rebase로 커밋이 재구성되면 git push --force가 필요할 수 있음

***

## merge와 rebase의 차이점
- merge는 두 브랜치를 병합하여 새로운 커밋을 생성
    - 커밋 히스토리가 병합 기록을 포함하므로 기록이 복잡해질 수 있음

- rebase는 브랜치를 다른 브랜치 위로 재구성하여 커밋 기록을 깔끔하게 유지
    - 재구성 중 커밋 해시가 변경되므로 원격 저장소에 이미 푸시한 커밋을 리베이스하면 git push --force가 필요

***