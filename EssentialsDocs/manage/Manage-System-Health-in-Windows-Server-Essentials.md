---
title: "Windows Server Essentials でのシステム正常性を管理します。"
description: "Windows Server Essentials を使用する方法について説明します。"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3043f83b-389c-4f37-a1ff-85afe99314fa
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 91635a58c64fbf74d3b0139be7c9c36365487319
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="manage-system-health-in-windows-server-essentials"></a>Windows Server Essentials でのシステム正常性を管理します。

>Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials での Windows Server 2012 Essentials を適用対象:
 
 このトピックでは、表示し、ダッシュ ボードを使用して、ネットワーク内のすべてのアラートに応答する方法について説明します。  
  
> [!NOTE]
>  Windows Server Essentials と Windows Server 2012 R2、Windows Server Essentials エクスペリエンス役割がインストールされた、サーバーと、ネットワーク内のクライアント コンピューターの正常性アラート ビューアーで、アラートが表示されなくが代わりで確認できます、**正常性レポート**のタブ、**ホーム**ページ。  
  
 Windows Server Essentials は、すべてのコンピューターをサーバーに接続されていて、マルウェア対策クライアント コンピューターで、古いウイルス定義、措置が必要なその他の重要な問題がない、s をシステム正常性、重要な更新プログラムなどに関連する問題を管理者に警告を積極的に監視します。 これらの問題が、サーバー ダッシュ ボードまたはクライアント コンピューター s または Windows Server Essentials でのスタート パッドから起動できるはアラート ビューアーにアラートとして表示されます、**正常性レポート**] タブの [Windows Server Essentials でします。 アラートには既定では、30 分おきには更新されますが、いつでも、ネットワークのアラートを評価する] をクリックして**更新**アラート ビューアーまたは [、**正常性レポート**] タブ。  
  
 次のトピックは理解、表示、およびアラート ビューアーでのアラートに応答およびもを電子メールでアラート通知を受信するようにサーバーを構成する方法を提供に役立ちます。  
  
-   [ヘルス レポートは、Add-In について](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_AddIn)  
  
-   [アラート ビューアーを使用してアラートの表示](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_View)  
  
-   [アラート ビューアーにアラートを整理します。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Organize)  
  
-   [アラートに対処します。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Respond)  
  
-   [アラートの電子メール通知をセットアップします。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Email)  
  
-   [潜在的なコンピューターのアラート](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Potential)  
  
##  <a name="BKMK_AddIn"></a>ヘルス レポートは、Add-In について  
 Windows Server Essentials の状態レポート アドインの Windows Server Essentials ネットワークに関する統合情報を提供して他のユーザーにこの情報を配布することができます。 この情報を表示することができます、**レポート**ダッシュ ボードのタブ。 **レポート**] タブで、次を行うことができます。  
  
-   [必要に応じて、またはスケジュールでレポートを生成します](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Generate)  
  
-   [レポートのコンテンツをカスタマイズします。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Customize)  
  
-   [電子メール レポート](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_emailreport)  
  
> [!NOTE]
>  **Windows Server Essentials:**から Windows Server Essentials の状態レポート アドインをダウンロードすることができます、[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=266342)します。  
>   
>  **Windows Server Essentials:**既定では、状態レポート アドインし、統合されて Windows Server Essentials または Windows Server 2012 R2 と Windows Server Essentials エクスペリエンス役割がインストールされたで正常性レポートが表示されます、**正常性レポート**s ダッシュ ボードのタブ**ホーム**ページ。  
  
###  <a name="BKMK_Generate"></a>必要に応じて、またはスケジュールでレポートを生成します  
 状態レポート アドインをインストールする新しい] タブで、ダッシュ ボードを再起動すると**レポート**ダッシュ ボードに追加されます。 をクリックして必要に応じていつでもヘルス レポートを生成することができます、**正常性レポートを生成する**タスクで、**レポート**] タブ。  
  
 正常性レポートを生成すると、一覧ウィンドウで、レポートが生成された日時で識別される新しい項目が作成されます。 アイテムを開くには、ダブルクリックして、一覧ウィンドウで、またはを選択し、をクリックして**状態レポートを開く**タスク ウィンドウでします。 レポートは HTML 形式の新しいウィンドウに表示されます。  
  
 手動で、レポートを生成するだけでなくすることも、毎日または毎時間のスケジュールで自動的に生成するレポートします。 [タスク] ウィンドウで、これには、をクリックして**状態レポートの設定をカスタマイズ**、をクリックし、**スケジュールと電子メール**] タブ。**スケジュール**機能は既定では、オフ、およびできますオンにすることを選択して、**、スケジュールされた時刻、正常性レポートを生成**チェック ボックスをオンします。  
  
###  <a name="BKMK_Customize"></a>レポートのコンテンツをカスタマイズします。  
 正常性レポートには、次のものが含まれています。  
  
-   **重大なアラートおよび警告**これは、ダッシュ ボードのアラート ビューアーに表示される警告と重大なアラートと一致します。 情報アラートは、正常性レポートには含まれません。  
  
-   **イベント ログの重大なエラー**アプリケーションとサービス ログがスキャン、および過去 24 時間にログに記録されるエラーに表示されます、**詳細**レポートのセクションです。  
  
-   **サーバー バックアップ**最後のサーバー バックアップに関する情報が記載、**詳細**レポートのセクションです。  
  
-   **自動的に開始サービスは実行されていません**レポートが生成された時点で、自動開始サービスが実行されていない場合、このサービスに関する情報が記載する、**詳細**レポートのセクションです。  
  
-   **更新プログラム**サーバーとすべてのクライアント コンピューターでの更新プログラムの状態を確認することができます、**詳細**セクションです。  
  
-   **記憶域**でドライブとその容量の一覧が表示される、**詳細**セクションです。  
  
 ヘルス レポートでは、最初に表示、**概要**、赤いエラー アイコンや黄色い警告アイコンとそれらの項目をクリックして、**詳細**項目に関する詳細を表示する同じ行にリンクします。  
  
 をクリックして、レポートのコンテンツをカスタマイズするには既定では、レポートに含まれているデータ ポイントの一部に興味がない場合、**状態レポートの設定をカスタマイズ**で、タスク ウィンドウで、クリックしてから、**コンテンツ**タブが表示されないが、レポートに表示するコンテンツのチェック ボックスをオフにします。 たとえば、独自のサーバー バックアップ計画があり、don t がサーバーのバックアップに関する警告を表示する場合でしたから除外するサーバーのバックアップ レポートをオフにして、**サーバー バックアップ**チェック ボックスをオンします。  
  
###  <a name="BKMK_emailreport"></a>電子メール レポート  
 レポートを読むためダッシュ ボードにログオンすることでは、にとって不便一部の管理者を管理する 1 つ以上のサーバーがある場合に特にです。 電子メール機能がオン、レポートが生成した後、電子メールが送信するレポートの内容が指定された電子メール アドレスの一覧にします。 簡単に、管理者は、任意のデバイスまたはすべてのクライアント アプリケーションからこのレポートを表示し、最適な状態で、サーバーが実行されていることを確認することができます。  
  
 **状態レポートの設定のカスタマイズ**ダイアログ ボックスで、電子メールを有効にする、SMTP 設定を変更して、電子メール受信者の一覧を指定したらが表示されます、タスク ウィンドウに新しいタスクと表示される:**正常性レポートを電子メールで送信**します。 SMTP 設定の詳細については、次を参照してください。[アラートの電子メール通知設定](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Email)します。  
  
 既存のレポートを選択し、をクリックしてできる**正常性レポートを電子メールで送信**します。 また、新しいレポートを生成し、させて、受信トレイに自動的に送信できます。 自動的に生成されるレポートのスケジュールを構成している場合、レポートは自動的に配信されます受信トレイにスケジュールに従って毎日 (または毎時間) 生成された後。  
  
##  <a name="BKMK_View"></a>アラート ビューアーを使用してアラートの表示  
 このセクションでは、サーバーのネットワーク上のすべてのコンピューターのヘルス状態を表示するのにはアラート ビューアーを開く、ダッシュ ボードまたはスタート パッドの使用方法について説明します。  
  
#### <a name="to-open-the-alert-viewer-by-using-the-dashboard"></a>ダッシュ ボードを使用してアラート ビューアーを開く  
  
1.  ダッシュ ボードを開きます。  
  
2.  ナビゲーション ウィンドウで、表示されている通知アイコン (重大、警告、情報案内のいずれか) のいずれかの] をクリックします。 これは、アラート ビューアーを開きます。  
  
#### <a name="to-open-the-alert-viewer-from-the-launchpad"></a>スタート パッドからアラート ビューアーを開く  
  
1.  サーバーに接続されているコンピューターから、スタート パッドを開きます。 要求された場合、ユーザー名とパスワードで、スタート パッドにログオンします。  
  
2.  表示されている通知アイコン (重大、警告、情報)、スタート パッドを開くには、アラート ビューアーの下部のいずれかをクリックし、指示に従って、詳細ウィンドウで、アラート ビューアーのアラートを解決する.  
  
##  <a name="BKMK_Organize"></a>アラート ビューアーにアラートを整理します。  
 アラート ビューアーにアラートを整理して表示する、重大度 (重大、警告、情報案内のいずれか) に基づいて、またはコンピューター名に基づきます。  
  
#### <a name="to-organize-alerts-in-the-alert-viewer"></a>アラート ビューアーにアラートを整理するには  
  
1.  ダッシュ ボードを開きます。  
  
2.  ナビゲーション ウィンドウで、表示されている通知アイコン (重大、警告、情報案内のいずれか) のいずれかをクリックします。 これは、アラート ビューアーを開きます。  
  
3.  展開、**整理**ドロップ ダウン リスト、および、次のいずれかの操作。  
  
    1.  選択**コンピューターによってフィルタ リング**、アラートを表示するコンピューター名前] をクリックします。 これには、選択したコンピューターに対してのみアラート ビューアーにアラートが表示されます。  
  
    2.  選択**アラートの種類でフィルター処理**、し、アラートの種類 (重大、警告、情報案内のいずれか) をするには、アラートを表示] をクリックします。 これには、のみ、選択したアラートの種類、アラート ビューアーが表示されます。  
  
##  <a name="BKMK_Respond"></a>アラートに対処します。  
 アラートが発生した場合、次のいずれかの操作を無効にすることができます。  
  
-   [アラートを解決します。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Resolve)  
  
-   [アラートを無視します。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_3)  
  
-   [アラートを有効にします。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_5)  
  
-   [アラートを削除します。](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_4)  
  
###  <a name="BKMK_Resolve"></a>アラートを解決します。  
 アラートを解決するのにはアラート ビューアーで、解決指示に従います。 アラートが解決したら、引き続き表示されます、アラート ビューアーでそれが更新されるまで。  
  
###  <a name="BKMK_3"></a>アラートを無視します。  
 後で返信する場合にアラートを無視することができます。 アラート ビューアーでも記載されているときに、アラートを無視してが無効にされ、使用できなくなります。 無視したアラートは、コンピューターの全体的な正常性評価に含まれません。 無視したアラートに対処するため、最初に、アラートを有効にする必要があります。  
  
##### <a name="to-ignore-an-alert"></a>アラートを無視するには  
  
1.  Windows Server Essentials サーバーに接続されているコンピューターから、スタート パッドを開きます。  
  
2.  スタート パッド、表示されている通知アイコン (重大、警告、情報) のいずれかの] をクリックします。 これは、アラート ビューアーを開きます。  
  
3.  アラート ビューアーで、無視するアラートを選択し、**タスク**セクションで、をクリックして**、アラートを無視して**します。  
  
 を無効になっているアラートに応答するのには、アラートを有効にする必要があります。  
  
###  <a name="BKMK_5"></a>アラートを有効にします。  
 以前に無視したアラートを有効にすることができます。 アラートを有効にすると、それを解決したり、必要に応じて、それを削除できます。 無視するマークされているときに無効になっていると、アラートが表示されます。 以前に無効にするアラートを有効にするとがアクティブになるしは、コンピューターの全体的な正常性評価に再度含まれます。  
  
##### <a name="to-enable-an-alert"></a>アラートを有効にするには  
  
1.  サーバーに接続されているコンピューターから、スタート パッドを開きます。  
  
2.  スタート パッドで、表示されている通知アイコン (重大、警告、情報) を開くには、アラート ビューアーのいずれかをクリックします。  
  
3.  アラート ビューアーで、有効化、およびをクリックするアラートを右クリックして**アラートを有効にする**します。  
  
###  <a name="BKMK_4"></a>アラートを削除します。  
 解決も無視もしない場合、アラートを削除することができます。 スタート パッドでアラート ビューアーを使用すると、コンピューターに対して生成されたアラートを削除します。 アラートを削除するサーバーでは、次のネットワーク正常性評価サイクルでもう一度、問題が検出された場合は、新しいアラートを生成します。  
  
##### <a name="to-delete-an-alert"></a>アラートを削除するには  
  
1.  サーバーに接続されているコンピューターから、スタート パッドを開きます。  
  
2.  スタート パッドで、表示されている通知アイコン (重大、警告、情報) を開くには、アラート ビューアーのいずれかをクリックします。  
  
3.  アラート ビューアーで、削除、およびをクリックするアラートを右クリックして**、アラートを削除**します。  
  
##  <a name="BKMK_Email"></a>アラートの電子メール通知をセットアップします。  
 アラートの発生について電子メールで通知するようにサーバーを構成することができます。 これらのアラートの電子メール通知が含まれているネットワークの問題とその解消手順についてはアラート ビューアーに表示される情報と同じです。 ネットワーク正常性評価の一部はプログラムを使用して行われます。  
  
 電子メールでアラート通知を送信するようにサーバーを構成するときに、ネットワーク正常性評価で見つかったアラートの電子メール通知が送信されます。 ただし、アラート ビューアーで報告されるすべてのアラートが電子メールで報告されます。  
  
 30 分おきにアラート電子メール評価タスクは、ネットワークのアラートを評価すると、サーバー上で実行されます。 電子メール通知が発生するのに設定されている任意のアラート、かどうかを電子メール通知が送信されます。 このアラートは、メールボックスの混雑を避けるためには、次の評価サイクルでまだアクティブな場合は、2 つ目の電子メールは送信されません。 ただし、新しいアラートが、将来のアラート評価サイクル内で検出された場合、電子メール通知が送信されるが含まれている、新しいと以前のアラート。  
  
###  <a name="BKMK_list"></a>電子メール通知を送信するアラート  
 アラート ビューアーに次のアラートは、アラートの電子メール通知を送信する、サーバーをセットアップするときに電子メール通知の結果します。  
  
-   エラーは、クライアント コンピューターのバックアップが存在します。  
  
-   サーバーは再起動されました。  
  
-   1 つまたは複数のサービスが実行されていません。  
  
-   Windows Server Storage Service が実行されていません。  
  
-   評価期間が超えています。  
  
-   今すぐ有効にします。  
  
-   移行元サーバーをシャット ダウンします。  
  
-   BPA スキャン結果には、エラーが含まれています。  
  
-   BPA スキャン結果には、警告が含まれています。  
  
-   証明書では、Anywhere Access の使用できません。  
  
-   Anywhere Access の証明書の有効期限が切れています。  
  
-   ルーターが正しく構成されていません。  
  
-   Web サーバーが正しく構成されていません。  
  
-   リモート デスクトップ サービスが正しく構成されていません。  
  
-   ファイアウォールが正しく構成されていません。  
  
-   インターネット ドメイン名の有効期限が切れています。  
  
-   インターネット ドメイン名を更新することはできません。  
  
-   ライセンス エラー: フォレストの信頼チェック。  
  
-   ライセンス エラー: ドメイン コントローラーの確認します。  
  
-   ライセンス エラー: FSMO 役割チェック。  
  
-   ライセンス エラー: 強制 FSMO ポリシー。  
  
-   ライセンス エラー: 強制読み込みポリシー。  
  
-   ライセンス エラー: Active Directory ドメイン サービス。  
  
-   Office 365 サブスクリプションの有効期限が切れています。  
  
-   Office 365 の認証に失敗しました。  
  
-   パスワード ポリシーが正しくありません。  
  
-   パスワード同期サービスは、Office 365 でユーザー パスワードを同期できません。  
  
-   Windows のパスワードを変更します。  
  
-   Office 365 パスワードが Windows パスワードと同じではないです。  
  
-   Exchange Server に接続できません。  
  
-   Microsoft Exchange Server には、問題があります。  
  
-   サーバー バックアップの 1 つまたは複数のハード ドライブが接続されていません。  
  
-   バックアップ ハード ドライブには、サーバー バックアップに十分な空き領域がありません。  
  
-   ドライブのスナップショットを取得できなかったために、サーバーのバックアップに失敗しました。  
  
-   スケジュールされたバックアップが正常に完了しませんでした。  
  
-   1 つまたは複数の定義済みのサーバー フォルダーが見つかりません。  
  
-   1 つまたは複数のサーバーのハード ドライブの空き領域が小さします。  
  
-   記憶域サービス用の VSS Writer が実行されていません。  
  
-   ハード ドライブの低い記憶域容量。  
  
-   1 つまたは複数のドライブが機能していないでオフラインになっています。  
  
###  <a name="BKMK_SMTP"></a>Windows Server Essentials で電子メールによりアラート通知を送信するようにサーバーの SMTP を設定します。  
 このセクションでは、アラートの電子メール通知を送信するようにサーバーを構成する方法について説明します。  
  
> [!NOTE]
>  Windows Server Essentials の状態レポート アドインをダウンロードすることができます、[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=266342)します。  
  
##### <a name="to-set-up-email-notification-for-alerts"></a>アラートの電子メール通知を設定するには  
  
1.  **ダッシュ ボード**、開かれている、**アラート ビューアー**します。  
  
2.  **アラート ビューアー**、] をクリックして**アラートの電子メール通知のセットアップ**します。  
  
3.  **アラートの電子メール通知設定**] ウィンドウで、をクリックして**を有効にする**します。  
  
4.  **SMTP 設定**] ウィンドウで、次の操作します。  
  
    1.  **送信元電子メール アドレス**からアラートを電子メールを送信するために使用する電子メール アドレスの種類。 このメール アドレスがアラート通知に送信者のアドレスとして表示されます。  
  
    2.  **SMTP サーバー名**で、**送信元電子メール アドレス**テキスト ボックスに、手順 4a で指定した SMTP サーバーの名前を入力します。 (表 1 を参照一部の SMTP サーバー名の一覧については)。  
  
    3.  **SMTP ポート**、電子メールを送受信する SMTP サーバーによって使用されるポート番号を入力します。 (表 1 を参照の一部の SMTP サーバーによって使用されるポート番号)。  
  
    4.  選択**このサーバーには、セキュリティで保護された接続 (SSL) が必要です。** SMTP サーバーが SSL を使用している場合 (表 1 参照)。  
  
    5.  選択**このサーバー認証が必要**SMTP サーバーは、ユーザー名とパスワード情報を必要とする場合 (表 1 参照)。 このチェック ボックスを選択した場合は、ユーザー名とパスワードの入力したメール アドレスを入力、**送信元電子メール アドレス**、手順 4a でフィールドをクリックして**OK**します。  
  
    > [!NOTE]
    >  SMTP サーバー名、ポート番号、および SSL の使用状況に関する情報は、インターネット サービス プロバイダーから取得できます。  
  
     **表 1** SMTP サーバー名、認証と SSL 暗号化の要件、およびポート番号  
  
    |SMTP サーバー|SSL が必要です。|認証が必要です。|ポート番号|アカウント名/ログイン名|  
    |-----------------|------------------|-----------------------------|-----------------|------------------------------|  
    |smtp.gmail.com|うん|うん|587|ドメイン名とパスワードで認証用の完全なメール アドレスを指定します。|  
    |smtp.live.com|うん|うん|587|ドメイン名とパスワードで認証用の完全なメール アドレスを指定します。|  
    |smtp.comcast.net|うん|違います|587|ドメイン名とパスワードで認証用の完全なメール アドレスを指定します。|  
    |smtp.mail.yahoo.com|違います|うん|25|ユーザー名のドメイン名を指定せず、メール アドレスのみを提供します。|  
  
5.  **アラートの通知のセットアップ**の**電子メール受信者**、電子メールでアラート通知を受信する人の電子メール アドレスを入力します。 セミコロン (;) では、各電子メール アドレスを分離することを確認します。  
  
6.  設定正しく、アラートの電子メール通知を送信する] をクリックして、SMTP サーバーを構成していることを確認する**適用して送信電子メール**します。  
  
    > [!NOTE]
    >  クリックすると**適用して送信電子メール**、正常性アラートが表示されているなしでサンプル電子メール通知を受信する通常します。 ただし、このテスト プロセス中に、電子メール通知を送信するように構成された正常性アラートを識別される場合このアラートはテスト電子メールに含まれています。  
  
### <a name="configuring-smtp-on-your-server-to-send-health-reports-in-windows-server-essentials"></a>Windows Server Essentials での正常性レポートを送信するようにサーバーの SMTP を設定します。  
 このセクションでは、電子メールで状態レポートを受信できるように、サーバーの SMTP 設定を構成する方法について説明します。  
  
> [!NOTE]
>  既定では、状態レポート アドインし、統合されて Windows Server Essentials または Windows Server 2012 R2 と Windows Server Essentials エクスペリエンス役割がインストールされたで正常性レポートが表示されます、**正常性レポート**s ダッシュ ボードのタブ**ホーム**ページ。  
  
##### <a name="to-set-up-email-notification-for-health-reports"></a>状態レポートの電子メール通知を設定するには  
  
1.  **ダッシュ ボード**、] をクリックして、**レポート**] タブ。  
  
2.  **状態レポート タスク**タスク ウィンドウで、をクリックして**状態レポートの設定をカスタマイズ**します。  
  
3.  **状態レポートの設定のカスタマイズ**] ウィンドウで、をクリックして、**スケジュールと電子メール**] タブ。  
  
4.  **スケジュールと電子メール**] タブで、**電子メール**] セクションで、次の操作します。  
  
    1.  をクリックして**を有効にする**、および正常性を送信するために使用する電子メール アドレスがからレポートの種類。 このメール アドレスが、電子メールで送信される状態レポートに送信者のアドレスとして表示されます。  
  
        1.  **SMTP サーバー名**、SMTP サーバーの名前を入力します。 (表 1 を参照一部の SMTP サーバー名の一覧については)。  
  
        2.  **SMTP ポート**、電子メールを送受信する SMTP サーバーによって使用されるポート番号を入力します。 (表 1 を参照の一部の SMTP サーバーによって使用されるポート番号)。  
  
        3.  選択**このサーバーには、セキュリティで保護された接続 (SSL) が必要です。** SMTP サーバーが SSL を使用している場合 (表 1 参照)。  
  
        4.  選択**このサーバー認証が必要**SMTP サーバーは、ユーザー名とパスワード情報を必要とする場合 (表 1 参照)。 このチェック ボックスを選択した場合は、ユーザー名とパスワードの入力したメール アドレスを入力、**送信元電子メール アドレス**、手順 4a でフィールドをクリックして**OK**します。  
  
            > [!NOTE]
            >  SMTP サーバー名、ポート番号、および SSL の使用状況に関する情報は、インターネット サービス プロバイダーから取得できます。  
  
            > [!NOTE]
            >  強くお勧めするレポートには、悪意のある人物によって脆弱性を検出するために使用できるサーバーの状態が含まれている可能性があるために SSL を使用する (例: windows update を見つからない)。 SSL を有効にすると、転送中にデータを暗号化し、サーバーの脆弱性を公開するリスクを軽減します。  
  
5.  電子メールを有効にした後、**SMTP 設定の変更**リンクが表示されます。 新しいタスクも、**正常性レポートを電子メールで送信**に表示を取得**状態レポート タスク**します。  
  
     **表 1** SMTP サーバー名、認証と SSL 暗号化の要件、およびポート番号  
  
    |SMTP サーバー|SSL が必要です。|認証が必要です。|ポート番号|アカウント名/ログイン名|  
    |-----------------|------------------|-----------------------------|-----------------|------------------------------|  
    |smtp.gmail.com|うん|うん|587|ドメイン名とパスワードで認証用の完全なメール アドレスを指定します。|  
    |smtp.live.com|うん|うん|587|ドメイン名とパスワードで認証用の完全なメール アドレスを指定します。|  
    |smtp.comcast.net|うん|違います|587|ドメイン名とパスワードで認証用の完全なメール アドレスを指定します。|  
    |smtp.mail.yahoo.com|違います|うん|25|ユーザー名のドメイン名を指定せず、メール アドレスのみを提供します。|  
  
6.  **状態レポートの設定のカスタマイズ**の**次の電子メール受信者に自動的に正常性レポートを送信:**、電子メールで状態レポートを受信する人の電子メール アドレスを入力します。 セミコロン (;) では、各電子メール アドレスを分離することを確認します。  
  
7.  SMTP サーバーを構成していることを確認する設定正しくダッシュ ボードの [状態レポート] タブから、電子メールで状態レポートを送信するレポートを選択し] をクリックして**正常性レポートを電子メールで送信**タスク] ウィンドウからです。  
  
##  <a name="BKMK_Potential"></a>潜在的なコンピューターのアラート  
 このセクションでは、理解し、アラートは、サーバーに接続されていると、コンピューターのスタート パッドに表示されるコンピューターに固有の管理について説明します。  
  
 次の表に、一部のコンピューターのアラートを生成し、コンピューターに適用している場合、アラート ビューアーに表示されることができます。  
  
|アラートのタイトル|アラートの影響と解決|  
|-----------------|---------------------------------|  
|ネットワーク ファイアウォールの現在の状態は、このコンピューターの保護が弱くを提供します。|承認されていないユーザーまたはソフトウェアは Windows ファイアウォールが有効でない場合は、このコンピューターにアクセスできる可能性があります。|  
|ウイルス対策が入っていないインストールされている、またはない最新の状態。|お使いのコンピューター上のデータが危険にさらされては場合、**ウイルス対策**セキュリティ設定がになっているかは更新されません。 [コンピューターを保護する](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Protect)、示されている手順に従います。|  
|スパイウェアと不要なソフトウェア対策が入っていないインストールされている、またはない最新の状態。|お使いのコンピューター上のデータが危険にさらされては場合、**スパイウェアおよびソフトウェア保護が不要な**がになっているかは更新されません。 [コンピューターを保護する](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Protect)、示されている手順に従います。|  
|Windows Update が無効になります。|Windows Update を有効にしない限り、更新プログラムの新しく、修正された機能からメリットを得ることはできません。 アラート ビューアーで、Windows Update を有効にする] をクリックして**Windows Update を開く**します。<br /><br /> 場合、**Windows Update を開く**タスクが表示されない場合、アラートが発生したコンピューターにログオンしていません。 アラート ビューアーでこのタスクを実行する、アラートが発生するコンピューターにログオンする必要があります。|  
|重要な更新プログラムをインストールする必要があります。|Windows Update を有効にしない限り、更新プログラムの新しく、修正された機能からメリットを得ることはできません。 アラート ビューアーで、Windows Update を有効にする] をクリックして**Windows Update を開く**します。<br /><br /> 場合、**Windows Update を開く**タスクが表示されない場合、アラートが発生したコンピューターにログオンしていません。 アラート ビューアーでこのタスクを実行する、アラートが発生するコンピューターにログオンする必要があります。|  
|コンピューターを再起動して更新プログラムを適用します。|適用されるまで、更新プログラムの新しく、修正された機能を活用することはできません。 すべてのデータを保存し、更新プログラムを適用するコンピューターを再起動します。|  
|空き領域がハード ドライブの低下します。|領域が利用可能な行われていない場合追加情報を保存することはできません。 コンピューター上の空き領域を増やすと、次のオプションを考慮してください。<br /><br /> 新しいハード ドライブを追加します。<br /><br /> -実行**ディスク クリーンアップ**古いと一時ファイルを削除します。<br /><br /> -別のコンピューター上の共有フォルダー、ファイルを移動します。<br /><br /> CD、DVD、または外部ハード ドライブなどのリムーバブル メディア上のファイルをアーカイブします。|  
|**ファイル履歴**このコンピューターで実行するサーバー上のエージェントが正しく構成されていません。|ファイル履歴のバックアップを作成することはできません。|  
|1 つまたは複数のサービスが実行されていません。||  
|Windows のパスワードを変更します。||  
|Microsoft Office 365 パスワードは、Windows のパスワードと同じです。||  
  
###  <a name="BKMK_Protect"></a>コンピューターを保護するには  
  
1.  セキュリティ センターを開きます。  
  
2.  インストールされているウイルス対策の状態を確認します。  
  
3.  保護の状態に応じて、次のタスクのいずれかを実行します。  
  
    -   有効でない場合は、それを有効にします。  
  
    -   その情報が最新の状態でない場合、シグネチャを更新するプロセスが完了します。  
  
    -   ウイルス対策がインストールされていない場合は、インストールすることを検討してください。  
  
## <a name="see-also"></a>参照してください。  
  
-   [Windows Server Essentials を使用します。](../use/Use-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials を管理します。](Manage-Windows-Server-Essentials.md)