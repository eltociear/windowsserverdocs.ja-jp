---
title: bootcfg ems
description: Bootcfg ems コマンドのリファレンストピック。これにより、ユーザーは、緊急管理サービスコンソールをリモートコンピューターにリダイレクトするための設定を追加または変更できます。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 57abdc50-c64a-45f1-8470-3f8c3a51f743
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c85231e094852feb673eb4f99b183f06014234b2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709520"
---
# <a name="bootcfg-ems"></a>bootcfg ems

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ユーザーが、緊急管理サービスコンソールをリモートコンピューターにリダイレクトするための設定を追加または変更できるようにします。 緊急管理サービスを有効にする`redirect=Port#`と、boot.ini ファイルの [ブートローダー] セクションに、指定したオペレーティングシステムのエントリ行に/リダイレクトオプションと共に行が追加されます。 緊急管理サービス機能は、サーバーでのみ有効になります。

## <a name="syntax"></a>構文

```
bootcfg /ems {on | off | edit}[/s <computer> [/u <domain>\<user> /p <password>]] [/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}] [/baud {9600 | 19200 | 38400 | 57600 | 115200}] [/id <osentrylinenum>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
| --------- | ----------- |
| `{on | off | edit}` | 次のような緊急管理サービスのリダイレクトの値を指定します。<ul><li>**代わっ.** 指定した`<osentrylinenum>`のリモート出力を有効にします。 また、指定<osentrylinenum>したに/リダイレクトオプションを追加`redirect=com<X>`し、[ブートローダー] セクションに設定を追加します。 の`com<X>`値は、 **/port**パラメーターによって設定されます。</li><li>**オート.** リモートコンピューターへの出力を無効にします。 また、指定<osentrylinenum>したおよび [ブートローダー] セクション`redirect=com<X>`からの設定に対して、/リダイレクトオプションを削除します。</li><li>**編集.** [ブートローダー] セクションの`redirect=com<X>`設定を変更することにより、ポート設定を変更できます。 の`com<X>`値は、 **/port**パラメーターによって設定されます。</li></ul> |
| `/s <computer>` | リモートコンピューターの名前または IP アドレスを指定します (円記号は使用しないでください)。 既定はローカル コンピュータです。 |
| `/u <domain>\<user>`  | または`<user>` `<domain>\<user>`によって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行します。 既定値は、コマンドを実行しているコンピューターの現在のログオンユーザーのアクセス許可です。 |
| `/p <password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| `/port {COM1 | COM2 | COM3 | COM4 | BIOSSET}` |  リダイレクトに使用する COM ポートを指定します。 BIOSSET パラメーターは、BIOS 設定を取得するように緊急管理サービスに指示し、リダイレクトに使用するポートを決定します。 リモートで管理されている出力が無効になっている場合は、このパラメーターを使用しないでください。 |
| `/baud {9600 | 19200 | 38400 | 57600 | 115200}` | リダイレクトに使用するボーレートを指定します。 リモートで管理されている出力が無効になっている場合は、このパラメーターを使用しないでください。 |
| `/id <osentrylinenum>` | Boot.ini ファイルの [オペレーティングシステム] セクションで、緊急管理サービスオプションが追加されるオペレーティングシステムエントリの行番号を指定します。 [オペレーティングシステム] セクションヘッダーの後の最初の行は1です。 このパラメーターは、緊急管理サービスの値が**オン**または**オフ**に設定されている場合に必要です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

**Bootcfg/ems**コマンドを使用するには、次のようにします。

```
bootcfg /ems on /port com1 /baud 19200 /id 2
bootcfg /ems on /port biosset /id 3
bootcfg /s srvmain /ems off /id 2
bootcfg /ems edit /port com2 /baud 115200
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /ems off /id 2
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bootcfg コマンド](bootcfg.md)
