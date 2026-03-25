# 시스템 요구사항

Claude Code를 설치하기 전에, 여러분의 시스템이 아래 요구사항을 충족하는지 확인하세요.

---

## 운영체제 (OS)

Claude Code는 다음 운영체제에서 지원됩니다:

### macOS
- **최소 버전:** macOS 10.15 (Catalina) 이상
- Intel Mac과 Apple Silicon (M1/M2/M3/M4) 모두 지원
- 대부분의 macOS 사용자는 추가 설정 없이 바로 사용할 수 있습니다

### Linux
- **Ubuntu:** 20.04 LTS 이상
- **Debian:** 10 (Buster) 이상
- 기타 주요 Linux 배포판도 지원되지만, 위 두 가지가 공식적으로 테스트된 환경입니다
- x86_64 및 ARM64 아키텍처 모두 지원

### Windows
- **Windows에서는 직접 실행이 불가능합니다**
- **WSL2 (Windows Subsystem for Linux 2)** 를 통해 사용해야 합니다
- WSL2 내에서 Ubuntu 20.04 이상을 설치한 후 Linux와 동일하게 사용합니다
- Windows 10 버전 2004 이상 또는 Windows 11이 필요합니다

> **Windows 사용자 참고:** WSL2는 Windows에서 Linux 환경을 실행하는 Microsoft 공식 기능입니다. 아직 WSL2를 설치하지 않았다면, [설치 가이드](./install-guide.md)에서 상세한 설정 방법을 확인할 수 있습니다.

---

## Node.js

Claude Code는 Node.js 기반으로 동작합니다.

- **최소 버전:** Node.js 18 이상
- **권장 버전:** Node.js 20 LTS 또는 Node.js 22 LTS

### Node.js 버전 확인 방법

터미널에서 다음 명령어를 실행하세요:

```bash
node --version
```

출력 예시:
```
v20.11.0
```

`v18` 이상이 출력되면 준비가 완료된 것입니다.

### Node.js가 설치되어 있지 않거나 버전이 낮은 경우

Node.js 설치 방법은 운영체제에 따라 다릅니다:

**macOS (Homebrew 사용):**
```bash
brew install node
```

**Ubuntu/Debian:**
```bash
# NodeSource 저장소를 통한 설치 (Node.js 20 LTS)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**노드 버전 관리자 (nvm) 사용 - 모든 OS:**
```bash
# nvm 설치
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# 터미널 재시작 후
nvm install 20
nvm use 20
```

> **팁:** 여러 프로젝트에서 서로 다른 Node.js 버전을 사용해야 한다면, `nvm`을 사용하는 것을 강력히 권장합니다. 프로젝트별로 Node.js 버전을 쉽게 전환할 수 있습니다.

---

## npm (Node Package Manager)

npm은 Node.js를 설치하면 함께 설치됩니다.

- **최소 버전:** npm 8 이상 (Node.js 18에 포함)

### npm 버전 확인

```bash
npm --version
```

npm이 오래된 경우 업데이트:
```bash
npm install -g npm@latest
```

---

## 하드웨어 요구사항

### 메모리 (RAM)

| 구분 | 용량 | 설명 |
|------|------|------|
| **최소** | 4GB | 기본적인 사용이 가능하지만, 대규모 프로젝트에서는 느릴 수 있습니다 |
| **권장** | 8GB 이상 | 대부분의 프로젝트에서 쾌적하게 사용할 수 있습니다 |

> **참고:** Claude Code 자체는 많은 메모리를 사용하지 않습니다. 다만, 개발 환경(IDE, 브라우저, Docker 등)과 함께 사용할 때 충분한 메모리가 필요합니다.

### 디스크 공간

| 구분 | 용량 | 설명 |
|------|------|------|
| **Claude Code 자체** | ~500MB | npm 패키지 및 의존성 포함 |
| **Node.js** | ~100MB | Node.js 런타임 |
| **여유 공간** | 1GB 이상 권장 | 임시 파일 및 캐시 용도 |

---

## 네트워크 요구사항

Claude Code는 **인터넷 연결이 필수**입니다.

- Claude Code는 로컬에서 AI 모델을 실행하지 않습니다
- 모든 AI 처리는 Anthropic의 API 서버에서 이루어집니다
- 요청을 보내고 응답을 받기 위해 안정적인 인터넷 연결이 필요합니다

### 네트워크 관련 참고사항

- **방화벽/프록시:** 회사 네트워크에서 사용하는 경우, `api.anthropic.com` 도메인에 대한 HTTPS (포트 443) 접근이 허용되어야 합니다
- **대역폭:** 일반적인 사용에서 많은 대역폭을 소모하지 않습니다. 텍스트 기반 API 통신이므로 일반 웹 브라우징 수준입니다
- **오프라인 사용:** 오프라인에서는 사용할 수 없습니다. 다만, 이전 대화 내용은 로컬에 캐시될 수 있습니다

---

## 인증 요구사항 (API 키 또는 구독)

Claude Code를 사용하려면 다음 중 하나가 필요합니다:

### 방법 1: Anthropic API 키

- [Anthropic Console](https://console.anthropic.com)에서 API 키를 발급받을 수 있습니다
- API 사용량에 따라 과금됩니다 (종량제)
- 개인 개발자나 소규모 프로젝트에 적합합니다

### 방법 2: Claude 구독 플랜

Claude Code는 다음 구독 플랜에서 사용할 수 있습니다:

| 플랜 | 설명 | Claude Code 포함 |
|------|------|------------------|
| **Claude Max** | 개인 사용자를 위한 프리미엄 플랜 | 포함 |
| **Claude Team** | 팀 단위 사용을 위한 플랜 | 포함 |
| **Claude Enterprise** | 기업용 플랜 (SSO, 감사 로그 등) | 포함 |

> **비용 참고:** API 키 방식은 사용량에 비례하여 과금됩니다. 구독 플랜은 월정액이므로 사용량이 많다면 구독이 더 경제적일 수 있습니다. 자세한 요금 정보는 [Anthropic 가격 페이지](https://www.anthropic.com/pricing)를 참조하세요.

---

## 요구사항 체크리스트

설치 전에 아래 항목을 확인하세요:

```
[ ] 운영체제: macOS 10.15+, Ubuntu 20.04+, Debian 10+, 또는 Windows + WSL2
[ ] Node.js 18 이상 설치 완료 (node --version 으로 확인)
[ ] npm 8 이상 설치 완료 (npm --version 으로 확인)
[ ] 메모리 4GB 이상 (8GB 권장)
[ ] 디스크 여유 공간 1GB 이상
[ ] 안정적인 인터넷 연결
[ ] Anthropic API 키 또는 Claude 구독 플랜 준비
```

모든 항목이 확인되었다면, [설치 가이드](./install-guide.md)로 진행하세요.

---

## 다음 단계

- [설치 가이드](./install-guide.md) - OS별 상세 설치 방법
- [첫 실행 가이드](./first-run.md) - 설치 후 첫 실행 및 초기 설정
