# AlcoholFree-PlotTree

노드그래프 기반 비주얼 노벨 저작 도구(**PlotTree**)와, 그 도구로 저작한 비주얼 노벨 **ALCOHOL FREE**의 이전 버전 프로젝트입니다.

> 이 저장소는 논문 *「렌더 스테이트 테이블에서 착안한 프레임-스테이트 실행 모델 기반 비주얼 노벨 저작 프레임워크 (Visual Wave)」* 의 참고문헌 **[2]** — 즉 Visual Wave가 개선 대상으로 삼은 **선행 노드그래프 저작 도구** — 를 공개 검증용으로 제공합니다.

## 개요

- **엔진**: Unity 2022.3 (C#)
- 저장소는 두 가지를 함께 담습니다.
  1. **PlotTree 저작 도구** — 장면(Scene)을 노드로, 장면 간 연결을 간선으로 구성하는 노드그래프 에디터(언리얼 블루프린트·유니티 셰이더그래프와 유사)와, 각 장면을 **PowerPoint식 슬라이드 UI**로 편집하는 프레임 편집기.
  2. **ALCOHOL FREE (이전 버전)** — 위 도구로 저작한 비주얼 노벨.

## 저작 모델 — 논문 [2]의 비교 대상

PlotTree는 한 화면(프레임)을 **배경·캐릭터·음향·연출 등 전체 상태를 담은 객체**로 저장한다. 상태가 바뀌지 않아도 프레임마다 전체를 반복 기록하므로, 장면 데이터(`Assets/StreamingAssets/PlotData.json`)는 프레임 단위 전체-상태 스냅샷의 나열이다. 이 "전체 상태 반복 저장" 방식이 Visual Wave가 **변화분만 선언하는 프레임-스테이트 모델**로 개선한 지점이며, 논문의 정량 비교(대사 1자당 저장 용량·상태 중복률 등)가 이 데이터를 근거로 한다.

## 구조

```
Assets/
├─ Scripts/                 PlotTree 저작 도구 + 게임 로직
│  └─ UIs/PlotTreePage/     노드그래프 편집(Link, SceneItem, ScreenTransition, GlobalVariableCondition, …)
├─ StreamingAssets/
│  └─ PlotData.json         장면 그래프 + 프레임(전체 상태) 데이터
├─ Scenes/  Prefabs/  Materials/  Shaders/  Fonts/  …
```

## 포함되지 않은 것 (중요)

공개 배포 범위를 지키기 위해 아래는 저장소에서 제외했다. 프로젝트를 그대로 빌드·실행하려면 별도 복원이 필요하다.

- **Febucci Text Animator** (`Assets/Plugins/Febucci`) — 유료 Unity Asset Store 에셋이라 재배포할 수 없어 제외. 빌드하려면 Asset Store에서 직접 설치할 것.
- **게임 아트** (`Assets/Resources`) — 캐릭터·배경·CG 등 팀 창작 자산이라 공개 저장소에서 제외.

따라서 이 저장소는 **저작 도구의 설계와 데이터 포맷을 확인하기 위한 참조용**이며, 완전한 게임 실행본이 아니다.

## 저작자 및 이용

- 유현수 (Hyun-su Yu), 동명대학교 컴퓨터공학과
- 비주얼 노벨 *ALCOHOL FREE* 의 서사·자산 저작권은 제작 팀에 있다. 코드와 데이터는 연구 참조 목적으로 공개한다.
