---
layout: resume
title: 이력서
description: 백엔드 개발자 문형주의 이력서
permalink: /resume/
---

<header class="resume-header">
  <div>
    <p>BACKEND ENGINEER</p>
    <h1>문형주</h1>
    <strong>서비스의 흐름을 이해하고 데이터의 일관성을 지킵니다.</strong>
  </div>
  <div class="resume-header-meta">
    <address>
      <a href="tel:+821097114528">010-9711-4528</a>
      <a href="mailto:luke4528@naver.com">luke4528@naver.com</a>
      <a href="https://github.com/moon4528">github.com/moon4528</a>
    </address>
    <div class="resume-header-photo">
      <img src="{{ '/assets/images/profile.png' | relative_url }}" alt="백엔드 개발자 문형주 프로필 사진">
    </div>
  </div>
</header>

<section class="resume-block resume-summary">
  <h2>소개</h2>
  <p><strong>30개 매장이 운영 중인 실서비스 BitePick</strong>의 백엔드를 개발하며, 주문·알림·리뷰 데이터가 일관되게 이어지는 구조를 개선하고 있습니다. 실시간 처리와 AI 연동 프로젝트에서도 시스템 간 책임을 분리하고 비관적 잠금·DB 제약·Redis 캐시를 적용한 뒤, 테스트와 부하 측정으로 결과를 검증했습니다.</p>
</section>

<section class="resume-block">
  <h2>핵심 역량</h2>
  <div class="resume-columns">
    <div><strong>실서비스 데이터 정합성</strong><p>상태 전이·Unique Constraint·사용자 기준 집계로 동시 요청과 중복 데이터에서도 비즈니스 규칙을 보장합니다.</p></div>
    <div><strong>실시간·외부 연동 경계 설계</strong><p>Polling·Redis와 커밋 이후 비동기 처리를 적용해 핵심 요청을 반복 조회 및 외부 AI 지연과 분리합니다.</p></div>
    <div><strong>테스트·로그 기반 검증</strong><p>k6 부하 테스트, 통합 테스트, 운영 로그로 선택의 결과와 예외 상황을 재현하고 확인합니다.</p></div>
  </div>
</section>

<section class="resume-block">
  <h2>기술 스택</h2>
  <dl class="resume-stack">
    <div><dt>Backend</dt><dd>Java 21 · Spring Boot 3 · REST API · JPA · QueryDSL</dd></div>
    <div><dt>Data</dt><dd>MariaDB · PostgreSQL · Redis</dd></div>
    <div><dt>Infra</dt><dd>AWS (EC2, RDS, S3, ECR) · Docker · GitHub Actions · Nginx</dd></div>
    <div><dt>Validation</dt><dd>JUnit 5 · k6 · Prometheus · Grafana</dd></div>
  </dl>
</section>

<section class="resume-block">
  <h2>프로젝트</h2>
  <article class="resume-project">
    <header><div><h3>BitePick</h3><span>Backend Developer · 2026.08 ~ 현재</span></div><b>LIVE · 30 STORES</b></header>
    <p><strong>Problem</strong> 운영 중인 지역 기반 픽업 서비스에서 가입·리뷰·알림 기능을 확장하면서 기존 사용자 흐름과 데이터 정합성을 유지해야 했습니다.</p>
    <p><strong>Analyze</strong> 헥사고날 구조·ERD·API·배포 환경을 먼저 분석하고, 애플리케이션 선검사와 DB 제약, FCM 토큰 수와 실제 사용자 수의 차이를 비교했습니다.</p>
    <p><strong>Action</strong> 일반·소셜 가입 경로 수집, 점주 리뷰 답글·관리자 신고 조회를 구현하고 review_id Unique Constraint와 distinct user 집계를 적용했습니다.</p>
    <p><strong>Result</strong> 중복 토큰 2개를 신청자 1명으로 집계하고, 동시 답글의 DB 제약 위반을 도메인 예외로 변환했으며 잘못된 가입 경로 요청이 400으로 반환됨을 테스트했습니다.</p>
  </article>
  <article class="resume-project">
    <header><div><h3>FitBack</h3><span>Backend Developer · TAVE 17기</span></div><b>AI · B2B</b></header>
    <p><strong>Problem</strong> AI 미전환 사유와 후속 액션 갱신 시점처럼 분야마다 다르게 해석되던 B2B 화면 값을 일관된 백엔드 규칙으로 정의해야 했습니다.</p>
    <p><strong>Analyze</strong> 각 값의 원천 데이터·계산 책임·갱신 트리거를 정리하고, 동기 AI 호출과 커밋 전·후 비동기 실행을 데이터 보존과 장애 전파 관점에서 비교했습니다.</p>
    <p><strong>Action</strong> API·시퀀스·스키마 계약을 정렬하고 AFTER_COMMIT·@Async 분석 상태와 비관적 잠금·DB 제약을 적용했습니다.</p>
    <p><strong>Result</strong> AI 완료를 기다리지 않고 201 Created를 반환하면서 상담 데이터를 보존하고, 동시 전환 2건 중 두 번째 처리가 첫 커밋 이후 중복 상태를 확인하는 것을 PostgreSQL 통합 테스트로 검증했습니다.</p>
  </article>
  <article class="resume-project">
    <header><div><h3>Postura</h3><span>Backend &amp; Infra · TABA 10기</span></div><b>PROJECT 1ST</b></header>
    <p><strong>Problem</strong> 웹캠 자세 분석 결과를 1초마다 제공하면서 반복 DB 조회와 로그 저장이 AI의 다음 프레임 처리를 지연시키지 않아야 했습니다.</p>
    <p><strong>Analyze</strong> WebSocket·SSE·Polling과 RDB·Redis를 연결 복잡도·조회 부하·1초 갱신 요구 기준으로 비교하고, 동기 저장·@Async·메시지 큐의 트레이드오프를 검토했습니다.</p>
    <p><strong>Action</strong> Stateless Polling·Redis Hash 캐시를 구성하고, AI 로그는 202 Accepted 응답 후 @Async로 저장하며 세션 종료·일일 배치로 통계를 집계했습니다.</p>
    <p><strong>Result</strong> k6 테스트에서 동시 사용자 100명 기준 평균 24ms·P95 62.54ms를 확인했으며, 6팀 중 프로젝트 최우수상과 우수교육생 IITP 원장상을 수상했습니다.</p>
  </article>
</section>

<section class="resume-block">
  <h2>학력 및 활동</h2>
  <div class="history-table-wrap history-table-wrap--resume">
    <table class="history-table">
      <thead><tr><th>기간</th><th>이력</th><th>상태</th><th>비고</th></tr></thead>
      <tbody>
        <tr><td>2021.03 ~ 2027.02</td><td>단국대학교 컴퓨터공학과</td><td>졸업 예정</td><td>DKU Honors 2기</td></tr>
        <tr><td>2025.08</td><td>ADsP (데이터분석 준전문가)</td><td>취득</td><td>한국데이터산업진흥원</td></tr>
        <tr><td>2025.10 ~ 2025.12</td><td><a href="https://www.cccr-edu.or.kr/mobile/page.jsp?code=swacademy">TABA 10기</a></td><td>수료</td><td>Backend &amp; Infra · 프로젝트 최우수상 (1위) · IITP 원장상</td></tr>
        <tr><td>2026.03 ~ 2026.07</td><td><a href="https://www.tave-wave.com/">TAVE 17기</a></td><td>수료</td><td>Backend · AWS SAA 스터디 · 프로젝트/스터디 공식 블로그 게시</td></tr>
        <tr><td>2026.08 ~ 현재</td><td><a href="https://www.bitepick.co.kr/">BitePick 참여</a></td><td>진행 중</td><td>Backend &amp; DevOps · 실서비스</td></tr>
        <tr><td>2026.09</td><td>정보처리기사</td><td>취득</td><td>한국산업인력공단</td></tr>
      </tbody>
    </table>
  </div>
</section>

<footer class="resume-note">이 이력서는 포트폴리오의 최신 내용을 기준으로 작성되었습니다.</footer>
