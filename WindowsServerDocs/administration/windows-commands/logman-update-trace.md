---
title: logman update trace
description: 'Windows コマンド」のトピック * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7111f7f-4162-4d1a-8e53-d766db0ede1f britw
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 30fe475fb6a8442558493dcd5a91ecb8fcee2de3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826433"
---
# <a name="logman-update-trace"></a>logman update trace

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

既存のイベント トレース データ コレクターのプロパティを更新します。  
  
## <a name="syntax"></a>構文  
```  
logman update trace <[-n] <name>> [options]  
```  
## <a name="parameters"></a>パラメーター  
|パラメーター|説明|  
|-------|--------|  
|/?|ヘルプ コンテキストを表示します。|  
|-s <computer name>|指定したリモート コンピューター上のコマンドを実行します。|  
|-config <value>|コマンド オプションを含む設定ファイルを指定します。|  
|-ets|イベント トレース セッションを保存したり、スケジュール設定なしで直接コマンドを送信します。|  
|[-n] <name>|ターゲット オブジェクトの名前。|  
|-f <bin&#124;bincirc&#124;csv&#124;tsv&#124;sql>|データ コレクターのログの形式を指定します。|  
|-[-] u < ユーザー [password] >|実行するユーザーを指定します。 入力、* のパスワードがパスワードのプロンプトが生成されます。 パスワード プロンプトで入力すると、パスワードは表示されません。|  
|-m <[start] [stop] [[start] [stop] [...]]>|変更を手動で開始またはスケジュールされた begin または end の時間ではなく停止します。|  
|-rf < [hh:] mm:] ss >|指定した期間には、データ コレクターを実行します。|  
|-b < m/d/yyyy h:mm:ss [AM&#124;PM] >|指定した時刻のデータの収集を開始します。|  
|-e < m/d/yyyy h:mm:ss [AM&#124;PM] >|指定した時間にデータ収集を終了します。|  
|-o <path&#124;dsn!log>|出力ログ ファイルまたは DSN とログは、SQL database の名を設定を指定します。|  
|-[-] r|指定した開始と終了時刻に毎日データ コレクターを繰り返します。|  
|-[-]、|既存のログ ファイルに追加します。|  
|-[-] ow|既存のログ ファイルを上書きします。|  
|-[-] v < ウズベキスタン&#124;指定されない >|ファイルのバージョン管理情報をログ ファイル名の末尾にアタッチします。|  
|-[-] rc <task>|指定されたコマンドを実行するたびに、ログは閉じられます。|  
|-[-] の最大数 <value>|最大ログ ファイルのサイズは、mb 単位または SQL ログ レコードの最大数。|  
|-[-] cnf < [hh:] mm:] ss >|時間を指定すると、指定した時間が経過すると、新しいファイルを作成します。 時間が指定されていない場合は、最大サイズを超えたときに新しいファイルを作成します。|  
|-y|メッセージを表示せず、すべての質問に [はい] 回答します。|  
|-ct <perf&#124;system&#124;cycle>|イベント トレース セッションのクロックの型を指定します。|  
|-ln <logger_name>|イベント トレース セッションのロガー名を指定します。|  
|-ft < [hh:] mm:] ss >|イベント トレース セッションのフラッシュ タイマーを指定します。|  
|-[-] p < プロバイダー [flags [レベル] >|有効にする 1 つのイベント トレース プロバイダーを指定します。|  
|-pf <filename>|有効にする複数のイベント トレース プロバイダーの一覧を含むファイルを指定します。 ファイルは、1 行につき 1 つのプロバイダーを含むテキスト ファイルである必要があります。|  
|-[-] rt|リアルタイム モードでは、イベント トレース セッションを実行します。|  
|-[-] ul|ユーザー モードでは、イベント トレース セッションを実行します。|  
|-bs <value>|イベント トレース セッション バッファー サイズを指定します (kb 単位)。|  
|-nb <min max>|イベント トレース セッション バッファーの数を指定します。|  
|-mode <globalsequence&#124;localsequence&#124;pagedmemory>|イベント トレース セッションのロガー モードを指定します。<br /><br />**Globalsequence**イベント トレースがトレースに関係なく、セッションは、イベントを受信した受信イベントはすべてシーケンス番号を追加することを指定します。<br /><br />**Localsequence**イベント トレースが特定のトレース セッションで受信したイベントのシーケンス番号を追加することを指定します。 ときに、 **localsequence**オプションを使用すると、シーケンス番号の重複は、すべてのセッションで存在できますが、各トレース セッション内で一意になります。<br /><br />**Pagedmemory**イベント トレースがその内部バッファーの割り当てのため、既定の非ページ メモリ プールではなく、ページングされたメモリを使用することを指定します。|  
## <a name="remarks"></a>注釈  
[-] がリスト表示と、余分なオプションを無効にします。  
## <a name="BKMK_examples"></a>例  
次のコマンドは、既存のデータ コレクター perf_log、ログの最大サイズを 10 MB に変更する、CSV へのログ ファイルの形式を更新および形式指定されないでファイルのバージョン管理の追加を更新します。  
```  
logman update perf_log -max 10 -f csv -v mmddhhmm  
```  
#### <a name="additional-references"></a>その他の参照  
[logman](logman.md)  
[logman トレースを作成します。](logman-create-trace.md)  