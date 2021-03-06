﻿---
title: '설치를 계속하려면 컴퓨터를 다시 시작해야 함: Exchange 2013 Help'
TOCTitle: 설치를 계속하려면 컴퓨터를 다시 시작해야 함
ms:assetid: d5c73280-4e54-473a-b328-9673af11e2c0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/ms.exch.setupreadiness.rebootpending(v=EXCHG.150)
ms:contentKeyID: 50484231
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 설치를 계속하려면 컴퓨터를 다시 시작해야 함

 

_**적용 대상:** Exchange Server_

_**마지막으로 수정된 항목:** 2016-12-09_

로컬 컴퓨터를 다른 프로그램의 설치를 완료 하려면 다시 시작 해야 또는 업데이트 하는 Windows 않기 때문에 Microsoft Exchange Server 2013 설치를 계속할 수는 없습니다.

## 그 이유는 무엇일까요?

프로그램 및 Windows 업데이트가 설치되면 컴퓨터에 저장되어 있는 파일이 변경됩니다. 설치하는 동안 프로그램 또는 Windows 업데이트가 사용 중인 파일을 변경해야 하는 경우도 있습니다. 이 경우 다른 프로그램(예: Exchange 2013)을 설치하려면 먼저 컴퓨터를 다시 시작해야 합니다. 올바른 작동에 필요한 모든 필수 구성 요소가 설치될 수 있도록 Exchange 설치 프로그램은 다른 모든 설치가 완료되도록 요구합니다.

경우에 따라 이전 프로그램 설치 또는 Windows 업데이트의 설치가 제대로 완료되지 않을 수 있습니다. 이 경우 컴퓨터를 다시 시작해야 한다고 생각하는 Windows 및 기타 프로그램 변경 내용이 남아 있을 수 있습니다. 그렇지만 설치가 실패할 경우 이러한 변경 내용이 절대 정리되지 않으므로 Windows 업데이트 및 기타 프로그램의 설치가 차단될 수 있습니다. 이 경우 Exchange 설치 프로그램을 실행할 때마다 이 오류가 계속 표시됩니다.

## 수정 방법

대부분의 경우 컴퓨터를 다시 시작하기만 하면 이 오류를 건너뛸 수 있습니다. 그러나 컴퓨터를 이미 다시 시작했어도 이 오류가 다시 표시될 수도 있습니다. 프로그램 또는 Windows 업데이트의 설치를 위해 추가 변경이 필요하며, 이러한 변경을 적용하기 위해 컴퓨터를 다시 시작해야 하는 경우에 이러한 상황이 발생할 수 있습니다. 컴퓨터를 다시 시작한 후에 이 오류가 표시되면 다시 시작해 보세요.

컴퓨터를 2~3번 넘게 다시 시작해도 이 오류가 계속 표시되면 최근에 설치한 프로그램 또는 Windows 업데이트를 다시 설치해 보세요. 이를 통해 실패한 설치가 완료될 수 있습니다.

컴퓨터를 다시 시작 하 고 최근 프로그램이 나 Windows 업데이트를 다시 설치 후 하면 *여전히* 이 오류가 발생 하는 경우에 Microsoft 지원 서비스에 문의 하는 것이 좋습니다. 이유 Windows 및 기타 프로그램 생각 컴퓨터를 다시 시작 해야 하는 이유를 찾을 수 있도록 해 표시 됩니다. Microsoft 기술 지원 서비스에 문의 하십시오 하려면 [Microsoft Exchange 서버에 대 한 지원](https://go.microsoft.com/fwlink/p/?linkid=525940)로 이동 합니다.


> [!WARNING]
> 절대로 Windows 레지스트리에서 키나 값을 수동으로 삭제 또는 변경하여 이 문제를 해결하지 않도록 합니다. 이렇게 하면 당장은 문제가 해결될 수 있으나 나중에 다른 문제가 발생할 수 있습니다. 실패한 설치가 Windows 업데이트인 경우에 특히 중요합니다.


