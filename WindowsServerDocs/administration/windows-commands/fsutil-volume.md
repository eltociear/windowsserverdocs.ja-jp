---
title: fsutil volume
description: ボリュームのマウントを解除する、またはハードディスクドライブにクエリを実行して、ハードディスクドライブ上で現在使用可能な空き領域の容量、または特定のクラスターを使用しているファイルを確認するには、fsutil volume コマンドの参照トピック。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 0397c204-b3f8-4fd8-b71d-b7efb117766d
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 18671447664c47af48b4ca074aab823fd2b78625
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436837"
---
# <a name="fsutil-volume"></a>fsutil volume

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows 10、Windows Server 2012 R2、Windows 8.1、Windows Server 2012、Windows 8

ボリュームのマウントを解除するか、ハードディスクドライブに照会して、現在ハードディスクドライブで使用できる空き領域の大きさ、または特定のクラスターを使用しているファイルを特定します。

## <a name="syntax"></a>構文

```
fsutil volume [allocationreport] <volumepath>
fsutil volume [diskfree] <volumepath>
fsutil volume [dismount] <volumepath>
fsutil volume [filelayout] <volumepath> <fileID>
fsutil volume [list]
fsutil volume [querycluster] <volumepath> <cluster> [<cluster>] … …
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| 割り当てレポート | 特定のボリュームで記憶域がどのように使用されているかについての情報を表示します。 |
| `<volumepath>` | ドライブ文字を指定します (その後にコロンが続きます)。 |
| diskfree | ハードディスクドライブを照会して、空き領域の容量を確認します。 |
| マウントの解除 | ボリュームのマウントを解除します。 |
| filelayout | 指定されたファイルの NTFS メタデータを表示します。 |
| `<fileID>` | ファイル id を指定します。 |
| list | システム上のすべてのボリュームを一覧表示します。 |
| querycluster | 指定されたクラスターを使用しているファイルを検索します。 **Querycluster**パラメーターを使用して複数のクラスターを指定できます。 |
| `<cluster>` | 論理クラスター番号 (LCN) を指定します。 |

### <a name="examples"></a>例

割り当てられたクラスターレポートを表示するには、次のように入力します。

```
fsutil volume allocationreport C:
```

ドライブ C のボリュームのマウントを解除するには、次のように入力します。

```
fsutil volume dismount c:
```

ドライブ C のボリュームの空き領域の量を照会するには、次のように入力します。

```
fsutil volume diskfree c:
```

指定したファイルに関するすべての情報を表示するには、次のように入力します。

```
fsutil volume C: *
fsutil volume C:\Windows
fsutil volume C: 0x00040000000001bf
```

ディスク上のボリュームを一覧表示するには、次のように入力します。

```
fsutil volume list
```

論理クラスター番号50および0x2000 によって指定されたクラスターを使用しているファイルを検索するには、C ドライブに次のように入力します。

```
fsutil volume querycluster C: 50 0x2000
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [NTFS の動作](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781134(v=ws.10))
