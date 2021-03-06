---
title: bitsadmin getnotifycmdline
description: Bitsadmin getnotifycmdline コマンドのリファレンストピックでは、ジョブがデータの転送を終了したときに実行されるコマンドラインコマンドを取得します。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90fa33e6-aca5-4a23-82bd-19a9f13f8416
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d4c47c4a1b9ea06fd804c8f2c48e9ac0ce1b319
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717799"
---
# <a name="bitsadmin-getnotifycmdline"></a>bitsadmin getnotifycmdline

指定されたジョブがデータの転送を終了した後に実行するコマンドラインコマンドを取得します。

> [!NOTE]
> このコマンドは、BITS 1.2 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /getnotifycmdline <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブが完了したときにサービスによって使用されるコマンドラインコマンドを取得すること。

```
bitsadmin /getnotifycmdline myDownloadJob
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
