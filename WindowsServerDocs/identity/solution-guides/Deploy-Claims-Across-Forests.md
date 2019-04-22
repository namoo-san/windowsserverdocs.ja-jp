---
ms.assetid: ceb9ce18-5a94-4166-9edd-2685b81fc15f
title: "フォレスト間にわたる要求を展開します。"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 7d78258d8f1db9889b6d2db8c497780940ed35a1
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
# <a name="deploy-claims-across-forests"></a>フォレスト間にわたる要求を展開します。

>適用対象: Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows Server 2012 では、要求の種類は、関連付けられたオブジェクトについてのアサーションです。 要求の種類は、Active directory フォレストごとに定義されます。 セキュリティ プリンシパルが信頼される側のフォレスト内のリソースにアクセスする信頼の境界を通過する必要があります多くのシナリオがあります。 Windows Server 2012 でのフォレスト間の信頼性情報変換では、信頼性情報が認識され、信頼する側および信頼される側のフォレストで許可されるように、フォレストを走査する要求を送信時および受信変換を行うことができます。 信頼性情報変換の実際のシナリオの例を示します。  
  
-   信頼する側のフォレストで使用できます信頼性情報の変換の特権の昇格に対するガードとして特定の値を持つ入力方向の要求をフィルター処理します。  
  
    信頼する側のフォレストと、信頼されたフォレストがサポートまたは任意のクレームを発行していない場合は、信頼の境界を越えて送られてきたプリンシパルの信頼性情報が発行することもできます。  
  
-   信頼済みフォレストは、信頼性情報の変換を使用して、特定の要求の種類および特定の値を持つ信頼性情報が信頼する側のフォレストに送られるようにできます。  
  
-   また、別にマップする変換要求の種類と信頼されている信頼される側のフォレスト間で信頼性情報を使用することができます。 信頼性情報の種類、信頼性情報の値、またはその両方を一般化するために使用できます。 これを行わない場合、信頼性情報を使用する前に、フォレスト間でデータを標準化する必要があります。 信頼されていると、信頼される側のフォレスト間で信頼性情報を一般化すると、IT コストが削減されます。  
  
## <a name="claim-transformation-rules"></a>要求変換規則  
変換規則言語の構文が 1 つの規則を次の 2 つの主要な部分に分割: 一連の条件ステートメントと問題ステートメントです。 各条件ステートメントには 2 つのサブコンポーネント: 要求の識別子と条件。 Issue ステートメントには、キーワード、区切り記号、および問題式が含まれています。 条件ステートメントは、必要に応じて、一致する入力信頼性情報を表す要求識別子変数から始まります。 条件式を確認します。 入力要求が条件に一致しない場合、変換エンジン問題ステートメントを無視し、変換ルールに対して次の入力信頼性を評価します。 すべての条件には、入力要求が一致する場合、は、問題ステートメントを処理します。  
  
要求規則言語の詳細については、次を参照してください。[Claims Transformation Rules Language](Claims-Transformation-Rules-Language.md)します。  
  
## <a name="linking-claim-transformation-policies-to-forests"></a>フォレストに信頼性情報変換ポリシーをリンクします。  
信頼性情報変換ポリシーの設定に関係している 2 つのコンポーネントが存在します。変換ポリシー オブジェクトと変換リンクを要求します。 ポリシー オブジェクトがフォレストでは、構成名前付けコンテキストで live し、信頼性情報のマッピング情報については、します。 どの信頼する側のリンクを指定し、信頼されるフォレスト マッピング適用します。  
  
これを理解するかどうかは、フォレスト信頼する側または信頼されたフォレスト情報変換ポリシー オブジェクトをリンクするための基礎なので重要です。 たとえば、信頼される側のフォレストは、アクセスを必要とするユーザー アカウントを含むフォレストです。 ユーザー アクセスを提供するリソースを含むフォレストを信頼する側のフォレストにです。 信頼性情報は、セキュリティ プリンシパルのアクセスを必要とすると同じ方向に移動します。 たとえば、adatum.com フォレストに contoso.com フォレストからの一方向の信頼がある場合、信頼性情報はからフロー adatum.com contoso.com、ユーザーが adatum.com からする contoso.com のリソースにアクセスします。  
  
既定では、信頼される側のフォレストに渡すと、すべての出力方向の要求は、信頼する側のフォレストは受信したすべての入力方向の要求を破棄します。  
  
## <a name="in-this-scenario"></a>このシナリオでは  
次のガイダンスは、このシナリオで使用できます。  
  
-   [フォレスト (&) #40; デモンストレーション手順 & #41 です。全体の信頼性情報を展開します。](Deploy-Claims-Across-Forests--Demonstration-Steps-.md)  
  
-   [Claims Transformation Rules Language](Claims-Transformation-Rules-Language.md)  
  
## <a name="BKMK_NEW"></a>役割と機能がこのシナリオに含まれる  
次の表は、役割と機能がこのシナリオの一部であるとその活かす方法について説明します。  
  
|役割/機能|このシナリオをサポートする方法|  
|-----------------|---------------------------------|  
|Active Directory ドメイン サービス|このシナリオでは、次の 2 つの Active Directory フォレストと双方向の信頼をセットアップする必要です。 両方のフォレストに信頼性情報があります。 また、集約型アクセス ポリシーを設定するで、信頼する側のフォレストのリソースがあります。|  
|ファイル サービスおよび記憶域サービスの役割|このシナリオでは、データの分類はファイル サーバー上のリソースに適用されます。 集約型アクセス ポリシーは、ユーザーのアクセスを許可するフォルダーに適用されます。 変換後に、要求は、ファイル サーバー上のフォルダーに適用される集約型アクセス ポリシーに基づいてリソースに対するユーザー アクセスを付与します。|  
  

