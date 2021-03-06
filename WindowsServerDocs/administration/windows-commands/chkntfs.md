---
title: chkntfs
description: Chkntfs コマンドのリファレンストピック。コンピューターの起動時に自動ディスクチェックを表示または変更します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 93eca810-8699-4716-8e9d-aecd54f704be
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 69b8e21a7b43538b6296666d813f2b33daa8045f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82713658"
---
# <a name="chkntfs"></a>chkntfs

コンピューターの起動時に自動ディスクチェックを表示または変更します。 オプションを指定せずに使用する場合は、指定されたボリュームのファイルシステム**を表示し**ます。 自動ファイルチェックの実行がスケジュールされている場合、指定されたボリュームがダーティであるか、次回コンピューターを起動したときにチェックされるようにスケジュールされているかどうかが**chkntfs**によって表示されます。

> [!NOTE]
> **Chkntfs**を実行するには、Administrators グループのメンバーである必要があります。

## <a name="syntax"></a>構文

```
chkntfs <volume> [...]
chkntfs [/d]
chkntfs [/t[:<time>]]
chkntfs [/x <volume> [...]]
chkntfs [/c <volume> [...]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
| --------- | ----------- |
| `<volume>` [...] | コンピューターの起動時に確認する1つ以上のボリュームを指定します。 有効なボリュームには、ドライブ文字 (その後にコロンが続く)、マウントポイント、またはボリューム名が含まれます。 |
| /d | 自動ファイルチェックのカウントダウン時間を除く、 **chkntfs**の既定の設定をすべて復元します。 既定では、コンピューターの起動時にすべてのボリュームがチェックされ、ダーティであるボリュームで**chkdsk**が実行されます。 |
| /t [`:<time>`] | Autochk.exe 開始カウントダウン時間を、秒単位で指定された時間に変更します。 時刻を入力しない場合、 **/t**には現在のカウントダウン時間が表示されます。 |
| /x `<volume>` [...] | ボリュームが**chkdsk**を必要としているとマークされている場合でも、コンピューターの起動時のチェック対象から除外する1つ以上のボリュームを指定します。 |
| /c `<volume>` [...] | コンピューターが起動したときに1つ以上のボリュームがチェックされるようにスケジュールを設定し、ダーティであるボリュームで**chkdsk**を実行します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

ドライブ C のファイルシステムの種類を表示するには、次のように入力します。

```
chkntfs c:
```

> [!NOTE]
> 自動ファイルチェックの実行がスケジュールされている場合、ドライブがダーティであるか、次回コンピューターを起動したときにチェックされるように手動でスケジュールされているかどうかを示す追加の出力が表示されます。

Autochk.exe 開始のカウントダウン時間を表示するには、次のように入力します。

```
chkntfs /t
```

Autochk.exe 開始のカウントダウン時間を30秒に変更するには、次のように入力します。

```
chkntfs /t:30
```

> [!NOTE]
> Autochk.exe の開始のカウントダウン時間を0に設定することもできますが、これを行うと、時間のかかる可能性がある自動ファイルチェックをキャンセルできなくなります。

複数のボリュームがチェックされないようにするには、各ボリュームを1つのコマンドで列挙する必要があります。 たとえば、D ボリュームと E ボリュームの両方を除外するには、次のように入力します。

```
chkntfs /x d: e:
```

> [!IMPORTANT]
> **/X**コマンドラインオプションは、累積的ではありません。 複数回入力した場合、最新のエントリは前のエントリよりも優先されます。

D ボリュームで自動ファイルチェックをスケジュールするには、C または E ボリュームではなく、次のコマンドを順番に入力します。

```
chkntfs /d
chkntfs /x c: d: e:
chkntfs /c d:
```

> [!IMPORTANT]
> **/C**コマンドラインオプションは、累積的です。 **/C**を複数回入力した場合、各エントリはそのまま残ります。 特定のボリュームのみがチェックされるようにするには、既定の設定をリセットして、前のすべてのコマンドをクリアし、すべてのボリュームをチェックしないようにしてから、目的のボリュームで自動ファイルチェックをスケジュールします。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
