---
title: reg アンロード
description: Reg unload コマンドのリファレンストピック。 reg 読み込み操作を使用して読み込まれたレジストリのセクションを削除します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1d07791d-ca27-454e-9797-27d7e84c5048
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 029b9225f8a437be18c3056d97e153075d9df7c9
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722502"
---
# <a name="reg-unload"></a>reg アンロード



レジストリを使用して既に読み込まれているセクションを削除、 **reg ロード** 操作します。



## <a name="syntax"></a>構文

```
reg unload <KeyName>
```

### <a name="parameters"></a>パラメーター

|パラメーター|[説明]|
|---------|-----------|
|\<KeyName>|アンロードするサブキーの完全なパスを指定します。 リモートコンピューターを指定する場合は、コンピューター名を*KeyName*の\\ \\一部\)として ComputerName という形式で指定します。 ComputerName \\ \\\ を省略すると、操作は既定でローカルコンピューターに設定されます。 *KeyName* 有効なルート キーを含める必要があります。 ローカル コンピューターの有効なルート キーは、HKLM、HKCU、HKCR、HKU、および HKCC です。 リモート コンピューターが指定されている場合は、有効なルート キーは HKLM および HKU です。|
|/?|ヘルプを表示 **reg アンロード** コマンド プロンプト。|

## <a name="remarks"></a>Remarks

次の表に、戻り値の **reg アンロード** オプション。

|値|[説明]|
|-----|-----------|
|0|Success|
|1|障害|

## <a name="examples"></a>例

TempHive ファイル HKLM ハイブをアンロードするには、次のように入力します。
```
REG UNLOAD HKLM\TempHive
```

> [!CAUTION]
> 代替手段があるない場合は、直接、レジストリを編集しないでください。 レジストリエディターでは、標準のセーフガードがバイパスされるため、パフォーマンスを低下させたり、システムに損害を与えたり、Windows の再インストールが必要になることもあります。 ほとんどのレジストリ設定は、コントロールパネルまたは Microsoft 管理コンソール (MMC) のプログラムを使用して、安全に変更できます。 レジストリを直接編集する必要がある場合は、最初にバックアップします。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [reg load コマンド](reg-load.md)