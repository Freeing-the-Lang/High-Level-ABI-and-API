# 🧽 Spongelang Meta — High-Level ABI & API Specification
모든 언어 변종을 하나의 파이프라인으로 연결하기 위한 **Spongelang 메타언어 중심 ABI/API 규격 리포**입니다.  
Spongelang은 메인 언어가 아니라 **모든 언어를 흡수·연결하는 Meta-Lang**입니다.

이 리포는 Spongelang 생태계 전체의 공통 인터페이스(ABI/API)와 언어 간 파이프라인 기준을 정의합니다.

---

## 🎯 목적
여러 언어(Rust-like-XX, Go-like-XX, Lua-like-XX 등)가 Spongelang을 통해 서로 호환되도록 하는  
**공통 ABI/API·메모리 레이아웃·호출 규칙**을 제공합니다.

Spongelang이 중앙 허브로 움직이기 위한 기반 규격입니다.

---

## 📦 구성 요소

### 1. High-Level ABI (Application Binary Interface)
Spongelang이 이해하는 메타 타입/메모리 구조를 정의합니다.

- 메타 Primitive: `MetaInt`, `MetaFloat`, `MetaByte`, `MetaBool`
- 메타 참조 타입: `MetaStringRef`, `MetaBuffer`, `MetaArrayRef`
- 메타 레이아웃: Stackless/Heap-Hop 기반 구조
- 언어 변종 간 데이터 변환 규칙

### 2. High-Level API (Function/Module Interface)
Spongelang이 호출하는 공통적 API 규격을 정의합니다.

- 함수 식별자 `MetaFunctionID`
- Meta 호출 규칙  
- Context 기반 실행 모델  
- 결과 핸들링 구조

### 3. Language Adapters
각 언어 변종 → Spongelang Meta 변환 계층입니다.

예:
- `rust_like_adapter/`
- `go_like_adapter/`
- `lua_like_adapter/`
- `swift_like_adapter/`

각 어댑터는:
- AST 변환
- Meta 타입 매핑
- Meta API 호출 래핑  
을 담당합니다.

### 4. Pipelines (언어A → Meta → 언어B/OS)
Spongelang 메타언어를 중심으로 언어들이 상호작용하는 전체 흐름을 정의합니다.

예:



Rust-like-Lua  →  Meta-ABI/API  →  Multi-Main-OS
Go-like-Rust   →  Meta-ABI/API  →  C++ Runtime
Lua-like-Java  →  Meta-ABI/API  →  Spongelang Toolchain



---

## 📁 디렉토리 구조




High-Level-ABI-and-API/
├── docs/
│   ├── overview.md
│   ├── abi_spec.md
│   ├── api_spec.md
│   └── pipelines.md
├── src/
│   ├── spongelang_meta/
│   │   ├── meta_types.h
│   │   ├── meta_api.h
│   │   └── meta_pipeline.cpp
│   ├── adapters/
│   │   ├── rust_like/
│   │   ├── go_like/
│   │   └── lua_like/
│   └── examples/
│       └── basic_pipeline.md
├── tests/
│   └── pipeline_tests/
└── README.md



---

## 🧪 Example: Meta Pipeline 흐름

### Rust-like → Meta → Multi-Main OS

```text
1. Rust-like 언어 코드 → Tracer → Meta AST 생성  
2. Meta AST → Meta IR 변환  
3. Meta IR → API 호출 패턴 생성  
4. Multi-Main OS 런타임에서 실행  



Lua-like → Meta → C++ Runtime


1. Lua-like 파서 → Meta 타입 매핑  
2. Meta 호출 규격으로 포장  
3. C++ 기반 런타임이 Meta 함수 실행  




⚙️ 빌드 / 테스트


git clone https://github.com/Freeing-the-Lang/High-Level-ABI-and-API
cd High-Level-ABI-and-API



(추후 Spongelang Meta Toolchain 연결 예정)


테스트:


./scripts/run-tests.sh




🧾 ProofLedger


릴리즈 시 자동 생성되는 ProofLedger에는 다음이 포함됩니다:




SHA256 체크섬


버전/브랜치 정보


생성 시간


Meta API/ABI 빌드 정보





🤝 기여




새로운 언어 어댑터 추가


Meta 타입 확장


파이프라인 테스트 케이스 추가


문서 보완




언제든 자유롭게 PR 가능.



📜 라이선스


MIT License



---

