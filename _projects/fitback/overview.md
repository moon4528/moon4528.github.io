---
layout: project
title: FitBack
project: FitBack
section: overview
order: 1
summary: 상담 후 미등록 고객의 이탈 사유를 AI로 분석하고 재연락 시점과 메시지를 제안하는 피트니스 센터 후속관리 서비스
project_image: /assets/images/projects/fitback.png
github: https://github.com/TAVE-FitBack/BE
stack:
  - Java 21
  - Spring Boot
  - PostgreSQL
  - Redis
  - AWS (EC2, RDS)
  - Docker
  - GitHub Actions
  - Nginx
  - FastAPI
  - OpenAI
  - Neo4j
impact:
  - value: TAVE 17기
    detail: IT 연합동아리 수료
    label: COMMUNITY
    emphasis: true
  - value: AWS SAA
    detail: 자격증 스터디 진행
    label: STUDY
    emphasis: true
  - value: 프로젝트 블로그
    detail: TAVE 공식 블로그 게시
    label: PROJECT FEATURE
    url: https://blog.naver.com/PostView.naver?blogId=t-ave&logNo=224385898251&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView
    emphasis: true
  - value: 스터디 블로그
    detail: TAVE 공식 블로그 게시
    label: STUDY FEATURE
    url: https://blog.naver.com/PostView.naver?blogId=t-ave&logNo=224364372758&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView
    emphasis: true
---

<section class="project-section">
  <header class="project-section-title"><span>02</span><h2>BACKGROUND</h2></header>
  <div class="project-copy project-background">
    <p class="project-background-intro">헬스장·PT 상담 및 운영 경험자 <strong>5명</strong>을 인터뷰한 결과, 상담 기록의 번거로움과 재연락 우선순위 기준의 부재로 미등록 잠재고객이 관리에서 누락되는 문제를 확인했습니다.</p>
    <div class="project-background-block">
      <strong class="project-background-label">핵심 기능</strong>
      <p class="project-background-tags"><code>AI 상담 분석</code><code>재연락 우선순위</code><code>맞춤 메시지 초안</code><code>후속관리 전환 리포트</code></p>
    </div>
    <div class="project-background-block">
      <strong class="project-background-label">주요 경험</strong>
      <ol class="project-background-list">
        <li>모호한 화면 표현값을 데이터 출처·상태·갱신 트리거로 구체화</li>
        <li>PM·Design·Frontend·AI 간 API 계약과 업무 흐름 정렬</li>
        <li>외부 AI 장애를 격리하는 비동기 분석 생명주기 설계</li>
        <li>상태 전이·DB 제약·잠금을 통한 고객 데이터 정합성 보장</li>
      </ol>
    </div>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>03</span><h2>ARCHITECTURE</h2></header>
  <div class="project-diagram-list">
    <figure class="project-diagram-card">
      <figcaption><span>01</span><div><strong>System Architecture</strong><p>Spring Boot·FastAPI와 AWS 인프라, AI 서비스 연동 구조</p></div></figcaption>
      <a href="{{ '/assets/images/projects/fitback-system-architecture.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
        <img src="{{ '/assets/images/projects/fitback-system-architecture.png' | relative_url }}" alt="FitBack 시스템 아키텍처 다이어그램" loading="lazy">
      </a>
    </figure>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>04</span><h2>CONTRIBUTIONS</h2></header>
  <div class="contributions-list">
    <article class="activity-card">
      <div class="activity-index">01</div>
      <div><p class="activity-label">DOMAIN MODELING</p><h3>화면 표현값을 데이터 규칙으로 구체화</h3><p>AI 미전환 사유의 판단 근거, 후속 연락 우선순위, Next Best Action 갱신 시점처럼 모호했던 요구를 데이터 출처·상태·트리거·이력 보존 규칙으로 변환했습니다.</p></div>
    </article>
    <article class="activity-card">
      <div class="activity-index">02</div>
      <div><p class="activity-label">SPECIFICATION WORKFLOW</p><h3>분야 간 소통을 실행 가능한 계약으로 정렬</h3><p>PM·Design·Frontend·AI가 서로 다른 기준을 참조하지 않도록 Issue·화면·시퀀스·API·스키마의 우선순위를 정하고, AI coding agent도 같은 SSOT와 충돌 보고 규칙을 따르게 했습니다.</p></div>
    </article>
    <article class="activity-card">
      <div class="activity-index">03</div>
      <div><p class="activity-label">ASYNC AI LIFECYCLE</p><h3>상담 저장과 AI 분석의 생명주기 분리</h3><p>트랜잭션 커밋 이후 @Async로 FastAPI 분석을 실행하고 PROCESSING·COMPLETED·FAILED 상태를 제공해, AI 장애와 지연이 상담 등록을 막지 않도록 구성했습니다.</p></div>
    </article>
    <article class="activity-card">
      <div class="activity-index">04</div>
      <div><p class="activity-label">DATA INTEGRITY</p><h3>고객 라이프사이클의 상태 정합성 보장</h3><p>문의→상담→AI 분석→후속 연락→재상담·등록 흐름을 상태 전이로 연결하고, 비관적 잠금과 PostgreSQL 제약으로 중복 전환과 복수 활성 후속관리를 방지했습니다.</p></div>
    </article>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>05</span><h2>TROUBLE SHOOTING</h2></header>
  <div class="trouble-list">
    <article class="trouble-card">
      <header class="trouble-card-header"><span>01</span><div><p>REQUIREMENT CLARIFICATION</p><h3>모호한 화면 표현값을 상태와 트리거 계약으로 변환</h3></div></header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>B2B 화면에 많은 정보를 담는 과정에서 AI 미전환 사유의 근거, 후속 연락 우선순위, Next Best Action의 동기화 시점이 명확하지 않아 분야마다 다르게 해석했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>화면 단위 요청을 그대로 구현하면 변경 때마다 API와 AI 계약이 흔들렸습니다. 각 표현값마다 원천 데이터·계산 책임·갱신 이벤트·이력 보존 여부를 먼저 확정해야 했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>PM과 화면 의도를 확인한 뒤 Issue·디자인·시퀀스·API·스키마 순으로 계약을 정렬하고, 모순은 선택지와 영향 범위를 문서화해 결정 이후에만 구현했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>Next Best Action 갱신을 신규 상담 분석·재상담 분석·명시적 재생성으로 한정하고, 단순 정보 수정과 메시지 작업이 불필요한 재분석을 만들지 않도록 분리했습니다.</p></div></section>
      </div>
    </article>

    <article class="trouble-card">
      <header class="trouble-card-header"><span>02</span><div><p>FAILURE ISOLATION</p><h3>외부 AI 장애가 상담 등록을 실패시키지 않도록 분리</h3></div></header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>상담 저장 트랜잭션 안에서 FastAPI와 LLM 응답을 기다리면 지연이나 장애가 고객·상담 데이터 저장까지 롤백시킬 수 있었습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>동기 호출, 커밋 전 비동기 호출, 커밋 후 이벤트 실행을 비교했습니다. 핵심 데이터의 영속화를 먼저 보장하면서 AI 결과는 최종 일관성으로 처리하는 방식을 선택했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>ApplicationEventPublisher와 AFTER_COMMIT 리스너, @Async를 조합하고 분석 상태를 PROCESSING·COMPLETED·FAILED로 관리했습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>상담 등록은 AI 완료를 기다리지 않고 201 Created를 반환하며, AI 실패 시에도 상담 데이터는 유지하고 FAILED 상태를 통해 프론트가 결과를 처리하도록 했습니다.</p></div></section>
      </div>
    </article>

    <article class="trouble-card">
      <header class="trouble-card-header"><span>03</span><div><p>CONCURRENCY CONTROL</p><h3>동일 문의가 두 개의 상담으로 전환되는 경쟁 조건 방지</h3></div></header>
      <div class="paar-grid">
        <section class="paar-item"><span>P</span><div><strong>Problem</strong><p>상담 전환 버튼을 빠르게 누르거나 동일 문의에 요청이 동시에 들어오면 상태 확인을 모두 통과해 상담이 중복 생성될 가능성이 있었습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Analyze</strong><p>애플리케이션의 선조회만으로는 경쟁 조건을 막을 수 없었습니다. 충돌 빈도보다 중복 생성의 비용이 커서 동일 inquiry row를 직렬화하는 비관적 잠금을 선택했습니다.</p></div></section>
        <section class="paar-item"><span>A</span><div><strong>Action</strong><p>PESSIMISTIC_WRITE로 문의를 조회하고 잠금 획득 후 CONVERTED 상태를 다시 검사했으며, 고객·상담 식별자에는 DB Unique Constraint를 추가 방어선으로 뒀습니다.</p></div></section>
        <section class="paar-item paar-result"><span>R</span><div><strong>Result</strong><p>두 트랜잭션을 동시에 실행한 PostgreSQL 통합 테스트에서 두 번째 요청이 첫 커밋까지 대기한 뒤 CONVERTED 상태를 확인하는 것을 검증했습니다.</p></div></section>
      </div>
    </article>
  </div>
</section>
