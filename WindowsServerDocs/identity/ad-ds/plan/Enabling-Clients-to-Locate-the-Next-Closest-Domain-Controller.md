---
ms.assetid: 7dd905ea-4235-4519-8400-31b4fa0ed1bf
title: "クライアントを次に最も近いドメイン コントローラーの検索を有効にします。"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 39b1b79bba944c10b0c74c4bb18f6dcf80f8230e
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="enabling-clients-to-locate-the-next-closest-domain-controller"></a>クライアントを次に最も近いドメイン コントローラーの検索を有効にします。

>適用対象: Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows Server 2008 または Windows Server 2008 R2 を実行するドメイン コントローラーがあれば、することができます、Windows Vista、Windows 7、Windows Server 2008、または有効にするより効率的にドメイン コントローラーを検索する Windows Server 2008 R2 を実行しているクライアント コンピューターで、**次の最も近いサイトを試す**グループ ポリシー設定です。 この設定では、特に多くのブランチ オフィスとサイトを持つ大企業でのネットワーク トラフィックを合理化することができ、ドメイン コントローラー ロケーター (DC ロケーター) が向上します。  
  
この新しい設定のドメイン コントローラーが配置されている順序に影響するためにサイト リンク コストを構成する方法に影響を与えることができます。 多くのハブ サイトとブランチ オフィスを持つ企業の場合、クライアントでフェールオーバーできる、次に最も近いハブ サイトに最も近いハブ サイトでドメイン コントローラーが見つからない場合ことを確認して、ネットワーク上の Active Directory のトラフィックを大幅に短縮できます。  
  
全般のベスト プラクティスとして、サイトのトポロジを簡略化する必要があり、サイト リンク コストと可能な限り有効にした場合、**次の最も近いサイトを試す**設定します。 ハブ サイトの多くの企業でこれには、プランに 1 つのサイト内のクライアントで別のサイト内のドメイン コントローラーにフェールオーバーが必要になる状況を処理することを簡略化できます。  
  
既定で、**次の最も近いサイトを試す**設定が有効になっていません。 設定が有効でないときに DC ロケーターは、次のアルゴリズムを使用して、ドメイン コントローラーを検索します。  
  
-   同じサイト内のドメイン コントローラーを検索しようとしてください。  
  
-   同じサイトで利用可能なドメイン コントローラーがない場合は、ドメイン内の任意のドメイン コントローラーを検索するしてください。  
  
> [!NOTE]  
> これは、DC ロケーターが以前のバージョンの Active Directory で使用される同じアルゴリズムです。 詳細については、Active Directory の機能の DNS のサポートを参照してください ([https://go.microsoft.com/fwlink/?LinkId=108587](https://go.microsoft.com/fwlink/?LinkId=108587))。  
  
有効にした場合、**次の最も近いサイトを試す**設定すると、DC ロケーター アルゴリズムを使用して、次のドメイン コントローラーを検出します。  
  
-   同じサイト内のドメイン コントローラーを検索しようとしてください。  
  
-   ドメイン コントローラーが利用できない場合、同じサイトに、次に最も近いサイトでドメイン コントローラーを探してください。 サイトは、コストが高いサイト リンクのコストが別のサイトよりも低いサイト リンクがある場合に似ています。  
  
-   次に最も近いサイトで利用可能なドメイン コントローラーがない場合、ドメイン内の任意のドメイン コントローラーを検索するお試しください。  
  
既定では、DC ロケーターでは、次に最も近いサイトを決定する場合は、読み取り専用ドメイン コントローラー (RODC) を含む任意のサイトは考慮しません。 さらに、Windows Server 2008 および Windows Server 2008 R2 ドメイン コントローラー サポートのみ、クライアントが以前のバージョンの Windows Server を実行しているドメイン コントローラーからの応答を取得するときの [次へ] の最も近いサイト機能、DC ロケーターの動作と同じですのでときに設定しは無効です。  
  
たとえば、サイトのトポロジに、次の図にサイト リンクの値を持つ 4 つのサイトがあると想定します。 この例では、すべてのドメイン コントローラーは、Windows Server 2008 または Windows Server 2008 R2 を実行する書き込み可能なドメイン コントローラーです。  
  
![クライアントを dc の検索を有効にします。](media/Enabling-Clients-to-Locate-the-Next-Closest-Domain-Controller/beff4087-fb2a-463b-96ac-d440a9e29b75.gif)  
  
ときに、**次の最も近いサイトを試す**場合、Windows Vista、Windows 7、Windows Server 2008 を実行しているクライアント コンピューターに、この例ではグループ ポリシー設定を有効に、サイト _b の Windows Server 2008 R2 ドメイン コントローラーを検出しようとするか、最初に、独自のサイト _b 内のドメイン コントローラーの検索を試みます。 [なし] がサイト _b で利用可能な場合は、サイト _a のドメイン コントローラーを検索しようとします。  
  
設定が有効でない場合、クライアントはサイト _b で利用可能なドメイン コントローラーがない場合は、サイト _a、Site_C、または Site_D でドメイン コントローラーを検索しようとします。  
  
> [!NOTE]  
> **次の最も近いサイトを試す**設定は、自動サイト カバレージと連携動作します。 たとえば、次に最も近いサイトにドメイン コントローラーにいない場合、DC ロケーターはそのサイトの自動サイト カバレージを実行するドメイン コントローラーを検索しようとします。  
  
適用する、**次の最も近いサイトを試す**設定、グループ ポリシー オブジェクト (GPO) を作成して、組織の適切なオブジェクトへのリンクまたは Windows Vista、Windows 7、Windows Server 2008、またはドメイン内の Windows Server 2008 R2 を実行しているすべてのクライアントに影響を与えることが既定のドメイン ポリシーを変更することができます。 設定する方法について、**次の最も近いサイトを試す**設定するを参照してください[次に最も近いサイト内でドメイン コントローラーを検索するクライアントを有効にする](https://technet.microsoft.com/library/cc772592.aspx)します。  
  

