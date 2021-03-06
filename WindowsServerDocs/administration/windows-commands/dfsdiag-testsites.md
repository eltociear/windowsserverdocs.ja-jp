---
title: dfsdiag testsites
description: Dfs diag testsites のリファレンストピック。名前空間サーバーまたはフォルダ (リンク) のターゲットとして機能するサーバーがすべてのドメインコントローラ上で同じサイトの関連付けを持つことを確認することで、active directory ドメインサービス (AD DS) サイトの構成を確認します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54eb7c7ec44d7cd4872960ca29cd3146b710f472
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992850"
---
# <a name="dfsdiag-testsites"></a>dfsdiag testsites

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

名前空間サーバーまたはフォルダー (リンク) のターゲットとして機能するサーバーがすべてのドメインコントローラー上で同じサイトの関連付けを持つことを確認して、active directory ドメインサービス (AD DS) サイトの構成を確認します。

## <a name="syntax"></a>構文

```
dfsdiag /testsites </machine:<server name>| /DFSpath:<namespace root or DFS folder> [/recurse]> [/full]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `/machine:<server name>` | サイトの関連付けを確認するサーバーの名前。 |
| `/DFSpath:<namespace root or DFS folder>` | サイトの関連付けを検証するターゲットを持つ名前空間のルートまたは分散ファイルシステム (DFS) フォルダー (リンク)。 |
| /recurse | 指定した名前空間のルートにあるすべてのフォルダーターゲットのサイトの関連付けを列挙し、検証します。 |
| /full | AD DS とサーバーのレジストリに同じサイトの関連付け情報が含まれていることを確認します。 |

## <a name="examples"></a>使用例

*Machine\MyServer*上のサイトの関連付けを確認するには、次のように入力します。

```
dfsdiag /testsites /machine:MyServer
```

分散ファイルシステム (DFS) フォルダーでサイトの関連付けを確認するには、AD DS とサーバーのレジストリに同じサイトの関連付け情報が含まれていることを確認するには、次のように入力します。

```
dfsdiag /TestSites /DFSpath:\\contoso.com\namespace1\folder1 /full
```

名前空間のルートでサイトの関連付けを確認するには、指定した名前空間のルートにあるすべてのフォルダーターゲットのサイトの関連付けを列挙して検証し、AD DS とサーバーのレジストリに同じサイトの関連付け情報が含まれていることを確認するには、次のように入力します。

```
dfsdiag /testsites /DFSpath:\\contoso.com\namespace2 /recurse /full
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [dfsdiag コマンド](dfsdiag.md)
