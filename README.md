# GoNetScan

GoNetScan은 Kubernetes 컨테이너의 네트워크 인터페이스 구조를 자동으로 수집하고 시각화 가능한 데이터로 정리하는 Go 기반 툴입니다.  
Flannel CNI 기반 클러스터에서 veth, bridge, netns 정보를 수집하여 eBPF 기반 트래픽 제어와 보안 정책 수립의 기초 자료로 활용할 수 있습니다.

---

##  주요 기능

- containerd 기반 컨테이너 목록 조회
- 컨테이너별 netns 접근 및 네트워크 인터페이스 정보 수집
- IP, MAC, Gateway, CIDR, Interface Index 등의 정보 구조화
- `netlink`, `procfs`, `ip netns`, `bash command` 활용
- 추후 eBPF 연동 및 정책 적용 기반 마련

---

##  기술 스택

- Go 1.20+
- containerd API
- vishvananda/netlink
- bash command parsing
- Kubernetes + Flannel (CNI)
- Ubuntu 20.04/22.04 (권장)

---

##  프로젝트 구조

gonetscan/
├── cmd/gonetscan/ # main() 실행 진입점
├── internal/
│ ├── container/ # 컨테이너 목록 수집 로직
│ ├── netns/ # netns 진입 및 처리
│ └── netinfo/ # 인터페이스 정보 수집
├── docs/ # 아키텍처 설명 및 실험 기록
├── go.mod
└── README.md


---
##  설치 및 실행

```bash
# Go 모듈 초기화 및 의존성 설치
go mod tidy

# 실행
go run cmd/gonetscan/main.go


---
broccoli-cake (https://github.com/broccoli-cake)
