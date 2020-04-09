---
title: getmac
description: Windows コマンドに関するトピック * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a749a348-7cd1-4336-9f33-bb42dd0e31e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b593bf61bb08d2c1c7868b1bbb175ed64a8bcf7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842615"
---
# <a name="getmac"></a>getmac

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ローカルまたはネットワーク経由で、各コンピューターのすべてのネットワークカードの各アドレスに関連付けられている、メディアアクセス制御 (MAC) アドレスとネットワークプロトコルの一覧を返します。 
## <a name="syntax"></a>構文
```
getmac[.exe][/s <computer> [/u <Domain\<User> [/p <Password>]]][/fo {TABLE | list | CSV}][/nh][/v]
```
#### <a name="parameters"></a>パラメーター

|             パラメーター              |                                                                                          説明                                                                                          |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /s <computer>            |                                      名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定はローカル コンピュータです。                                       |
|        /u <Domain>\\<User>         | ユーザーまたは Domain\user によって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行します。 既定値は、コマンドを実行しているコンピューターの現在のログオンユーザーのアクセス許可です。 |
|           /p <Password>            |                                                     指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。                                                     |
| /fo {テーブル&#124;一覧&#124;の CSV} |                       クエリ出力に使用する形式を指定します。 有効な値は、 **TABLE**、 **List**、および**CSV**です。 出力の既定の形式は**TABLE**です。                        |
|                /nh                 |                                             出力に列ヘッダーを表示しません。 **/Fo**パラメーターが**TABLE**または**CSV**に設定されている場合に有効です。                                              |
|                 /v                 |                                                                    出力に詳細情報を表示するように指定します。                                                                     |
|                 /?                 |                                                                                                                                                                                               |

## <a name="remarks"></a>コメント
**getmac**は、MAC アドレスをネットワークアナライザーに入力する場合や、コンピューターの各ネットワークアダプターで現在使用されているプロトコルを知る必要がある場合に役立ちます。
## <a name="examples"></a><a name=BKMK_Examples></a>例
次の例は、 **getmac**コマンドを使用する方法を示しています。
```
getmac /fo table /nh /v
```
```
getmac /s srvmain
```
```
getmac /s srvmain /u maindom\hiropln
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo list /v
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo table /nh
```
## <a name="additional-references"></a>その他の参照情報
-   - [コマンド ライン構文の記号](command-line-syntax-key.md)
