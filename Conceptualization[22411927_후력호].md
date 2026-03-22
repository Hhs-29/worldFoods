# Conceptualization
# 전 세계의 음식들

**Student No**: 22411927
**Name**: 후력호  
**E-mail**: 654106904@qq.com

## Revision history
| Revision date | Version # | Description | Author |
| --- | --- | --- | --- |
| 03/22/2026 | 0.00 | First draft | 후력호 |

---

# Contents
1. Business purpose
2. System context diagram
3. Use case list
4. Concept of operation
5. Problem statement
6. Glossary
7. References

---

# 1. Business purpose
세상에는 요리 조리법을 알려주는 많은 앱이 있다. 하지만 대부분의 앱들은 단지 어떻게 음식을 만드는지를 알려주기만 하는 단조로운 패턴을 가지고 있다. 이런 앱과 차별화를 가진 조리법 앱을 만들고자 ‘전 세계의 음식들’ 프로젝트를 기획하였다.

본 앱은 **나라별로 고유한 음식과 조리법**을 제공하는 것이 핵심이다. 기존 앱들이 음식 종류나 대륙별로만 분류하는 것과 달리, 각 나라의特色 있는 음식을 보여주며 여행이 어려운 시기에 집에서 전 세계 요리를 경험할 수 있도록 한다. 또한 OPEN API를 통해 재료 가격과 정보를 제공하여 편의성을 높인다.

**Goal**:
- 나라별 특색 음식 및 조리법 제공
- 재료 정보 및 가격 연동 서비스
- 사용자 간 리뷰 및 평가 시스템
- 요리사 사용자의 콘텐츠 등록

**Target market**: 요리를 좋아하는 일반 사용자, 집에서 요리하는 사람, 세계 음식에 관심 있는 사람.

---

# 2. System context diagram
```
+-----------------+        +------------------------+        +-------------+
|    Users        | -----> |    전 세계의 음식들     | -----> | DB 서버     |
|    (일반사용자) |        |    시스템              |        | (음식,회원, |
|    Cooks        |        |                        |        |  리뷰 저장) |
|    Admin        |        |                        |        |             |
+-----------------+        +------------------------+        +-------------+
```
**설명**:
- **Users/Cooks/Admin**: 시스템을 사용하는 주체
- **시스템**: 회원관리, 음식/조리법 관리, 추천, 리뷰 기능 수행
- **DB 서버**: 회원 정보, 음식 정보, 조리법, 별점/리뷰 저장

---

# 3. Use case list
| No | Use case name | Actor | Description |
| --- | --- | --- | --- |
| 1 | 회원가입 | Users, Cooks | 서비스 사용을 위해 회원 등록 |
| 2 | 로그인 | Users, Cooks, Admin | 등록된 계정으로 로그인 |
| 3 | 로그아웃 | Users, Cooks, Admin | 로�그아웃 |
| 4 | 나라 조회 | Users, Cooks | 나라 목록 조회 |
| 5 | 음식 리스트 조회 | Users, Cooks | 해당 나라 음식 목록 조회 |
| 6 | 음식 정보 조회 | Users, Cooks | 음식 재료 및 정보 확인 |
| 7 | 조리법 조회 | Users, Cooks | 음식 조리 과정 확인 |
| 8 | 요리사 등록 요청 | Users | 일반 사용자가 요리사로 등록 신청 |
| 9 | 음식 등록 요청 | Cooks | 요리사가 음식 등록 요청 |
| 10 | 조리법 등록 요청 | Cooks | 요리사가 조리법 등록 요청 |
| 11 | 음식 추천 | Users, Cooks | 무작위/취향 기반 음식 추천 |
| 12 | 요리사 관리 | Admin | 요리사 등록 승인/거부 |
| 13 | 음식/조리법 관리 | Admin | 음식/조리법 등록 심사 |
| 14 | 리뷰 조회 | Users, Cooks | 다른 사용자의 리뷰 확인 |
| 15 | 리뷰 작성 | Users, Cooks | 별점 및 리뷰 등록 |

---

# 4. Concept of operation
### 1) 회원가입
| Purpose | 서비스 사용을 위한 회원 등록 |
| --- | --- |
| Approach | 정보 입력 후 DB에 저장 |
| Dynamics | 서비스를 처음 사용할 때 |
| Goals | 정상 회원가입 완료 |

### 2) 로그인
| Purpose | 사용자 인증 |
| --- | --- |
| Approach | ID/PW 입력 후 서버에서 확인 |
| Dynamics | 서비스 이용 시 |
| Goals | 로그인 성공 |

### 3) 로그아웃
| Purpose | 계정 전환 또는 종료 |
| --- | --- |
| Approach | 로그아웃 버튼 클릭 |
| Dynamics | 사용 종료 시 |
| Goals | 안전한 로그아웃 |

### 4) 나라 조회
| Purpose | 국가 선택 통한 음식 탐색 |
| --- | --- |
| Approach | Card View 형태로 나라 목록 제공 |
| Dynamics | 특정 나라 음식을 찾을 때 |
| Goals | 쉬운 국가 선택 |

### 5) 음식 리스트 조회
| Purpose | 선택한 나라의 음식 목록 확인 |
| --- | --- |
| Approach | 나라 선택 → 음식 리스트 출력 |
| Dynamics | 나라를 선택했을 때 |
| Goals | 음식 목록 제공 |

### 6) 음식 정보 조회
| Purpose | 음식 재료 및 정보 확인 |
| --- | --- |
| Approach | 음식 클릭 시 재료와 가격 정보 표시 |
| Dynamics | 음식을 선택했을 때 |
| Goals | 재료 정보 제공 |

### 7) 조리법 조회
| Purpose | 단계별 조리 방법 확인 |
| --- | --- |
| Approach | 화면에 순서대로 표시 |
| Dynamics | 조리법을 보고 싶을 때 |
| Goals | 조리 과정 제공 |

### 8) 요리사 등록 요청
| Purpose | 일반 사용자가 요리사로 권한 상승 |
| --- | --- |
| Approach | 관리자에게 등록 신청 |
| Dynamics | 요리사가 되고 싶을 때 |
| Goals | 요리사 권한 획득 |

### 9) 음식 등록 요청
| Purpose | 새로운 음식 등록 |
| --- | --- |
| Approach | 요리사가 정보 입력 후 관리자 심사 |
| Dynamics | 요리사가 음식을 추가할 때 |
| Goals | 음식 등록 |

### 10) 조리법 등록 요청
| Purpose | 조리법 추가 |
| --- | --- |
| Approach | 단계별 내용 작성 후 요청 |
| Dynamics | 조리법을 등록할 때 |
| Goals | 조리법 등록 |

### 11) 음식 추천
| Purpose | 사용자에게 맞는 음식 추천 |
| --- | --- |
| Approach | 무작위 또는 선호도 기반 추천 |
| Dynamics | 추천을 받고 싶을 때 |
| Goals | 추천 기능 제공 |

### 12) 요리사 관리
| Purpose | 요리사 자격 심사 |
| --- | --- |
| Approach | 관리자가 승인/거부 |
| Dynamics | 요리사 등록 신청 시 |
| Goals | 신뢰할 수 있는 요리사 관리 |

### 13) 음식/조리법 관리
| Purpose | 등록 요청 심사 |
| --- | --- |
| Approach | 내용 확인 후 승인/거부 |
| Dynamics | 음식/조리법 등록 요청 시 |
| Goals | 정확한 콘텐츠 관리 |

### 14) 리뷰 조회
| Purpose | 다른 사용자 평가 확인 |
| --- | --- |
| Approach | DB에서 리뷰 불러와 표시 |
| Dynamics | 후기를 보고 싶을 때 |
| Goals | 리뷰 열람 기능 |

### 15) 리뷰 작성
| Purpose | 경험 공유 및 평가 |
| --- | --- |
| Approach | 별점과 내용 작성 후 저장 |
| Dynamics | 요리 후 평가할 때 |
| Goals | 리뷰 등록 |

---

# 5. Problem statement
1. **조리법 다양성 확보**
   초기 콘텐츠 양이 부족할 수 있으며 사용자 동기부여 필요.

2. **API 및 서버 관리 어려움**
   재료 API 연동, DB 서버 안정적 운영 필요.

3. **데이터 저장 용량 확보**
   음식/조리법/회원 정보를 일관성 있게 저장.

4. **저작권 문제**
   조리법 출처 및 저작권 확인 필요.

5. **요리사 자격 기준 모호함**
   명확한 자격 기준 필요.

6. **추천 알고리즘 정확도**
   사용자 취향에 맞는 추천 필요.

### Non-Functional Requirements (NFRs)
① DB 조회 후 화면 표시 시간 < 3초
② 페이지 로딩 시간 < 2초
③ 모든 콘텐츠는 신뢰 가능한 출처 사용
④ 부드러운 화면 전환
⑤ 최소 안드로이드 Lollipop (API 21) 지원

---

# 6. Glossary
| 용어 | 설명 |
| --- | --- |
| 전 세계의 음식들 | 본 프로젝트 앱 이름 |
| 조리법 | 음식 만드는 방법 |
| 관리자 | 시스템 운영 및 심사 |
| 요리사 | 음식/조리법 등록 가능 사용자 |
| 사용자 | 일반 회원 |
| REST API | 재료 정보 가져오는 API |
| DB 서버 | 데이터 저장 서버 |

---

# 7. References
1. Cooking at Home More During COVID-19. healthline.com
2. OSS Design Project Plan, Yeungnam University
3. UML 2.5 Specification, OMG

---
