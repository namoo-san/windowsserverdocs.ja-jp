---
title: ボリューム ライセンス認証情報を取得するための Slmgr.vbs オプション
description: Slmg.vbs スクリプトで使用できるオプションを一覧表示し、その使用方法について説明します
TOCTitle: Slmgr.vbs Options
ms.date: 09/24/2019
ms.technology: server-general
ms.topic: article
author: Teresa-Motiv
ms.author: v-tea
manager: dcscontentpm
ms.localizationpriority: medium
appliesto:
- Windows Server 2012 R2
- Windows 10
- Windows 8.1
ms.openlocfilehash: 3b1ce54fe1e1e855d605aba58a0f0e37f0324469
ms.sourcegitcommit: 9855d6b59b1f8722f39ae74ad373ce1530da0ccf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2019
ms.locfileid: "71963068"
---
# <a name="slmgrvbs-options-for-obtaining-volume-activation-information"></a>ボリューム ライセンス認証情報を取得するための Slmgr.vbs オプション

Slmgr.vbs スクリプトの構文は次のとおりです。この記事の表は、各コマンドライン オプションの説明です。

```cmd
slmgr.vbs [<ComputerName> [<User> <Password>]] [<Options>]
```

> [!NOTE]
> この記事では、省略可能な引数に角かっこ \[] を使用し、プレースホルダーに山かっこ \<> を使用しています。 これらのステートメントを入力するときは、かっこを省略し、対応する値でプレースホルダーを置き換えてください。

> [!NOTE]
> ボリューム ライセンス認証を使用するその他のソフトウェア製品の詳細については、そのアプリケーションのために作成されたドキュメントを参照してください。

## <a name="using-slmgr-on-remote-computers"></a>リモート コンピューターでの Slmgr の使用

リモート クライアントを管理するには、ボリューム ライセンス認証管理ツール (VAMT) バージョン 1.2 以降を使用するか、プラットフォームの違いに合わせた WMI スクリプトを独自に作成してください。 ボリューム ライセンス認証のための WMI のプロパティとメソッドの詳細については、「[ボリューム ライセンス認証のための WMI のプロパティとメソッド](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn502536(v=ws.11))」を参照してください。

> [!IMPORTANT]
> Windows 7 と Windows Server 2008 R2 での WMI の変更が理由で、Slmgr.vbs スクリプトはどのプラットフォームでも動作するようには作られていません。 Slmgr.vbs を使用した Windows Vista® オペレーティング システムからの Windows 7 または Windows Server 2008 R2 システムの管理はサポートされていません。 古いバージョンのシステムの管理を Windows 7 や Windows Server 2008 R2 から実行しようとすると、バージョン不一致エラーが発生します。 たとえば、**cscript slmgr.vbs \<vista\_machine\_name\> /dlv** を実行すると、出力は次のようになります。
>  
>> Microsoft (R) Windows Script Host Version 5.8 Copyright (C) Microsoft Corporation. All rights reserved.
>>  
>> リモート コンピューターではこのバージョンの Slmgr.vbs はサポートされていません

## <a name="general-slmgrvbs-options"></a>一般的な Slmgr.vbs のオプション

|構成方法 |説明 |
| - | - |
|\[\<ComputerName\>] |リモート コンピューターの名前 (既定値はローカル コンピューター) |
|\[\<User\>] |リモート コンピューター上の、必要な特権が付与されているアカウント |
|\[\<Password\>] |リモート コンピューター上の、必要な特権が付与されているアカウントのパスワード |

## <a name="global-options"></a>グローバルなオプション

|構成方法 |説明 |
| - | - |
|\/ipk&nbsp;&lt;ProductKey&gt; |5×5 プロダクト キーのインストールを試行します。 このパラメーターで指定されるプロダクト キーは、有効であることが確認済みであり、インストールされているオペレーティング システムに適用可能なものであることが必要です。<br />そうでない場合は、エラーが返されます。<br />キーが有効で適用可能な場合は、キーがインストールされます。 キーがインストール済みの場合は、警告なしでそのキーが置き換えられます。<br />ライセンス サービスが不安定になるのを防止するために、システムを再起動するか、ソフトウェア保護サービスを再起動してください。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウから実行する必要があります。または、特権なしのユーザーが特別にソフトウェア保護サービスにアクセスできるように Standard User Operations レジストリ値が設定されている必要があります。 |
|/ato&nbsp;\[\<Activation&nbsp;ID\>] |リテール エディションやボリューム システムに KMS ホスト キーまたはマルチ ライセンス認証キー (MAK) がインストールされている場合は、 **/ato** を指定するとオンライン ライセンス認証が試行されます。<br />システムに Generic Volume License Key (GVLK) がインストールされている場合は、これにより KMS ライセンス認証が試行されます。 自動 KMS ライセンス認証を試行しないようにシステムが設定されている場合も ( **/stao**)、 **/ato** を指定すると KMS ライセンス認証が試行されます。<br />**注:** Windows 8 以降 (および Windows Server 2012) では、 **/stao** オプションが非推奨となっています。 **/act-type** オプションを代わりに使用してください。<br />パラメーター \<**Activation ID**\> は、コンピューター上にインストールされている Windows のエディションを **/ato** で指定できるようにするためのものです。 \<**Activation ID**\> パラメーターを指定すると、このオプションの効果が及ぶのは、その Activation ID に関連付けられたエディションに限定されます。 **slmgr.vbs /dlv all** を実行すると、インストールされているバージョンの Windows のすべての Activation ID が表示されます。 その他のアプリケーションもサポートする必要がある場合の詳しい手順については、そのアプリケーションから提供されているガイダンスをご覧ください。<br />KMS ライセンス認証を行うときに、特権の昇格は必要ありません。 ただし、オンライン ライセンス認証を行うには昇格が必要です。昇格しない場合は、特権なしのユーザーが特別にソフトウェア保護サービスにアクセスできるように Standard User Operations レジストリ値が設定されている必要があります。 |
|\/dli&nbsp;\[<Activation&nbsp;ID\>&nbsp;\|&nbsp;All\] |ライセンス情報を表示します。<br />**/dli** だけを指定すると、インストール済みのアクティブな Windows エディションのライセンス情報が表示されます。 \<**Activation ID**\> パラメーターを指定すると、その Activation ID に関連付けられている、特定のエディションのライセンス情報が表示されます。 **All** をパラメーターとして指定すると、該当するすべてのインストール済み製品のライセンス情報が表示されます。<br />この操作には、特権の昇格は必要ありません。 |
|\/dlv&nbsp;\[<Activation&nbsp;ID\>&nbsp;\|&nbsp;All\] |詳細なライセンス情報を表示します。<br />**/dlv** だけを指定すると、インストール済みのオペレーティング システムのライセンス情報が表示されます。 \<**Activation ID**\> パラメーターを指定すると、その Activation ID に関連付けられている、特定のエディションのライセンス情報が表示されます。 **All** パラメーターを指定すると、該当するすべてのインストール済み製品のライセンス情報が表示されます。<br />この操作には、特権の昇格は必要ありません。 |
|\/xpr \[\<Activation&nbsp;ID\>] |製品のライセンス認証有効期限を表示します。 パラメーターを省略した場合は、最新の Windows エディションを指定したことになります。これが役立つのは主に、KMS クライアントの場合です。MAK やリテールのライセンス認証は無期限です。<br />\<**Activation ID**\> パラメーターを指定すると、その Activation ID に関連付けられている、特定のエディションのライセンス認証有効期限が表示されます。この操作には、特権の昇格は必要ありません。 |

## <a name="advanced-options"></a>詳細設定オプション

|構成方法 |説明 |
| - | - |
|\/cpky |サービス操作の中には、Out-of-Box Experience (OOBE) 操作のときにプロダクト キーがレジストリに格納されていることを必要とするものがあります。 **/cpky** オプションを指定すると、プロダクト キーがレジストリから削除されるので、悪意のあるコードによってこのキーが盗まれるのを防止できます。<br />キーを展開するリテール インストールの場合は、このオプションを実行することをお勧めします。 このオプションは、MAK ホスト キーや KMS ホスト キーの場合は不要です。これらのキーでは、これが既定の動作であるからです。 このオプションが必要になるのは、他のタイプのキーの既定の動作でキーがレジストリから削除されない場合のみです。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/ilc&nbsp;&lt;license_file&gt; |必須パラメーターで指定したライセンス ファイルがインストールされます。 このようにしてライセンスをインストールする目的としては、トラブルシューティングや、トークン ベースのライセンス認証のサポートがあります。オンボード アプリケーションの手動インストールの一部として使用することもできます。<br />このプロセスの中で、ライセンスの検証は行われません。ライセンス検証は、Slmgr.vbs の機能には含まれていません。 代わりに、検証は実行時にソフトウェア保護サービスによって処理されます。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウから実行する必要があります。または、特権なしのユーザーが特別にソフトウェア保護サービスにアクセスできるように **Standard User Operations** レジストリ値が設定されている必要があります。 |
|\/rilc |%SystemRoot%\system32\oem と %SystemRoot%\System32\spp\tokens に格納されているすべてのライセンスを再インストールします。 これらは、インストール時に格納された "既知の正常な" コピーです。<br />信頼されたストアにある、一致するライセンスはすべて置き換えられます。 その他のライセンス&mdash;たとえば、信頼された機関 (TA) 発行ライセンス (IL) やアプリケーション用のライセンス&mdash;は影響を受けません。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。または、特権なしのユーザーが特別にソフトウェア保護サービスにアクセスできるように **Standard User Operations** レジストリ値が設定されている必要があります。 |
|\/rearm |ライセンス認証タイマーをリセットします。 **/rearm** プロセスは、**sysprep /generalize** からも呼び出されます。<br />**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform\SkipRearm** レジストリ エントリが **1** に設定されている場合は、この操作を行っても何も変化しません。 このレジストリ エントリの詳細については、「[ボリューム ライセンス認証のためのレジストリ設定](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn502532(v=ws.11))」を参照してください。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。または、特権なしのユーザーが特別にソフトウェア保護サービスにアクセスできるように **Standard User Operations** レジストリ値が設定されている必要があります。 |
|\/rearm-app &lt;Application&nbsp;ID&gt; |指定されたアプリのライセンス ステータスをリセットします。 |
|\/rearm-sku &lt;Application&nbsp;ID&gt; |指定された SKU のライセンス ステータスをリセットします。 |
|\/upk&nbsp;\[&lt;Application&nbsp;ID&gt;] |現在の Windows エディションのプロダクト キーをアンインストールします。 再起動後に、システムは "ライセンスなし" 状態になります。これを解除するには、新しいプロダクト キーをインストールする必要があります。<br />\<**Activation ID**\> パラメーターを使用して別のインストール済み製品を指定することもできます。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウから実行する必要があります。 |
|\/dti&nbsp;\[\<Activation&nbsp;ID\>] |オフラインでのライセンス認証のためのインストール ID を表示します。 |
|\/atp &lt;Confirmation&nbsp;ID&gt; |指定された確認 ID を使用して製品のライセンス認証を行います。 |

## <a name="kms-client-options"></a>KMS クライアントのオプション

|構成方法 |説明 |
| - | - |
|\/skms \<Name\[:Port]&nbsp;\|&nbsp;\:&nbsp;port\> \[\<Activation&nbsp;ID\>] |問い合わせ先となる KMS ホスト コンピューターの名前を指定します。ポートを指定することもできます。 この値を設定すると、KMS ホストの自動検出は行われなくなります。<br />KMS ホストで IPv6 (Internet Protocol version 6) のみが使用されている場合は、アドレスを \<hostname\>:\<port\> の形式で指定する必要があります。 IPv6 アドレスにはコロン (:) が含まれていますが、このコロンは Slmgr.vbs スクリプトで正しく解析されません。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/skms-domain&nbsp;&lt;FQDN&gt; \[\<Activation&nbsp;ID\>] |すべての KMS SRV レコードが存在する、特定の DNS ドメインを設定します。 この設定は、 **/skms** オプションで特定の KMS ホストが 1 つだけ設定されている場合は効果を持たなくなります。 このオプションを使用すると、特に不整合名前空間環境において、DNS サフィックス検索リストが無視されて、代わりに指定の DNS ドメインの中で KMS ホスト レコードが検索されます。 |
|\/ckms&nbsp;\[\<Activation&nbsp;ID\>] |指定された KMS ホスト名、アドレス、ポート情報をレジストリから削除します。再び KMS 自動検出が行われるようになります。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/skhc |このオプションにより、KMS ホスト キャッシュが有効になります (既定)。 クライアントが動作している KMS ホストを検出すると、この設定によって、ドメイン ネーム システム (DNS) の優先順位と重みがホストとのそれ以降の通信に影響を与えなくなります。 動作している KMS ホストにシステムからアクセスできなくなった場合は、クライアントが新しいホストを検出しようとします。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/ckhc |KMS ホスト キャッシュを無効にします。 この設定を行うと、クライアントが KMS ライセンス認証を試行するときに必ず DNS 自動検出が使用されるようになります (優先度と重みを使用する場合はこの設定をお勧めします)。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |

## <a name="kms-host-configuration-options"></a>KMS ホストの構成オプション

|構成方法 |説明 |
| - | - |
|\/sai&nbsp;&lt;Interval&gt; |まだライセンス認証を受けていないクライアントが KMS への接続を試行する間隔を分単位で設定します。 ライセンス認証間隔は 15 分以上 30 日以下で指定する必要がありますが、既定値 (2 時間) をお勧めします。<br />KMS クライアントは、この間隔の値を最初はレジストリから取得しますが、最初の KMS 応答を受け取った後は KMS での設定値に切り替えます。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/sri &lt;Interval&gt; |ライセンス認証済みのクライアントが更新のために KMS への接続を試行する間隔を分単位で設定します。 更新の間隔は 15 分以上 30 日以下で指定する必要があります。 このオプションは、最初に KMS サーバー側とクライアント側の両方で設定されます。 既定値は 10,080 分 (7 日) です。<br />KMS クライアントは、最初にレジストリからこの間隔を取得しますが、最初の KMS 応答を受け入れた後、KMS 設定に切り替えます。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/sprt&nbsp;&lt;Port&gt; |KMS ホストのどのポートでクライアント ライセンス認証要求をリッスンするかを設定します。 既定の TCP ポートは 1688 です。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウから実行する必要があります。 |
|\/sdns |KMS ホストによる DNS 発行を行うように設定します (既定の動作)。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/cdns |KMS ホストによる DNS 発行を行わないように設定します。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/spri |KMS 優先度を "通常" (既定値) に設定します。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/cpri |KMS 優先度を "低" に設定します。<br />このオプションは、共同ホスト環境で KMS が原因で発生する競合を最小化したい場合に使用します。 なお、他にどのアプリケーションやサーバーの役割がアクティブになっているかによっては、このオプションが KMS のスタベーションの原因となるおそれがあります。 十分に注意のうえお使いください。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。 |
|\/act-type \[\<Activation-Type\>] \[\<Activation&nbsp;ID\>] |ボリューム ライセンス認証のタイプを 1 つに限定するようにレジストリ値を設定します。 Activation Type に **1** を指定すると Active Directory によるライセンス認証のみとなり、**2** を指定すると KMS ライセンス認証のみ、**3** を指定するとトークンベースのライセンス認証のみとなります。 **0** を指定すると、どのライセンス認証タイプも使用できるようになります。これが既定値です。 |

## <a name="token-based-activation-configuration-options"></a>トークンベース ライセンス認証の構成オプション

|構成方法 |説明 |
| - | - |
|/lil |インストール済みのトークンベース ライセンス認証発行ライセンスのリストを返します。 |
|\/ril&nbsp;&lt;ILID&gt;&nbsp;&lt;ILvID&gt; |インストール済みのトークンベース ライセンス認証発行ライセンスを削除します。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウから実行する必要があります。 |
|\/stao |**Token-based Activation Only** フラグを設定します。自動 KMS ライセンス認証が行われなくなります。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。<br />このオプションは、Windows Server 2012 R2 および Windows 8.1 で削除されました。 **/act–type** オプションを代わりに使用してください。 |
|\/ctao |**Token-based Activation Only** フラグを解除します (既定の動作)。自動 KMS ライセンス認証が行われるようになります。<br />この操作は、管理者特権でのコマンド プロンプト ウィンドウで実行する必要があります。<br />このオプションは、Windows Server 2012 R2 および Windows 8.1 で削除されました。 **/act-type**</strong> オプションを代わりに使用してください。 |
|\/ltc |インストール済みソフトウェアのライセンス認証に使用できる、有効なトークンベース ライセンス認証証明書のリストを返します。 |
|\/fta &lt;Certificate&nbsp;Thumbprint&gt; \[&lt;PIN&gt;] |指定した証明書を使用してトークンベース ライセンス認証を強制します。 必要に応じて、暗証番号 (PIN) を指定できます。指定しておくと、ハードウェア (たとえばスマート カード) で保護されている証明書を使用するときに画面から PIN を入力しなくても秘密キーのロックを解除できるようになります。 |

## <a name="active-directory-based-activation-configuration-options"></a>Active Directory によるライセンス認証の構成オプション

|構成方法 |説明 |
| - | - |
|\/ad-activation-online &lt;Product&nbsp;Key&gt; \[\<Activation&nbsp;Object&nbsp;name\>] |Active Directory データを収集して Active Directory フォレスト ライセンス認証を実行します。コマンド プロンプトの実行に使用されている資格情報が使用されます。 ローカル管理者のアクセス権は必要ありません。 ただし、フォレストのルート ドメインにあるライセンス認証オブジェクト コンテナーに対する読み取り/書き込みアクセス権が必要です。 |
|\/ad-activation-get-IID &lt;Product&nbsp;Key&gt; |Active Directory フォレスト ライセンス認証を電話モードで開始します。 出力はインストール ID (IID) です。インターネットに接続できないときに、この IID を使用して電話でフォレストのライセンス認証を行うことができます。 ライセンス認証窓口に電話をかけてこの IID を伝えると CID が返されるので、この CID を使用してライセンス認証を完了します。 |
|\/ad-activation-apply-cid &lt;Product&nbsp;Key&gt; &lt;Confirmation&nbsp;ID&gt; \[\<Activation&nbsp;Object&nbsp;name>] |このオプションを使用する場合は、ライセンス認証窓口に電話をかけて受け取った CID を入力してライセンス認証を完了してください |
|\[/name:&lt;AO_Name&gt;] |上記のどのコマンドも、必要に応じて末尾に **/name** オプションを付加することができます。このオプションでは、Active Directory に格納されているライセンス認証オブジェクトの名前を指定します。 名前は Unicode で 40 文字を超えないようにする必要があります。 名前の文字列を明示的に定義するには、二重引用符を使用します。<br />Windows Server 2012 R2 と Windows 8.1 では、 **/ad-activation-online &lt;Product&nbsp;Key&gt;** や **/ad-activation-apply-cid** の後に、 **/name** オプションを使用せずに名前を直接指定できます。 |
|\/ao-list |このローカル コンピューターで使用できるライセンス認証オブジェクトをすべて表示します。 |
|\/del-ao &lt;AO_DN&gt;<br />\/del-ao &lt;AO_RDN&gt; |指定したライセンス認証オブジェクトをフォレストから削除します。 |

## <a name="see-also"></a>関連項目

- [ボリューム ライセンス認証のテクニカル リファレンス](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn502529%28v%3dws.11%29)
- [ボリューム ライセンス認証の概要](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831612%28v%3dws.11%29)
