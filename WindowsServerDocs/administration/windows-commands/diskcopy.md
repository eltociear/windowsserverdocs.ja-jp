---
title: diskcopy
description: Diskcopy コマンドの参照トピック。コピー先ドライブのフォーマット済みまたは未フォーマットのフロッピーディスクに、ソースドライブのフロッピーディスクの内容をコピーします。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5fd21efa-52cc-4e70-a7fe-35125a435106
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/07/2018
ms.openlocfilehash: 99d1007a7c6f154b621e43d674d06f25b2911f00
ms.sourcegitcommit: aed942d11f1a361fc1d17553a4cf190a864d1268
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235184"
---
# <a name="diskcopy"></a>diskcopy

コピー元ドライブのフロッピーディスクの内容を、ドライブのフォーマット済みまたは未フォーマットのフロッピーディスクにコピーします。 パラメーターを指定せずに使用した場合、 **diskcopy**では、ソースディスクとターゲットディスクの現在のドライブが使用されます。

## <a name="syntax"></a>構文

```
diskcopy [<drive1>: [<drive2>:]] [/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<drive1>` | ソースディスクを含むドライブを指定します。 |
| /v | 情報が正しくコピーされていることを確認します。 このオプションを選択すると、コピー処理が遅くなります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>Remarks

- **Diskcopy**は、同じ種類である必要があるフロッピーディスクなどのリムーバブルディスクでのみ機能します。 ハードディスクでは、 **diskcopy**を使用できません。 *Drive1*または*drive2*のハードディスクドライブを指定すると、次のエラーメッセージ**が表示さ**れます。

    ```
    Invalid drive specification
    Specified drive does not exist or is nonremovable
    ```

    **Diskcopy**コマンドを実行すると、コピー元とコピー先のディスクを挿入するように求められ、続行する前にキーボードの任意のキーを押すようにします。

    ディスクのコピーが完了すると、次のメッセージ**が表示さ**れます。

    ```
    Copy another diskette (Y/N)?
    ```

    **Y**キーを押すと、次のコピー操作のためにソースディスクとターゲットディスクを挿入するよう**に求めるメッセージ**が表示されます。 **Diskcopy**プロセスを停止するには、 **N**キーを押します。

    ドライブ1のフォーマットされていないフロッピーディスクにコピーする場合、 **diskcopy** *を使用すると、ディスク*のサイドとセクターの数が同じに*なります*。 **Diskcopy**でディスクをフォーマットしてファイルをコピーするときに、次のメッセージが表示されます。

    ```
    Formatting while copying
    ```

- ソースディスクにボリュームシリアル番号がある場合、 **diskcopy**を実行すると、コピー先ディスクの新しいボリュームシリアル番号が作成され、コピー操作が完了したときの番号が表示されます。

- *Drive2*パラメーターを省略した場合、 **diskcopy**では現在のドライブが宛先ドライブとして使用されます。 両方のドライブパラメーターを省略した場合、 **diskcopy**では、両方に現在のドライブが使用されます。 現在のドライブが*drive1*と同じ場合は、必要に応じてディスクをスワップするよう**にメッセージが**表示されます。

- フロッピーディスクドライブ以外のドライブ (C ドライブなど) から、 **diskcopy**を実行します。 フロッピー*ディスクドライブ 1*とフロッピーディスク*drive2*が同じ場合は、ディスクの切り替え**を求めるメッセージが表示**されます。 使用可能なメモリよりも多くの情報がディスクに含まれている場合、 **diskcopy**ですべての情報を一度に読み取ることはできません。 ソースディスクから**の読み取り、** コピー先ディスクへの書き込み、ソースディスクの再挿入を求めるメッセージが表示されます。 このプロセスは、ディスク全体をコピーするまで続行されます。

- 断片化とは、ディスク上の既存のファイル間に未使用のディスク領域の小さな領域が存在することです。 フラグメント化されたソースディスクでは、ファイルの検索、読み取り、または書き込みの処理速度が低下する可能性があります。

    **Diskcopy**ではコピー元ディスクのコピーがコピー先ディスクにコピーされるため、ソースディスクの断片化は移行先ディスクに転送されます。 ディスク間での断片化の転送を回避するには、 [copy コマンド](copy.md)または[xcopy コマンド](xcopy.md)を使用してディスクをコピーします。 **コピー**と**xcopy**によってファイルが順次コピーされるため、新しいディスクは断片化されません。

    > [!NOTE]
    > **Xcopy**を使用して起動ディスクをコピーすることはできません。

- **diskcopy**終了コード:

    | 終了コード | 説明 |
    | --------- | ----------- |
    | 0 | コピー操作に成功しました |
    | 1 | 致命的でない読み取り/書き込みエラーが発生しました |
    | 3 | 致命的なハードエラーが発生しました |
    | 4 | 初期化エラーが発生しました |

    **によって**返される終了コードを処理するには、バッチプログラムの**if**コマンドラインで*ERRORLEVEL*環境変数を使用します。

## <a name="examples"></a>例

ドライブ B のディスクをドライブ A のディスクにコピーするには、次のように入力します。

```
diskcopy b: a:
```

フロッピーディスクドライブ A を使用してフロッピーディスクを別のフロッピーディスクにコピーするには、まず C ドライブに切り替えて、次のように入力します。

```
diskcopy a: a:
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [xcopy コマンド](xcopy.md)

- [copy コマンド](copy.md)
