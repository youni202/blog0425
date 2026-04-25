---
layout: default
title: Microsoft Learn MCP 서버와 Microsoft 365 Agents Toolkit 연결 기록
date: 2026-04-25 17:30:00 +0900
nav_exclude: true
image_dir: /assets/images/posts/microsoft-learn-mcp-agents-toolkit
---

# Microsoft Learn MCP 서버와 Microsoft 365 Agents Toolkit 연결 기록

Microsoft 365 Agents Toolkit으로 Declarative Agent를 만드는 과정에서 Microsoft Learn MCP 서버를 함께 확인해 보았다. 이번 글은 화면을 따라가며 어떤 도구를 열었고, 어떤 설정을 확인했는지 정리한 작업 기록이다.

핵심 흐름은 다음과 같다.

1. MCP Inspector에서 Microsoft Learn MCP 서버 도구를 확인한다.
2. 모델 컨텍스트 프로토콜 서버 정보를 등록한다.
3. Microsoft 365 Agents Toolkit에서 Declarative Agent 생성 흐름을 시작한다.
4. 로컬 서버와 포트 공개 상태를 확인한다.

## MCP Inspector에서 도구 확인

먼저 MCP Inspector에서 Microsoft Learn MCP 서버가 어떤 도구를 제공하는지 확인했다. 화면에는 `Microsoft Docs Search`, `Microsoft Code Sample Search`, `Microsoft Docs Fetch` 같은 도구가 보인다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/01-mcp-inspector-tools.png"
  alt="MCP Inspector에서 Microsoft Learn MCP Server가 연결되어 있고 Microsoft Docs Search, Microsoft Code Sample Search, Microsoft Docs Fetch 도구가 표시된 화면"
  caption="MCP Inspector에서 Microsoft Learn MCP 서버의 도구 목록을 확인한다."
  credit="출처: 직접 캡처"
%}

이 단계에서는 서버가 정상 연결되는지, 도구 목록이 노출되는지를 먼저 보는 것이 중요하다. 도구가 보이지 않으면 이후 에이전트나 클라이언트에서 호출할 기능도 확인하기 어렵다.

## MCP 서버 정보 등록

다음으로 모델 컨텍스트 프로토콜 서버를 추가하는 화면에서 서버 정보를 입력했다. 서버 이름, 설명, 서버 URL을 넣고 인증 방식은 없음으로 둔 상태다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/02-add-mcp-server.png"
  alt="모델 컨텍스트 프로토콜 서버 추가 화면에서 서버 이름, 서버 설명, 서버 URL을 입력하는 폼"
  caption="MCP 서버를 추가할 때는 이름, 설명, URL, 인증 방식을 명확히 입력한다."
  credit="출처: 직접 캡처"
%}

여기서는 서버 URL이 가장 중요하다. 예시 화면에서는 Microsoft Learn MCP 엔드포인트를 넣는 흐름을 보여준다.

## Microsoft 365 Agents Toolkit 시작

Microsoft 365 Agents Toolkit에서는 `Build a Declarative Agent` 튜토리얼 흐름을 선택했다. 이 화면은 환경 준비, 에이전트 생성, 미리 보기, 개선 단계로 이어지는 가이드 역할을 한다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/03-agents-toolkit-start.png"
  alt="Visual Studio Code의 Microsoft 365 Agents Toolkit 시작 화면에서 Build a Declarative Agent 가이드가 열린 모습"
  caption="Microsoft 365 Agents Toolkit에서 Declarative Agent 생성 가이드를 시작한다."
  credit="출처: 직접 캡처"
%}

처음에는 Copilot 라이선스, Node.js, npm 같은 기본 개발 환경을 확인한다. 이 단계가 준비되어야 에이전트 프로젝트 생성과 미리 보기가 자연스럽게 이어진다.

## Declarative Agent 생성 옵션 선택

에이전트를 만들 때는 어떤 형태로 시작할지 선택한다. 화면에는 액션 없이 생성하는 옵션, 액션을 추가하는 옵션, Copilot connector를 추가하는 옵션, TypeSpec으로 시작하는 옵션이 보인다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/04-create-agent-action.png"
  alt="Create Declarative Agent 선택 창에서 No Action, Add an Action, Add a Copilot connector, Start with TypeSpec 옵션이 표시된 화면"
  caption="Declarative Agent 생성 시 액션이나 커넥터를 붙일지 선택한다."
  credit="출처: 직접 캡처"
%}

처음 구조를 확인할 때는 `No Action`처럼 가장 단순한 옵션으로 시작하는 편이 좋다. 이후 필요한 기능이 명확해지면 액션이나 커넥터를 추가해도 늦지 않다.

## 작업 영역 폴더 선택

에이전트 프로젝트를 만들 위치도 지정해야 한다. 기본 폴더를 사용하거나 직접 찾아보기로 프로젝트 루트 폴더를 선택할 수 있다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/05-select-workspace-folder.png"
  alt="작업 영역 폴더 선택 창에서 기본 폴더와 찾아보기 옵션이 표시된 화면"
  caption="에이전트 프로젝트가 생성될 작업 영역 폴더를 선택한다."
  credit="출처: 직접 캡처"
%}

프로젝트가 늘어날 것을 생각하면 에이전트 실험용 폴더를 따로 두는 편이 관리하기 쉽다.

## Microsoft Learn MCP 서버 직접 연결 확인

다시 MCP Inspector에서 Microsoft Learn MCP 서버를 직접 연결해 보았다. 이번 화면에서는 URL이 `https://learn.microsoft.com/api...` 형태로 들어가 있고, 도구 목록이 다시 표시된다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/06-microsoft-learn-mcp-server.png"
  alt="MCP Inspector에서 Microsoft Learn API URL로 연결하고 Microsoft Docs Search, Microsoft Code Sample Search, Microsoft Docs Fetch 도구 목록을 확인하는 화면"
  caption="Microsoft Learn MCP 서버에 직접 연결해 제공 도구를 다시 확인한다."
  credit="출처: 직접 캡처"
%}

이 화면은 서버 연결이 정상인지 검증하는 기준점으로 쓸 수 있다. 도구 목록이 보이고 `tools/list` 호출 이력이 남으면 서버가 응답하고 있다는 뜻이다.

## 로컬 서버와 포트 공개 확인

마지막 화면은 VS Code에서 로컬 MCP 서버와 포트 상태를 확인하는 장면이다. 포트 8000이 전달되어 있고, 포트 가시성 메뉴에서 공개/비공개 설정을 확인하고 있다.

{% include figure.html
  src="/assets/images/posts/microsoft-learn-mcp-agents-toolkit/07-local-server-port.png"
  alt="Visual Studio Code에서 로컬 MCP 서버 프로젝트를 열고 포트 8000의 포트 가시성 메뉴를 확인하는 화면"
  caption="로컬 MCP 서버를 외부에서 접근해야 할 때는 포트 전달과 공개 여부를 확인한다."
  credit="출처: 직접 캡처"
%}

MCP Inspector나 다른 클라이언트에서 로컬 서버를 호출하려면 서버 프로세스가 실행 중이어야 하고, 필요한 경우 포트가 접근 가능한 상태여야 한다.

## 정리

이번 흐름은 Microsoft Learn MCP 서버를 단순히 등록하는 데서 끝나지 않고, 실제 도구 목록이 보이는지와 로컬 서버 접근 경로가 준비되는지까지 확인하는 과정이었다.

체크할 지점은 다음과 같다.

| 단계 | 확인할 것 |
| --- | --- |
| MCP Inspector 연결 | 서버 URL과 연결 상태 |
| 도구 목록 확인 | `Microsoft Docs Search`, `Microsoft Docs Fetch` 등 |
| Agents Toolkit 시작 | Declarative Agent 생성 흐름 |
| 프로젝트 폴더 선택 | 작업 영역 위치 |
| 로컬 서버 확인 | 실행 중인 프로세스와 포트 공개 여부 |

{: .tip }
이미지 기반으로 작업 기록을 남길 때는 화면 순서뿐 아니라 “왜 이 화면을 확인했는지”를 함께 적어두면 나중에 다시 따라가기 쉽다.
