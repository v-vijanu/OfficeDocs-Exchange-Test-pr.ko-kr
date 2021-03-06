﻿---
title: '사용자에 대 한 음성 메일 호출을 검토 합니다.: Exchange 2013 Help'
TOCTitle: 사용자에 대 한 음성 메일 호출을 검토 합니다.
ms:assetid: 95768fe3-3ae2-43bd-9cbf-18c3b85c4592
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ659070(v=EXCHG.150)
ms:contentKeyID: 50556044
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 사용자에 대 한 음성 메일 호출을 검토 합니다.

 

_<strong>적용 대상:</strong> Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>마지막으로 수정된 항목:</strong> 2013-02-22_

사용자 호출 로그를 사용하면 특정 UM(통합 메시징) 사용자에 대한 다음 정보를 볼 수 있습니다.

  - 지난 90일 동안 사용자의 UM 호출에 대한 자세한 정보

  - 각 호출의 오디오 품질. 오디오 품질 메트릭이 호출의 유형과 길이 등의 몇 가지 요소에 따라 달라지기 때문에 일부 호출에는 오디오 품질 메트릭을 사용하지 못할 수도 있습니다.

UM 보고와 관련된 추가 작업에 대한 자세한 내용은 [UM 보고서 절차](um-reports-procedures-exchange-2013-help.md)를 참조하십시오.

## UM 사용 가능 사용자에 대한 호출 로그를 가져오려면 어떻게 해야 합니까?

1.  EAC(Exchange 관리 센터)에서 <strong>통합 메시징 </strong>\> <strong>기타 옵션</strong>![기타 옵션 아이콘](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "기타 옵션 아이콘") \> <strong>사용자 호출 로그</strong>를 선택합니다.

2.  <strong>사용자 선택</strong>을 클릭한 다음 데이터를 보려는 사용자를 선택합니다.

3.  보고서 행의 오디오 품질에 대한 자세한 정보를 보려면 해당 행을 선택하고 <strong>오디오 품질 정보</strong>를 클릭합니다. 오디오 품질을 해석하는 방법에 대한 자세한 내용은 [사용자에 대 한 음성 통화의 오디오 품질을 확인 합니다.](investigate-the-audio-quality-of-voice-calls-for-a-user-exchange-2013-help.md)을 참조하십시오.

4.  보고서를 클립보드에 복사하려면 <strong>모든 행을 클립보드에 복사합니다.</strong>를 클릭합니다.

## UM 사용자 호출 로그를 어떻게 해석합니까?

사용자 호출 로그에는 각 호출에 대한 다음 정보가 포함됩니다.

  - <strong>날짜 및 시간</strong> 선택된 사용자가 Microsoft Outlook Web App에서 설정한 표준 시간대를 기준으로 한 호출 날짜 및 시간입니다.

  - <strong>기간</strong> 분(MM)과 초(SS)로 나타낸 호출 지속 시간입니다. MM:SS 형식입니다.

  - <strong>통화 유형   </strong>통화 유형입니다.
    
      - <strong>전화 응답</strong>   전화에 응답하지 않았으며 사서함 서버로 통화가 전달되었습니다. 발신자가 음성 메시지를 남겼습니다.
    
      - <strong>전화 응답 부재 중 전화</strong>   전화에 응답하지 않았으며 사서함 서버로 통화가 전달되었습니다. 발신자가 음성 메시지를 남기지 않았습니다.
    
      - <strong>구독자 액세스</strong>   구독자 액세스 번호가 호출되었습니다. 발신자가 전화를 통해 전자 메일 메시지, 일정 및 음성 메시지에 액세스하기 위해 내선 번호와 암호를 사용하여 UM에 로그인하고 인증되었습니다.
    
      - <strong>자동 전화 교환</strong>   UM 자동 전화 교환에서 전화에 응답했습니다. 이러한 호출은 보통 전화 건 사람이 조직의 대표 전화 번호로 건 전화입니다.
    
      - <strong>팩스</strong>   팩스 톤이 감지된 호출을 받았습니다. 팩스 파트너를 구성한 경우 이 호출이 파트너에게 전송되었습니다.
    
      - <strong>PlayonPhone</strong>   사용자가 Microsoft Outlook Web App 또는 Outlook에서 음성 메시지에 있는 전화에서 재생 단추를 클릭했으므로 UM에서 호출을 수행했습니다.
    
      - <strong>FindMe</strong>   전화 응답 규칙에서 내 번호 찾기 규칙을 사용한 결과 UM에서 아웃바운드 호출을 수행했습니다.
    
      - <strong>인증되지 않은 파일럿 번호</strong>   Outlook Voice Access 번호에 대해 호출이 수행되었습니다. 발신자가 로그인하지 않았고 인증되지 않았습니다.
    
      - <strong>인사말 녹음</strong>   사용자의 개인 인사말을 녹음하기 위해 UM에서 호출을 수행했습니다.
    
      - <strong>없음</strong>   호출이 수행되었지만 유형이 정의되지 않았습니다.

  - <strong>호출 번호</strong> 발신자의 전화 번호 또는 SIP 주소입니다.

  - <strong>호출된 번호</strong> 지정된 호출 받는 사람의 전화 번호 또는 SIP 주소(Microsoft Office Communications Server 2007 R2 또는 Microsoft Lync Server 사용자와 같은 SIP URI 다이얼 플랜의 사용자인 경우)입니다.

  - <strong>UM IP 게이트웨이</strong> 호출에 사용된 UM IP 게이트웨이입니다.

  - <strong>오디오 품질</strong> 호출의 전체적인 오디오 품질입니다. 오디오 품질에 대한 자세한 정보를 보려면 해당 행을 선택하고 <strong>오디오 품질 정보</strong>를 클릭하십시오.

