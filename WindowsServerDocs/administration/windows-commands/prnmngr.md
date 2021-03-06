---
title: prnmngr
description: プリンターと接続を追加、削除、および一覧表示する方法について説明します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39eee1a8-4b41-4c9f-941e-486495135eb8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 0851e5c24d743a80b7edc611306df4f65338d95d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722824"
---
# <a name="prnmngr"></a>prnmngr

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

追加、削除、およびプリンターまたは設定し、既定のプリンターを表示するだけでなく、プリンター接続を一覧表示します。

## <a name="syntax"></a>構文
```
cscript Prnmngr {-a | -d | -x | -g | -t | -l | -?}[c] [-s <ServerName>] 
[-p <printerName>] [-m <printermodel>] [-r <PortName>] [-u <UserName>] 
[-w <Password>]
```

### <a name="parameters"></a>パラメーター

|           パラメーター           |                                                                                                                                                                                        [説明]                                                                                                                                                                                        |
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              -a               |                                                                                                                                                                             ローカルプリンター接続を追加します。                                                                                                                                                                              |
|              -d               |                                                                                                                                                                               プリンター接続を削除します。                                                                                                                                                                               |
|              -X               |                                                                                                               指定されたサーバーからすべてのプリンターを削除、 **-s**パラメーター。 サーバーを指定しない場合、Windows は、ローカル コンピューター上のすべてのプリンターを削除します。                                                                                                               |
|              -g               |                                                                                                                                                                               既定のプリンターが表示されます。                                                                                                                                                                               |
|              -t               |                                                                                                                                                        指定されているプリンタを通常使うプリンターを設定、 **-p** パラメーター。                                                                                                                                                         |
|              -l               |                                                                                                         **-s**パラメーターによって指定されたサーバーにインストールされているすべてのプリンターを一覧表示します。 サーバーを指定しない場合、Windows には、ローカル コンピューターにインストールされているプリンターが一覧表示します。                                                                                                         |
|               c               |                                                                                                                                      パラメーターは、プリンターの接続に適用されることを指定します。 使用できる、 **-a** と **-x** パラメーター。                                                                                                                                      |
|        -s<ServerName>        |                                                                                                                  管理するプリンターをホストするリモート コンピューターの名前を指定します。 コンピューターを指定しないと、ローカル コンピューターが使用されます。                                                                                                                  |
|       -p \<printerName>       |                                                                                                                                                                管理するプリンターの名前を指定します。                                                                                                                                                                 |
|     -m \<DrivermodelName>     |                                                                                                          インストールするドライバーを (名) を指定します。 ドライバーは、サポートするプリンターのモデルの名前は多くの場合です。 詳細については、プリンターのマニュアルを参照してください。                                                                                                           |
|        -r \<PortName>         |                                                                         プリンターが接続されているポートを指定します。 パラレル ポートまたはシリアル ポートの場合は、ポートの ID を使用して (たとえば、LPT1: や com1 など:)。 TCP/IP ポートである場合は、ポートを追加したときに指定したポート名を使用します。                                                                          |
| -u \<ユーザー名>- \<w パスワード> | 管理するプリンターをホストするコンピューターに接続するアクセス許可を持つアカウントを指定します。 ターゲット コンピューターのローカル Administrators グループのすべてのメンバーはこれらのアクセス許可を持っていますが、アクセス許可を他のユーザーに与えることもできます。 アカウントを指定しない場合は、コマンドを実行するこれらのアクセス許可を持つアカウントでログオンする必要があります。 |
|              /?               |                                                                                                                                                                           コマンド プロンプトにヘルプを表示します。                                                                                                                                                                            |

## <a name="remarks"></a>Remarks
-   **Prndrvr.vbs**コマンドは、%windir%\system32\ printing_Admin_Scripts\\ <language>ディレクトリにある Visual Basic スクリプトです。 このコマンドを使用するには、コマンドプロンプトで「 **cscript** 」と入力し、 **prnmngr**ファイルへの完全なパスを入力するか、ディレクトリを適切なフォルダーに変更します。 次に例を示します。
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnmngr
    ```
-   入力した情報にスペースが含まれている場合は、テキストを引用符で囲み`"computer Name"`ます (たとえば、)。

## <a name="examples"></a><a name="BKMK_examples"></a>例
ローカルコンピューター上の LPT1 に接続され、color printer Driver1 というプリンタードライバーを必要とする colorprinter_2 という名前のプリンターを追加するには、次のように入力します。
```
cscript prnmngr -a -p colorprinter_2 -m "color printer Driver1" -r lpt1:
```
HRServer という名前のリモートコンピューターから colorprinter_2 という名前のプリンターを削除するには、次のように入力します。
```
cscript prnmngr -d -s HRServer -p colorprinter_2 
```

## <a name="additional-references"></a>その他のリファレンス
- [コマンドライン構文キー](command-line-syntax-key.md)
[印刷コマンドのリファレンス](print-command-reference.md)
