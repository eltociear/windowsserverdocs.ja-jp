---
title: fsutil resource
description: トランザクションリソースマネージャーとその動作を管理する fsutil resource コマンドのリファレンストピックです。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: b198d8ca-a5b7-430f-8911-5cbb9f50484c
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: b64dab3a0d0e772f067b0d3fa548692aad38a4c5
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83435737"
---
# <a name="fsutil-resource"></a>fsutil resource

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows 10、Windows Server 2012 R2、Windows 8.1、Windows Server 2012、Windows 8

セカンダリトランザクションリソースマネージャーを作成し、トランザクションリソースマネージャーを開始または停止します。または、トランザクションリソースマネージャーに関する情報を表示し、次の動作を変更します。

- 既定のトランザクションリソースマネージャーが、次回のマウント時にそのトランザクションメタデータをクリーンアップするかどうかを指定します。

- 可用性よりも一貫性を優先する、指定されたトランザクションリソースマネージャー。

- 整合性よりも可用性を優先する、指定されたトランザクションリソースマネージャー。

- 実行中のトランザクションリソースマネージャーの特性。

## <a name="syntax"></a>構文

```
fsutil resource [create] <rmrootpathname>
fsutil resource [info] <rmrootpathname>
fsutil resource [setautoreset] {true|false} <Defaultrmrootpathname>
fsutil resource [setavailable] <rmrootpathname>
fsutil resource [setconsistent] <rmrootpathname>
fsutil resource [setlog] [growth {<containers> containers|<percent> percent} <rmrootpathname>] [maxextents <containers> <rmrootpathname>] [minextents <containers> <rmrootpathname>] [mode {full|undo} <rmrootpathname>] [rename <rmrootpathname>] [shrink <percent> <rmrootpathname>] [size <containers> <rmrootpathname>]
fsutil resource [start] <rmrootpathname> [<rmlogpathname> <tmlogpathname>
fsutil resource [stop] <rmrootpathname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| create | セカンダリトランザクションリソースマネージャーを作成します。 |
| `<rmrootpathname>` | トランザクションリソースマネージャーのルートディレクトリへの完全パスを指定します。 |
| info | 指定されたトランザクションリソースマネージャーの情報を表示します。 |
| setautoreset | 既定のトランザクションリソースマネージャーが次のマウントでトランザクションメタデータをクリーンアップするかどうかを指定します。<ul><li>**true** -トランザクションリソースマネージャーが、既定で、次回のマウント時にトランザクションメタデータをクリーンアップすることを指定します。</li><li>**false** -既定では、トランザクションリソースマネージャーが次のマウントでトランザクションメタデータをクリーンアップしないことを指定します。 |
| `<defaultrmrootpathname>` | ドライブ名の後にコロンを付けて指定します。 |
| setavailable | トランザクションリソースマネージャーが整合性よりも可用性を優先することを指定します。 |
| setconsistent | トランザクションリソースマネージャーが可用性よりも一貫性を優先することを指定します。 |
| growth | 既に実行されているトランザクションリソースマネージャーの特性を変更します。 |
| 成長 | トランザクションリソースマネージャーのログを拡張できる量を指定します。<p>拡張パラメーターは次のように指定できます。<ul><li>形式を使用したコンテナーの数:`<containers> containers`</li><li>形式を使用したパーセンテージ。`<percent> percent`</li></ul> |
| `<containers>` | トランザクションリソースマネージャーによって使用されるデータオブジェクトを指定します。 |
| maxextent | 指定したトランザクションリソースマネージャーのコンテナーの最大数を指定します。 |
| minextent | 指定されたトランザクションリソースマネージャーのコンテナーの最小数を指定します。 |
| mode`{full|undo}` | すべてのトランザクションをログに記録するか (**完全**)、ロールバックされたイベントのみをログに記録するか (**元に戻す**) を指定します。 |
| rename | トランザクションリソースマネージャーの GUID を変更します。 |
| shrink | トランザクションリソースマネージャーのログを自動的に減らすことができる割合を指定します。 |
| size | 指定された*コンテナー*数として、トランザクションリソースマネージャーのサイズを指定します。 |
| start | 指定されたトランザクションリソースマネージャーを開始します。 |
| stop | 指定されたトランザクションリソースマネージャーを停止します。 |

### <a name="examples"></a>例

*C:\test*によって指定されたトランザクションリソースマネージャーのログを設定するには、次のように入力します。

```
fsutil resource setlog growth 5 containers c:test
```

*C:\test*によって指定されたトランザクションリソースマネージャーのログを設定するには、次のように入力します。

```
fsutil resource setlog growth 2 percent c:test
```

既定のトランザクションリソースマネージャーで、次にドライブ C にマウントするときにトランザクションメタデータをクリーンアップするように指定するには、次のように入力します。

```
fsutil resource setautoreset true c:\
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [トランザクション NTFS](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730726(v=ws.10))
