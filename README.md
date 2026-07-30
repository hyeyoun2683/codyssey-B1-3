프로젝트 1. 자동화 도구 비교 구현 보고서
1. 프로젝트 개요
주제

Google Sheets에 새로운 데이터가 추가되면 조건(금액 10,000원 초과)을 확인한 후 Discord 채널에 알림을 보내고 Gmail로 이메일을 발송하는 자동화 워크플로우를 구현하였다.

사용한 자동화 도구
Make
Zapier

동일한 자동화 흐름을 두 도구에서 각각 구현하여 기능과 사용성을 비교하였다.
2. 구현한 워크플로우
Google Sheets
      │
      ▼
새로운 행(Row) 추가
      │
      ▼
Filter
(금액 > 10,000원)
      │
      ▼
Discord 알림 전송
      │
      ▼
Gmail 이메일 발송
3. Trigger와 Action 설명
Trigger

Trigger는 자동화를 시작시키는 이벤트이다.

이번 프로젝트에서는 Google Sheets에 새로운 행(Row)이 추가되는 순간 Trigger가 발생하도록 설정하였다.

사용한 Trigger

Google Sheets → Watch New Rows(Make)

Google Sheets → New Spreadsheet Row(Zapier)

Action

Action은 Trigger 이후 자동으로 수행되는 작업이다.

이번 프로젝트에서는 두 가지 Action을 사용하였다.

Discord(Webhook)로 알림 전송
Gmail로 이메일 발송

즉,

Google Sheets에 데이터가 추가되면

→ 조건을 검사하고

→ Discord에 알림을 보낸 뒤

→ Gmail로 이메일을 자동 발송하도록 구현하였다.

4. Filter(조건 분기)의 역할

이번 프로젝트에서는

금액 > 10,000원

이라는 조건을 설정하였다.

조건을 만족하는 경우에만

Discord 알림
Gmail 발송

이 실행된다.

조건을 만족하지 않는 데이터는 자동화가 실행되지 않도록 하여 불필요한 알림을 줄일 수 있었다.

5. Make 구현 과정
Google Sheets를 Trigger로 설정하였다.
금액이 10,000원 초과인지 Filter를 추가하였다.
HTTP(Webhook)를 이용하여 Discord에 메시지를 전송하였다.
Gmail 모듈을 추가하여 이메일을 발송하였다.
Run Once를 실행하여 실제 동작을 확인하였다.
6. Zapier 구현 과정
Google Sheets를 Trigger로 설정하였다.
Filter by Zapier를 이용하여 금액 조건을 설정하였다.
Webhooks by Zapier(POST)를 이용하여 Discord Webhook을 호출하였다.
Gmail Send Email Action을 추가하였다.
Test를 수행하여 Discord 알림과 Gmail 발송을 확인하였다.
7. Make와 Zapier 비교
비교 항목	Make	Zapier
UI/UX	시각적인 워크플로우가 보기 쉽다.	단계별 진행 방식이라 초보자가 이해하기 쉽다.
설정 난이도	다양한 기능이 있지만 처음에는 다소 복잡하다.	화면 안내가 잘 되어 있어 비교적 쉽다.
Filter 설정	Router와 Filter 기능이 강력하다.	Filter 설정이 직관적이다.
연동 서비스	다양한 앱과 HTTP 기능을 자유롭게 사용할 수 있다.	대부분의 유명 서비스를 쉽게 연결할 수 있다.
실행 로그 확인	Scenario 실행 기록을 자세히 확인할 수 있다.	Task History에서 실행 결과를 쉽게 확인할 수 있다.
무료 플랜	월 1,000 Operations 제공	월 Task 수 제한이 있어 무료 사용량이 상대적으로 적다.
8. 각 도구의 장단점
Make
장점
시각적인 워크플로우가 이해하기 쉽다.
Router와 Filter 기능이 매우 강력하다.
HTTP 기능을 자유롭게 사용할 수 있다.
복잡한 자동화를 구성하기 좋다.
단점
처음 사용하는 사람에게는 메뉴가 다소 어렵게 느껴질 수 있다.
설정 항목이 많아 익숙해지는 시간이 필요하다.
Zapier
장점
단계별 화면이 제공되어 초보자도 쉽게 사용할 수 있다.
Gmail, Google Sheets 등 주요 서비스를 간단히 연결할 수 있다.
테스트 기능이 직관적이다.
단점
무료 플랜의 사용량이 제한적이다.
복잡한 분기 구조에서는 Make보다 기능이 제한될 수 있다.
9. 어떤 상황에서 적합한가
Make

여러 서비스가 연결되는 복잡한 자동화나 다양한 조건 분기가 필요한 업무에 적합하다.

예를 들어

쇼핑몰 주문 처리
ERP 연동
다단계 승인 프로세스

등에 활용하기 좋다.

Zapier

간단한 반복 업무를 자동화하거나 처음 자동화를 배우는 사용자에게 적합하다.

예를 들어

Gmail 자동 발송
Google Sheets 관리
Slack 또는 Discord 알림

등의 업무를 쉽게 자동화할 수 있다.
