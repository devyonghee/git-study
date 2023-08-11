## 커밋

커밋을 하게 되면 다음과 같은 구조로 git database 에 저장

![commit raw data](img/commit-raw-data.png)
![commit tree data](img/commit-tree-data.png)
 
- git 은 key-value 형태의 storage 를 사용

- commit 구성 정보
  - 메타데이터: 커밋 메세지, 작성자, 이메일, 날짜, 시간 등
  - 프로젝트 스냅샷
  - 부모 커밋의 `hash` 값 (최초의 커밋은 없을 수 있음)
- git objects
  - blob (binary large object)
    - 파일의 내용을 담고 있는 객체 (파일 이름은 없음)
    - 파일의 내용을 해싱하여 키로 가짐
  - tree
    - 디렉터리를 저장하는 객체, 파일의 이름을 저장
    - 파일의 `hash` 값과 파일의 이름을 해싱하여 키로 가짐
  - commit
    - 프로젝트의 루트 트리의 `hash` 값, 부모 commit 의 `hash` 값, 메타데이터를 저장 
- `git diff` 를 사용하게 되면 tree 구조에서 `hash` 값만을 비교하여 다른 내용의 파일을 찾음
  - `hash` 를 비교하여 변경된 폴더만 찾기 때문에 빠른 성능을 보임
