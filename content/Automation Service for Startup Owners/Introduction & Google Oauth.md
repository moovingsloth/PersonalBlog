---
title: '"Introduction"'
draft: false
tags:
  - Udemy
  - MondoDB
  - ExpressJS
  - REACT
created: 2024-06-24
---
 
Fist goal : integrate different tech-stack into one: Express.js, React, MongoDB, Redux, associated technologies.

draw.io를 통한 workflow 그리기.

Express.js 간단하게 학습.
### Heroku란?

Heroku는 Java, Node.js, Python등 여러 언어를 지원하는 클라우드 Paas이다.
Heroku는 한 계정당 **5개**의 앱을 무료로 호스팅 할 수 있다. 

무료인 만큼 치명적인 단점이 있는데, 해당 도메인에 몇 시간 동안 접속 요청이 없는 경우에는 앱이 수면 상태로 전환되어, 초기 접속이 느려진다. 

수면 상태로 전환되는 것을 방지하기 위해 계속 request를 해주는 방법
요청을 일정 시간 단위로 보내주는 사이트 ([https://kaffeine.herokuapp.com/](https://kaffeine.herokuapp.com/))

많은 사람이 접속할 일이 없는 개인 포트폴리오 사이트나, 스터디용 미니 프로젝트 등을 배포하기에 적합하다.

### Oauth란?
[네이버 로그인](https://developers.naver.com/products/login/api/), [카카오 로그인](https://developers.kakao.com/features/platform#%EC%82%AC%EC%9A%A9%EC%9E%90-%EA%B4%80%EB%A6%AC)를 왜 사용할까? 여러 가지 이유가 있을 수 있다. 예를 들어 쉬운 회원가입&로그인을 위해 사용할 수 있다. 회사에서 이런 이유 때문에 사용하기로 결정났다고 하자. 그러면 우리 개발자들은 이를 구현해야만 한다.

이제 기술적인 문제를 생각해보자. 우리 서비스를 사용하려는 고객이 네이버 회원임을 어떻게 알 수 있을까?

간단한 방법은 고객한테 네이버 아이디/비밀번호를 받아서 네이버에 로그인을 해보면 된다. 근데 이 방법은 말도 안되는 방법이다. 그래서 `OAuth`가 생겼다.

`OAuth`는 쉽게 말해서 다른 서비스의 회원 정보를 **안전하게** 사용하기 위한 방법이라고 생각하면 된다. 여기에서 **안전하게**의 주체는, 회원 정보를 가지고 있는 주체, 우리의 **고객**이다. 즉, 우리의 **고객이 안전하게** 다른 서비스의 정보를 우리 서비스에 건네주기 위한 방법이다.

고객이 자신의 네이버 아이디/비밀번호를 우리 서비스에 알려주지 않아도, 네이버에 있는 고객의 정보를 우리 서비스에서 안전하게 사용하기 위한 방법이다.

크게 3단계로 나뉘어져 있다.

1. 서비스를 등록하는 과정
    - 네이버에 자사 서비스 등록하기
    - 이 과정에서 redirect_uri 등을 합의하기
2. 토큰을 받기 위한 과정
    - 사용자를 네이버 로그인 페이지로 이동시키기
    - 네이버가 사용자를 우리 서비스로 리다이렉트 시키기
3. 토큰을 이용해 정보를 요청하는 과정

### Passport JS
Oauth의 OS flow를 간결하게 자동화할 수 있도록 해준다. 
다만, 주의해야할 점은 자동화하면서 Code를 짤 때, 각 코드가 어떤 역할을 하는지 꼭 알아야 한다. 
두 개의 라이브러리를 이용한다. 
passport :  general helpers for handling auth in Express apps
pasport starategy : helpers for authenticating with open very specific method(email, password, Google, Facebook, etc)

이번 프로젝트에서는 Google로만 진행하며, 추후에는 동일한 과정으로 다른 인증 과정을 추가할 수 있다. 

### Nodemon
디렉토리의 파일 변경이 감지되면 자동으로 노드 응용 프로그램을 다시 시작하여 Node.js 기반 응용 프로그램 개발을 돕는 도구

#### Cookie based Authentication
Http is stateless: we can't identify who is making any given request between any given number of requests.
=> cookie: unique identifying piece of information, token

### MongoDB

대표적은 NoSQL, Document DB  
Mongo는 Humongous에서 따온말로, 엄청나게 큰 DB라는 의미  
->**대용량 데이터**를 처리하기 용이

JS World -> MondoDB world
One model class -> One collection
One model instance -> One individual record

### Mongoose ODM

(1)Object Data Modiling  
MongoDB의 **Collection에 집중하여 관리**하도록 도와주는 패키지  
Collection을 **모델화**하여, 관련 기능들을 **쉽게 사용할 수 있도록** 도와줌

(2)연결관리  
MongoDB의 기본 Node.js 드라이버는 **연결상태를 관리하기 어려움**  
Mongoose를 사용하면 **간단하게 데이터베이스와의 연결상태를 관리**해줌

(3)스키마관리  
스키마를 정의하지 않고 데이터를 사용할 수 있는 것은 NoSQL의 장점이지만,  
데이터 형식을 미리 정의 해야 코드작성과 프로젝트 관리에 유용함  
Mongoose는 Code-Level에서 스키마를 정의하고 관리 할 수 있게 해줌

(4)populate  
MongoDB는 기본적으로 **Join을 제공하지 않음**  
Join과 유사한 기능을 사용하기 위해선 **aggregate라는 복잡한 쿼리**를 해야 하지만,  
Mongoose는 **populate를 사용하여 간단하게 구현**할 수 있음

### MongoDB Atlas
MongoDB Atlas는 MongoDB의 완전 관리형 클라우드 데이터베이스 서비스입니다. 이 서비스는 MongoDB 데이터베이스를 클라우드에서 호스팅 하고 관리하는 것을 중심으로 하며, 개발자 및 기업이 손쉽게 애플리케이션을 빌드하고 배포할 수 있도록 지원합니다.

MongoDB Atlas는 데이터베이스 클러스터를 프로비저닝 하고, 모니터링하고, 관리하기 쉽도록 도와줍니다. 또한 사용자 지정 보안 정책을 설정하고, 데이터를 안전하게 저장하며, 백업과 복구를 수행할 수 있습니다.

MongoDB Atlas는 다양한 클라우드 플랫폼에서 사용할 수 있습니다. 예를 들어, Amazon Web Services (AWS), Google Cloud Platform (GCP), Microsoft Azure 등의 클라우드 플랫폼에서 호스팅 할 수 있으며, MongoDB Atlas는 이러한 클라우드 플랫폼에서 쉽게 사용할 수 있도록 구성되어 있습니다.

MongoDB Atlas는 개발자 및 기업이 데이터베이스 관리 및 인프라 관리에 대한 부담을 줄여줌으로써 애플리케이션 개발 및 배포를 더욱 빠르고 안정적으로 만들어줍니다.

//문제
중복된 user record => redirection code를 수정하여 해결.
