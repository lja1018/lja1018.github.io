---
title:  "2020-03-11 답장/전달 오류 해결"
excerpt: "2020-03-11 답장/전달 오류 해결"

categories:
  - 베이스캠프
tags:
  - 베이스캠프
  - QA
  - 소감
---

# 답장/전달 버튼 클릭 시 오류 발생

테스트 결과 유효기간이 설정된 메일의 경우 유효기간이 설정된 메일의 경우 오류가 발생하는 것으로 확인되었다.

![답장전달 오류](https://imgur.com/ANwwOia.png)

확인 결과 'T'가 없는 시간 표기법에서 LocalDateTime으로의 파싱 시 오류가 발생하는 것이였다.


![파싱 오류](https://imgur.com/yTJRpCg.png)

# 해결 방법

따라서 파싱 전에 띄어쓰기 대신 'T'로 대체한 String을 파싱함으로써 해결할 수 있었다.

![결과](https://imgur.com/8VHi5mN.png)