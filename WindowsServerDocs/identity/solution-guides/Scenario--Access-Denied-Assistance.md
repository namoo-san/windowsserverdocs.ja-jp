---
ms.assetid: aae907eb-11cf-4a87-a046-8680872ed0b1
title: "アクセス拒否アシスタンスのシナリオ"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: d6b8d8a094aa86fd5be78d2eae13bae50df3fd79
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
# <a name="scenario-access-denied-assistance"></a>シナリオ: アクセス拒否アシスタンス

>適用対象: Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

共有ファイルやフォルダーにアクセス許可のいないファイル サーバーにアクセスしようとすると、ユーザーは、アクセス拒否メッセージを取得します。 多くの場合、管理者には、問題を解決するが困難アクセスの問題のトラブルシューティングに適切なコンテキストはありません。  
  
## <a name="scenario-description"></a>シナリオの説明  
アクセス拒否アシスタンスは、次の関連する問題をトラブルシューティングする方法を Windows Server 2012 の新機能のファイルとフォルダーへのアクセスに。  
  
-   **自己アシスタンス。** ユーザーは、問題を特定し、問題を修復できるようにすることが要求されたアクセス、ビジネスに及ぶ影響は低く、および、集約型アクセス ポリシーに特別な例外は必要ありません。 アクセス拒否アシスタンスは、ファイル サーバー管理者が、組織に固有の情報をカスタマイズできますアクセス拒否メッセージを提供します。 たとえばの管理者は、ユーザーが要求できるようにアクセス、データ所有者からファイル サーバー管理者の関与なしなどに、メッセージを設定します。  
  
-   **データ所有者によるアシスタンス。** 共有フォルダーの配布リストを定義し、ユーザーのアクセスに必要なときに、フォルダーの所有者は電子メール通知を受信するように構成できます。 データ所有者が、ユーザーがアクセスを保護する方法を把握していない場合、所有者は、ファイル サーバー管理者にこの情報を転送できます。  
  
-   **ファイル サーバー管理者によるアシスタンス。** この種類のアシスタンスは、ユーザーが問題を修正できないし、データ所有者が支援できないときに使用できます。  Windows Server 2012 を提供、ユーザー ファイル サーバー管理者表示できるインターフェイスをユーザーの有効なアクセス許可、ファイルまたはフォルダーにアクセスの問題のトラブルシューティングを簡素化されるようにします。  
  
Windows Server 2012 でのアクセス拒否アシスタンスはことができますを判別して、問題と適切なツールのアクセス要求を満たすための構成の変更を行えるようにファイル サーバー管理者に関連するアクセス詳細を提供します。 たとえば、ユーザーには、このプロセスが現在実装されていないへのアクセスをファイルにアクセスする可能性がありますに従います。  
  
-   ユーザーが、\\\financeshares 共有フォルダーのファイルの読み取り試みますが、サーバーがアクセス拒否メッセージが表示されます。  
  
-    Windows Server 2012 では、使用してユーザーがアシスタンスを要求するためのオプション、アクセス拒否アシスタンス情報を表示します。  
  
-   ユーザーは、リソースへのアクセスを要求している場合、サーバーは、フォルダーの所有者に、アクセス要求情報を含むメールを送信します。  
  
検索できますでアクセス拒否アシスタンスの構成に関する計画情報[アクセス拒否アシスタンスの計画](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1)します。  
  
アクセス拒否アシスタンスの構成に関する手順があります[アクセス拒否アシスタンスの (&) #40; デモンストレーション手順 & #41 です。](Deploy-Access-Denied-Assistance--Demonstration-Steps-.md).  
  
## <a name="in-this-scenario"></a>このシナリオでは  
このシナリオは、ダイナミック アクセス制御シナリオの一部です。 ダイナミック アクセス制御についての詳細についてを参照してください。  
  
-   [ダイナミック アクセス制御: シナリオの概要](Dynamic-Access-Control--Scenario-Overview.md)  
  
## <a name="practical-applications"></a>実際の適用  
Windows Server 2012 でのアクセス拒否アシスタンスは、ユーザーがアクセス拒否メッセージから直接、共有ファイルおよびフォルダーへのアクセスを要求する機能のことで、ダイナミック アクセス制御に貢献します。  
  
## <a name="BKMK_NEW"></a>このシナリオでは含まれている機能  
次の表は、このシナリオの一部である機能の一覧し、活かす方法について説明します。  
  
|機能|このシナリオをサポートする方法|  
|-----------|---------------------------------|  
|[ファイル サーバー リソース マネージャーの概要](https://technet.microsoft.com/library/hh831701.aspx)|アクセス拒否アシスタンスは、ファイル サーバー上のファイル サーバー リソース マネージャーのコンソールを使用して構成できます。|  
|[ファイル サービスおよび記憶域サービスの概要](https://technet.microsoft.com/library/hh831487.aspx)|ファイル サーバー リソース マネージャーはファイル サービスおよび記憶域サービスの役割サービス、およびネットワーク上のファイル サーバーを管理するために使用できる機能のセットで構成されます。|  
  

