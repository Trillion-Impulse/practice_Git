브랜치를 사용하는 방법

브랜치 목록 확인
    로컬 브랜치 목록 확인
        현재 체크아웃 중인 브랜치 *로 표시
    git branch

    원격 브랜치 목록 확인
    git branch -r

로컬에서 브랜치 생성
git branch 브랜치이름

로컬에서 브랜치 삭제
    해당 브랜치가 병합되지 않은 경우 삭제 거부
    강제로 삭제하려면 -D 사용
git branch -d 브랜치이름

로컬에서 지정한 브랜치로 전환
    전환시 현재 작업중인 변경사항이 커밋 되지 않았다면 경고
git checkout 브랜치이름

로컬에서 브랜치 생성후 생성한 브랜치로 전환
git checkout -b 브랜치이름

원격 저장소에 브랜치 푸시
git push -u origin 브랜치이름

원격 저장소의 변경 사항 가져오기
    로컬과 병합하지 않아 자동반영되지 않음
git fetch
git fetch 특정 원격 저장소 이름
git fetch --prune 원격 저장소에서 삭제된 브랜치를 로컬에서도 제거

next -> merge에 대하여