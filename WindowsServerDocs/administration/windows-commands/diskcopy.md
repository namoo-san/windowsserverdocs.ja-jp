---
title: diskcopy
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fd21efa-52cc-4e70-a7fe-35125a435106
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/07/2018
ms.openlocfilehash: 553a85ac4fd9b7708d7adc668be4e000b36a9346
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377820"
---
# <a name="diskcopy"></a>diskcopy



コピー元ドライブのフロッピーディスクの内容を、ドライブのフォーマット済みまたは未フォーマットのフロッピーディスクにコピーします。 パラメーターを指定せずに使用した場合、 **diskcopy**では、ソースディスクとターゲットディスクの現在のドライブが使用されます。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

> [!NOTE]
> このコマンドは、Windows 10 には含まれていません。

## <a name="syntax"></a>構文

```
diskcopy [<Drive1>: [<Drive2>:]] [/v]
```

## <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|\<ドライブ 1 >|ソースディスクを含むドライブを指定します。|
|\<ドライブ 2 >|宛先ディスクを含むドライブを指定します。|
|/v|情報が正しくコピーされていることを確認します。 このオプションを選択すると、コピー処理が遅くなります。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>コメント

-   ディスクの使用

    **Diskcopy**は、同じ種類である必要があるフロッピーディスクなどのリムーバブルディスクでのみ機能します。 ハードディスクでは、 **diskcopy**を使用できません。 *Drive1*または*Drive2*のハードディスクドライブを指定すると、次のエラーメッセージ**が表示さ**れます。  
    ```
    Invalid drive specification
    Specified drive does not exist or is nonremovable
    ```  
    **Diskcopy**コマンドを実行すると、コピー元とコピー先のディスクを挿入するように求められ、続行する前にキーボードの任意のキーを押すようにします。

    ディスクのコピーが完了すると、次のメッセージ**が表示さ**れます。  
    ```
    Copy another diskette (Y/N)?
    ```  
    Y キーを押すと、次のコピー操作のためにソースディスクとターゲットディスクを挿入するよう**に求めるメッセージ**が表示されます。 **Diskcopy**プロセスを停止するには、 **N**キーを押します。

    ブートドライブのフォーマットされていないフロッピーディスクにコピーする場合、 **diskcopy**で*は、ドライブ*1 のディスクにあるトラックあたりのサイド数とセクター数が同じであることを確認し*ます。* **Diskcopy**でディスクをフォーマットしてファイルをコピーするときに、次のメッセージが表示されます。  
    ```
    Formatting while copying
    ```  
-   ディスクのシリアル番号

    ソースディスクにボリュームシリアル番号がある場合、 **diskcopy**を実行すると、コピー先ディスクの新しいボリュームシリアル番号が作成され、コピー操作が完了したときの番号が表示されます。
-   ドライブパラメーターの省略

    *Drive2*パラメーターを省略した場合、 **diskcopy**では現在のドライブが宛先ドライブとして使用されます。 両方のドライブパラメーターを省略した場合、 **diskcopy**では、両方に現在のドライブが使用されます。 現在のドライブが*Drive1*と同じ場合は、必要に応じてディスクをスワップするよう**にメッセージが**表示されます。
-   コピーに1つのドライブを使用する

    フロッピーディスクドライブ以外のドライブ (C ドライブなど) から、 **diskcopy**を実行します。 フロッピー*ディスクドライブ 1*とフロッピーディスク*Drive2*が同じ場合は、ディスクの切り替え**を求めるメッセージが表示**されます。 使用可能なメモリよりも多くの情報がディスクに含まれている場合、 **diskcopy**ですべての情報を一度に読み取ることはできません。 ソースディスクから**の読み取り、** コピー先ディスクへの書き込み、ソースディスクの再挿入を求めるメッセージが表示されます。 このプロセスは、ディスク全体をコピーするまで続行されます。
-   ディスクの断片化の回避

    断片化とは、ディスク上の既存のファイル間に未使用のディスク領域の小さな領域が存在することです。 フラグメント化されたソースディスクでは、ファイルの検索、読み取り、または書き込みの処理速度が低下する可能性があります。

    **Diskcopy**ではコピー元ディスクのコピーがコピー先ディスクにコピーされるため、ソースディスクの断片化は移行先ディスクに転送されます。 ディスク間での断片化の転送を回避するには、 **copy**または**xcopy**を使用してディスクをコピーします。 **コピー**と**xcopy**によってファイルが順次コピーされるため、新しいディスクは断片化されません。

> [!NOTE]
> **Xcopy**を使用して起動ディスクをコピーすることはできません。
> -   **Diskcopy**終了コードについて

    The following table explains each exit code.  
    |終了コード|説明|
    |---------|-----------|
    |0|コピー操作に成功しました|
    |1|致命的でない読み取り/書き込みエラーが発生しました|
    |3|致命的なハードエラーが発生しました|
    |4|初期化エラーが発生しました|

    To process the exit codes that are returned by **diskcomp**, you can use the *ERRORLEVEL* environment variable on the **if** command line in a batch program.

## <a name="BKMK_examples"></a>例

ドライブ B のディスクをドライブ A のディスクにコピーするには、次のように入力します。
```
diskcopy b: a:
```
フロッピーディスクドライブ A を使用してフロッピーディスクを別のフロッピーディスクにコピーするには、まず C ドライブに切り替えて、次のように入力します。

diskcopy a:

#### <a name="additional-references"></a>その他の参照情報

[コマンド ライン構文の記号](command-line-syntax-key.md)