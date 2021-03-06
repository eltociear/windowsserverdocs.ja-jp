---
title: rd
description: '* * * * のリファレンストピック'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 42e672f6-5bc2-4c16-af25-18e7ed2dd555
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cb169a44f9613b237af71321f9619d9ea93a6912
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722642"
---
# <a name="rd"></a>rd



ディレクトリを削除します。 このコマンドと同じ、 **rmdir** コマンドです。



## <a name="syntax"></a>構文

```
rd [<Drive>:]<Path> [/s [/q]]
rmdir [<Drive>:]<Path> [/s [/q]]
```

### <a name="parameters"></a>パラメーター

|     パラメーター     |                                                                 [説明]                                                                  |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| [\<ドライブ>:]<Path> |                      場所を削除するディレクトリの名前を指定します。 *パス* が必要です。                       |
|        /s         |                     (指定されたディレクトリとすべてのファイルを含むすべてのサブディレクトリ) は、ディレクトリ ツリーを削除します。                      |
|        /q         | クワイエット モードを指定します。 ディレクトリ ツリーを削除するときに、確認を表示しません。 (ことに注意 **/q** 場合にのみ、works **/s** が指定されている)。 |
|        /?         |                                                     コマンド プロンプトにヘルプを表示します。                                                     |

## <a name="remarks"></a>Remarks

-   含むファイルを格納するディレクトリを削除することはできません隠しファイルやシステム ファイルです。 これを行おうとすると、次のメッセージが表示されます。

    `The directory is not empty`

    **Dir/a**コマンドを使用して、すべてのファイル (隠しファイルおよびシステムファイルを含む) を一覧表示します。 使用して、 **attrib** コマンドに **-h** 隠しファイル属性を削除する **-s** システム ファイルの属性を削除するか、 **-h-s** 削除両方非表示にしてシステム ファイル属性。 非表示の後にファイルの属性が削除されていると、ファイルを削除することができます。
-   \) *パス*の先頭に円記号を挿入すると、(現在のディレクトリに関係なく) ルートディレクトリから*パス*が開始されます。
-   使用することはできません **rd** を現在のディレクトリを削除します。 現在のディレクトリを削除しようとすると、次のエラーメッセージが表示されます。

    `The process cannot access the file because it is being used by another process.`

    このエラーメッセージが表示された場合は、(現在のディレクトリのサブディレクトリではなく) 別のディレクトリに変更し、 **rd** (必要に応じて*パス*を指定) を使用する必要があります。
-   **Rd** コマンドで他のパラメーターは、回復コンソールから利用できます。

## <a name="examples"></a>例

現在作業中のディレクトリを削除することはできません。 現在のディレクトリ内にないディレクトリに変更する必要があります。 たとえば、親ディレクトリに変更する、次のように入力します。
```
cd ..
```
目的のディレクトリを安全に削除できます。

使用して、 **/s** ディレクトリ ツリーを削除するにはオプションです。 たとえば、ディレクトリを削除するには、テスト (すべてのサブディレクトリおよびファイル)、現在のディレクトリから、型を名前しました。
```
rd /s test
```
で非表示モードを、前の例を実行するには、次のように入力します。
```
rd /s /q test
```

> [!CAUTION]
> 実行すると **rd/s** quiet モードは、確認なしディレクトリ ツリー全体を削除します。 重要なファイルを移動または使用する前にバックアップすることを確認、 **/q** コマンド ライン オプションです。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)