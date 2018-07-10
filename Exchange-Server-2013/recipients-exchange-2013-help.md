﻿---
title: '받는 사람: Exchange 2013 Help'
TOCTitle: 받는 사람
ms:assetid: 40300ed4-85a5-463d-bb3a-cf787bd44e9d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Bb201680(v=EXCHG.150)
ms:contentKeyID: 50482945
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 받는 사람

 

_**적용 대상:** Exchange Online, Exchange Server 2013_

_**마지막으로 수정된 항목:** 2015-03-09_

메시지를 주고받는 사람과 리소스는 메시징 및 공동 작업 시스템의 핵심입니다. Exchange 조직에서 이러한 사람과 리소스를 *받는 사람*이라고 합니다. 받는 사람은 Microsoft Exchange에서 메시지를 배달하거나 라우팅할 수 있는 Active Directory의 메일 사용 가능 개체입니다.

## Exchange 받는 사람 유형

Exchange에는 여러 가지 명시적인 받는 사람 유형이 포함되어 있습니다. 각 받는 사람 유형은 EAC(Exchange 관리 센터)에서 식별되며 Exchange 관리 셸의 *RecipientTypeDetails* 속성에 고유한 값을 갖고 있습니다. 명시적인 받는 사람 유형을 사용하면 다음과 같은 이점을 얻을 수 있습니다.

  - 여러 받는 사람 유형을 쉽게 구분할 수 있습니다.

  - 각 받는 사람 유형별로 검색하고 정렬할 수 있습니다.

  - 선택된 받는 사람 유형에 대해 더욱 쉽게 대량 관리 작업을 수행할 수 있습니다.

  - EAC는 받는 사람 유형을 사용하여 여러 속성 페이지를 렌더링하므로 받는 사람 속성을 보다 쉽게 볼 수 있습니다. 예를 들어 대화방 사서함에 대해서는 리소스 용량이 표시되지만 사용자 사서함에 대해서는 표시되지 않습니다.

다음 표에서는 사용 가능한 받는 사람 유형을 보여 줍니다. 이러한 모든 받는 사람 유형은 이 항목 뒷부분에 보다 자세히 설명되어 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>받는 사람 유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>동적 메일 그룹</p></td>
<td><p>받는 사람 필터와 조건을 사용하여 메시지가 전송될 때 해당 구성원을 파생하는 메일 그룹입니다.</p></td>
</tr>
<tr class="even">
<td><p>장비 사서함</p></td>
<td><p>휴대용 컴퓨터, 프로젝터, 마이크 또는 회사 차량과 같은 위치가 한정되지 않은 리소스에 할당되는 리소스 사서함입니다. 장비 사서함은 모임 요청 시 리소스로 포함될 수 있으며 사용자를 위한 간편하고 효율적인 리소스 사용 방법을 제공합니다.</p></td>
</tr>
<tr class="odd">
<td><p>연결된 사서함</p></td>
<td><p>별도의 트러스트된 포리스트의 개별 사용자에게 할당되는 사서함입니다.</p></td>
</tr>
<tr class="even">
<td><p>메일 연락처</p></td>
<td><p>Exchange 조직 외부에 있는 사람이나 조직에 대한 정보가 포함된 메일 사용이 가능한 Active Directory 연락처입니다. 각 메일 연락처에는 외부 전자 메일 주소가 있습니다. 메일 연락처로 전송되는 모든 메시지는 이 외부 전자 메일 주소로 라우팅됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>메일 포리스트 연락처</p></td>
<td><p>다른 포리스트의 받는 사람 개체를 나타내는 메일 연락처입니다. 메일 포리스트 연락처는 일반적으로 MIIS(Microsoft Identity Integration Server) 동기화에 의해 만들어집니다.</p>

> [!IMPORTANT]
> 메일 포리스트 연락처는 MIIS 또는 유사한 사용자 지정 동기화를 통해서만 업데이트되는 읽기 전용 받는 사람 개체입니다. EAC 또는 셸을 사용하여 메일 포리스트 연락처를 제거하거나 수정할 수 없습니다.


</td>
</tr>
<tr class="even">
<td><p>메일 사용자</p></td>
<td><p>Exchange 조직 외부의 사용자를 나타내는 메일 사용이 가능한 Active Directory 사용자입니다. 각 메일 사용자에게는 외부 전자 메일 주소가 있습니다. 메일 사용자에게 전송되는 모든 메시지는 이 외부 전자 메일 주소로 라우팅됩니다.</p>
<p>Active Directory 로그온 자격 증명을 갖고 있으며 리소스에 액세스할 수 있다는 점을 제외하면 메일 사용자는 메일 연락처와 유사합니다.</p></td>
</tr>
<tr class="odd">
<td><p>메일 사용 가능 비유니버설 그룹</p></td>
<td><p>메일 사용이 가능한 Active Directory 글로벌 또는 로컬 그룹 개체입니다. 메일 사용이 가능한 비유니버설 그룹은 Exchange Server 2007에서 더 이상 지원되지 않으며 Exchange 2003 또는 이전 버전의 Exchange에서 마이그레이션된 경우에만 존재할 수 있습니다. Exchange Server 2013에서 비유니버설 메일 그룹을 만들 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p>메일 사용 가능 공용 폴더</p></td>
<td><p>메시지를 받도록 구성되어 있는 Exchange 공용 폴더입니다.</p></td>
</tr>
<tr class="odd">
<td><p>메일 그룹</p></td>
<td><p>메일 그룹은 받는 사람 그룹으로 메시지를 배포하는 데만 사용할 수 있는 메일 사용이 가능한 Active Directory 메일 그룹 개체입니다.</p></td>
</tr>
<tr class="even">
<td><p>메일 사용 가능 보안 그룹</p></td>
<td><p>메일 사용 가능 보안 그룹은 Active Directory의 리소스에 대한 액세스 권한을 할당하는 데 사용되며 메시지를 배포하기 위해서도 사용될 수 있는 Active Directory 유니버설 보안 그룹 개체입니다.</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange 받는 사람</p></td>
<td><p>시스템 생성 메시지와 기타 메시지를 구분하는, 잘 알려진 통합 메시지 보낸 사람을 제공하는 특수한 받는 사람 개체입니다. 이 개체는 이전 버전의 Exchange에서 시스템 생성 메시지에 대해 사용되었던 시스템 관리자 보낸 사람을 대체합니다.</p></td>
</tr>
<tr class="even">
<td><p>대화방 사서함</p></td>
<td><p>회의실, 강당 및 교육실과 같은 모임 장소에 할당되는 리소스 사서함입니다. 대화방 사서함은 모임 요청 시 리소스로 포함될 수 있으며 사용자를 위한 간편하고 효율적인 모임 구성 방법을 제공합니다.</p></td>
</tr>
<tr class="odd">
<td><p>공유 사서함</p></td>
<td><p>기본적으로 단일 사용자에게 연결되어 있지 않으며 일반적으로 여러 사용자의 액세스를 허용하도록 구성된 사서함입니다.</p></td>
</tr>
<tr class="even">
<td><p>사이트 사서함</p></td>
<td><p>전자 메일 메시지를 저장하기 위한 Exchange 사서함과 문서를 저장하기 위한 SharePoint 사이트로 구성된 사서함입니다. 사용자는 동일한 클라이언트 인터페이스를 사용하여 전자 메일 메시지와 문서에 액세스할 수 있습니다. 자세한 내용은 <a href="site-mailboxes-exchange-2013-help.md">사이트 사서함</a> 항목을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p>사용자 사서함</p></td>
<td><p>Exchange 조직의 개별 사용자에게 할당되는 사서함입니다. 일반적으로 이 사서함에는 메시지, 일정 항목, 연락처, 작업, 문서 및 기타 중요한 업무 데이터가 들어 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>Office 365 사서함</p></td>
<td><p>하이브리드 배포에서 Office 365 사서함은 온-프레미스의 Active Directory에 있는 메일 사용자와 Exchange Online에 있는 연결된 클라우드 사서함으로 구성되어 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>연결된 사용자</p></td>
<td><p>연결된 사용자는 사용자가 있는 포리스트가 아닌 포리스트에 있는 사서함을 가진 사용자입니다.</p></td>
</tr>
</tbody>
</table>


## 사서함

사서함은 Exchange 조직의 정보 근로자가 사용하는 가장 일반적인 받는 사람 유형입니다. 각 사서함은 Active Directory 사용자 계정과 연결되어 있습니다. 사용자는 사서함을 사용하여 메시지를 주고받고, 메시지, 약속, 작업, 메모 및 문서를 저장할 수 있습니다. 사서함은 Exchange 조직의 사용자를 위한 기본적인 메시징 및 공동 작업 도구입니다.

## 사서함 구성 요소

다음 그림에 표시된 것과 같이 각 사서함은 Active Directory 사용자와 Exchange 사서함 데이터베이스에 저장되어 있는 사서함 데이터로 구성됩니다. 사서함에 대한 모든 구성 데이터는 Active Directory 사용자 개체의 Exchange 특성에 저장됩니다. 사서함 데이터베이스에는 사용자 계정과 연결된 사서함에 있는 실제 데이터가 포함됩니다.


> [!IMPORTANT]
> 새 사용자나 기존 사용자에 대해 사서함을 만들 때 사서함에 필요한 Exchange 특성은 Active Directory의 해당 사용자 개체에 추가됩니다. 연결된 사서함 데이터는 사서함이 메시지를 수신하거나 사용자가 사서함에 로그인할 때까지 만들어지지 않습니다.



**사서함 구성 요소**

![사서함을 구성하는 요소](images/Bb201680.5fcb5e6d-656e-42ae-871f-0eef8aea456b(EXCHG.150).gif "사서함을 구성하는 요소")

> [!CAUTION]
> 사서함을 제거하는 경우 Exchange 사서함 데이터베이스에 저장되어 있는 사서함 데이터는 삭제되도록 표시되고 연결된 사용자 계정도 Active Directory에서 삭제됩니다. 사용자 계정을 보존하고 사서함 데이터만 삭제하려면 사서함을 사용할 수 없도록 설정해야 합니다.


## 사서함 유형

Exchange에서는 다음과 같은 사서함 유형을 지원합니다.

  - **사용자 사서함   **사용자 사서함은 Exchange 조직의 개별 사용자에게 할당됩니다. 사용자 사서함은 사용자에게 다양한 공동 작업 플랫폼을 제공합니다. 사용자는 메시지를 주고받고, 연락처를 관리하고, 모임을 예약하고, 작업 목록을 유지 관리할 수 있으며 사서함으로 음성 메일 메시지가 배달되도록 할 수도 있습니다. 사용자 사서함은 가장 보편적으로 사용되는 사서함 유형이며 일반적으로 조직의 사용자에게 할당되는 사서함 유형입니다.

  - **연결된 사서함**   연결된 사서함은 사용자가 별도의 트러스트된 포리스트에서 액세스하는 사서함입니다. 연결된 사서함은 리소스 포리스트에 Exchange를 배포하는 조직에 필요할 수 있습니다. 리소스 포리스트 시나리오를 사용하면 조직에서 Exchange를 단일 포리스트로 중앙 집중화하면서 하나 이상의 트러스트된 포리스트에서 사용자 계정으로 Exchange 조직에 액세스할 수 있도록 허용합니다.
    
    앞에서 설명한 대로 모든 사서함에는 연결되어 있는 사용자 계정이 있어야 합니다. 그러나 연결된 사서함에 액세스하는 사용자 계정은 Exchange가 배포되어 있는 포리스트에 존재하지 않습니다. 따라서 Exchange와 같은 포리스트에 있는 사용할 수 없도록 설정된 사용자 계정이 연결된 각 사서함에 연결됩니다. 다음 그림에서는 연결된 사서함 액세스에 사용되는 연결된 사용자 계정과, 연결된 사서함과 연결되어 있는 Exchange 리소스 포리스트의 사용할 수 없도록 설정된 사용자 계정 간의 관계를 보여 줍니다.
    
    **연결된 사서함**
    
    ![리소스 포리스트가 있는 복잡한 Exchange 조직](images/Aa998031.706725cf-e520-4b89-a275-acd8fb58943a(EXCHG.150).gif "리소스 포리스트가 있는 복잡한 Exchange 조직")  

  - **Office 365 사서함   **하이브리드 배포에서 Exchange Online에 Office 365 사서함을 만들 때 메일 사용자가 온-프레미스의 Active Directory에 만들어집니다. 디렉터리 동기화가 구성된 경우 이 새로운 사용자 개체를 Office 365와 자동으로 동기화합니다. Office 365에서 이 개체는 Exchange Online의 클라우드 사서함으로 변환됩니다. Office 365 사서함을 일반 사용자 사서함, 회의실용 리소스 사서함. 장비 및 공유 사서함으로 만들 수 있습니다.

  - **공유 사서함**   공유 사서함은 기본적으로는 개별 사용자와 연결되어 있지 않으며 일반적으로 여러 사용자의 액세스를 허용하도록 구성되어 있습니다.
    
    다른 사용자에게 추가로 모든 사서함 유형에 대한 로그온 액세스 권한을 할당할 수 있지만 공유 사서함은 이 기능에만 사용됩니다. 공유 사서함과 연결되어 있는 Active Directory 사용자는 사용할 수 없도록 설정된 계정이어야 합니다. 공유 사서함을 만든 후에 해당 공유 사서함에 액세스해야 하는 모든 사용자에게 사용 권한을 할당해야 합니다.

  - **리소스 사서함**   리소스 사서함은 리소스를 예약하는 데 사용하는 특수 사서함입니다. 모든 사서함 유형과 마찬가지로 리소스 사서함에는 연결된 Active Directory 사용자 계정이 있지만 이것은 사용할 수 없도록 설정된 계정이어야 합니다. 리소스 사서함의 유형은 다음과 같습니다.
    
      - **대화방 사서함**   이러한 사서함은 회의실, 강당 및 교육실과 같은 모임 장소에 할당됩니다.
    
      - **장비 사서함**   이러한 사서함은 휴대용 컴퓨터, 프로젝터, 마이크 또는 회사 차량과 같이 위치가 한정되지 않은 리소스에 할당됩니다.
    
    모임 요청에 두 유형의 리소스 사서함을 모두 포함하여, 사용자가 간편하고 효율적으로 리소스를 사용하도록 할 수 있습니다. 리소스 소유자가 정의한 리소스 예약 정책에 따라 들어오는 모임 요청을 자동으로 처리하도록 리소스 사서함을 구성할 수 있습니다. 예를 들어 리소스 소유자의 승인이 필요할 수 있는 되풀이 모임을 제외한 들어오는 모임 요청을 자동으로 수락하도록 회의실을 구성할 수 있습니다.

## 시스템 사서함

시스템 사서함은 설치하는 동안 Exchange에 의해 Active Directory 포리스트의 루트 도메인에 만들어집니다. 사용자나 관리자는 이러한 사서함에 로그인할 수 없습니다. 시스템 사서함은 UM(통합 메시징), 마이그레이션, 메시지 승인 및 원본 위치 eDiscovery와 같은 Exchange 기능을 위해 만들어졌습니다. 이 표에서는 Active Directory에 표시된 대로 시스템 사서함에 대한 정보를 보여 줍니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>사서함</th>
<th>이름</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>조직</p></td>
<td><p>SystemMailbox {bb558c35-97f1-4cb9-8ff7-d53741dc928c}</p></td>
</tr>
<tr class="even">
<td><p>메시지 승인</p></td>
<td><p>SystemMailbox {1f05a927-<em>xxxx</em>- <em>xxxx</em> - <em>xxxx</em> -<em>xxxxxxxxxxxx</em>}</p>
<p>여기서 <em>x</em>는 각 Exchange 포리스트에 대해 무작위로 할당된 고유 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p>UM 데이터 저장소</p></td>
<td><p>SystemMailbox {e0dc1c29-89c3-4034-b678-e6c29d823ed9}</p></td>
</tr>
<tr class="even">
<td><p>검색</p></td>
<td><p>DiscoverySearchMailbox {D919BA05-46A6-415f-80AD-7E09334BB852}</p></td>
</tr>
<tr class="odd">
<td><p>페더레이션된 전자 메일</p></td>
<td><p>FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042</p></td>
</tr>
<tr class="even">
<td><p>마이그레이션</p></td>
<td><p>Migration.8f3e7716-2011-43e4-96b1-aba62d229136</p></td>
</tr>
</tbody>
</table>


Exchange 조직에 있는 마지막 사서함 서버의 서비스를 해제하려는 경우 먼저 [Disable-Mailbox](https://technet.microsoft.com/ko-kr/library/aa997210\(v=exchg.150\)) cmdlet을 사용하여 이러한 시스템 사서함을 사용하지 않도록 설정해야 합니다. 이러한 시스템 사서함이 포함된 사서함 서버의 서비스를 해제하는 경우, 기능을 그대로 유지하려면 다른 사서함 서버로 시스템 사서함을 이동해야 합니다.

## 사서함 계획

사서함은 사서함 서버 역할이 설치된 Exchange 서버의 사서함 데이터베이스에 만들어집니다. 사서함 사용자에게 안정적이고 효과적인 플랫폼을 제공하기 위해서는 사서함 서버 및 데이터베이스의 상세한 배포 계획이 반드시 필요합니다. 사서함 서버 및 데이터베이스 계획에 대한 자세한 내용은 [계획 및 배포](planning-and-deployment-for-exchange-2013-installation-instructions.md) 항목을 참조하십시오.

## 메일 그룹

메일 그룹은 여러 받는 사람에게 메시지를 배포하는 데 주로 사용되는 메일 사용이 가능한 Active Directory 그룹 개체입니다. 모든 받는 사람 유형이 메일 그룹의 구성원이 될 수 있습니다.


> [!IMPORTANT]
> Active Directory와 Exchange 간의 용어 차이에 주의하십시오. Active Directory에서는 메일 사용이 가능한지 여부에 관계없이 보안 컨텍스트가 없는 모든 그룹을 메일 그룹이라고 합니다. Exchange에서는 보안 컨텍스트가 있는지 여부에 관계없이 메일 사용이 가능한 모든 그룹을 메일 그룹이라고 합니다.



Exchange에서는 다음과 같은 유형의 메일 그룹을 지원합니다.

  - **메일 그룹**   메일 사용이 가능하도록 설정된 Active Directory 유니버설 메일 그룹 개체입니다. 받는 사람 그룹에 메시지를 배포하는 데만 사용할 수 있습니다.

  - **메일 사용 가능 보안 그룹**   메일 사용이 가능하도록 설정된 Active Directory 유니버설 보안 그룹 개체입니다. Active Directory의 리소스에 액세스 권한을 할당하는 데 사용할 수 있으며 메시지를 배포하는 데도 사용할 수 있습니다.

  - **메일 사용 가능 비유니버설 그룹**   메일 사용이 가능하도록 설정되어 있는 Active Directory 글로벌 또는 로컬 그룹 개체입니다. 유니버설 메일 그룹만 만들거나 메일을 사용하도록 설정할 수 있습니다. 유니버설 그룹이 아닌 이전 버전의 Exchange에서 마이그레이션된 그룹에 대해 메일을 사용하도록 설정할 수 있습니다. 이러한 그룹은 EAC 또는 셸을 사용하여 계속 관리할 수 있습니다.
    

    > [!NOTE]
    > 도메인 로컬 그룹이나 글로벌 그룹을 유니버설 그룹으로 변환하려면 셸에서 <A href="https://technet.microsoft.com/ko-kr/library/bb123770(v=exchg.150)">Set-Group</A> cmdlet을 사용할 수 있습니다.



## 동적 메일 그룹

동적 메일 그룹은 구성원 자격의 기준이 정의된 받는 사람 집합이 아닌 특정 받는 사람 필터인 메일 그룹입니다.

일반 메일 그룹과 달리 동적 메일 그룹의 구성원 목록은 지정된 필터 및 조건을 기반으로 메시지가 해당 그룹으로 전송될 때마다 계산됩니다. 동적 메일 그룹에 전자 메일 메시지를 보내면, 해당 동적 메일 그룹에 대해 정의된 기준과 일치하는 조직의 모든 받는 사람에게 메시지가 배달됩니다.


> [!IMPORTANT]
> 동적 메일 그룹은 메시지 전송 시 그룹의 필터와 일치하는 특성을 갖는 모든 받는 사람이 Active Directory에 포함됩니다. 받는 사람의 속성을 그룹 필터와 일치하게 수정하는 경우 받는 사람이 실수로 그룹 구성원이 되어 동적 메일 그룹으로 전송된 메시지를 수신할 수 있습니다. 적절하게 정의되고 일관된 계정 프로비전 프로세스를 통해 이러한 문제가 발생할 가능성을 낮출 수 있습니다.



동적 메일 그룹에 대한 받는 사람 필터를 만드는 데 미리 만든 필터를 사용할 수 있습니다. *미리 만든 필터*는 일반적으로 사용되는 필터로, 다양한 받는 사람 필터링 기준을 충족합니다. 이러한 필터를 사용하여 동적 메일 그룹에 포함할 받는 사람 유형을 지정할 수 있습니다. 또한 받는 사람이 충족해야 하는 조건 목록을 지정할 수도 있습니다. 다음 속성을 기준으로 미리 만든 조건을 만들 수 있습니다.

  - 사용자 지정 특성 1–15

  - 시/도

  - 회사

  - 부서

  - 받는 사람 컨테이너

위에서 나열된 것 이외의 받는 사람 속성을 기준으로 조건을 지정할 수도 있습니다. 이렇게 하려면 셸을 사용하여 동적 메일 그룹에 대한 사용자 지정 쿼리를 만들어야 합니다. 사용자 지정 받는 사람 필터가 있는 동적 메일 그룹의 필터 및 조건 설정은 셸을 통해서만 관리할 수 있습니다. 사용자 지정 쿼리를 사용하여 동적 메일 그룹을 만드는 방법의 예는 [동적 메일 그룹 관리](manage-dynamic-distribution-groups-exchange-2013-help.md)을 참조하십시오.

## 메일 연락처

메일 연락처는 일반적으로 Exchange 조직 외부에 있는 사람이나 조직에 대한 정보를 포함합니다. 메일 연락처는 GAL(전체 주소 목록) 및 기타 주소 목록이라고도 하는 조직의 공유 주소록에 표시될 수 있으며 메일 그룹에 구성원으로 추가될 수 있습니다. 각 연락처에는 외부 전자 메일 주소가 있으며 연락처로 전송되는 모든 전자 메일 메시지는 해당 주소로 자동 전달됩니다. 연락처는 공유 주소록에서 내부 리소스에 액세스할 필요가 없는 Exchange 조직 외부 사람을 나타내는 데 적합합니다. 메일 연락처 유형은 다음과 같습니다.

  - **메일 연락처**   Exchange 조직 외부의 사람이나 조직에 대한 정보를 포함하는 메일 사용이 가능한 Active Directory 연락처입니다.

  - **메일 포리스트 연락처**   다른 포리스트의 받는 사람 개체를 나타냅니다. 이러한 연락처는 일반적으로 디렉터리 동기화에 의해 만들어집니다. 메일 포리스트 연락처는 동기화를 통해서만 업데이트 또는 제거할 수 있는 읽기 전용 받는 사람 개체입니다. Exchange 관리 인터페이스를 사용하여 메일 포리스트 연락처를 수정하거나 제거할 수는 없습니다.

## 메일 사용자

메일 사용자는 메일 연락처와 비슷합니다. 둘 다 외부 전자 메일 주소가 있고 Exchange 조직 외부에 있는 사람에 대한 정보를 포함하며 공유 주소록과 기타 주소 목록에 표시될 수 있습니다. 그러나 메일 사용자는 메일 연락처와 달리 Active Directory 로그온 자격 증명을 가지며 사용 권한이 할당된 리소스에 액세스할 수 있습니다.

조직 외부 사람이 네트워크의 리소스에 액세스해야 할 경우 메일 연락처 대신 메일 사용자를 만들어야 합니다. 예를 들면 서버 인프라에 대한 액세스 권한이 필요하지만 고유한 외부 주소를 사용해야 하는 단기 컨설턴트에 대한 메일 사용자를 만들려고 할 수 있습니다.

또 다른 경우로 사용자의 조직에서 Exchange 사서함을 유지 관리하지 않을 사용자에 대해 메일 사용자를 만들 수도 있습니다. 예를 들어 인수 후에는, 인수된 해당 회사가 별도의 메시징 인프라를 유지 관리할 수 있지만 사용자 네트워크의 리소스에 대한 액세스 권한이 필요할 수 있습니다. 이러한 사용자를 위해 사서함 사용자 대신 메일 사용자를 만들 수 있습니다.


> [!NOTE]
> EAC에서 <STRONG>받는 사람</STRONG> &gt; <STRONG>연락처</STRONG> 페이지를 사용하여 메일 사용자를 만들고 관리합니다. 메일 사용자를 위한 별도의 페이지는 없습니다.



## 메일 사용이 가능한 공용 폴더

공용 폴더는 많은 사용자들이 공유하는 정보의 리포지토리로 사용됩니다. 공용 폴더를 메일 사용 가능하도록 설정하면 추가 수준의 기능이 사용자에게 제공됩니다. 사용자는 메시지를 폴더에 게시할 수 있을 뿐 아니라 전자 메일 메시지를 폴더에 보낼 수 있으며 어떤 경우에는 공용 폴더에서 전자 메일 메시지를 받을 수도 있습니다. 메일 사용 가능 폴더마다 해당 전자 메일 주소, 주소록 이름 및 기타 메일 관련 특성을 저장하는 개체가 Active Directory에 있습니다.

EAC 또는 셸을 사용하여 공용 폴더를 관리할 수 있습니다. 공용 폴더를 관리하는 방법에 대한 자세한 내용은 [공용 폴더](public-folders-exchange-2013-help.md)를 참조하십시오.

## Microsoft Exchange 받는 사람

Microsoft Exchange 받는 사람은 시스템 생성 메시지와 기타 메시지를 구분하는, 잘 알려진 통합 메시지 보낸 사람을 제공하는 특수한 받는 사람 개체입니다. 이 개체는 이전 버전의 Exchange에서 시스템 생성 메시지에 대해 사용되었던 시스템 관리자 보낸 사람을 대체합니다.

Microsoft Exchange 받는 사람은 사서함, 메일 사용자 또는 메일 연락처 같은 일반적인 받는 사람 개체가 아니며 일반적인 받는 사람 도구를 사용하여 관리되지 않습니다. 하지만 셸에서 [Set-OrganizationConfig](https://technet.microsoft.com/ko-kr/library/aa997443\(v=exchg.150\)) cmdlet을 사용하여 Microsoft Exchange 받는 사람을 구성할 수 있습니다.


> [!NOTE]
> 시스템 생성 메시지를 외부 보낸 사람에게 보내면 Microsoft Exchange 받는 사람이 메시지 보낸 사람으로 사용되지 않습니다. 대신 <A href="https://technet.microsoft.com/ko-kr/library/bb124151(v=exchg.150)">Set-TransportConfig</A> cmdlet의 <EM>ExternalPostmasterAddress</EM> 매개 변수로 지정된 전자 메일 주소가 사용됩니다.



## 받는 사람 설명서

다음 표에는 Exchange 받는 사람에 대해 자세히 알아보고 Exchange 받는 사람을 관리하는 데 유용한 항목에 대한 링크가 포함되어 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="create-user-mailboxes-exchange-2013-help.md">사용자 사서함 만들기</a></p></td>
<td><p>Exchange 관리 센터나 Exchange 관리 셸을 사용하여 사용자 사서함을 만드는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-user-mailboxes-exchange-2013-help.md">사용자 사서함 관리</a></p></td>
<td><p>사용자 사서함을 만들고, 사서함 속성을 변경하고, 여러 사서함의 선택된 속성을 대량으로 편집하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-linked-mailboxes-exchange-2013-help.md">연결 된 사서함 관리</a></p></td>
<td><p>연결된 사서함에 대한 요구 사항, 연결된 사서함을 만들고 마스터 계정에 연결하는 방법 및 연결된 사서함 속성을 변경하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-and-manage-distribution-groups-exchange-2013-help.md">메일 그룹 만들기 및 관리</a></p></td>
<td><p>메일 그룹을 만들고 관리하는 방법과 조직의 그룹 명명 정책을 만드는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-mail-enabled-security-groups-exchange-2013-help.md">메일 사용이 가능한 보안 그룹 관리</a></p></td>
<td><p>메일 사용 가능 보안 그룹을 만들고 관리하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-dynamic-distribution-groups-exchange-2013-help.md">동적 메일 그룹 관리</a></p></td>
<td><p>동적 메일 그룹을 만들고 사용자 지정 특성 및 기타 속성을 사용하여 그룹 구성원을 확인하는 등의 동적 메일 그룹 속성을 관리하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-mail-contacts-exchange-2013-help.md">메일 연락처 관리</a></p></td>
<td><p>메일 연락처를 만들고 관리하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-mail-users-exchange-2013-help.md">메일 사용자 관리</a></p></td>
<td><p>메일 사용자를 만들고 관리하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="create-and-manage-room-mailboxes-exchange-2013-help.md">대화방 사서함 만들기 및 관리</a></p></td>
<td><p>대화방 사서함을 만들고 되풀이 모임을 사용하도록 설정하고 예약 옵션을 구성하는 등의 대화방 사서함 속성을 관리하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-equipment-mailboxes-exchange-2013-help.md">장비 사서함 관리</a></p></td>
<td><p>장비 사서함을 만들고, 예약 옵션을 구성하고, 기타 사서함 속성을 관리하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="disconnected-mailboxes-exchange-2013-help.md">연결이 끊어진 사서함</a></p></td>
<td><p>연결이 끊어진 두 유형의 사서함 및 이러한 사서함이 작동하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="custom-attributes-exchange-2013-help.md">사용자 정의 특성</a></p></td>
<td><p>사용자 지정 특성을 사용하여 받는 사람에 대한 정보를 추가하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/ko-kr/library/bb124268(v=exchg.150)">받는 사람 셸 명령에 대 한 필터</a></p></td>
<td><p>명령과 함께 미리 만든 필터나 사용자 지정 필터를 사용하여 받는 사람 집합을 필터링하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-permissions-for-recipients-exchange-online-help.md">받는 사람에 대 한 사용 권한 관리</a></p></td>
<td><p>EAC 또는 셸을 사용하여 사용자 및 그룹에 사용 권한을 할당하는 방법에 대해 알아봅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="automatic-mailbox-distribution-exchange-2013-help.md">자동 사서함 배포</a></p></td>
<td><p>자동 사서함 배포가 작동하는 방법과 새 사서함 및 이동된 사서함에 대해 선택되는 사서함 데이터베이스를 제어하는 방법에 대해 알아봅니다.</p></td>
</tr>
</tbody>
</table>
