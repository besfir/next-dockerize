# Development 환경의 Dockerfile에는 왜 별 내용이 없는가

> 실서버와 개발서버가 `환경`만 같도록 해주는 역할.

실서버와 똑같이 COPY로 소스를 복사하면, 코드를 수정할 때마다 매번 빌드를 해줘하 하는 불편함이 생긴다.
이 때문에 프로젝트 자체를 마운트해서 독립된 환경에서 소스코드만 이용할 수 있도록 했다.

`node_modules`제어는 호스트 OS에서 하기 위해 install류 명령어(npm i, yarn, pnpm i)를 걷어냈다.

# Production 환경을 3개 스테이지로 나눈 이유

확실치는 않지만 2개 스테이지(builder와 runner)로 나눴을 경우 속도가 2~3초 정도 더 빠른 경향이 있는것으로 보이는데, 
Nextjs 공식 예제에서는 3개로 나누고 있기에 공식 예제를 따랐다.

# Development Dockerfile에는 왜 `apk add --no-cache libc6-compat`을 사용하지 않았는가?

`process.dlopen`에러를 방지하기 위해 설치하는 패키지인데, 검색해보니 `node xx.js`명령어로 앱을 실행할 때에 발생하는 것으로 확인돼서 일단 제거해봤다.

