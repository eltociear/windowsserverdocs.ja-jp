---
title: title
description: '[タイトル] のリファレンストピック。コマンドプロンプトウィンドウのタイトルを作成します。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a94fe033bfd43d825c5beb7c915937bc4419b18f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721343"
---
# <a name="title"></a>title

コマンド プロンプト ウィンドウのタイトルを作成します。



## <a name="syntax"></a>構文

```
title [<String>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|[説明]|
|---------|-----------|
|\<文字列>|コマンド プロンプト ウィンドウのタイトルを指定します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>Remarks

-   バッチ プログラムのウィンドウのタイトルを作成するには、 **タイトル** バッチ ファイルの先頭にあるコマンドです。
-   ウィンドウのタイトルを設定した後のみを使用してリセットできます、 **タイトル** コマンドです。

## <a name="examples"></a>例

次のサンプルスクリプトでは、バッチファイルによって**copy**コマンドが実行されている間、コマンドプロンプトウィンドウのタイトルがファイルの更新に変更されます。 コマンドが実行されると、テキスト`Files Updated`が表示され、コマンドプロンプトウィンドウのタイトルがコマンドプロンプトに戻されます。
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)