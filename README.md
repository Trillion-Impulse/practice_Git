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

