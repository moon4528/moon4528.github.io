---
layout: project
title: BitePick
project: BitePick
section: overview
order: 1
summary: 사용자의 취향과 상황에 맞는 선택을 돕는 실서비스 백엔드 프로젝트입니다.
project_image: /assets/images/projects/bitepick.png
github: https://github.com/moon4528
stack:
  - Spring Boot
  - PostgreSQL
impact:
  - value: 실서비스
    label: SERVICE
  - value: Backend
    label: ROLE
  - value: 2026.08 ~ 현재
    label: PERIOD
---

<section class="project-section">
  <header class="project-section-title"><span>02</span><h2>BACKGROUND</h2></header>
  <div class="project-copy">
    <h3>취향과 상황에 맞는 선택을 더 쉽게</h3>
    <p>BitePick은 사용자가 자신의 취향과 현재 상황에 맞는 선택을 할 수 있도록 돕는 실서비스입니다. 백엔드 개발자로 참여해 핵심 사용자 흐름을 API와 데이터 구조로 구체화하고, 개발 결과가 실제 운영 환경까지 자연스럽게 이어질 수 있는 기반을 만들고 있습니다.</p>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>03</span><h2>ARCHITECTURE</h2></header>
  <div class="architecture-grid">
    <article><span>01</span><h3>API SERVER</h3><p>사용자 흐름과 비즈니스 규칙을 API의 책임으로 구분합니다.</p></article>
    <article><span>02</span><h3>DATA</h3><p>서비스 데이터의 저장 책임과 변경 흐름을 명확히 정리합니다.</p></article>
    <article><span>03</span><h3>OPERATION</h3><p>개발 환경, 배포 방식, 환경 변수 관리 기준을 운영 관점에서 연결합니다.</p></article>
  </div>
</section>

<section class="project-section">
  <header class="project-section-title"><span>04</span><h2>CONTRIBUTIONS</h2></header>
  <article class="activity-card">
    <div class="activity-index">01</div>
    <div>
      <p class="activity-label">DEVELOPMENT &amp; DEPLOYMENT</p>
      <h3>기능 개발 전에 실행과 배포의 기준부터 맞추다</h3>
      <p>서비스 기능이 늘어난 뒤 환경 차이를 해결하려 하면 재현과 배포 비용이 커질 수 있어, 초기 단계부터 동일한 실행 기준이 필요했습니다. 로컬 개발의 편의성만 보는 방식과 운영 환경을 먼저 고정하는 방식을 비교하고, 현재 인프라에서 바로 적용할 수 있는 배포 대상·실행 방식·환경 변수 관리부터 정리했습니다.</p>
      <p>그 결과 개발 환경과 배포 환경에서 분리해야 할 항목이 명확해졌고, 이후 로그와 모니터링 및 데이터베이스 백업 정책을 붙일 수 있는 기준을 마련했습니다. 정량적인 효과는 운영 데이터가 확보된 뒤 실제 수치로 검증해 추가할 예정입니다.</p>
      <div class="activity-tags"><span>환경 분리</span><span>배포 기준</span><span>운영 준비</span></div>
    </div>
  </article>
</section>

<section class="project-section">
  <header class="project-section-title"><span>05</span><h2>TROUBLE SHOOTING</h2></header>
  <div class="trouble-empty">
    <span>DOCUMENTING</span>
    <p>현재 공개 가능한 트러블슈팅 사례를 정리하고 있습니다. 문제의 재현 조건, 원인 후보와 선택지, 해결 과정, 검증 지표를 함께 기록할 예정입니다.</p>
  </div>
</section>
