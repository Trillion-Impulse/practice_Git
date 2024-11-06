# how to use repository
***

## how to use clone
1. IDE의 터미널 열기

    CLI에서 터미널 명령어를 사용할 예정

1. 지정한 디렉토리로 이동

    ```
    cd 폴더의\위치\...
    ```

1. repository clone

    ```
    git clone 저장소 URL
    
    ex) git clone https://github.com/{본인_아이디}/{저장소 아이디}.git
    ```

## how to switch to another repository
1. 현재 연결된 원격 repository 확인

    ```
    git remote -v
    ```

1. 현재 연결된 repository와의 연결 제거

    ```
    git remote remove origin
    ```

1. 새로운 원격 리포지토리 추가

    ```
    git remote add origin 새로운 원격 리포지토리 URL
    ```
## how to switch to new url of renamed repository
1. 원격의 repository의 이름을 바꾸면, 새로운 url이 생성된다.

1. 그러므로 로컬에 연결되어있던 url을 새로운 url로 변경해야한다.

1. 원격 연결 제거 -> 새로운 원격 리포지토리 추가 방법을 사용해도된다.

1. 기존의 연결 제거 과정 없이, url만 변경하는 방법도 있다.

   ```
   git remote set-url origin 새로운 원격 리포지토리 URL
   ```
   
1. 이후 로컬의 디렉토리명은 수동으로 변경해야한다.

   ```
   mv <기존의 로컬 리포지토리 이름> <새로운 로컬 리포지토리 이름>
   ```
   - mv는 move의 약자로 터미널에서 디렉토리를 이동시키거나 이름을 변경할 때 사용한다.
   - 이동의 경우에는 filename.txt /path/to/destination/

