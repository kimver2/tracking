---
name: autonomous-workflow
description: Guide and runbook for fully autonomous execution, hybrid model delegation (Argon + pro/flash subagents), testing, and GitHub Pages deployment in /Users/kimver2/orca/projects/tracking.
---

# Autonomous Workflow & Live Deployment Runbook

이 스킬은 `/Users/kimver2/orca/projects/tracking` 작업 공간에서 **선박 및 컨테이너 실시간 위치 조회 시스템**의 기능 개발, 품질 검증 및 GitHub Pages(`https://kimver2.github.io/tracking/`) 자동 배포를 수행하기 위한 자율 실행 런북입니다.

---

## 1. 모델 이원화 역할 분담 (Argon + `pro` / `flash`)

1. **메인 에이전트 (`Argon`) — 설계 및 명세 수립 전담**:
   - 요구사항을 분석하고 UI 컴포넌트, 해운 데이터 소스 매핑, 검색 로직 구조를 명세화합니다.
2. **고성능 구현 서브에이전트 (`pro-coder`, `Model: "pro"`)**:
   - 해운사 BIC 컨테이너 번호 접두사 파싱, AIS API/임베드 브릿지 연동, 지도 시각화 레이어 등 복잡한 프론트엔드/백엔드 로직을 작성합니다.
3. **경량 고속 서브에이전트 (`flash-coder`, `Model: "flash"`)**:
   - UI 스타일링, 문구 수정, HTML 구문 검사, Git 커밋 및 GitHub Pages 배포(`git push origin main`)를 신속하게 완수합니다.

---

## 2. 배포 및 라이브 파이프라인

1. **코드 변경 및 로컬 검증**:
   - `index.html` 내 JavaScript 구문 오류 검사 (`node -c` 등 활용)
   - 모바일(375px~430px) 및 PC(1200px+) 레이아웃 무결성 확인
2. **GitHub Pages 자동 배포**:
   - `git add -A && git commit -m "..." && git push origin main` 실행
   - `https://kimver2.github.io/tracking/` 에서 즉각 라이브 서비스 제공
