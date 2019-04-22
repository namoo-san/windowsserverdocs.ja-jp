---
title: "AD FS 2.0 WID ファームの移行を準備します。"
description: "Windows Server 2012 への AD FS 2.0 サーバー WID ファームの移行の準備について説明します。"
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4985a8d16614bd12bce991e196d105464d37634d
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
# <a name="prepare-to-migrate-an-ad-fs-20-wid-farm"></a>AD FS 2.0 WID ファームの移行を準備します。  
 Windows Server 2012 への Windows Internal Database (WID) ファームに属している AD FS 2.0 フェデレーション サーバーの移行の準備、エクスポートして、これらのサーバーから AD FS 構成データをバックアップする必要があります。  
  
 AD FS 構成データをエクスポートするには、次のタスクを実行します。  
  
-   [手順 1: - サービスの設定をエクスポートします。](#step-1-export-service-settings)  
  
-   [手順 2: カスタム属性ストアをバックアップします。](#step-2-back-up-custom-attribute-stores)  
  
-   [手順 3: Web ページのカスタマイズをバックアップします。](#step-3-back-up-webpage-customizations)  
  
## <a name="step-1-export-service-settings"></a>手順 1: サービスの設定をエクスポートします。  
 サービスの設定をエクスポートするには、次の手順を実行します。  
  
### <a name="to-export-service-settings"></a>サービスの設定をエクスポートするには  
  
1.  フェデレーション サービスによって使用される SSL 証明書の証明書のサブジェクト名と拇印値を記録します。 SSL 証明書を検索するには、インターネット インフォメーション サービス (IIS) 管理コンソールを開き、選択**既定の Web サイト**左側のウィンドウで [**バインドしています.** **アクション**、ウィンドウの検索と選択、https バインド] をクリックして**編集**、] をクリックし、**ビュー**します。  
  
> [!NOTE]
>  必要に応じて、.pfx ファイルにも SSL 証明書とその秘密キーをエクスポートすることができます。 詳細については、次を参照してください。[サーバー認証証明書の秘密キー部分のエクスポート](Export-the-Private-Key-Portion-of-a-Server-Authentication-Certificate.md)します。  
>   
>  この証明書はローカル コンピューターの個人証明書ストアに格納され、オペレーティング システムのアップグレードに保存されているために、この手順は省略します。  
  
2.  内部生成されない、自己署名証明書だけでなくキー、トークン署名、トークン暗号化、またはサービス通信証明書をエクスポートします。  
  
Windows PowerShell を使用して、サーバーで使用されているすべての証明書を表示することができます。 Windows PowerShell を開き、AD FS のコマンドレットを Windows PowerShell セッションに追加するには、次のコマンドを実行します。`PSH:>add-pssnapin “Microsoft.adfs.powershell”`します。 サーバーで使用されているすべての証明書を表示するのには、次のコマンドを実行し、`PSH:>Get-ADFSCertificate`します。 このコマンドの出力には、各証明書の格納場所を指定する StoreLocation および StoreName の値が含まれています。  ガイダンスを使用することができます、[サーバー認証証明書の秘密キー部分のエクスポート](Export-the-Private-Key-Portion-of-a-Server-Authentication-Certificate.md)各証明書とその秘密キーを .pfx ファイルにエクスポートします。  
  
> [!NOTE]
>  この手順は、すべての外部証明書は、オペレーティング システムのアップグレード中に保存されるため、省略可能です。  
  
3.  AD FS 2.0 フェデレーション サービス アカウントの ID とこのアカウントのパスワードを記録します。  
  
Id 値を検索するを調べて、**ログとして**の列**AD FS 2.0 Windows サービス**で、**サービス**コンソールし、値を手動で記録します。  
  
## <a name="step-2-back-up-custom-attribute-stores"></a>手順 2: カスタム属性ストアをバックアップします。  
 Windows PowerShell を使用して AD FS によって使用中のカスタム属性ストアに関する情報を見つけることができます。 Windows PowerShell を開き、AD FS のコマンドレットを Windows PowerShell セッションに追加するには、次のコマンドを実行します。`PSH:>add-pssnapin “Microsoft.adfs.powershell”`します。 カスタム属性ストアの情報を見つけるには、次のコマンドを実行し、:`PSH:>Get-ADFSAttributeStore`します。 アップグレードまたはカスタム属性ストアを移行する手順は異なります。  
  
## <a name="step-3-back-up-webpage-customizations"></a>手順 3: Web ページのカスタマイズをバックアップします。  
 任意の Web ページのカスタマイズをバックアップするには、AD FS Web ページをコピーし、**Web.config**仮想パスにマップされているディレクトリからファイル**"/adfs/ls"** IIS でします。 既定では、**%systemdrive%\inetpub\adfs\ls**ディレクトリ。  

## <a name="next-steps"></a>次の手順
 [AD FS 2.0 フェデレーション サーバーの移行を準備します。](prepare-to-migrate-ad-fs-fed-server.md)   
 [AD FS 2.0 フェデレーション サーバー プロキシの移行を準備します。](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [AD FS 2.0 フェデレーション サーバーを移行します。](migrate-the-ad-fs-fed-server.md)   
 [AD FS 2.0 フェデレーション サーバー プロキシを移行します。](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [AD FS 1.1 Web エージェントを移行します。](migrate-the-ad-fs-web-agent.md)