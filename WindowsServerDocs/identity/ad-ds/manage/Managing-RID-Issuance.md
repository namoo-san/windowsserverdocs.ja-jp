---
ms.assetid: aac117a7-aa7a-4322-96ae-e3cc22ada036
title: "RID 発行の管理"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: f84bcc1aa32e9993903e094fc43feffcbe16a05b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="managing-rid-issuance"></a>RID 発行の管理

>適用対象: Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

このトピックでは、RID マスター FSMO の役割、新規の発行を含むおよび RID マスターと分析し、RID 発行のトラブルシューティングを行う方法の機能を監視する変更について説明します。  
  
-   [RID 発行の管理](../../ad-ds/manage/Managing-RID-Issuance.md#BKMK_Manage)  
  
-   [RID 発行のトラブルシューティング](../../ad-ds/manage/Managing-RID-Issuance.md#BKMK_Tshoot)  
  
詳細については、 [AskDS ブログ](http://blogs.technet.com/b/askds/archive/2012/08/10/managing-rid-issuance-in-windows-server-2012.aspx)します。  
  
## <a name="BKMK_Manage"></a>RID 発行の管理  
既定では、ドメインは、ユーザー、グループ、およびコンピューターなど、約 10億セキュリティ プリンシパルの容量を持ちます。 当然ながら、アクティブに使用される多くのオブジェクトを持つドメインではありません。 ただし、Microsoft カスタマー サポートのケースが見つかった場所。  
  
-   ソフトウェアまたは誤って一括管理用のスクリプトをプロビジョニングすると、ユーザー、グループ、およびコンピューターが作成されます。  
  
-   多くの未使用のセキュリティと配布グループは、委任されたユーザーによって作成されました。  
  
-   多くのドメイン コントローラーが降格、復元、またはメタデータ消去されました。  
  
-   フォレストの回復が実行されました。  
  
-   InvalidateRidPool 操作が頻繁に実行  
  
-   RID ブロック サイズのレジストリ値が不適切に増加されました。  
  
これらすべての状況を誤って多くの場合、不必要な Rid を使用します。 長年にわたり、rid が枯渇、いくつかの環境を実行し、新しいドメインへの移行またはフォレスト回復の実行を余儀なきます。  
  
Windows Server 2012 は、年齢と Active Directory の偏在性に関して最近問題になってきた、RID 割り当てに関する問題に対処します。 これらには、イベント ロギングの向上より適切な制限、およびドメインのグローバル RID 空間の全体的なサイズの 2 倍にする、緊急時における機能が含まれます。  
  
### <a name="periodic-consumption-warnings"></a>定期的な消費の警告  
Windows Server 2012 では、主要マイルス トーンを超えた場合にグローバル RID 空間のイベントを追跡、早期に警告を追加します。 モデルは、10%、グローバル プール内の使用済みマークされ、イベントに達したときに計算します。 次に、残りの 10% を計算し、イベント サイクルが続けられます。 グローバル RID 空間が枯渇は、イベントは加速 10% 到達として高速化、減少するプールで (が、イベント ログ ダンペング 1 時間ごとに 1 つ以上のエントリができなくなります)。 すべてのドメイン コントローラーのシステム イベント ログでは、ディレクトリ-サービス-SAM 警告イベント 16658 を書き込みます。  
  
想定すると、既定 30 ビット グローバル RID 空間、最初のイベント ログ、107,374,182 を含むプールを割り当てるときに<sup>nd</sup> RID します。 イベント レート自然に加速し、100,000 の最後のチェックポイントまで 110 イベントの合計で生成されるとします。 この動作はロック解除された 31 ビット グローバル RID 空間の: 214,748,365 から開始し、117 個のイベントで作業を完了します。  
  
> [!IMPORTANT]  
> このイベントは想定されていません。ユーザー、コンピューター、およびドメインですぐにグループの作成プロセスを調査します。 100 人を超える AD DS オブジェクトを作成するは、通常のかなり不足です。  
  
![RID 発行](media/Managing-RID-Issuance/ADDS_RID_TR_EventWaypoints2.png)  
  
### <a name="rid-pool-invalidation-events"></a>RID プール無効イベント  
新しいイベントは、ローカルの DC RID プールが破棄されたことを警告します。 これらは情報案内のいずれであり、特に、新しい VDC 機能により、予想される可能性があります。 イベントの詳細については下イベントの一覧を参照してください。  
  
### <a name="BKMK_RIDBlockMaxSize"></a>RID ブロック サイズの制限  
通常、ドメイン コントローラー RID の割り当て要求 500 個のブロックで同時に 1 つです。 ドメイン コントローラーで、次の REG_DWORD レジストリ値を使用してこの既定値を上書きすることができます。  
  
```  
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NTDS\RID Values  
RID Block Size  
  
```  
  
Windows Server 2012 では、前に、暗黙的な DWORD 最大値 (0 xffffffff または 4294967295 の値を持つ) を除く、レジストリ キーに適用される最大値がありませんでした。 この値は、合計グローバル RID 空間よりかなり大きくなっています。 管理者が不適切に、または誤って、グローバル RID が莫大なレートで枯渇する値を持つ RID ブロック サイズを構成します。  
  
Windows Server 2012 では、このレジストリ値を 10 進の 15,000 (16 進 0x3A98) よりも高いを設定することはできません。 これには、意図しない莫大なの RID 割り当てができないようにします。  
  
値を設定すると*高い*15,000 個よりも、値は 15,000 として扱わし、ドメイン コントローラーのログにイベント 16653 値が訂正されるまで再起動のたびにディレクトリ サービス イベント ログします。  
  
### <a name="BKMK_GlobalRidSpaceUnlock"></a>グローバル RID 空間サイズのロックを解除します。  
Windows Server 2012 では、前に、グローバル RID 空間が 2 に制限されていました<sup>30</sup> (つまり 1,073, 741,823) Rid を合計します。 達すると、のみドメインの移行またはフォレストへの回復、古いタイム フレームは、任意の測定値で新しい Sid の作成、障害回復が許可されます。 以降、2、Windows Server 2012 で<sup>31</sup> 、グローバル プールを 2,147, 483,648 Rid を高めるためにビットのロックを解除することができます。  
  
AD DS では、この設定をという名前の特殊な非表示属性を**SidCompatibilityVersion**すべてのドメイン コントローラの RootDSE コンテキストにします。 この属性は ADSIEdit や LDP など、他のツールを使用して読み取ることはできません。 グローバル RID 空間の増加を見るには、ディレクトリ-サービス-SAM から警告イベント 16655 のシステム イベント ログを調べますか、次の Dcdiag コマンドを使用します。  
  
```  
Dcdiag.exe /TEST:RidManager /v | find /i "Available RID Pool for the Domain"  
  
```  
  
グローバル RID プールを増やすと、利用可能なプールも既定の 1,073, 741,823 2,147, 483,647 に変化します。 例えば：  
  
![RID 発行](media/Managing-RID-Issuance/ADDS_RID_TR_Dcdiag.png)  
  
> [!WARNING]  
> このロック解除の対象読者は*のみ*RID の枯渇を防ぐために使用して*のみ*RID シーリングの適用と組み合わせて (次のセクションを参照してください)。 何百万もの残りの Rid と低の増加をように、ロック解除の RID プールから生成される Sid とアプリケーションの互換性の問題が存在する可能性がある環境ではこの設定しない「先制」します。  
>   
> これは、ロック解除操作元に戻すことはできません、または削除すると、によって、以前のバックアップに完全なフォレストの回復を除きます。  
  
#### <a name="important-caveats"></a>重要な注意事項  
Windows Server 2003 および Windows Server 2008 ドメイン コントローラー Rid を発行できません、グローバル RID プールの 31 とき<sup>st</sup>ビットがロック解除します。 Windows Server 2008 R2 domain controllers *can* use 31<sup>st</sup> bit RIDs *but only if* they have hotfix [KB 2642658](https://support.microsoft.com/kb/2642658) installed. サポートされていないと見なしますのドメイン コントローラーは、ロックを解除するときに枯渇ように、グローバル RID プールを処理します。  
  
この機能は、ドメイン機能レベルでは強制されません。ドメインの Windows Server 2012 または更新された Windows Server 2008 R2 ドメイン コントローラーのみが存在する優れた注意してください。  
  
#### <a name="implementing-unlocked-global-rid-space"></a>ロック解除されたグローバル RID 空間の実装  
RID プールの 31 のロックを解除する<sup>st</sup>ビット RID シーリングの警告 (下記参照) を受信した後は、次の手順を実行します。  
  
1.  RID マスターの役割が Windows Server 2012 ドメイン コントローラーで実行されていることを確認します。 ない場合は、Windows Server 2012 ドメイン コントローラーに転送します。  
  
2.  LDP.exe を実行します。  
  
3.  をクリックして、**接続**] メニューとクリック**接続**、Windows Server 2012 RID マスター上のポート 389、クリックして**バインド**ドメイン管理者として。  
  
4.  をクリックして、**参照**] メニューとクリック**変更**します。  
  
5.  いることを確認**DN**は空です。  
  
6.  **エントリ属性の編集**、種類。  
  
    ```  
    SidCompatibilityVersion  
    ```  
  
7.  **値**、種類。  
  
    ```  
    1  
    ```  
  
8.  いることを確認**追加**で選択された**操作**] をクリック**Enter**します。 これにより、更新、**エントリ一覧**します。  
  
9. 選択、**同期**と**拡張**オプション] をクリックし、**実行**します。  
  
    ![RID 発行](media/Managing-RID-Issuance/ADDS_RID_TR_LDPModify.png)  
  
10. 成功した場合の LDP 出力ウィンドウが表示されます。  
  
    ```  
    ***Call Modify...  
     ldap_modify_ext_s(Id, '(null)',[1] attrs, SvrCtrls, ClntCtrls);  
    modified "".  
  
    ```  
  
    ![RID 発行](media/Managing-RID-Issuance/ADDS_RID_TR_LDPModifySuccess.png)  
  
11. グローバル RID プールが増加して Directory-サービス-SAM 情報イベント 16655 のドメイン コントローラーのシステム イベント ログを調べることを確認します。  
  
### <a name="rid-ceiling-enforcement"></a>RID シーリングの適用  
保護措置を提供して、管理意識を高める、Windows Server 2012 では、グローバル空間内の Rid の残 10% で、グローバル RID 範囲に対するの人為的シーリングが導入されています。 1 台の人為的シーリング %、内で RID プールを要求しているドメイン コントローラー SAM-ディレクトリ-サービス警告イベント 16656、システム イベント ログに書き込みます。 RID マスター FSMO の 10% シーリングに達すると、ディレクトリ-サービス-SAM イベント 16657 をそのシステム イベント ログに書き込み、割り当てられず、さらに RID プール、シーリングを上書きするまで。 これにより、ドメイン内の RID マスターの状態を評価し、潜在的なランナウェイ RID 割り当てを対応にします。ドメイン全体の RID 空間が枯渇することも保護されます。  
  
このシーリングは、利用可能な RID 空間の残りの 10% にハードコードされます。 つまり、RID マスター、グローバル RID 空間の 90% に対応する、RID を含むプールを割り当てるとき、シーリングがアクティブにします。  
  
-   既定のドメイン、最初のトリガー ポイントは 2<sup>30</sup>-1 * 0.90 = 966,367,640 (または 107,374,183 Rid の残)。  
  
-   ロック解除された 31 ビット RID スペースを持つドメインは、トリガー ポイントは 2<sup>31</sup>-1 * 0.90 = 1,932,735,282 Rid (または 214,748,365 Rid の残)。  
  
RID マスターが Active Directory 属性を設定してトリガーされると、 **Msds-ridpoolallocationenabled** (共通名**MS-DS - RID - プールの割り当て-有効になっている**) を FALSE にオブジェクト。  
  
CN RID Manager を $、CN = System, DC = =*<domain>*  
  
これにより、16657 イベントを書き込み、すべてのドメイン コントローラーに RID ブロックの発行をさらにできないようにします。 ドメイン コントローラーは、既に発行させる未使用の RID プールの使用を継続します。  
  
ブロックを削除し、RID プール割り当てを続行できるように、その値を TRUE に設定します。 RID マスターによって実行される次回の RID 割り当てでは、属性を既定の NOT SET 値に戻ります。 その後、それ以上のシーリングはありませんし、最終的には、グローバル RID 空間が切れる、フォレストの回復またはドメインの移行を必要とします。  
  
#### <a name="removing-the-ceiling-block"></a>シーリング ブロックの削除  
1 回人為的シーリングに達するブロックを削除するのには、次の手順を実行します。  
  
1.  RID マスターの役割が Windows Server 2012 ドメイン コントローラーで実行されていることを確認します。 ない場合は、Windows Server 2012 ドメイン コントローラーに転送します。  
  
2.  LDP.exe を実行します。  
  
3.  をクリックして、**接続**] メニューとクリック*接続*、Windows Server 2012 RID マスター上のポート 389、クリックして**バインド**ドメイン管理者として。  
  
4.  をクリックして、**ビュー** ] メニューとクリック**ツリー**、**ベース DN** RID マスターの独自のドメイン名前付けコンテキストを選択します。 をクリックして**OK**します。  
  
5.  ナビゲーション ウィンドウで、ドリルダウンして、 **CN = System**コンテナーと] をクリック、 **CN = RID Manager$**オブジェクト。 右クリックし、をクリックして**変更**します。  
  
6.  [エントリ属性の編集、次のように入力します。  
  
    ```  
    MsDS-RidPoolAllocationEnabled  
    ```  
  
7.  **値**に入力します (大文字の場合)。  
  
    ```  
    TRUE  
    ```  
  
8.  選択**置換**で**操作**] をクリック**Enter**します。 これにより、更新、**エントリ一覧**します。  
  
9. 有効にする、**同期**と**拡張**オプション] をクリックし、**実行**:  
  
    ![RID 発行](media/Managing-RID-Issuance/ADDS_RID_TR_LDPRaiseCeiling.png)  
  
10. 成功した場合の LDP 出力ウィンドウが表示されます。  
  
    ```  
    ***Call Modify...  
    ldap_modify_ext_s(ld, 'CN=RID Manager$,CN=System,DC=<domain>',[1] attrs, SvrCtrls, ClntCtrls);  
    Modified "CN=RID Manager$,CN=System,DC=<domain>".  
  
    ```  
  
    ![RID 発行](media/Managing-RID-Issuance/ADDS_RID_TR_LDPRaiseCeilingSuccess.png)  
  
### <a name="other-rid-fixes"></a>その他の RID 修正  
以前の Windows Server オペレーティング システムでは、RID プールのリークときに rIDSetReferences 属性が不足しています。 To resolve this problem on domain controllers that run Windows Server 2008 R2, install the hotfix from [KB 2618669](https://support.microsoft.com/kb/2618669).  
  
### <a name="unfixed-rid-issues"></a>未修正の RID の問題  
これまでした RID のリークのアカウントの作成に失敗しました。アカウントを作成するときにエラーも RID が使用されます。 一般的な例では、パスワードの複雑さを満たしていないを持つユーザーを作成します。  
  
### <a name="rid-fixes-for-earlier-versions-of-windows-server"></a>以前のバージョンの Windows Server での RID 修正  
リリースされた Windows Server 2008 R2 の修正プログラムがあるすべての修正プログラムと上記の変更。 現在存在していない Windows Server 2008 の修正プログラム計画中または進行中です。  
  
## <a name="BKMK_Tshoot"></a>RID 発行のトラブルシューティング  
  
### <a name="introduction-to-troubleshooting"></a>トラブルシューティングの概要  
RID 発行のトラブルシューティングには、論理的かつ直線的メソッドが必要です。 イベント ログで注意深く RID トリガーされる警告やエラーを監視している場合を除き、問題の時にまず疑われることは障害が発生したアカウントの作成します。 RID 発行のトラブルシューティングにキーはことはありません。 または、現象が予想される場合を理解するにはRID 発行に関する問題の多くが 1 つだけのドメイン コントローラーに影響してコンポーネントの機能強化を行うには何もします。 次の簡単な図を下すそれらより明確に役立ちます。  
  
![RID 発行](media/Managing-RID-Issuance/adds_rid_issuance_troubleshooting.png)  
  
### <a name="troubleshooting-options"></a>トラブルシューティングのオプション  
  
#### <a name="logging-options"></a>ログ オプション  
RID 発行のすべてのログ記録は、[ソース ディレクトリのサービスの SAM、システム イベント ログで発生します。 ログが有効になっているし、冗長性を最大にするには、既定で構成されています。 エントリが記録されていない Windows Server 2012 で新しいコンポーネントの変更を問題を従来型の (レガシーの Windows Server 2012) として扱う RID 発行の問題が Windows 2008 R2 または以前のオペレーティング システムで発生します。  
  
#### <a name="utilities-and-commands-for-troubleshooting"></a>ユーティリティとコマンドのトラブルシューティング  
前に示したログで説明されていない問題をトラブルシューティングするには、は、特に古い RID 発行の問題 - は、開始点として次のツールの一覧を使用します。  
  
-   Dcdiag.exe  
  
-   Repadmin.exe  
  
-   ネットワーク モニター 3.4  
  
### <a name="general-methodology-for-troubleshooting-domain-controller-configuration"></a>ドメイン コントローラー構成のトラブルシューティングの一般的な方法  
  
1.  エラーの単純な原因は、アクセス許可またはドメイン コントローラーの可用性の問題ですか?  
  
    1.  セキュリティに必要なアクセス許可を持たないプリンシパルを作成しようとしていますか。 アクセス拒否エラーの出力を確認します。  
  
    2.  利用可能なドメイン コントローラーですか。 返されたエラー、あるいは LDAP またはドメイン コントローラーの可用性メッセージを調べます。  
  
2.  具体的には返されたエラーは、Rid を説明し、ガイダンスとして使用するのに十分な固有のですか? その場合は、指示に従います。  
  
3.  具体的には返されたエラーは、Rid は触れが、それ以外の場合以外に固有ですか。 たとえば、「オブジェクトを作成できません、ため、ディレクトリ サービスは相対識別子を割り当てることができませんでした。」  
  
    1.  Examine the System Event log on the domain controller for "legacy" (pre-Windows Server 2012) RID events detailed in [RID Pool Request](https://technet.microsoft.com/en-us/library/ee406152(WS.10).aspx) (16642, 16643, 16644, 16645, 16656).  
  
    2.  ドメイン コントローラーのシステム イベントと RID マスターの詳細を以下に示します (16655、16656、16657) は、このトピックで、新しいブロックを示すイベントを調べます。  
  
    3.  Active Directory レプリケーションの正常性の検証と Repadmin.exe および RID マスターの可用性を備えた**Dcdiag.exe/test: ridmanager/v**します。 これらのテスト結論が得られない場合は、ドメイン コントローラーおよび RID マスターの間で両側のネットワーク キャプチャを有効にします。  
  
### <a name="troubleshooting-specific-problems"></a>特定の問題のトラブルシューティング  
次の新しいメッセージは、Windows Server 2012 ドメイン コントローラーのシステム イベント ログに記録します。 自動化された AD 正常性は、System Center Operations Manager などのシステムを追跡する必要があります。 これらのイベントの監視すべて、重要ないくつかの重要なドメインの問題のインジケーターいます。  
  
|||  
|-|-|  
|イベント ID|16653|  
|ソース|SAM-ディレクトリ-サービス|  
|重要度|警告|  
|メッセージ|管理者によって構成されたアカウント識別子 (Rid) プールのサイズは、サポートされている最大を超えています。 %1 の最大値は、ドメイン コントローラーが RID マスターときに適用されます。<br /><br />詳細については、次を参照してください。 [RID ブロック サイズの制限](../../ad-ds/manage/../../ad-ds/manage/../../ad-ds/manage/../../ad-ds/manage/Managing-RID-Issuance.md#BKMK_RIDBlockMaxSize)します。|  
|説明と解決策|RID ブロック サイズの最大値は 10 進の 15000 (16 進 3A98) ではようになりました。 ドメイン コントローラーは 15,000 個を超える Rid を要求できなくなります。 このイベントは、値がこの最大値以下の値に設定されるまで起動するたびのログを記録します。|  
  
|||  
|-|-|  
|イベント ID|16654|  
|ソース|SAM-ディレクトリ-サービス|  
|重要度|情報提供|  
|メッセージ|アカウント識別子 (Rid) のプールが無効化されました。 これは、次のような場合に発生する可能性があります。<br /><br />1. ドメイン コントローラーがバックアップから復元されます。<br /><br />2 仮想マシンで実行されている: ドメイン コントローラーがスナップショットから復元します。<br /><br />3。 管理者が、プールと手動で無効化します。<br /><br />See https://go.microsoft.com/fwlink/?LinkId=226247 for more information.|  
|説明と解決策|このイベントが予想される場合は、すべてのドメイン管理者に連絡し、アクションを実行すると、それらのかを決定します。 ディレクトリ サービス イベント ログ情報も含まれますさらのいずれかの手順の実行時にします。|  
  
|||  
|-|-|  
|イベント ID|16655|  
|ソース|SAM-ディレクトリ-サービス|  
|重要度|情報提供|  
|メッセージ|アカウント識別子 (Rid) のグローバルな最大値 %1 に増加しました。|  
|説明と解決策|このイベントが予想される場合は、すべてのドメイン管理者に連絡し、アクションを実行すると、それらのかを決定します。 このイベント増加を示しの全体的な RID プール サイズの 2 の既定値を超える<sup>30</sup>が自動的に行われませんし管理者の操作によってのみ|  
  
|||  
|-|-|  
|イベント ID|16656|  
|ソース|SAM-ディレクトリ-サービス|  
|重要度|警告|  
|メッセージ|アカウント識別子 (Rid) のグローバルな最大値 %1 に増加しました。|  
|説明と解決策|操作は必要です。 このドメイン コントローラに、アカウント識別子 (RID) プールが割り当てられました。 プールの値は、このドメインが、利用可能なアカウント識別子の総数のかなりの部分を使用していることを示します。<br /><br />ドメインが利用可能なアカウント識別子の総数の残りの次のしきい値に達すると、保護メカニズムを有効になります。 1% です。  この保護メカニズムは、手動で再度有効にするまで、RID マスター ドメイン コントローラーでアカウント識別子の割り当て、アカウントの作成をできなくなります。<br /><br />See https://go.microsoft.com/fwlink/?LinkId=228610 for more information.|  
  
|||  
|-|-|  
|イベント ID|16657|  
|ソース|SAM-ディレクトリ-サービス|  
|重要度|エラー|  
|メッセージ|操作は必要です。 このドメインは、利用可能なアカウント識別子の総数 (Rid) のかなりの部分で使用されています。 利用可能なアカウント識別子の総数の残りがあるために、保護メカニズムがアクティブ化されて未満の場合: X % [人為的シーリングの引数] です。<br /><br />この保護メカニズムでは、手動で再度有効にするまで、RID マスター ドメイン コントローラーでアカウント識別子の割り当て、アカウントの作成ができないようにします。<br /><br />アカウントが異常に高い割合でアカウント識別子が消費されていないため、このドメインの作成を再度有効にする前に特定の診断を行うことが非常に重要です。 特定されたすべての問題は、アカウントの作成を再度有効にする前に、解決する必要があります。<br /><br />エラーを診断し、アカウント識別子が消費の異常に高い割合を引き起こしている根本的問題を解決するまでアカウントの作成が完全に無効になりますこのドメインのドメイン内のアカウント識別子枯渇可能性があります。<br /><br />See https://go.microsoft.com/fwlink/?LinkId=228610 for more information.|  
|説明と解決策|すべてのドメイン管理者にお問い合わせくださいし、さらにセキュリティ プリンシパルを作成できないこのドメインにこの保護を上書きするまでそれらを通知します。 プールの保護を上書きし、場合によって、全体的な RID を増やす方法の詳細については、「[グローバル RID 空間サイズのロック解除](../../ad-ds/manage/../../ad-ds/manage/../../ad-ds/manage/../../ad-ds/manage/Managing-RID-Issuance.md#BKMK_GlobalRidSpaceUnlock)します。|  
  
|||  
|-|-|  
|イベント ID|16658|  
|ソース|SAM-ディレクトリ-サービス|  
|重要度|警告|  
|メッセージ|このイベントは、使用可能なアカウント識別子 (Rid) の残り数量を合計で定期的に更新します。 残りのアカウント識別子の数は、約: 1% です。<br /><br />ドメインのない新しいアカウントを作成する可能性がありますが使い果たされると、アカウントが作成されると、Account-identifiers が使用されます。<br /><br />See https://go.microsoft.com/fwlink/?LinkId=228745 for more information.|  
|説明と解決策|すべてのドメイン管理者に連絡し、RID 消費が重要なマイルス トーンを超えたことを通知これは予期される動作かセキュリティ トラスティの作成パターンを確認していないかを確認します。 このイベントを見たではありませんきわめてまれようにするには、少なくとも 1億個 RID が割り当てられたことを意味します。|  
  
## <a name="see-also"></a>参照してください。  
[Windows Server 2012 での RID 発行の管理](http://blogs.technet.com/b/askds/archive/2012/08/10/managing-rid-issuance-in-windows-server-2012.aspx)  
  

