---
title: chcp
description: アクティブなコンソールのコードページを変更する chcp コマンドのリファレンストピックです。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dc7b1c71-7b80-443d-9cf1-9bcf305aa1fd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0f1291176ed5245b06c68491f0d5cb0ae9b0b600
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82715329"
---
# <a name="chcp"></a>chcp

アクティブなコンソールのコードページを変更します。 パラメーターを指定せずに使用した場合、 **chcp**には、アクティブなコンソールコードページの数が表示されます。

## <a name="syntax"></a>構文

```
chcp [<nnn>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
| --------- | ----------- |
| `<nnn>` | コードページを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

次の表に、サポートされているコードページとその国/地域または言語を示します。

| コード ページ | 国/地域または言語 |
| --------- | -------------------------- |
| 437 | United States |
| 850 | 多言語 (ラテン I) |
| 852 | スラブ語 (ラテン II) |
| 855 | キリル語 (ロシア) |
| 857 | トルコ語 |
| 860 | Portuguese |
| 861 | アイスランド語 |
| 863 | カナダ-フランス語 |
| 865 | 北欧 |
| 866 | ロシア語 |
| 869 | モダンギリシャ語 |
| 936 | Chinese |

#### <a name="remarks"></a>Remarks

- Windows と共にインストールされる相手先ブランド供給 (OEM) コードページのみが、ラスターフォントを使用するコマンドプロンプトウィンドウに正しく表示されます。 他のコードページは、全画面表示モードまたは TrueType フォントを使用するコマンドプロンプトウィンドウで正しく表示されます。

- (MS-DOS のように) コードページを準備する必要はありません。

- 新しいコードページを割り当てた後に起動するプログラムでは、新しいコードページが使用されます。 ただし、新しいコードページを割り当てる前に開始したプログラム (Cmd.exe を除く) では、引き続き元のコードページが使用されます。

## <a name="examples"></a>例

アクティブなコードページの設定を表示するには、次のように入力します。

```
chcp
```

次のようなメッセージが表示されます。`Active code page: 437`

アクティブなコードページを 850 (多言語) に変更するには、次のように入力します。

```
chcp 850
```

指定したコードページが無効な場合は、次のエラーメッセージが表示されます。`Invalid code page`

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
