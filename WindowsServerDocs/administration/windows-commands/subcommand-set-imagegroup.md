---
title: サブコマンドセット-ImageGroup
description: イメージグループの属性を変更するサブコマンド set ImageGroup のリファレンストピックです。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 429a8fee5b0236d264eb421f110219a1bc037368
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721697"
---
# <a name="subcommand-set-imagegroup"></a>サブコマンド: セット ImageGroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージグループの属性を変更します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Set-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|[説明]|
|-------|--------|
mediaGroup:<Image group name>|イメージグループの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 指定しない場合、ローカル サーバーが使用されます。|
|[/Name:<New image group name>]|イメージグループの新しい名前を指定します。|
|[セキュリティ:<SDDL>]|セキュリティ記述子定義言語 (SDDL) 形式で、イメージグループの新しいセキュリティ記述子を指定します。|
## <a name="examples"></a>例
イメージグループの名前を設定するには、次のように入力します。
```
wdsutil /Set-ImageGroumediaGroup:ImageGroup1 /Name:New Image Group Name
```
イメージグループのさまざまな設定を指定するには、次のように入力します。
```
wdsutil /verbose /Set-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /Name:New Image Group Name 
/Security:O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンドライン構文のキー](command-line-syntax-key.md)
[追加 imagegroup コマンド](using-the-add-imagegroup-command.md)
を使用して[get allimagegroups コマンド](using-the-get-allimagegroups-command.md)
を使用して[get imagegroup](using-the-get-imagegroup-command.md)
コマンドを使用して[削除 imagegroup](using-the-remove-imagegroup-command.md)コマンド
