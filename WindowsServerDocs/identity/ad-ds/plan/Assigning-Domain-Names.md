---
ms.assetid: 73897497-b189-4305-b234-e057ffda163a
title: ドメイン名を割り当てる
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 357c136f108c6d8e9e2a15dd9449ab61663079e2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408999"
---
# <a name="assigning-domain-names"></a>ドメイン名を割り当てる

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

プラン内のすべてのドメインに名前を割り当てる必要があります。 Active Directory Domain Services (AD DS) ドメインには、次の2種類の名前があります。ドメインネームシステム (DNS) 名と NetBIOS 名。 一般に、エンドユーザーには両方の名前が表示されます。 Active Directory ドメインの DNS 名には、プレフィックスとサフィックスという2つの部分があります。 ドメイン名を作成する場合は、まず DNS プレフィックスを決定します。 これは、ドメインの DNS 名の最初のラベルです。 サフィックスは、フォレストのルートドメインの名前を選択したときに決定されます。 次の表に、DNS 名のプレフィックスの名前付け規則を示します。  
  
|Rule|説明|  
|--------|---------------|  
|古くなる可能性のないプレフィックスを選択してください。|将来変更される可能性のある製品ラインやオペレーティングシステムなどの名前は避けてください。 地理的な名前を使用することをお勧めします。|  
|インターネット標準文字のみが含まれているプレフィックスを選択します。|A-z、a-z、0-9、および (-) ですが、完全な数値ではありません。|  
|プレフィックスに15文字以下を含めます。|プレフィックス長として15文字以下を選択した場合、NetBIOS 名はプレフィックスと同じになります。|  
  
詳細については、「Active Directory のコンピューター、ドメイン、サイト、および Ou の名前付け規則」 ([https://go.microsoft.com/fwlink/?LinkId=106629](https://go.microsoft.com/fwlink/?LinkId=106629)) を参照してください。  
  
> [!NOTE]  
>  Windows Server 2008 および Windows Server 2003 の Dcpromo.exe を使用すれば、単一ラベル DNS ドメイン名を作成できますが、いくつかの理由からドメインに対しては単一ラベル DNS 名を使用しないでください。 Windows Server 2008 R2 では、Dcpromo.exe を使用して、ドメインに対して単一ラベル DNS 名を作成することはできません。 詳細については、「 [https://go.microsoft.com/fwlink/?LinkId=92467](https://go.microsoft.com/fwlink/?LinkId=92467) 」を参照してください。   
  
ドメインの現在の NetBIOS 名が、リージョンを表すのに適していない場合、またはプレフィックスの名前付け規則に適合しない場合は、新しいプレフィックスを選択します。 この場合、ドメインの NetBIOS 名がドメインの DNS プレフィックスと異なっています。  
  
デプロイする新しいドメインごとに、プレフィックスの名前付け規則を満たす、リージョンに適したプレフィックスを選択します。 ドメインの NetBIOS 名は、DNS プレフィックスと同じにすることをお勧めします。  
  
フォレスト内の各ドメインに対して選択した DNS プレフィックスと NetBIOS 名を文書化します。 DNS と NetBIOS 名の情報は、新しく作成したドメインの計画を文書化するために作成した "ドメイン計画" ワークシートに追加できます。 これを開くには、Windows Server 2003 Deployment Kit のジョブエイド ([https://go.microsoft.com/fwlink/?LinkID=102558](https://go.microsoft.com/fwlink/?LinkID=102558)) から Job_Aids_Designing_and_Deploying_Directory_and_Security_Services をダウンロードして、"ドメインの計画" (DSSLOGI_5) を開きます。  
  


