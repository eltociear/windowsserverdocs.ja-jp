---
title: ksetup addkpasswd
description: Ksetup addkpasswd コマンドのリファレンストピックです。これにより、領域の Kerberos パスワード (kpasswd) サーバーアドレスが追加されます。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3196995-1b38-48ff-ba08-911cfab77317
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e0cff2f3d74e6d862bbdd000602a1d03312373d2
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818072"
---
# <a name="ksetup-addkpasswd"></a>ksetup addkpasswd

領域の Kerberos パスワード (kpasswd) サーバーアドレスを追加します。

## <a name="syntax"></a>構文

```
ksetup /addkpasswd <realmname> [<kpasswdname>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<realmname>` | CORP など、大文字の DNS 名を指定します。CONTOSO.COM は、 **ksetup**の実行時に既定の領域または**領域 =** として表示されます。 |
| `<kpasswdname>` | Kerberos パスワードサーバーを指定します。 大文字と小文字を区別しない、完全修飾ドメイン名 (mitkdc.contoso.com など) として記述されています。 KDC 名を省略した場合、DNS を使用して Kdc を見つけることができます。 |

#### <a name="remarks"></a>注釈

- ワークステーションで認証される kerberos 領域が Kerberos 変更パスワードプロトコルをサポートしている場合は、Windows オペレーティングシステムを実行しているクライアントコンピューターで Kerberos パスワードサーバーを使用するように構成できます。

- KDC 名は、一度に1つずつ追加できます。

### <a name="examples"></a>例

CORP を構成します。CONTOSO.COM realm Windows 以外の KDC サーバーを使用する場合は、パスワードサーバーとして、次のように入力します。

```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```

KDC 名が設定されていることを確認するには、「」と入力して `ksetup` 出力を表示し、 **kpasswd =** というテキストを探します。 テキストが表示されない場合は、マッピングが構成されていないことを意味します。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup delkpasswd コマンド](ksetup-delkpasswd.md)
