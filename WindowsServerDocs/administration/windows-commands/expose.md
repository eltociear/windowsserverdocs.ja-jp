---
title: さらす
description: '[公開] コマンドのリファレンストピック。ドライブ文字、共有、またはマウントポイントとして永続的なシャドウコピーを公開します。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d4e8ebf71f6ddcb457460f8174793586e81c73a6
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83437177"
---
# <a name="expose"></a>さらす

は、ドライブ文字、共有、またはマウントポイントとして、永続的なシャドウコピーを公開します。

## <a name="syntax"></a>構文

```
expose <shadowID> {<drive:> | <share> | <mountpoint>}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| shadowID | 公開するシャドウコピーのシャドウ ID を指定します。 *ShadowID*の代わりに、既存のエイリアスまたは環境変数を使用することもできます。 既存のエイリアスを表示するには、パラメーターを指定せずに**add**を使用します。 |
| `<drive:>` | 指定されたシャドウコピーをドライブ文字として公開します (たとえば、 `p:` )。 |
| `<share>` | 指定されたシャドウコピーを共有に公開します (たとえば、 `\\machinename` )。   |
| `<mountpoint>` | 指定されたシャドウコピーをマウントポイントに公開します (たとえば、 `C:\shadowcopy` )。 |

### <a name="examples"></a>例

VSS_SHADOW_1 環境変数に関連付けられている永続的なシャドウコピーをドライブ X として公開するには、次のように入力します。

```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [diskshadow コマンド](diskshadow.md)
