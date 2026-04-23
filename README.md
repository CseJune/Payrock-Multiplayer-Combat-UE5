# 폐의록: 왕이 남기고 간 죄

Unreal Engine 5와 C++ 기반으로 멀티플레이 전투 시스템을 구현하고 그 과정에서 발생한 동기화 문제를 해결한 프로젝트입니다.

[Gameplay](https://www.youtube.com/watch?v=LPgUK3iawyQ)
---

## 프로젝트 개요

- 개발 기간: 2025.05 ~ 2025.07
- 팀 구성: 7인
- 담당 역할: 캐릭터 전투 시스템 및 애니메이션 연동

---

## 사용 기술

- Unreal Engine 5
- C++
- Gameplay Ability System (GAS)
- Replication / RPC / Multicast
- Animation Blueprint / Montage / BlendSpace
- Enhanced Input

---

## 주요 구현 내용

### 1. 멀티플레이 전투 동기화

- Server RPC 기반으로 공격 및 데미지 처리 통합
- ReplicatedUsing으로 상태 동기화
- Multicast를 통해 사운드 및 이펙트 동기화

멀티플레이 환경에서 클라이언트 간 전투 결과 불일치를 해결하여 안정적인 전투 경험 구현

---

### 2. 루트모션 기반 공격 동기화 문제 해결

- 클라이언트 MovementMode를 MOVE_None으로 설정해 예측 이동 차단
- 루트모션을 서버에서만 처리하도록 구조 변경
- 클라이언트는 서버 위치 기준으로 보간 처리

공격 시 위치 오차 제거 및 자연스러운 전투 흐름 구현

---

### 3. 사운드 및 이펙트 동기화

- AnimNotify → Server RPC → Multicast 구조로 개선
- PlaySoundAtLocation 기반으로 위치 동기화
- Sound Attenuation 적용

모든 클라이언트에서 동일한 타이밍으로 사운드 재생

---

### 4. 콤보 기반 데미지 시스템

- 몽타주 섹션 이름 기반 콤보 인덱스 추출
- 콤보 단계별 데미지 계수 적용
- 무기 타입(Enum) 기반 추가 배율 적용
- GAS를 통한 유연한 데미지 계산 구조

콤보 흐름에 따른 타격감 개선 및 전투 차별화

---

### 5. 애니메이션 시스템 구현

- BlendSpace 및 Animation Blueprint 기반 이동 애니메이션 구현
- 무기 타입(Enum)에 따른 애니메이션 분기 처리
- Layered Blend Per Bone을 활용한 상체/하체 분리 애니메이션 적용

전투 상황에 맞는 자연스러운 애니메이션 전환 구현

## 플레이 영상

(추후 업로드 예정)

---

## 프로젝트를 통해 얻은 경험

- 멀티플레이 환경에서의 상태 동기화 및 네트워크 구조 설계 경험
- GAS 기반 전투 시스템 구현 및 확장 가능한 구조 설계
- 애니메이션과 게임 로직을 연동한 전투 흐름 설계
- 문제 원인 분석 및 구조 개선을 통한 해결 경험

---

## 참고

※ 현재 포트폴리오 정리 및 영상 업로드 진행 중입니다.
