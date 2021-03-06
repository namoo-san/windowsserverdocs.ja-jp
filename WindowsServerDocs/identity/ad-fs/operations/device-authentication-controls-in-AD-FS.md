---
title: AD FS でのデバイス認証の制御
description: このドキュメントでは、Windows Server 2016 および 2012 R2 の AD FS でデバイス認証を有効にする方法について説明します。
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 11/09/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 87c011b18ad4a1d464072c1ea90b09a44e831378
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407367"
---
# <a name="device-authentication-controls-in-ad-fs"></a>AD FS でのデバイス認証の制御
次のドキュメントは、Windows Server 2016 および 2012 R2 でデバイス認証コントロールを有効にする方法を示しています。

## <a name="device-authentication-controls-in-ad-fs-2012-r2"></a>AD FS 2012 R2 のデバイス認証の制御
AD FS 2012 R2 では、デバイス認証を制御する `DeviceAuthenticationEnabled` と呼ばれるグローバル認証プロパティが1つありました。

この設定を構成するには、次のように `Set-AdfsGlobalAuthenticationPolicy` コマンドレットを使用します。


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```



デバイス認証を無効にするには、同じコマンドレットを使用して、値を $false に設定します。

## <a name="device-authentication-controls-in-ad-fs-2016"></a>AD FS 2016 のデバイス認証の制御
2012 R2 でサポートされているデバイス認証の種類は、clientTLS のみでした。  AD FS 2016 では、clientTLS に加えて、最新のデバイス認証用に2つの新しい種類のデバイス認証があります。  それらを次に示します。
- PKeyAuth
- PRT

新しい動作を制御するには、`DeviceAuthenticationEnabled` プロパティを `DeviceAuthenticationMethod`という新しいプロパティと組み合わせて使用します。  

デバイスの認証方法によって、実行されるデバイス認証の種類 (PRT、PKeyAuth、clientTLS、またはその一部) が決まります。
次の値があります。
 - SignedToken: PRT のみ
 - PKeyAuth: PRT + PKeyAuth
 - ClientTLS: PRT + clientTLS
 - All: 上記のすべて

ご覧のように、PRT はすべてのデバイス認証方法の一部であるため、`DeviceAuthenticationEnabled` が `$true`に設定されている場合、常に有効になっている既定のメソッドが有効になります。

例: メソッドを構成するには、上記の DeviceAuthenticationEnabled コマンドレットと新しいプロパティを使用します。

``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```

>[!NOTE]
> ADFS 2019 では、`Set-AdfsRelyingPartyTrust` コマンドで `DeviceAuthenticationMethod` を使用できます。

``` powershell
PS:\>Set-AdfsRelyingPartyTrust -DeviceAuthenticationMethod ClientTLS
```

>[!NOTE]
> デバイス認証を有効にする (`DeviceAuthenticationEnabled` を `$true`に設定する) ことは、`DeviceAuthenticationMethod` が暗黙的に `SignedToken`に設定されることを意味します。これは、 **PRT**に相当します。


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationMethod All
```
> [!NOTE]
> 既定のデバイスの認証方法は `SignedToken`です。  その他の値は **、PKeyAuth、** <strong>Clienttls、</strong>および**All**です。

AD FS 2016 がリリースされたため、`DeviceAuthenticationMethod` 値の意味が少し変更されています。  更新レベルに応じて、次の表を参照して各値の意味を確認してください。


|AD FS のバージョン|DeviceAuthenticationMethod の値|と|
| ----- | ----- | ----- |
|2016 RTM|SignedToken|PRT + PkeyAuth|
||用 clienttls|用 clienttls|
||すべての|PRT + PkeyAuth + clientTLS|
|2016 RTM + 最新の Windows Update|SignedToken (変更された意味)|PRT (のみ)|
||PkeyAuth (新規)|PRT + PkeyAuth|
||用 clienttls|PRT + clientTLS|
||すべての|PRT + PkeyAuth + clientTLS|

## <a name="see-also"></a>参照
[AD FS の運用](../../ad-fs/AD-FS-2016-Operations.md)
