﻿---
title: '고가용성 및 사이트 복원 계획: Exchange 2013 Help'
TOCTitle: 고가용성 및 사이트 복원 계획
ms:assetid: 29bb0358-fc8e-4437-8feb-d2959ed0f102
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dd638104(v=EXCHG.150)
ms:contentKeyID: 50482760
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 고가용성 및 사이트 복원 계획

 

_**적용 대상:** Exchange Server 2013_

_**마지막으로 수정된 항목:** 2016-12-09_

계획 단계에서 시스템 설계자, 관리자 및 기타 핵심 관계자는 비즈니스 요구 사항과 배포 시 아키텍처 요구 사항 외에 특히 고가용성과 사이트 복구에 대한 요구 사항을 확인해야 합니다.

이러한 기능 배포를 위해 충족해야 할 일반적인 요구 사항뿐 아니라, 마찬가지로 충족해야 할 하드웨어, 소프트웨어 및 네트워킹 요구 사항도 있습니다.

**목차**

General requirements

Hardware requirements

Storage requirements

Software requirements

Network requirements

Witness server requirements

Planning for site resilience

## 일반 요구 사항

DAG(데이터베이스 사용 가능 그룹)를 배포하고 사서함 데이터베이스 복사본을 생성하기 전에 먼저 다음과 같은 시스템 전반의 권장 사항을 충족해야 합니다.

  - DNS(Domain Name System)를 실행해야 합니다. 이상적으로 DNS 서버는 동적 업데이트를 허용해야 합니다. DNS 서버가 동적 업데이트를 허용하지 않는 경우 각 Exchange 서버에 대한 DNS 호스트 (A) 레코드를 만들어야 합니다. 그렇지 않으면 Exchange가 제대로 작동하지 않습니다.

  - DAG의 각 사서함 서버는 같은 도메인의 구성원 서버여야 합니다.

  - 디렉터리 서버이기도 한 Exchange 2013 사서함 서버는 DAG에 DAG에 추가할 수 없습니다.

  - DAG에는 유효하고 사용 가능하며 15자 이하의 고유한 컴퓨터 이름을 지정해야 합니다.

맨 위로 이동

## 하드웨어 요구 사항

일반적으로 DAG나 사서함 데이터베이스 복사본에 한정되는 특별한 하드웨어 요구 사항은 없습니다. 사용되는 서버는 [Exchange 2013 필수 구성 요소](exchange-2013-prerequisites-exchange-2013-help.md) 및 [Exchange 2013 시스템 요구 사항](exchange-2013-system-requirements-exchange-2013-help.md) 항목에 명시된 요구 사항을 모두 충족해야 합니다.

맨 위로 이동

## 저장소 요구 사항

일반적으로 DAG나 사서함 데이터베이스 복사본에 한정되는 특별한 저장소 요구 사항은 없습니다. DAG는 클러스터 관리 공유 저장소를 필요로 하거나 사용하지 않습니다. 클러스터 관리 공유 저장소는 Exchange 2013에 기본적으로 제공되는 타사 복제 API를 활용하는 솔루션을 사용하도록 DAG가 구성된 경우에만 DAG에서 사용할 수 있습니다.

맨 위로 이동

## 소프트웨어 요구 사항

DAG는 Exchange 2013 Standard 및 Exchange 2013 Enterprise에서 모두 사용할 수 있습니다. 또한 DAG에는 Exchange 2013 Standard 및 Exchange 2013 Enterprise를 실행 중인 서버가 혼합되어 포함될 수 있습니다.

DAG의 각 구성원은 같은 운영 체제를 실행해야 합니다. Exchange 2013은 Windows Server 2008 R2, Windows Server 2012 및 Windows Server 2012 R2 운영 체제에서 지원됩니다. 특정 DAG의 모든 구성원이 동일한 운영 체제를 실행해야 합니다. Windows Server 2012 R2는 Exchange 2013 서비스 팩 1 이상을 실행하는 DAG 구성원에만 지원됩니다.

Exchange 2013 을 설치하기 위한 선행 조건 외에도 반드시 충족해야 하는 운영 체제 요구 사항이 있습니다. DAG에서는 Windows 장애 조치(failover) 클러스터링 기술을 사용하므로 Windows Server 2008 R2의 Enterprise 또는 Datacenter 버전이나 Windows Server 2012 운영 체제의 Standard 또는 Datacenter 버전 또는 Windows Server 2012 R2 운영 체제가 필요합니다.

맨 위로 이동

## 네트워크 요구 사항

각 DAG 및 각 DAG 구성원에 대해 충족해야 할 특정 네트워킹 요구 사항이 있습니다. 각 DAG에는 DAG 구성원이 기타 Exchange 2013 서버나 디렉터리 서버 등의 다른 서버와 통신하는 데 사용하는 *MAPI 네트워크* 하나와 로그 전달 및 시드 전용 네트워크인 *복제 네트워크*가 0개 이상 있어야 합니다.

Exchange 의 이전 버전에서 Dag에 대 한 최소 두 네트워크 (MAPI 네트워크와 복제 네트워크) 권장 합니다. Exchange 2013 여러 네트워크는 지원 되지만 권장 하는 것은 실제 네트워크 토폴로지에 따라 달라 집니다. 여러 실제 네트워크에서 서로 물리적으로 분리 된 DAG 구성원 사이 있는 경우 다음 별도 MAPI 및 복제 네트워크를 사용 하 여 추가 중복성을 제공 합니다. 부분적으로 물리적으로 분리 되어 있지만 단일 실제 네트워크 (등 단일 WAN 링크)로 수렴 하는 여러 네트워크에 있는 다음 MAPI 및 복제 트래픽 모두에 대 한 단일 네트워크 (가능 하면 10 기가 비트 이더넷)를 사용 하는 것이 좋습니다. 이 네트워크 및 네트워크 경로 대 한 간편 하 게를 제공합니다.

DAG 네트워크 인프라를 디자인할 때는 다음과 같은 사항을 고려하십시오.

  - 각 구성원은 DAG의 다른 모든 DAG 구성원와 통신할 수 있는 하나 이상의 네트워크 어댑터가 있어야 합니다. 단일 네트워크 경로 사용 하는 경우에 1 기가 비트 이더넷, 하지만 가능 하면 10 기가 비트 이더넷 최소를 사용 하는 것이 좋습니다. 또한 각 DAG 구성원에서 단일 네트워크 어댑터를 사용할 때의 단일 네트워크 어댑터와 경로 염두에 전체 솔루션을 디자인 하는 것이 좋습니다.

  - 각 DAG 구성원에 두 개의 네트워크 어댑터를 사용하면 MAPI 네트워크와 복제 네트워크가 각각 하나씩 제공되며, 복제 네트워크의 중복성 및 다음 복구 동작이 지원됩니다.
    
      - MAPI 네트워크에 영향을 주는 오류가 발생하면 활성화할 수 있는 정상 상태의 사서함 데이터베이스 복사본이 있다는 가정 하에 서버 장애 조치(failover)가 수행됩니다.
    
      - 복제 네트워크에 영향을 주는 오류가 발생하는 경우 MAPI 네트워크의 *ReplicationEnabled* 속성이 False로 설정되어 있더라도 MAPI 네트워크가 이 오류의 영향을 받지 않으면 로그 전달 및 시드 작업을 되돌려 MAPI 네트워크를 사용합니다. 오류가 발생한 복제 네트워크가 정상으로 복원되어 로그 전달 및 시드 작업을 다시 시작할 준비가 되면 수동으로 복제 네트워크로 전환해야 합니다. MAPI 네트워크에서 복원된 복제 네트워크로 복제를 변경하려면 **Suspend-MailboxDatabaseCopy** 및 **Resume-MailboxDatabaseCopy** cmdlet을 사용하여 연속 복제를 일시 중단한 후 계속해서 다시 시작하거나, Microsoft Exchange Replication Service를 다시 시작합니다. Microsoft Exchange Replication Service를 다시 시작해서 작업이 잠시 중단되는 상황이 발생하지 않도록 하려면 작업을 일시 중단한 후 다시 시작하는 것이 좋습니다.

  - 각 DAG 구성원에 같은 수의 네트워크가 포함되어야 합니다. 예를 들어, 한 DAG 구성원의 네트워크 어댑터를 하나만 사용하려면 모든 DAG 구성원도 한 네트워크 어댑터를 사용해야 합니다.

  - 각 DAG에는 MAPI 네트워크가 하나만 있어야 합니다. MAPI 네트워크에서는 Active Directory와 DNS 등의 다른 Exchange 서버 및 서비스에 연결할 수 있어야 합니다.

  - 필요에 따라 복제 네트워크는 추가할 수 있습니다. 또한 네트워크 어댑터 팀 또는 유사한 기술을 활용하여 개별 네트워크 어댑터가 단일 실패 지점이 되는 것을 방지할 수도 있습니다. 그러나 팀을 사용한다 해도 네트워크 자체가 단일 실패 지점이 되는 것을 방지할 수는 없습니다. 또한 DAG에 불필요한 복잡성이 추가됩니다.

  - 각 DAG 구성원 서버의 각 네트워크는 자체 네트워크 서브넷에 있어야 합니다. DAG의 각 서버는 서로 다른 서브넷에 있을 수 있지만, MAPI와 복제 네트워크는 라우팅이 가능해야 하고 다음과 같은 연결을 제공해야 합니다.
    
      - 각 DAG 구성원 서버의 각 네트워크는 이 서버의 다른 네트워크가 사용하는 서브넷과 별개인 자체 네트워크 서브넷에 있습니다.
    
      - 각 DAG 구성원 서버의 MAPI 네트워크는 다른 DAG 구성원의 MAPI 네트워크와 서로 통신할 수 있습니다.
    
      - 각 DAG 구성원 서버의 복제 네트워크는 다른 DAG 구성원의 복제 네트워크와 서로 통신할 수 있습니다.
    
      - 한 DAG 구성원 서버의 복제 네트워크에서 다른 DAG 구성원 서버의 MAPI 네트워크로, 또는 그 반대로, 또는 DAG의 여러 복제 네트워크 간에 하트비트 트래픽을 허용하는 직접 라우팅은 없습니다.

  - 다른 DAG 구성원과 관련된 물리적 위치에 상관없이 각 DAG 구성원은 상호 간의 왕복 네트워크 대기 시간이 500밀리초를 넘지 않아야 합니다. 데이터베이스 복사본을 호스트하는 두 사서함 서버 간의 왕복 대기 시간이 늘어나면 복제 작업이 최신 상태로 진행되지 않을 가능성도 커집니다. 솔루션 대기 시간에 상관없이 고객은 모든 DAG 구성원 간의 네트워크가 배포에 관한 데이터 보호 및 가용성 목표를 충족할 수 있는지 확인해야 합니다. 대기 시간 값이 높은 구성에서 원하는 목표를 달성하려면 데이터베이스 수를 늘리거나 데이터베이스별 사서함 수를 줄이는 등 DAG, 복제 및 네트워크 매개 변수를 특별히 조정해야 할 수 있습니다.

  - 왕복 대기 시간 요구 사항은 다중 데이터 센터 구성에 대한 가장 엄격한 네트워크 대역폭 및 대기 시간 요구 사항이 아닐 수 있습니다. 클라이언트 액세스, Active Directory, 전송, 연속 복제 및 기타 응용 프로그램 트래픽을 포함한 전체 네트워크 부하를 평가하여 환경에 필요한 네트워크 요구 사항을 결정해야 합니다.

  - DAG 네트워크는 IPv4(인터넷 프로토콜 버전 4) 및 IPv6을 지원합니다. IPv6은 IPv4를 함께 사용하는 경우에만 지원되며, 순수한 IPv6 환경은 지원되지 않습니다. IPv6 주소와 IP 주소 범위 사용은 IPv6 및 IPv4 모두를 해당 컴퓨터에서 사용하도록 설정되어 있고, 네트워크가 두 IP 주소 버전을 모두 지원하는 경우에만 지원됩니다. 이 구성에서 Exchange 2013을 배포하면 모든 서버 역할에서 IPv6 주소를 사용하는 장치, 서버 및 클라이언트와 데이터를 주고받을 수 있습니다.

  - APIPA(자동 개인 IP 주소)는 네트워크에서 DHCP(Dynamic Host Configuration Protocol) 서버를 사용할 수 없을 때 IP 주소를 자동으로 할당하는 Windows의 기능입니다. APIPA 주소(APIPA 주소 범위에서 수동으로 할당된 주소 포함)는 DAG 또는 Exchange 2013에서 사용할 수 없습니다.

## DAG 이름 및 IP 주소 요구 사항

DAG가 만들어질 때 각 DAG에는 고유한 이름이 지정되고, 하나 이상의 고정 IP 주소에 할당되거나 DHCP를 사용하도록 구성됩니다. 고정 주소 또는 동적으로 할당된 주소 중 무엇을 사용하든 상관없이 DAG에 할당된 IP 주소는 MAPI 네트워크에 있어야 합니다.

Windows Server 2008 R2 또는 Windows Server 2012에서 실행되는 각 DAG에는 MAPI 네트워크의 IP 주소가 하나 이상 필요합니다. MAPI 네트워크가 여러 서브넷으로 확장될 경우 DAG는 추가 IP 주소를 필요로 하게 됩니다. Windows Server 2012 R2에서 실행되며 클러스터 관리 액세스 포인트 없이 작성된 DAG에는 IP 주소가 필요하지 않습니다.

다음 그림은 DAG의 모든 노드가 같은 서브넷에 MAPI 네트워크가 있는 DAG를 나타냅니다.

**같은 서브넷에 MAPI 네트워크가 있는 DAG**

![단일 서브넷의 DAG](images/Dd638104.bcb7ef68-6d18-4516-a736-b936991c82cb(EXCHG.150).gif "단일 서브넷의 DAG")

이 예에서, 각 DAG 구성원의 MAPI 네트워크는 172.19.18.*x* 서브넷에 있습니다. 결과적으로 DAG에는 해당 서브넷의 IP 주소 하나만 필요합니다.

다음 그림은 두 서브넷, 172.19.18.*x* 및 172.19.19.*x*에서 확장되는 MAPI 네트워크가 있는 DAG를 보여 줍니다.

**여러 서브넷에 MAPI 네트워크가 있는 DAG**

![여러 서브넷에 걸쳐 있는 DAG](images/Dd638104.ffb57c64-3cb1-435c-8148-1b7154d1575c(EXCHG.150).gif "여러 서브넷에 걸쳐 있는 DAG")

이 예에서, 각 DAG 구성원의 MAPI 네트워크는 별도의 서브넷에 있습니다. 따라서 DAG는 MAPI 네트워크의 각 서브넷에 하나씩, 두 개의 IP 주소를 필요로 합니다.

DAG의 MAPI 네트워크가 추가 서브넷으로 확장될 때마다 해당 서브넷에 대한 추가 IP 주소를 DAG에 구성해야 합니다. DAG에 구성한 각 IP 주소는 DAG의 기본 장애 조치(failover) 클러스터에 할당되어 사용됩니다. DAG의 이름은 기본 장애 조치(failover) 클러스터의 이름으로도 사용됩니다.

특정 시점에서, DAG의 클러스터는 할당된 IP 주소 중 하나만을 사용하게 됩니다. 클러스터 IP 주소 및 네트워크 이름 리소스가 온라인 상태가 되면 Windows 장애 조치(failover) 클러스터링은 이 IP 주소를 DNS에 등록합니다. IP 주소와 네트워크 이름 사용 외에, CNO(클러스터 이름 개체)가 Active Directory에 만들어집니다. 클러스터의 이름과 IP 주소, CNO는 DAG 보안 및 내부 통신용으로 시스템에서 내부적으로 사용합니다. 따라서 관리자와 최종 사용자는 DAG 이름 또는 IP 주소에 연결할 필요가 없습니다.


> [!NOTE]
> 클러스터의 IP 주소와 네트워크 이름을 시스템에서 내부적으로 사용하기는 하지만 Exchange 2013에서 이러한 리소스를 사용해야 할 특별한 이유는 없습니다. 기본 클러스터의 관리 액세스 포인트(해당 IP 주소 및 네트워크 이름 리소스)가 오프라인 상태인 경우에도 DAG는 DAG 구성원의 서버 이름을 사용하여 계속해서 내부적으로 통신합니다. 그러나 이 리소스가 30일을 초과하여 오프라인 상태로 있지 않도록 리소스의 가용성을 정기적으로 모니터링하는 것이 좋습니다. 기본 클러스터가 30일을 초과하여 오프라인 상태일 경우 Active Directory의 가비지 수집 메커니즘으로 클러스터 CNO 계정의 유효성을 검사할 수도 있습니다.



## DAG 네트워크 어댑터 구성

각 네트워크 어댑터의 용도에 따라 제대로 구성 되어야 합니다. MAPI 네트워크에 연결 하는데 사용 되는 네트워크 어댑터는 복제 네트워크에 연결 하는데 사용 되는 네트워크 어댑터에서와 다르게 구성 됩니다. 각 네트워크 어댑터를 올바르게 구성 외에 구성 해야 네트워크 연결 순서 Windows 에서 MAPI 네트워크는 연결 순서의 맨 위쪽에 되도록 합니다. 네트워크 연결 순서를 수정 하는 방법에 대 한 자세한 단계 [프로토콜 바인딩 및 네트워크 공급자 순서를 수정할](https://go.microsoft.com/fwlink/p/?linkid=179138)을 참조 하십시오.

## MAPI 네트워크 어댑터 구성

MAPI 네트워크에서 사용할 네트워크 어댑터는 다음 표에 설명된 대로 구성해야 합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>네트워킹 기능</th>
<th>설정</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Networks용 클라이언트</p></td>
<td><p>사용</p></td>
</tr>
<tr class="even">
<td><p>QoS 패킷 스케줄러</p></td>
<td><p>필요시 사용</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Networks용 파일 및 프린터 공유</p></td>
<td><p>사용</p></td>
</tr>
<tr class="even">
<td><p>TCP/IP v6(인터넷 프로토콜 버전 6)</p></td>
<td><p>사용</p></td>
</tr>
<tr class="odd">
<td><p>TCP/IP v4(인터넷 프로토콜 버전 4)</p></td>
<td><p>사용</p></td>
</tr>
<tr class="even">
<td><p>링크 계층 토폴로지 검색 매퍼 I/O 드라이버</p></td>
<td><p>사용</p></td>
</tr>
<tr class="odd">
<td><p>링크 계층 토폴로지 검색 응답자</p></td>
<td><p>사용</p></td>
</tr>
</tbody>
</table>


MAPI 네트워크 어댑터의 TCP/IP v4 속성은 다음과 같이 구성됩니다.

  - DAG 구성원의 MAPI 네트워크에 대한 IP 주소는 수동으로 할당하거나 DHCP를 사용하도록 구성할 수 있습니다. DHCP를 사용할 경우 서버 IP 주소에는 영구 예약을 사용하는 것이 좋습니다.

  - 일반적으로 MAPI 네트워크는 기본 게이트웨이 하나를 사용하지만 필요하지는 않습니다.

  - 하나 이상의 DNS 서버 주소를 구성해야 합니다. 중복성을 위해 여러 DNS 서버를 사용하는 것이 좋습니다.

  - **DNS에 이 연결의 주소를 등록** 확인란을 선택해야 합니다.

## 복제 네트워크 어댑터 구성

복제 네트워크에서 사용할 네트워크 어댑터는 다음 표에 설명된 대로 구성해야 합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>네트워킹 기능</th>
<th>설정</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Networks용 클라이언트</p></td>
<td><p>사용 안 함</p></td>
</tr>
<tr class="even">
<td><p>QoS 패킷 스케줄러</p></td>
<td><p>필요시 사용</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Networks용 파일 및 프린터 공유</p></td>
<td><p>사용 안 함</p></td>
</tr>
<tr class="even">
<td><p>TCP/IP v6(인터넷 프로토콜 버전 6)</p></td>
<td><p>사용</p></td>
</tr>
<tr class="odd">
<td><p>TCP/IP v4(인터넷 프로토콜 버전 4)</p></td>
<td><p>사용</p></td>
</tr>
<tr class="even">
<td><p>링크 계층 토폴로지 검색 매퍼 I/O 드라이버</p></td>
<td><p>사용</p></td>
</tr>
<tr class="odd">
<td><p>링크 계층 토폴로지 검색 응답자</p></td>
<td><p>사용</p></td>
</tr>
</tbody>
</table>


복제 네트워크 어댑터의 TCP/IP v4 속성은 다음과 같이 구성됩니다.

  - DAG 구성원의 복제 네트워크에 대한 IP 주소는 수동으로 할당하거나 DHCP를 사용하도록 구성할 수 있습니다. DHCP를 사용할 경우 서버 IP 주소에는 영구 예약을 사용하는 것이 좋습니다.

  - 일반적으로 복제 네트워크에는 기본 게이트웨이가 없지만, MAPI 네트워크에 기본 게이트웨이가 있는 경우 다른 네트워크에 기본 게이트웨이가 있으면 안 됩니다. 복제 네트워크에서 네트워크 트래픽의 라우팅은 복제 네트워크 간을 라우팅할 수 있는 게이트웨이 주소를 사용하는 다른 DAG 구성원의 해당 네트워크에 대한 영구 고정 경로를 사용하여 구성할 수 있습니다. 이 경로와 일치하지 않는 다른 모든 트래픽은 MAPI 네트워크 어댑터에 구성된 기본 게이트웨이에서 처리합니다.

  - DNS 서버 주소는 구성하지 않아야 합니다.

  - **DNS에 이 연결의 주소를 등록** 확인란을 선택하면 안 됩니다.

맨 위로 이동

## 미러링 모니터 서버 요구 사항

*미러링 모니터 서버*는 DAG 구성원이 짝수인 경우 쿼럼을 확보하고 유지 관리하는 데 사용되는 DAG 외부의 서버입니다. 구성원이 홀수인 DAG는 미러링 모니터 서버를 사용하지 않습니다. 구성원이 짝수인 DAG는 모두 미러링 모니터 서버를 사용해야 합니다. 미러링 모니터 서버는 Windows Server를 실행하는 모든 컴퓨터가 될 수 있습니다. 미러링 모니터 서버의 Windows Server 운영 체제 버전이 DAG 구성원에서 사용되는 운영 체제와 일치할 필요는 없습니다.

쿼럼은 DAG 아래에서 클러스터 레벨로 유지 관리됩니다. DAG는 구성원의 과반수가 온라인일 때 쿼럼을 갖게 되며 DAG의 다른 온라인 구성원과 통신할 수 있습니다. 이러한 쿼럼의 개념은 Windows 장애 조치(failover) 클러스터링에서의 쿼럼 개념이 갖는 한 측면입니다. 장애 조치(failover) 클러스터의 쿼럼에 관련되고 필수적인 측면이 *쿼럼 리소스*입니다. 쿼럼 리소스는 클러스터 상태 및 구성원 결정으로 이어지는 중재 수단을 제공하는 장애 조치(failover) 클러스터 내부의 리소스입니다. 또한 쿼럼 리소스는 구성 정보를 저장하는 영구 저장소도 제공합니다. 쿼럼 리소스와 함께 사용되는 *쿼럼 로그*는 클러스터에 대한 구성 데이터베이스입니다. 쿼럼 로그에는 클러스터의 구성원인 서버, 클러스터에 설치되어 있는 리소스 및 이러한 리소스의 상태(예: 온라인 또는 오프라인)와 같은 정보가 포함됩니다.

각 DAG 구성원이 DAG의 기본 클러스터 구성 방식에 대해 일관된 관점을 갖는 것이 중요합니다. 쿼럼은 클러스터와 관련 있는 모든 구성 정보를 위한 가장 확실한 리포지토리 역할을 합니다. 또한 쿼럼은 *분할 브레인* 현상을 방지하기 위한 연결 분리기로도 사용됩니다. 분할 브레인 현상은 DAG 구성원이 서로 통신할 수는 없지만 실행 중인 경우에 발생하는 상황입니다. 브레인 신드롬 분할은 항상 DAG 구성원의 과반수(DAG 구성원 수가 짝수인 경우 DAG 미러링 모니터 서버)를 사용 가능한 상태로 유지하고, DAG가 작동하도록 상호 작용하게 함으로써 방지할 수 있습니다.

맨 위로 이동

## 사이트 복구 계획

날마다 점점 더 많은 기업들이 안정적이고 가용성 높은 메시징 시스템을 갖추는 것이 비즈니스를 성공으로 이끄는 필수 요소라는 사실을 인식하고 있습니다. 상당수의 조직에서 메시징 시스템은 업무 지속 계획의 일부이며, 메시징 서비스 배포 또한 사이트 복구를 고려하여 디자인됩니다. 기본적으로 대부분의 사이트 복구 솔루션은 보조 데이터 센터에서의 하드웨어 배포를 포함합니다.

궁극적으로, DAG 구성원의 수와 사서함 데이터베이스 복사본의 수를 비롯한 DAG의 전체 디자인은 다양한 오류 시나리오에 적용될 수 있는 각 조직의 복구 SLA(서비스 수준 계약)에 따라 달라집니다. 계획 단계에서 솔루션 설계자와 관리자는 사이트 복구를 위한 특정 요구 사항을 포함하여, 배포에 필요한 요구 사항을 확인합니다. 즉 사용할 위치와 필요한 복구 SLA 대상을 확인합니다. SLA는 고가용성 및 사이트 복구를 제공하는 솔루션 디자인에 대한 기본 사항인 두 가지 특정 요소, 복구 시간 목표와 복구 지점 목표입니다. 이 값은 모두 분 단위 시간으로 정해집니다. 복구 시간 목표는 서비스를 복원하는 데 걸리는 시간을 의미하고, 복구 지점 목표는 복구 작업이 완료된 후 데이터가 얼마나 최신 상태인지를 나타냅니다. 또한 SLA는 문제가 해결된 후 기본 데이터 센터가 완전한 서비스를 제공하도록 복원하기 위해서도 정의됩니다.

솔루션 설계자와 관리자는 사이트 복구 보호가 필요한 사용자 집합을 확인하고, 다중 사이트 솔루션을 활성/수동 상태로 구성할지, 활성/활성 상태로 구성할지 결정합니다. 활성/수동 구성의 경우, 일반적으로 대기 데이터 센터에서는 사용자를 호스트하지 않습니다. 활성/활성 구성에서는 사용자를 두 곳에서 호스트하고, 솔루션에 포함된 데이터베이스 중 일부의 기본 설정 활성 위치가 보조 데이터 센터에 있습니다. 한 데이터 센터의 사용자에 대한 서비스가 실패하면 이 사용자들은 다른 데이터 센터에서 활성화됩니다.

적절한 SLA를 구성하려면 다음 기본 질문에 답해야 합니다.

  - 기본 데이터 센터에 오류가 발생할 경우 필요한 서비스 수준은 무엇입니까?

  - 사용자에게 자신의 데이터가 필요합니까 아니면 메시징 서비스만 필요합니까?

  - 어느 정도나 빠르게 데이터가 필요합니까?

  - 지원해야 하는 사용자 수는 몇 명입니까?

  - 사용자가 자신의 데이터에 어떻게 액세스합니까?

  - 대기 데이터 센터 활성화 SLA란 무엇입니까?

  - 서비스를 기본 데이터 센터로 다시 이동하는 방법은 무엇입니까?

  - 리소스가 사이트 복구 솔루션 전용입니까?

이러한 질문에 답함으로써 메시징 솔루션을 위한 사이트 복구 디자인의 기본 틀을 갖출 수 있습니다. 사이트 오류 복구의 핵심 요구 사항은 백업 메시징 서비스를 호스트하는 백업 데이터 센터로 필요한 메시징 데이터를 가져오는 솔루션을 만드는 것입니다.

## 인증서 계획

단일 데이터 센터에 DAG를 배포하는 경우에는 인증서 디자인에 대해 특별히 고려할 점이 없습니다. 그러나 사이트 복구 구성에서 여러 데이터 센터로 DAG를 확장할 때는 인증서와 관련된 특정 고려 사항이 있습니다. 일반적으로 인증서 디자인은 사용 중인 클라이언트를 비롯하여, 인증서를 사용하는 다른 응용 프로그램에 의한 인증서 요구 사항에 따라 결정됩니다. 그러나 인증서의 유형과 개수에 관해 반드시 따라야 할 특정 권장 사항 및 모범 사례가 있습니다.

Exchange 서버 및 역방향 프록시 서버에 사용하는 인증서의 수를 최소화하는 것이 가장 좋습니다. 또한 각 데이터 센터에서 이들 서비스의 끝점에 한 인증서를 사용하는 것이 좋습니다. 이러한 접근 방식을 통해 필요한 인증서 수를 최소화하고, 솔루션의 비용과 복잡성을 동시에 줄일 수 있습니다.

외부에서 Outlook 사용 클라이언트의 경우, 각 데이터 센터에 한 가지 SAN(주체 대체 이름)을 사용하고 인증서에 여러 호스트 이름을 포함하는 것이 좋습니다. 데이터베이스, 서버 또는 데이터 센터 전환 후 외부에서 Outlook 사용 연결을 확인하려면 각 인증서에 동일한 인증서 사용자 이름을 사용하고, Microsoft 표준 형식(msstd)에 동일한 사용자 이름으로 Outlook 공급자 구성 개체 Active Directory를 구성해야 합니다. 예를 들어, 인증서 사용자 이름 mail.contoso.com을 사용하는 경우 특성을 다음과 같이 구성합니다.

    Set-OutlookProvider EXPR -CertPrincipalName "msstd:mail.contoso.com"

Exchange와 통합되는 일부 응용 프로그램에는 추가 인증서를 사용해야 할 수도 있는 특정 인증서 요구 사항이 있습니다. Exchange 2013은 OCS(Office Communications Server)와 함께 사용할 수 있습니다. OCS에는 인증서 사용자 이름에 OCS 서버 이름을 사용하는 1024비트 이상의 인증서가 필요합니다. 인증서 사용자 이름에 OCS 서버 이름을 사용하면 외부에서 Outlook 사용이 제대로 작동하지 않으므로, OCS 환경에 별도의 추가 인증서를 사용해야 합니다.

## 네트워크 계획

각 DAG에서 충족해야 할 특정 네트워킹 요구 사항과 더불어, DAG의 구성원인 각 서버에 대해서는 사이트 복구 구성에 한정되는 일부 요구 사항과 권장 사항이 있습니다. 모든 DAG와 마찬가지로 DAG 구성원이 단일 사이트에 배포되어 있든, 여러 사이트에 배포되어 상관없이 DAG 구성원 간의 왕복 반환 네트워크 대기 시간은 500밀리초 이하여야 합니다. 또한 여러 사이트로 확장된 DAG에 권장되는 특정 구성 설정도 있습니다.

  - **MAPI 네트워크는 복제 네트워크에서 격리되어야 합니다.**   Windows 네트워크 정책, Windows 방화벽 정책 또는 라우터 ACL(액세스 제어 목록)을 사용하여 MAPI 네트워크와 복제 네트워크 간 트래픽을 차단해야 합니다. 이 구성은 네트워크 하트비트 혼선을 막는 데 필요합니다.

  - **클라이언트에 연결된 DNS 레코드의 TTL(Time to Live)은 5분이어야 합니다.**   클라이언트의 가동 중지 시간은 얼마나 빠르게 전환할 수 있는지, 그리고 얼마나 빨리 DNS를 복제하는지, 클라이언트가 업데이트된 DNS 정보를 얼마나 빨리 쿼리하는지에 달려 있습니다. 내/외부 DNS 서버에서 모두 Microsoft Office Exchange, Microsoft Outlook Web App, Exchange ActiveSync 웹 서비스, 외부에서 Exchange 사용, SMTP, POP3 및 IMAP4를 비롯한 모든 Outlook 클라이언트 서비스에 대한 DNS 레코드의 TTL은 5분으로 설정해야 합니다.

  - **고정 경로를 사용하여 복제 네트워크에 대한 연결을 구성합니다.**   각 복제 네트워크 어댑터 간에 네트워크 연결을 제공하려면 영구 고정 경로를 사용합니다. 이는 고정 IP 주소를 사용할 때 각 DAG 구성원에게 수행되는 신속한 일회성 구성입니다. DHCP를 사용하여 복제 네트워크의 IP 주소를 가져오는 중이면 DHCP를 복제 네트워크의 고정 경로를 지정하는 데에도 사용할 수 있으므로 구성 프로세스가 간소화됩니다.

## 일반 사이트 복구 계획

고가용성의 경우 위에서 언급한 요구 사항 외에도, 사이트 복구 구성에 Exchange 2013을 배포(예: 여러 데이터 센터로 DAG 확장)하기 위한 다른 권장 사항이 있습니다. 계획 단계에서의 작업은 사이트 복구 솔루션의 성공과 직결됩니다. 예를 들어 네임스페이스 디자인이 부실하면 인증서와 관련된 문제를 유발할 수 있으며, 인증서 구성이 올바르지 않으면 사용자가 서비스에 액세스할 수 없습니다.

보조 데이터 센터를 활성화하는 데 걸리는 시간을 최소화하고, 보조 데이터 센터에서 오류가 발생한 데이터 센터의 서비스 끝점을 호스팅하려면 적절한 계획이 완료되어야 합니다. 예를 들면 다음과 같습니다.

  - 사이트 복구 솔루션의 SLA 목표는 잘 파악하여 문서화해야 합니다.

  - 보조 데이터 센터의 서버는 두 데이터 센터의 사용자를 호스트할 만큼의 충분한 용량을 갖추어야 합니다.

  - 서비스가 사이트 복구 SLA의 일부로 포함되지 않은 경우 외에는 보조 데이터 센터가 기본 데이터 센터에서 제공하는 서비스를 모두 제공해야 합니다. 여기에는 Active Directory, 네트워킹 인프라(예: DNS, TCP/IP 등), 전화 통신 서비스(통합 메시징을 사용 중인 경우) 및 사이트 인프라(예: 전력, 냉각 등)가 포함됩니다.

  - 오류가 발생한 데이터 센터의 서비스 사용자에게 일부 서비스를 제공하려면 적절한 서버 인증서가 구성되어 있어야 합니다. POP3 및 IMAP4 등의 일부 서비스는 인스턴싱을 허용하지 않고 단일 인증서만 사용하도록 허용합니다. 이런 경우 인증서가 여러 이름이 포함된 SAN 인증서이거나, 조직의 보안 정책이 와일드카드 인증서를 사용하도록 허용한다는 가정하에 여러 이름이 와일드카드 인증서를 사용할 수 있을 정도로 아주 유사해야 합니다.

  - 필요한 서비스를 보조 데이터 센터에 정의해야 합니다. 예를 들어, 기본 데이터 센터가 서로 다른 전송 서버에 각기 다른 세 가지 SMTP URL을 포함하고 있는 경우 보조 데이터 센터에 적절한 구성이 정의되어 있어야 세 가지 모두는 아니더라도 하나 이상의 전송 서버가 작업을 호스팅할 수 있습니다.

  - 필요한 네트워크 구성은 데이터 센터 전환을 지원할 준비가 되어 있어야 합니다. 이는 부하 분산 구성이 준비되어 있고, 전역 DNS가 구성되어 있으며, 라우팅이 적절하게 구성된 인터넷에 연결할 수 있어야 한다는 의미입니다.

  - 데이터 센터 전환에 필요한 DNS를 변경할 수 있도록 하는 전략을 이해해야 합니다. TTL 설정을 비롯한 특정 DNS 변경 사항은 시행 중인 SLA를 지원하도록 정의되고 문서화되어야 합니다.

  - 솔루션 테스트 전략을 수립하고 SLA에 반영해야 합니다. 정기적으로 배포를 검사하는 것만이 오랫동안 배포 품질과 실행 가능성의 수준을 저하시키지 않는 유일한 방법입니다. 배포의 유효성을 검사한 후에는 솔루션의 성공에 직접적인 영향을 주는 구성 부분을 명시적으로 문서화하고, 해당 배포 요소에 대한 변경 관리 프로세스를 강화하는 것이 좋습니다.

맨 위로 이동
