# Vue.js

1. 뷰 시작하기

    - 큰 프로젝트에서는 CDN 보다는 NPM 사용
   
    - 환경 세팅
      1. node.js 설치 (npm 사용하기 위해)
      2. 터미널에서 Vue 설치
      
      npm install -g @vue/cli
      vue --version

      3. 뷰 프로젝트 시작하기
      cd 폴더명
      vue create vue3-test //vue3-test 라는 폴더(프로젝트명) 만듬
      또는 git clone 받아올 경우: npx degit 저장소이름 만들프로젝트명
      //선택창에서 vue3 버전 선택
      cd vue3-test
      npm run serve //개발 서버 열림
      code . -r //코드 오픈
  
   4. vetur 플러그인 설치 // .vue 파일을 하이라이팅 해준다
    

    - vsCode, intelliJ 등 에서 프로젝트 열기

    - package.json 에서 프로젝트 상세정보 확인 가능

    - 

   프로젝트 안에서 vue3 설치
   npm i vue@next
   