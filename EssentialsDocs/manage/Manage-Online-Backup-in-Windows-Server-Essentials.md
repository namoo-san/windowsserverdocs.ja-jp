---
title: "Windows Server Essentials でのオンライン バックアップを管理します。"
description: "Windows Server Essentials を使用する方法について説明します。"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95a9f593-fad7-4335-bd4d-c7bb8c033efb
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 37d59d500a2de1e2b98c848e7484ae13639d09b7
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="manage-online-backup-in-windows-server-essentials"></a>Windows Server Essentials でのオンライン バックアップを管理します。

>Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials での Windows Server 2012 Essentials を適用対象:
  
 Microsoft Azure backup を統合した後、**オンライン バックアップ**の管理] ページは、Windows Server Essentials ダッシュ ボードに表示されます。 **オンライン バックアップ**ページでは、一般的な管理タスクを実行することです。 [オンライン バックアップ] ページの機能は次のとおりです。  
  
-   次のサブセクション ページ:  
  
    -   **オンライン バックアップ**このセクションには、現在のバックアップの状態、記憶域の状態、およびアカウント情報が表示されます、サーバーのオンライン バックアップを登録した後です。  
  
    -   **保護されたフォルダー**このセクションでは、すべての共有フォルダーと、サーバー上のすべてのファイル履歴フォルダー、および Azure でのバックアップを選択したその他のすべてのフォルダーを示します。 一覧には、フォルダ名、フォルダーのパス、および各共有フォルダーの状態が含まれています。  
  
    -   **履歴のバックアップ**このセクションでは、最近のオンライン バックアップの一覧を表示します。 一覧には、操作、および、時間と各バックアップの状態の種類が含まれています。  
  
-   選択したバックアップ ジョブまたは復元ジョブに関する追加情報の詳細ウィンドウ。  
  
-   タスクのウィンドウで、実行できる管理タスクのセットが含まれています。  
  
 ベスト プラクティスとしてには、最も重要なビジネスおよびユーザー データをバックアップする必要があります。 たとえば、重要なデータ ファイルを含むサーバー フォルダーをバックアップする必要があります。 重要な情報が含まれているネットワーク コンピューターのファイル履歴もバックアップする必要があります。  
  
 オンライン バックアップを作成するデータを決定するときに実装するバックアップの頻度と保持ポリシーを検討してください。 予算を確認し、許容できる記憶域の容量を決定します。 コストと、ニーズに対する記憶域のボリュームのバランスし、可能な重要なデータを保護するオンライン バックアップを構成します。 料金情報については、次を参照してください。[Azure Backup の料金詳細](https://azure.microsoft.com/pricing/details/backup/)します。  
  
 次のセクションでは、Windows Server Essentials ダッシュ ボードに表示できる各種のオンライン バックアップ タスクについて説明します。  
  
## <a name="online-backup-tasks-in-the-dashboard"></a>ダッシュ ボードでのオンライン バックアップ タスク  
  
-   [Azure Backup コンテナーに証明書のアップロードします。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)  
  
-   [オンライン バックアップを構成します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)  
  
-   [オンライン バックアップを開始します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_3)  
  
-   [オンライン バックアップからファイルとフォルダーを復元します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_4)  
  
-   [このサーバーをバックアップ用の登録します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)  
  
-   [サーバーの登録解除します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_6)  
  
###  <a name="BKMK_1"></a>Azure Backup コンテナーに証明書のアップロードします。  
 Windows Server Essentials でのオンライン バックアップの Azure Backup を使用することができます、前に、バックアップ コンテナーに登録するパブリック証明書をアップロードする必要があります。 証明書は、Microsoft Online Services サブスクリプションの所有者、サブスクリプションに関連付けられているリソースを管理する代わりに機能し、Azure Backup 展開 (エージェント) の認証に使用されます。  
  
> [!NOTE]
>  証明書をアップロードする前に、手順を実行する必要があります[Azure Backup サービスにサインアップ](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_16)します。  
  
##### <a name="to-upload-a-certificate-to-use-with-the-azure-backup-service"></a>Azure Backup サービスで使用する証明書をアップロードするには  
  
1.  管理者アカウントでは、Windows Server Essentials のダッシュ ボードにログオンします。  
  
2.  ダッシュ ボードで**ホーム**] ページで [**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ**領域で、をクリックして**Azure Backup コンテナーに証明書をアップロード**します。  
  
     開きます**Recovery Services** Azure 管理ポータルでします。 T は既にログインして Azure に、Microsoft アカウントを使用してログインする必要があります。  
  
4.  使用するオンライン バックアップを開くには、バックアップ コンテナーの名前をクリックして、**クイック スタート**バックアップ コンテナーのページです。  
  
5.  をクリックして**証明書を管理**します。  
  
6.  **証明書の管理**パブリック証明書のパスは、Windows Server Essentials によって生成された] ダイアログ ボックスを貼り付けます。 パブリック証明書のパスを取得するには、次の操作を行います。  
  
    1.  Windows Server Essentials ダッシュ ボード] をクリックして、**オンライン バックアップ**] タブ。  
  
    2.  **オンライン バックアップ**] ページで、生成された証明書のパスをコピーします。  
  
    3.  切り替えて、Azure 管理ポータルで、**証明書の管理**] ダイアログ ボックスで、生成されたパブリック証明書をアップロードするパスを貼り付けます。  
  
    > [!NOTE]
    >  また、独自のパブリック証明書を使用することができます。 どのような証明書が必要となる、上に、**クイック スタート**] ページで [、**証明書を取得**リンクします。  
  
    > [!NOTE]
    >   Azure では、公開キーを持つ x.509 v2 証明書が必要です。 詳細については、次を参照してください。[資格情報コンテナー証明書を管理](https://msdn.microsoft.com/library/azure/dn169036.aspx)します。  
  
7.  証明書を選択してクリックして**OK** (チェック マーク)。  
  
8.  **クイック スタート**ページ。 をクリックして**ダッシュ ボード**、し、証明書が正常にアップロードされたことを確認します。 証明書が正常にアップロードされると、ダッシュ ボードに証明書の拇印と有効期限の日付が表示されます。  
  
 この手順を完了した後、次の手順を実行します。  
  
1.  Azure Backup サービスに、サーバーを登録します。 詳細については、次を参照してください。[このサーバーをバックアップ用の登録](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)します。  
  
2.  サーバーのオンライン バックアップを構成します。 詳細については、次を参照してください。[オンライン バックアップの構成](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)します。  
  
###  <a name="BKMK_2"></a>オンライン バックアップを構成します。  
 Azure Backup にサーバーを登録した後は、Windows Server Essentials のオンライン バックアップ設定を構成できます。  
  
##### <a name="to-configure-online-backup"></a>オンライン バックアップを構成するには  
  
1.  サーバーの登録ウィザードからまたはのいずれか、**Online Backup** ] ページの Windows Server Essentials ダッシュ ボード] をクリックして**オンライン バックアップの構成**します。 オンライン バックアップの構成ウィザードが表示されます。  
  
2.  **オンライン バックアップの構成**ページ、ウィザードの [Azure Backup にバックアップする各サーバー フォルダーのチェック ボックスをオンします。 バックアップに含めるしたくないする各サーバー フォルダーのチェック ボックスをオフにします。 一覧に表示されていないフォルダーを追加する] をクリックして**フォルダーの追加**します。 選択が完了したら、クリックして**次**します。  
  
    > [!NOTE]
    >  ローカルのサーバー上にあるフォルダーまたは ReFS としてフォーマットされているドライブ上にあるフォルダーを選択することはできません。  
  
3.  **追加 File History Backups**ページ、ウィザードのファイル履歴機能をサポートするネットワーク コンピューターのファイル履歴のバックアップを含めるように選択できます。 をクリックして**次**を続行します。  
  
4.  **バックアップ スケジュールを指定**ページ、ウィザードの次の構成] をクリック**次**を続行します。  
  
    -   選択するか、オンライン バックアップを実行する時刻を受け入れます。 既定の時間は、10時 00分 PM です。 2 番目のバックアップを実行する時刻を指定することも可能性があります。  
  
    -   選択するか、オンライン バックアップを実行する曜日を受け入れます。 既定では、オンライン バックアップは月曜日金曜日までから実行されます。  
  
5.  **バックアップの保持ポリシーを指定**ページ、ウィザードの [クリックして、オンライン バックアップを保持する日数] を選択**次**します。 既定では 7 日です。 オンライン バックアップを 15 または 30 日間保持することもできます。  
  
    > [!NOTE]
    >   Azure Backup は、常に最新のバックアップを保持します。 バックアップ先がバックアップを格納するための十分な空きを持たない場合、バックアップ処理は成功しません。 このような状況を避けるために、追加の記憶域を購入するか、データの保持期間を短くください。 料金情報については、次を参照してください。[料金詳細](https://azure.microsoft.com/pricing/details/backup/)Microsoft Azure Backup 用です。  
  
6.  **、帯域幅の使用を選択して**オンライン バックアップに割り当てられているインターネット帯域幅の量を制限する場合、ウィザードのページ**を有効にするインターネット帯域幅の使用**します。 このページのオプションを使用すると、時間と非営業時間中に、作業中に使用するのにオンライン バックアップを許可するようにインターネット帯域幅の量を指定できます。 営業時間と営業日を定義します。  
  
    > [!NOTE]
    >   Azure Backup では、統合ソフトウェアが情報バックアップまたは復元時にネットワーク帯域幅を利用する方法をカスタマイズすることができます。 調整と呼ばれる一般的な手法を使用して、バックアップで使用可能なネットワーク帯域幅の量を制御し、特定の曜日と時間間隔中にプロセスを復元できます。 選択した後、**を有効にするインターネット帯域幅の使用**オンライン バックアップの構成ウィザードで] チェック ボックスと、営業日と営業時間帯域幅の制限を適用する営業時間を指定できます。 非営業時間制限はそれ以外の時間に使用されます。 有効な帯域幅の範囲は 256 Kbps ~ 無制限両方の制限です。  
  
7.  オンライン バックアップの構成が完了したら、クリックして**閉じる**します。  
  
    > [!TIP]
    >  成功したバックアップの構成後、**Online Backup**ページは、最新のオンライン バックアップと、バックアップ コンテナーで使用される記憶域の容量の状態を示しています。 以前のバックアップの状態を表示するには、次のようにクリックします。**バックアップ履歴**します。  
  
###  <a name="BKMK_3"></a>オンライン バックアップを開始します。  
  
> [!NOTE]
>  オンライン バックアップを開始する前にする必要があります[このサーバーをバックアップ用の登録](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)、し、[オンライン バックアップの構成](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)します。  
  
##### <a name="to-start-an-online-backup-immediately"></a>オンライン バックアップをすぐに開始するには  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ タスク**] ウィンドウで、をクリックして**バックアップを今すぐ開始**します。  
  
###  <a name="BKMK_4"></a>オンライン バックアップからファイルとフォルダーを復元します。  
 復元のファイルとフォルダーのウィザード順を追っての検索、選択すると、およびオンラインでバックアップされているファイルとフォルダーを復元するプロセスです。 ウィザードを昇格すると、次のタスクを実行します。  
  
1.  **オンライン バックアップからファイルとフォルダーの復元先を選択します。**  
  
     復元のファイルとフォルダーのウィザードを実行すると、最初に行う必要がありますは、現在ログオンして、サーバーのオンライン バックアップから、または別のサーバーのバックアップからファイルを復元するかを指定します。  
  
2.  **ファイルとフォルダーの復元元となるサーバーを選択します。**  
  
     別のサーバーからファイルとフォルダーを復元することを選択する場合で利用可能なサーバーの一覧から復元し、をクリックするサーバーを選択**次**します。  
  
3.  **ファイルとフォルダーを復元するボリュームを選択します。**  
  
     オンライン バックアップには、バックアップ元のサーバー上のボリュームに対応するボリュームが含まれます。 選択した後、ボリューム、選択の日付と時刻、バックアップから復元、およびをクリックする**次**します。  
  
4.  **[ファイルとフォルダーを復元するには**  
  
     **復元する項目を選択して**ページ、ウィザードのさまざまなフォルダーの場所を開くし、各ファイルまたはフォルダーを復元することのチェック ボックスをオンにします。 ファイルの選択が完了したら、クリックして**次**します。  
  
5.  **復元されたファイルとフォルダーの移行先の場所を指定します。**  
  
     **復元オプションの指定**ウィザードのページでは、ファイルとフォルダーを復元する場所を指定することができます。 次の 2 つのオプションがあります。  
  
    -   **元の場所に復元**します。 バックアップの元となる正確な場所にファイルとフォルダーを復元するには、このオプションを選択します。  
  
    -   **別の場所に復元**します。  ファイルを復元するために、サーバー上の別の場所を指定するには、このオプションを選択します。  
  
         既定のインストールで移行先の場所に復元ファイルと同じ名前を持つファイルが既に存在する場合、ウィザードは、元のファイルのコピーを作成します。 さらに、アクセス制御リスト (ACL) が現在のファイル アクセス許可を反映するように更新されます。 をクリックすることができます**詳細**を既定の設定をカスタマイズします。  
  
6.  **復元情報を確認します。**  
  
     **復元情報の確認**ページは、指定した復元手順の概要を説明します。 ファイルの復元を続行するには、オンライン バックアップ アカウントの正しいパスフレーズを入力する必要があります。  
  
###  <a name="BKMK_5"></a>このサーバーをバックアップ用の登録します。  
 バックアップまたは復元するファイル、フォルダー、および Windows Server Essentials サーバー上のファイル履歴 Azure Backup に、まず Microsoft Azure Backup サービスで、サーバーを登録する必要があります。  
  
> [!NOTE]
>  サーバーを登録する前に、オンライン バックアップを保存するバックアップ コンテナーで使用する証明書をアップロードする必要があります。 詳細については、次を参照してください。[Azure Backup コンテナーに証明書のアップロード](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)します。  
  
##### <a name="to-register-your-server-with-azure-backup"></a>Azure Backup にサーバーを登録するには  
  
1.  管理者は、サーバーにログオンし、ダッシュ ボードを開きます。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ**サブセクションで、をクリックして**登録**します。  
  
4.  オンライン バックアップのバックアップ コンテナーで使用する証明書を選択します。 既定では既定の証明書が選択されています。別の証明書を選択する場合は、使用**参照**します。 をクリックして**次**します。  
  
5.  パスフレーズを作成し、登録を完了し、ウィザードの指示に従います。  
  
###  <a name="BKMK_6"></a>サーバーの登録解除します。  
  
> [!CAUTION]
>  Microsoft Azure Backup サービスから Windows Server Essentials サーバーの登録を解除する場合、Azure Backup はサーバーを不要になったバックアップできます。 さらに、以前にアップロードされたサーバーのデータが消去されます。 オンライン バックアップを再開するには、サーバーを再登録する必要があります。  
  
##### <a name="to-unregister-your-server-with-azure-backup"></a>Azure Backup を使用してサーバーの登録を解除するには  
  
1.  ログイン、[Azure 管理ポータル](https://manage.windowsazure.com)します。  
  
2.  をクリックして**Recovery Services**します。  
  
3.  **Recovery Services**、バックアップ資格情報コンテナーの名前をクリックします。  
  
4.  **クイック スタート**、資格情報コンテナーのページで、[**サーバー**します。  
  
5.  サーバーの選択] をクリックして**削除**、] をクリックし、**はい**確認プロンプトでします。  
  
## <a name="related-tasks"></a>関連するタスク  
  
-   [オンライン バックアップ ポリシーを変更します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_7)  
  
-   [オンライン バックアップ記憶域の使用状況の表示](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_8)  
  
-   [オンライン バックアップに新しいフォルダーを含める](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_9)  
  
-   [削除またはオンライン バックアップ ポリシーからファイル履歴のバックアップを除外します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_10)  
  
-   [無効にするか、またはオンライン サーバー バックアップを再度有効にします。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_11)  
  
-   [進行中のオンライン サーバー バックアップを停止します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_12)  
  
-   [オンライン バックアップ ステータスを表示](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_13)  
  
-   [表示およびオンライン バックアップのアラートの管理](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_14)  
  
-   [オンライン バックアップを既定の設定にリセットします。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_15)  
  
-   [Azure Backup サービスにサインアップします。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_16)  
  
-   [Azure Backup を Windows Server Essentials と統合します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_17)  
  
-   [Windows Server Essentials でのオンライン バックアップのフォルダーを保護します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_18)  
  
-   [Windows Server Essentials のオンライン バックアップ履歴](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_19)  
  
###  <a name="BKMK_7"></a>オンライン バックアップ ポリシーを変更します。  
 Windows Server Essentials ダッシュ ボードを使用して、オンライン バックアップ ポリシーを変更する簡単です。  
  
##### <a name="to-change-the-online-backup-policy"></a>オンライン バックアップ ポリシーを変更するには  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ タスク**] ウィンドウで、をクリックして**オンライン バックアップの構成**します。  
  
4.  オンライン バックアップ ポリシーをカスタマイズするのには、ウィザードの指示に従います。  
  
 詳細については、カスタマイズ可能な設定についてを参照してください。[オンライン バックアップの構成](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)します。  
  
###  <a name="BKMK_8"></a>オンライン バックアップ記憶域の使用状況の表示  
  
##### <a name="to-view-the-amount-of-storage-space-that-online-backup-uses"></a>オンライン バックアップを使用する記憶域の容量を表示するには  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ**] タブで、**記憶域の状態**情報ウィンドウに表示されます。  
  
###  <a name="BKMK_9"></a>オンライン バックアップに新しいフォルダーを含める  
  
##### <a name="to-include-a-new-folder-in-the-online-backup-policy"></a>オンライン バックアップ ポリシーに新しいフォルダーを含める  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ タスク**] ウィンドウで、をクリックして**オンライン バックアップの構成**します。  
  
4.  **変更または削除するバックアップ ポリシー** ] ページで [**オンライン バックアップ ポリシーをカスタマイズ**します。  
  
5.  **オンライン バックアップの構成**ページでは、追加するフォルダーが一覧に表示しない] をクリックして**フォルダーを追加**します。  
  
6.  **フォルダーを追加**ウィンドウを参照して、オンライン バックアップに含めるし、をクリックするフォルダーを選択して**OK**します。  
  
7.  **オンライン バックアップの構成**] ページで、をクリックし、必要に応じてその他のフォルダーを選択して**次**します。  
  
8.  オンライン バックアップ ポリシーのカスタマイズを完了するウィザードの指示に従います。  
  
 詳細についてはカスタマイズ可能なその他の設定についてを参照してください。[オンライン バックアップの構成](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)します。  
  
###  <a name="BKMK_10"></a>削除またはオンライン バックアップ ポリシーからファイル履歴のバックアップを除外します。  
  
##### <a name="to-remove-or-exclude-a-folder-from-the-online-backup-policy"></a>削除するか、オンライン バックアップ ポリシーからフォルダーを除外するには  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  をクリックして、**保護されているフォルダー** ] タブ。詳細ウィンドウには、オンライン バックアップの状態を含むフォルダーの一覧が表示されます。  
  
4.  オンライン バックアップ ポリシーから除外し、[タスク ウィンドウで、] をクリックするフォルダーを選択して**オンライン バックアップからフォルダーを削除する**します。  
  
###  <a name="BKMK_11"></a>無効にするか、またはオンライン サーバー バックアップを再度有効にします。  
 Azure Backup を使用して、バックアップまたはサーバーのデータを復元する方法については、次を参照してください。[このサーバーをバックアップ用の登録](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)します。  
  
 Azure Backup を使用してバックアップまたはサーバーのデータを復元するを停止する方法については、次を参照してください。[登録解除サーバー](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_6)します。  
  
###  <a name="BKMK_12"></a>進行中のオンライン サーバー バックアップを停止します。  
  
##### <a name="to-stop-an-online-server-backup-in-progress"></a>進行中のオンライン サーバー バックアップを停止するには  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  **オンライン バックアップ タスク**] ウィンドウで、をクリックして**バックアップを停止**します。  
  
     状態のバックアップを停止した後**Canceled**でバックアップに対して表示される、**バックアップ履歴**一覧します。  
  
###  <a name="BKMK_13"></a>オンライン バックアップ ステータスを表示  
  
##### <a name="to-view-the-backup-status"></a>バックアップの状態を表示するには  
  
1.  管理者としてダッシュ ボードにログオンします。  
  
2.  ナビゲーション バーをクリックして**オンライン バックアップ**します。  
  
3.  をクリックして、**バックアップ履歴**] タブ。リスト ビューには、各バックアップ ジョブの状態が表示されます。 そのジョブに関する追加の詳細を表示するバックアップ ジョブを選択します。  
  
###  <a name="BKMK_14"></a>表示およびオンライン バックアップのアラートの管理  
 その他の多くのアラートと同様に Azure Backup のアラートはアラート ビューアーに表示されます。  
  
##### <a name="to-view-online-backup-alerts-in-the-alert-viewer"></a>オンライン バックアップのアラートをアラート ビューアーに表示するには  
  
1.  ダッシュ ボードを開きます。  
  
2.  次のいずれかの操作を行います。  
  
      Windows Server Essentials: ナビゲーション ウィンドウで、アラート アイコンをクリックして \ (重大、警告、または Informational\ 場合があります)。 これは、アラート ビューアーを開きます。  
  
      Windows Server Essentials: で、**ホーム**] ページで [、**正常性の監視**] タブ。  
  
3.  Azure Backup に関連する問題のアラートの一覧を確認します。  
  
 アラート ビューアーまたは [正常性の監視] タブを使用してアラートを管理する方法の詳細については、次を参照してください。[Manage System Health](Manage-System-Health-in-Windows-Server-Essentials.md)します。  
  
###  <a name="BKMK_15"></a>オンライン バックアップを既定の設定にリセットします。  
 Windows Server Essentials では、オンライン バックアップの設定を構成するためのウィザードを提供します。 既定の設定を復元する場合は、実行、**オンライン バックアップの構成**タスク、および選択、**オンライン バックアップ ポリシーを削除する**オプションです。 を実行し、**オンライン バックアップの構成**タスクを再します。 以前アップロードしたデータは変更されません。  
  
###  <a name="BKMK_16"></a>Azure Backup サービスにサインアップします。  
 Microsoft Azure Backup と Windows Server Essentials を統合するための準備が、Microsoft Online Services アカウントを使用して、Azure 管理ポータルにログオンされ、Azure でオンライン バックアップを保存するバックアップ コンテナーを作成します。 Azure Backup 統合モジュールをダウンロードし、ダウンロードしたファイルを使用して Azure Backup は、Add-In を Windows Server Essentials サーバーにインストールされます。 Microsoft アカウントを持っていない場合は、無料試用版にサインアップすることができます。  
  
 このセットアップを実行するには、次のタスクを実行します。  
  
1.  Microsoft Online Services アカウントおよび Backup プレビュー版にサインアップします。  
  
2.  オンライン バックアップを保存するバックアップ コンテナーを作成します。  
  
3.  Azure Backup エージェントをダウンロードします。  
  
4.  Azure Backup は、Add-In サーバーをインストールします。  
  
####  <a name="BKMK_SignupforaMicrosoftOnlineServiceAccount"></a>Microsoft Online Services アカウントおよび Backup プレビュー版にサインアップします。  
  
1.  Windows Server Essentials ダッシュ ボードにログオンします。  
  
2.  ダッシュ ボードで**ホーム**] ページで [、**アドイン**カテゴリ、] をクリックして**Azure Backup との統合**、] をクリックし、**Azure Backup にサインアップする] をクリックします。**します。  
  
3.  Azure で**Recovery Services** ] ページで、**Backup (プレビュー)** ] セクションで詳細を確認します。  
  
4.  Azure サブスクリプションを持っていない場合はクリックして**無料試用版**、し、Azure サブスクリプションを取得するための手順に従います。  
  
     Azure サブスクリプションが既に、] をクリックして**ポータル**Azure 管理ポータルに移動する Web ページの右上隅にします。  
  
5.  Azure 管理ポータル] ページが表示されます**Recovery Services**左側のウィンドウでします。 S ll するが、バックアップを管理資格情報コンテナーそのストア オンライン バックアップから Windows Server Essentials します。  
  
####  <a name="BKMK_Createabackupvaulttostoreonlinebackups"></a>オンライン バックアップを保存するバックアップ コンテナーを作成します。  
  
1.  ログイン、[Azure 管理ポータル](https://manage.windowsazure.com)、Windows Server Essentials サーバー上の Web ブラウザーからです。  
  
2.  Azure 管理ポータルで、をクリックして**新規**、] をクリックして**データ サービス**、] をクリックして**Recovery Services**、] をクリックして**バックアップ資格情報コンテナー**、] をクリックし、**簡易作成**します。  
  
3.  バックアップ資格情報コンテナーの名前を入力し、クリックして、バックアップを保存する地域を選択**簡易作成**します。  
  
     **Recovery Services**領域が開き、新しいバックアップ コンテナーが表示されます。  
  
####  <a name="BKMK_DownloadtheWindowsAzureBackupAgent"></a>Azure Backup エージェントをダウンロードします。  
  
1.  Windows Server Essentials ダッシュ ボードを開きます。  
  
2.  ダッシュ ボードの**ホーム**] ページで [、**始める**タブをクリックし、**アドイン**カテゴリ、] をクリックして**Azure Backup との統合**、] をクリックし、**Azure Backup 統合モジュールをダウンロードする] をクリックします。**します。  
  
####  <a name="BKMK_InstalltheWindowsAzureBackupAddIn"></a>Azure Backup は、Add-In サーバーにインストールします。  
  
1.  管理者アカウントを使用して、サーバーにログインし、実行、**OnlineBackupAddin.wssx**前の手順でダウンロードしたファイルをします。  
  
2.  **ソフトウェア ライセンス条項**が表示されます。 諸条件に同意する場合はクリックして**Accept**インストールを続行します。  
  
3.  **アドインのインストール**] ページで [**アドインのインストール**します。  
  
    > [!NOTE]
    >  前提条件となるソフトウェアをインストールするために、サーバーを再起動する必要があります。  
  
     **インストール**ページが表示されます。 進行状況インジケーターは、インストールが開始し、インストールの進行状況が表示が表示されます。 インストールが完了したら、Azure Backup は、Add-in がインストールされたことが正常にメッセージが表示されます。  
  
4.  をクリックして**完了**します。  
  
5.  ダッシュ ボードを閉じてから。  
  
     新しいタブ、**オンライン バックアップ**、ダッシュ ボードに追加されます。 このタブから、サーバーの登録、バックアップの設定を構成して開く**Recovery Services**、サーバーのバックアップ資格情報コンテナーを管理する Azure 管理ポータルでします。  
  
 次の手順を完了した後、次の手順を実行します。  
  
1.  Windows Server Essentials では、オンライン バックアップに使用する証明書をアップロードします。 詳細については、次を参照してください。[Azure Backup コンテナーに証明書のアップロード](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)します。  
  
2.  Azure Backup コンテナーに、サーバーを登録します。 詳細については、次を参照してください。[このサーバーをバックアップ用の登録](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)します。  
  
3.  サーバーのオンライン バックアップを構成します。 詳細については、次を参照してください。[オンライン バックアップの構成](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)します。  
  
###  <a name="BKMK_17"></a>Azure Backup を Windows Server Essentials と統合します。  
 Microsoft Azure Backup 統合モジュールは、暗号化し、Microsoft によって提供される Azure でホストされる記憶域システムにサーバーからファイルとフォルダーをバックアップすることができます、Windows Server Essentials の新しい機能です。 Azure Backup を使用すると、サーバー上のデータのバックアップの暗号化と、重要なビジネス データが、火災、水害、盗難、またはその他の災害の致命的な損失を回避することができます。 Azure Backup を使用してサーバー データをバックアップするときに、インターネット上のセキュリティで保護されたデータ センターにアップロードされる前に、パスフレーズを使用して、情報が暗号化されます。 オンラインからデータにアクセスするには、バックアップする証明書で認証されているサーバーが必要し、パスフレーズを入力する必要があります。  
  
 統合すると、Azure Backup にサーバーを登録、定期的にスケジュールされたバックアップを実行するオンライン バックアップの設定を構成できます。 をクリックして、いつでもオンライン バックアップを開始することも、**バックアップを今すぐ開始**オンライン バックアップ ダッシュ ボードで作業します。  
  
 オンライン バックアップのセットアップには、次の手順が含まれます。  
  
1.  [Azure Backup サービスにサインアップ](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_16)サインアップした後 - Backup サービスでは、バックアップ コンテナーを作成、ダウンロードして Azure Backup 統合モジュールをインストールします。  
  
2.  [Azure Backup コンテナーに証明書のアップロードします。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)  
  
3.  [このサーバーをバックアップ用の登録します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)  
  
4.  [オンライン バックアップを構成します。](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)  
  
> [!NOTE]
>   Azure Backup は、オンライン バックアップでファイルとフォルダーを暗号化するパスフレーズを使用します。 暗号化パスフレーズを変更すると、サーバーを登録するときに指定したパスフレーズが置き換えられます。 パスフレーズは ASCII コード文字のみを受け入れます。  
  
###  <a name="BKMK_18"></a>Windows Server Essentials でのオンライン バックアップのフォルダーを保護します。  
 **保護されているフォルダー**サブセクションのダッシュ ボードの [オンライン バックアップ] セクションでは、サーバーですべての共有フォルダーの一覧を表示します。 次の表では、一覧に含まれている情報について説明します。  
  
|列|説明|  
|------------|-----------------|  
|**フォルダー名:**|オンライン バックアップに含まれているフォルダーの名前。<br /><br /> 追加またはフォルダーを除外する、実行、**オンライン バックアップの構成**タスクです。|  
|**フォルダーのパス:**|フォルダーの場所。|  
|**ステータス:**|次の 3 つの種類の状態がある**Protected**、**保護されていない**、および**不明な**します。|  
  
###  <a name="BKMK_19"></a>Windows Server Essentials のオンライン バックアップ履歴  
 **バックアップ履歴**サブセクションのダッシュ ボードの [オンライン バックアップ] セクションでは、最近のオンライン バックアップの一覧を表示します。 成功したバックアップを使用して、ファイルとフォルダーを復元することができます。 次の表では、一覧に含まれている情報について説明します。  
  
|列|説明|  
|------------|-----------------|  
|**操作:**|次の 2 つの種類の操作がある**バックアップ**と**復元**します。|  
|**時間:**|これは、最新の状態のログに記録時間です。|  
|**ステータス:**|5 種類の状態がある**成功**、**進行中の**、**Canceled**、**警告**、および**失敗しました**します。|  
  
## <a name="see-also"></a>参照してください。  
  
-   [バックアップの管理と復元](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)  
  
-   [Microsoft Online Services を管理します。](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials を管理します。](Manage-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials を使用します。](../use/Use-Windows-Server-Essentials.md)