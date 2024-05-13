---
layout: default
title: IT프로젝트 정보 시스템 구축 관리
parent: 정보시스템 구축 관리
grand_parent: 정보처리기사

nav_order: 6.2
---

- [네트워크 관련 신기술](#네트워크-관련-신기술)
  - [메쉬 네트워크(Mesh Network)](#메쉬-네트워크mesh-network)
  - [PICONET](#piconet)
  - [WDM(Wavelength Division Multiplexing)](#wdmwavelength-division-multiplexing)
  - [AllJoin](#alljoin)
  - [SDS(Software Defined Storage)](#sdssoftware-defined-storage)
  - [SSO(Single Sign On)](#ssosingle-sign-on)
  - [PaaS-TA](#paas-ta)
  - [스마트 그리드](#스마트-그리드)
  - [SDN(Software Defined Networking)](#sdnsoftware-defined-networking)
  - [클라우드 기반 HSM(Cloud Based Hardware Security Module)](#클라우드-기반-hsmcloud-based-hardware-security-module)
- [버스형 - 네트워크 구축](#버스형---네트워크-구축)
- [IEEE 802](#ieee-802)
  - [CSMA/CD(Carrier Sense Multiple Access/Collision Detection)](#csmacdcarrier-sense-multiple-accesscollision-detection)
  - [CSMA/CA(Carrier Sense Multiple Access/Collision Avoidance)](#csmacacarrier-sense-multiple-accesscollision-avoidance)
- [경로 제어 프로토콜](#경로-제어-프로토콜)
  - [IGP(Interior Gateway Protocol, 내부 게이트웨이 프로토콜)](#igpinterior-gateway-protocol-내부-게이트웨이-프로토콜)
- [SW관련 신기술](#sw관련-신기술)
  - [AR(Argument Reality)](#arargument-reality)
  - [매시업(MashUp)](#매시업mashup)
  - [서비스 지향 아키텍쳐(SOA, Service Oriented Architecture)](#서비스-지향-아키텍쳐soa-service-oriented-architecture)
  - [Scrapy](#scrapy)
  - [Vaporware](#vaporware)
  - [디지털 트윈](#디지털-트윈)
  - [텐서플로](#텐서플로)
  - [도커](#도커)
- [보안 관련 신기술](#보안-관련-신기술)
  - [블록체인](#블록체인)
  - [비트로커(BitLocker)](#비트로커bitlocker)
  - [서비스형 블록체인(BaaS)](#서비스형-블록체인baas)
  - [OWASP(Open Web Application Security Project, 오픈 웹 애플리케이션 보안 프로젝트)](#owaspopen-web-application-security-project-오픈-웹-애플리케이션-보안-프로젝트)
  - [TCP 래퍼](#tcp-래퍼)
  - [허니팟(HoneyPot)](#허니팟honeypot)
  - [DPI(Deep Packet Inspection)](#dpideep-packet-inspection)
- [HW 관련 신기술](#hw-관련-신기술)
  - [HACMP(High Availability Clustering Multi Processing, 고가용성 솔루션)](#hacmphigh-availability-clustering-multi-processing-고가용성-솔루션)
  - [N-Screen](#n-screen)
- [Secure OS](#secure-os)
- [DB관련 신기술](#db관련-신기술)
  - [하둡(Hadoop)](#하둡hadoop)
  - [맵리듀스(MapReduce)](#맵리듀스mapreduce)
  - [타조(Tajo)](#타조tajo)
  - [데이터 마이닝(Data Mining)](#데이터-마이닝data-mining)
  - [OLAP(Online Analytical Processing)](#olaponline-analytical-processing)
- [병행 제어(Concurrency Control)](#병행-제어concurrency-control)
  - [Locking](#locking)
  - [타임 스탬프 순서](#타임-스탬프-순서)
- [교착상태(Dead Lock)](#교착상태dead-lock)
  - [상호 배제](#상호-배제)
  - [점유와 대기(Hold and Wait)](#점유와-대기hold-and-wait)
  - [비선점(Non Preemptive)](#비선점non-preemptive)
  - [환형 대기(Circular Wait)](#환형-대기circular-wait)
  - [해결 방법](#해결-방법)


# 네트워크 관련 신기술

## 메쉬 네트워크(Mesh Network)
대규모 디바이스의 네트워크 생성에 최적화되어 차세대 이동통신, 홈네트워킹, 공공안전 등의 특수목적에 사용되는 새로운 방식의 네트워크 기술

## PICONET
여러 개의 독립된 통신장치가 UWB(Ultra Wide Band) 기술 또는 블루투스 기술을 사용하여 통신망을 형성하는 무선 네트워크 기술

## WDM(Wavelength Division Multiplexing)
광섬유를 이용한 통신 기술. 파장이 서로 다른 복수의 광신호를 동시에 이용하는 것으로 광섬유를 다중화하는 방식.

## AllJoin
오픈소스 기반의 사물인터넷 플랫폼으로 서로 다른 운영체제나 하드웨어를 사용하는 기기들이 표준화된 플랫폼을 이용함으로써 서로 통신 및 제어가 가능한 기술

## SDS(Software Defined Storage)
컴퓨팅 소프트웨어로 규정하는 데이터 스토리지 체계이며, 일정 조직 내 여러 스토리지를 하나처럼 관리하고 운용하는 컴퓨터 이용 환경

## SSO(Single Sign On)
시스템이 몇대가 되어도 하나의 시스템에서 인증에 성공하면 다른 시스템에 대한 접근 권한도 얻는 시스템

## PaaS-TA
국내 IT서비스 경쟁력 강화를 목표로 개발되었으며, 인프라 제어 및 관리 환경, 실행환경, 개발환경, 서비스환경, 운영환경으로 구성되어 있는 개방형 클라우드 컴퓨팅 플랫폼

## 스마트 그리드
전기 및 정보통신기술을 활용하여 전력망을 지능화, 고도화함으로써 고품질의 전력서비스를 제공하고 에너지 이용효율을 극대화하는 전력망

## SDN(Software Defined Networking)
기존 라우터, 스위치 등과 같이 하드웨어에 의존하는 네트워크 체계에서 안정성, 속도, 보안 등을 소프트웨어로 제어, 관리하기 위해 개발된 기술

## 클라우드 기반 HSM(Cloud Based Hardware Security Module)
클라우드를 기반으로 암호화 키의 생성, 저장, 처리 등의 작업을 수행하는 보안기기를 가리키는 용어

# 버스형 - 네트워크 구축
한개의 통신 회선에 여러 대의 단말장치가 연결되어 있는 형태

# IEEE 802
LAN 표준 규격.

- 802.11e : QoS 기능이 지원되도록 하기 위해 MAC 계층에 해당하는 부분 수정
- 802.11i : 보안 기능 표준, 인증방식에 WPA(Wifi Protected Access)/WPA2 사용

## CSMA/CD(Carrier Sense Multiple Access/Collision Detection)
통신 회선이 사용중인지를 점검(Carrier Sense)하다가 통신 회선이 비어 있으면 누구든지 사용 가능(Multiple Access)하며, 데이터 프레임을 전송하면서 충돌 여부를 감시(Collision Detection)하는 방식

- 데이터 프레임 간의 충돌이 발생하는 것을 인정하고 이를 해소하기 위해 CSMA 방식에 충돌 검출 기능과 충돌 발생시 재송신하는 기능 추가


## CSMA/CA(Carrier Sense Multiple Access/Collision Avoidance)
무선 랜에서 데이터 전송 시 매체가 비어있음을 확인한 뒤 충돌을 피하기 위해 일정 시간을 기다린 후 데이터를 전송하는 방법

# 경로 제어 프로토콜
효율적인 경로 제어를 위해 네트워크 정보를 생성, 교환, 제어하는 프로토콜을 총칭.

## IGP(Interior Gateway Protocol, 내부 게이트웨이 프로토콜)
하나의 자율 시스템 내의 라우팅에 사용되는 프로토콜

- RIP : 최단 경로 탐색에 벨만포드 알고리즘이 사용. 최대 홉 수를 15로 제한, 라우팅 정보를 30초마다 네트워크 내 모든 라우터에 알리고, 180초 이내에 새로운 라우팅 정보가 수신되지 않으면 해당 경로를 이상 상태로 간주.
- OSPF : RIP의 단점을 해결하여 새로운 기능을 지원하는 인터넷 프로토콜, 대규모 네트워크에서 많이 사용. 다익스트라 사용.

# SW관련 신기술

## AR(Argument Reality)
실제 촬영한 화면에 가상의 정보를 부가하여 보여주는 기술

## 매시업(MashUp)
웹에서 제공하는 정보 및 서비스를 이용하여 새로운 소프트웨어나 서비스, 데이터베이스 등을 만드는 기술

## 서비스 지향 아키텍쳐(SOA, Service Oriented Architecture)
기업의 소프트웨어 인프라인 정보시스템을 공유와 재사용이 가능한 서비스 단위나 컴포넌트 중심으로 구축하는 정보기술 아키텍처

- 표현 계층, 업무 프로세스 계층, 서비스 중간 계층, 애플리케이션 계층, 데이터 저장 계층

## Scrapy
Python 기반 웹 크롤링 프레임워크

## Vaporware
판매 계획 또는 배포 계획은 발표되었으나 실제로 고객에게 판매되거나 배포되지 않고 있는 소프트웨어

## 디지털 트윈
현실속의 사물을 소프트웨어로 가상화한 모델로, 실제 자산의 특성에 대한 정확한 정보를 얻을 수 있고, 최적화, 돌발사고 최소화, 생산성 증가 등 설계부터 제조, 서비스에 이르는 모든 과정의 효율성을 향상시킬 수 있음.

## 텐서플로
다양한 작업에 대해 데이터 흐름 프로그래밍을 위한 오픈소스 소프트웨어 라이브러리

## 도커
컨테이너 기술을 자동화하여 쉽게 사용할 수 있게 하는 오픈소스 프로젝트. 소프트웨어 컨테이너 안에 응용 프로그램들을 배치시키는 일을 자동화해 주는 역할 수행

- **컨테이너** : 앱이 운영체제 상관없이 독립적으로 실행되기 위한 파일들을 묶어놓은 패키지

# 보안 관련 신기술

## 블록체인
P2P 네트워크를 이용하여 온라인 금융거래 정보를 온라인 네트워크 참여자(Peer)의 디지털 장비에 분산저장하는 기술

## 비트로커(BitLocker)
Windows 전용 볼륨 암호화 기능. TPM과 AES-128의 알고리즘을 사용.

## 서비스형 블록체인(BaaS)
블록체인 앱의 개발환경을 클라우드 기반으로 제공하는 서비스

## OWASP(Open Web Application Security Project, 오픈 웹 애플리케이션 보안 프로젝트)
웹 정보 노출이나 악성코드, 스크립트, 보안이 취약한 부분을 연구하는 비영리단체

## TCP 래퍼
외부 컴퓨터의 접속인가 여부를 점검하여 접속을 허용 및 거부하는 보안용 도구

## 허니팟(HoneyPot)
비정상적인 접근을 탐지하기 위해 설치해 둔 시스템

## DPI(Deep Packet Inspection)
OSI 7 Layer 전 계층의 프로토콜과 패킷 내부의 콘텐츠를 파악하여 침입 시도, 해킹 등을 탐지하고 트래픽을 조정하기 위한 패킷 분석 기술

# HW 관련 신기술

## HACMP(High Availability Clustering Multi Processing, 고가용성 솔루션)
긴 시간동안 안정적인 서비스 운영을 위해 장애 발생 시 즉시 다른 시스템으로 대체 가능한 환경을 구축하는 매커니즘

## N-Screen
N개의 서로 다른 단말기에서 동일한 콘텐츠를 자유롭게 이용할 수 있는 서비스

# Secure OS
기존 운영체제에 내재된 보안 취약점을 해소하기 위해 보안 기능을 갖춘 커널을 이식하여 외부의 침입으로부터 시스템 자원을 보호하는 운영체제. 참조 모니터의 개념을 구현하고 집행

- 식별 및 인증
- 임의적 접근통제
- 강제적 접근통제
- 객체 재사용 보호 : 메모리가 기존데이터에 남아있지 않도록 초기화
- 완전한 조정
- 신뢰 경로
- 감사 및 감사기록 축소

**참조 모니터**
보호대상의 객체에 대한 접근 통제를 수행하는 추상머신.
- 격리성(Isolation, 부정 조작이 불가능), 검증가능성(Verifiability, 적절히 구현되었다는걸 확인 가능), 완전성(Completeness, 우회 불가능)이 필요

# DB관련 신기술

## 하둡(Hadoop)
분산 컴퓨팅 플랫폼. 일반 PC급 컴퓨터들로 가상화된 대형 스토리지를 형성하고 그안에 보관된 거대한 데이터 세트를 병렬로 처리할 수 있도록 개발된 자바 소프트웨어 프레임워크.

## 맵리듀스(MapReduce)
대용량 데이터를 분산 처리하기 위한 목적으로 개발된 프로그래밍 모델

## 타조(Tajo)
하둡기반의 분산 데이터 웨어하우스 프로젝트. 

## 데이터 마이닝(Data Mining)
데이터 웨어하우스에 저장된 데이터 집합에서 사용자의 요구에 따라 유용하고 가능성 있는 정보를 발견하기 위한 기법

## OLAP(Online Analytical Processing)
다차원으로 이루어진 데이터로부터 통계적인 요약 정보를 분석하여 의사결정에 활용하는 방식

- 연산 : Roll-up, Drill-down, Drill-through, Drill-across, Pivoting, Slicing, Dicing

# 병행 제어(Concurrency Control)
다중 프로그램의 이점을 활용해 동시에 여러개의 트랜잭션을 병행수행할 때 동시에 실행되는 트랜잭션들이 일관성을 파괴하지 않도록 트랜잭션 간의 상호 작용을 제어하는 것.

## Locking
주요 데이터의 액세스를 상호배타적으로 하는 것

## 타임 스탬프 순서
트랜잭션과 트랜잭션이 읽거나 갱신한 데이터에 대해 트랜잭션이 실행을 시작하기 전에 시간표를 부여하여 부여된 시간에 따라 트랜잭션 작업을 수행하는 기법. 교착상태가 발생하지 않음.

# 교착상태(Dead Lock)
상호 배제에 의해 나타나는 문제점. 둘 이상의 프로세스들이 자원을 점유한 상태에서 서로 다른 프로세스가 점유하고 있는 자원을 요구하며 무한정 기다리는 현상.  
아래 네가지 조건 중 하나라도 충족되지 않으면 교착상태가 발생하지 않음(필요충분조건).

## 상호 배제
한번의 한개의 프로세스만이 공유자원을 사용할 수 있어야 함

## 점유와 대기(Hold and Wait)
최소한 하나의 자원을 점유하고 있으면서 다른 프로세스에 할당되어 사용되고 있는 자원을 추가로 점유하기 위해 대기하는 프로세스가 있어야 함.

## 비선점(Non Preemptive)
다른 프로세스에 할당된 자원은 사용이 끝날 때까지 강제로 빼앗을 수 없어야 함.

## 환형 대기(Circular Wait)
공유자원과 공유 자원을 사용하기 위해 대기하는 프로세스들이 원형으로 구성되어 있어 자신에게 할당된 자원을 점유하면서 앞이나 뒤에 있는 프로세스의 자원을 요구해야 함.

## 해결 방법
- 회피 기법 : 교착상태가 발생할 가능성을 배제하지 않고, 발생하면 적절히 피해나가는 방법. 주로 은행원 알고리즘(자원을 공유할 때 안전한 상태를 유지할 수 있는지 확인후 빌려주는 방식)이 사용됨.