---
title: '"First Lecture"'
draft: false
tags:
  - Udemy
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

###Oauth란?
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

과정
1. 