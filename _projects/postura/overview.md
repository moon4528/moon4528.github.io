---
layout: project
title: Postura
project: Postura
section: overview
order: 1
summary: MediaPipe Pose/Hands와 Redis를 활용해 웹 캠으로 사용자의 자세를 실시간으로 분석 및 교정 피드백을 제공하는 서비스
project_image: /assets/images/projects/postura.png
github: https://github.com/TABA-postura
stack:
  - JAVA
  - Spring BOOT
  - AWS (EC2, RDS, Redis, ALB)
  - Docker
  - Github Action
  - Nginx
impact:
  - value: 프로젝트 최우수상
    detail: 6팀 중 1위
    label: PROJECT AWARD
    emphasis: true
  - value: 우수교육생 IITP 원장상
    detail: 30명 중 3명 선정
    label: ACADEMY AWARD
    emphasis: true
  - value: 1초 주기 Polling
    detail: Redis 캐시 기반 최신 자세 피드백
    label: REAL-TIME FEEDBACK
    emphasis: true
  - value: 7개 자세 유형
    detail: 로직 기반 실시간 자세 집계
    label: POSTURE ANALYTICS
    emphasis: true
---

<section class="project-section">
  <header class="project-section-title"><span>02</span><h2>BACKGROUND</h2></header>
  <div class="project-copy project-background">
    <p class="project-background-intro">하루 6시간 이상 컴퓨터를 사용하는 비율이 <strong>84.5%</strong>에 이르고, 어깨·목 통증 발생 비율도 각각 <strong>57%</strong>, <strong>38.3%</strong>로 나타나 일상 속 자세 예방 관리의 필요성에 주목했습니다.</p>
    <div class="project-background-block">
      <strong class="project-background-label">핵심 기능</strong>
      <p class="project-background-tags"><code>실시간 자세 분석</code><code>1초 주기 피드백</code><code>자세 통계 리포트</code><code>맞춤 스트레칭 추천</code></p>
    </div>
    <div class="project-background-block">
      <strong class="project-background-label">주요 경험</strong>
      <ol class="project-background-list">
        <li>Frontend–FastAPI–Spring Boot 간 데이터 흐름 연동</li>
        <li>Polling·Redis 기반 실시간 데이터 파이프라인 최적화</li>
        <li>@Async 로그 처리와 일일 통계 집계 배치 설계</li>
        <li>k6를 활용한 피드백 조회·AI 로그 수신 API 부하 테스트</li>
      </ol>
    </div>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>03</span><h2>ARCHITECTURE</h2></header>
  <div class="project-diagram-list">
    <figure class="project-diagram-card">
      <figcaption><span>01</span><div><strong>Sequence Diagram</strong><p>모니터링 세션과 실시간 자세 피드백 데이터 흐름</p></div></figcaption>
      <a href="{{ '/assets/images/projects/postura-sequence-diagram.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
        <img src="{{ '/assets/images/projects/postura-sequence-diagram.png' | relative_url }}" alt="Postura 실시간 자세 분석 시퀀스 다이어그램" loading="lazy">
      </a>
    </figure>
    <figure class="project-diagram-card">
      <figcaption><span>02</span><div><strong>System Architecture</strong><p>Frontend·Backend·AI 서버와 AWS 인프라 구성</p></div></figcaption>
      <a href="{{ '/assets/images/projects/postura-system-architecture.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
        <img src="{{ '/assets/images/projects/postura-system-architecture.png' | relative_url }}" alt="Postura 시스템 아키텍처 다이어그램" loading="lazy">
      </a>
    </figure>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>04</span><h2>CONTRIBUTIONS</h2></header>
  <div class="contributions-list">
    <article class="activity-card">
      <div class="activity-index">01</div>
      <div>
        <p class="activity-label">DATA FLOW INTEGRATION</p>
        <h3>Frontend–FastAPI–Spring Boot 데이터 흐름 연동</h3>
        <p>세션 ID를 기준으로 웹캠 프레임 전송부터 AI 분석 결과 수신, 실시간 피드백 조회까지 이어지는 3-tier 데이터 흐름을 설계했습니다.</p>
      </div>
    </article>

    <article class="activity-card">
      <div class="activity-index">02</div>
      <div>
        <p class="activity-label">REAL-TIME PIPELINE</p>
        <h3>Polling·Redis 기반 실시간 파이프라인 최적화</h3>
        <p>1초마다 발생하는 피드백 조회의 DB 부하를 줄이기 위해 Stateless Polling과 Redis Hash 캐시를 적용해 실시간 조회 구조를 단순화했습니다.</p>
      </div>
    </article>

    <article class="activity-card">
      <div class="activity-index">03</div>
      <div>
        <p class="activity-label">ASYNC &amp; BATCH</p>
        <h3>비동기 로그 처리 및 통계 집계 설계</h3>
        <p>AI 서버가 다음 프레임을 지연 없이 처리하도록 로그 수신 즉시 202 Accepted를 반환하고, @Async 저장과 세션 종료·일일 배치 기반 통계 집계를 구성했습니다.</p>
      </div>
    </article>

    <article class="activity-card">
      <div class="activity-index">04</div>
      <div>
        <p class="activity-label">LOAD TEST</p>
        <h3>k6 기반 실시간 피드백 API 부하 테스트</h3>
        <p>1초 주기 Polling 환경을 가정해 최대 100명의 동시 사용자를 테스트하고, 로컬 환경에서 평균 24ms·P95 62.54ms의 응답 성능을 확인했습니다.</p>
      </div>
    </article>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>05</span><h2>TROUBLE SHOOTING</h2></header>
  <div class="trouble-list">
    <article class="trouble-card">
      <header class="trouble-card-header">
        <span>01</span>
        <div><p>REAL-TIME FEEDBACK</p><h3>실시간 피드백에 WebSocket 대신 Polling을 선택한 이유</h3></div>
      </header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>1초마다 최신 자세 피드백을 제공하면서 반복 조회로 발생하는 DB와 서버 부하를 관리해야 했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>WebSocket·SSE·Polling을 연결 관리 복잡도, 확장성, 현재 서비스의 1초 갱신 주기 측면에서 비교했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>지속 연결의 복잡도를 감수하는 대신 Stateless Polling을 선택하고, MySQL 반복 조회를 Redis Hash 캐시 조회로 대체했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>로컬 환경의 Redis 피드백 조회 API를 k6로 검증한 결과, 동시 사용자 100명에서 평균 24ms·P95 62.54ms를 기록했습니다.</p></div></section>
      </div>
    </article>

    <article class="trouble-card">
      <header class="trouble-card-header">
        <span>02</span>
        <div><p>ASYNC PROCESSING</p><h3>AI 로그 저장과 HTTP 응답을 분리해 분석 지연 방지</h3></div>
      </header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>Spring Boot의 DB 저장이 끝날 때까지 FastAPI가 기다리면 다음 웹캠 프레임 분석이 함께 지연될 수 있었습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>동기 저장, 애플리케이션 비동기 처리, 메시지 큐 도입을 응답 속도·구현 복잡도·전달 안정성 관점에서 검토했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>별도 메시지 인프라 없이 적용 가능한 @Async로 저장 로직을 분리하고, 로그 수신 즉시 202 Accepted를 반환하도록 구성했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>FastAPI가 DB 저장 완료를 기다리지 않고 다음 프레임을 분석할 수 있도록 로그 수신과 저장의 실행 흐름을 분리했습니다.</p></div></section>
      </div>
    </article>

    <article class="trouble-card">
      <header class="trouble-card-header">
        <span>03</span>
        <div><p>DATA AGGREGATION</p><h3>Redis 실시간 집계와 MySQL 통계 저장의 역할 분리</h3></div>
      </header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>매초 발생하는 자세 상태를 모두 RDB에 저장하고 리포트마다 원본 로그를 집계하면 I/O와 조회 비용이 계속 증가합니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>RDB 단독, Redis 단독, Redis–MySQL 병행 구조를 실시간성·영속성·통계 신뢰도 측면에서 비교했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>실시간 상태와 카운트는 Redis Hash로 관리하고 경고 로그는 MySQL에 보관하며, 세션 종료 시점과 매일 03시에 통계를 집계했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>실시간 피드백과 장기 통계의 저장 책임을 분리하고, 세션 종료 직후 최신 결과가 리포트에 반영되는 구조를 구현했습니다.</p></div></section>
      </div>
    </article>
  </div>
</section>
