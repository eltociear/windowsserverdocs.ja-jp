---
title: 機能の追加、削除、更新
description: System Insights を使用すると、既存のデータコレクションおよび管理機能を活用した新しい機能を作成できます。 また、これらの機能の追加、削除、および更新を管理するためのプラットフォームサポートも必要です。 このトピックでは、System Insights の機能を追加、削除、および更新するための高レベルの機能について説明します。
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 7/31/2018
ms.openlocfilehash: 0a760f25de79bc89b2aa67aec6bb1e3a493c1310
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856265"
---
# <a name="adding-removing-and-updating-capabilities"></a>機能の追加、削除、更新

>適用対象: Windows Server 2019

System Insights を使用すると、既存のデータコレクションおよび管理機能を活用した新しい機能を作成できます。 ただし、これらの機能を作成した後は、これらの機能の追加、削除、および更新を管理するためのプラットフォームをサポートすることも同様に重要です。 

このトピックでは、System Insights の機能を追加、削除、および更新するための高レベルの機能について説明します。 

## <a name="adding-a-capability"></a>機能の追加
System Insights では、 **InsightsCapability**コマンドレットを使用して、いつでも新しい機能を追加することができます。 **InsightsCapability**を使用するには、機能名と機能ライブラリを指定する必要があります。 機能ライブラリには、機能の説明、データソース、および予測ロジックが含まれています。

```PowerShell
Add-InsightsCapability -Name Sample capability -Library C:\SampleCapability.dll
```

システムインサイトに機能を追加した後は、PowerShell または Windows 管理センターを使用して、すぐに機能を起動して管理することができます。 

## <a name="updating-a-capability"></a>機能の更新
System Insights では、 **InsightsCapability**コマンドレットを使用して機能を更新することもできます。

```PowerShell
Update-InsightsCapability -Name Sample capability -Library C:\SampleCapabilityv2.dll
```

機能を更新すると、新しい機能ライブラリを指定できます。これにより、機能の説明、データソース、およびその機能に関連付けられている予測ロジックを変更できます。 重要な点として、機能を更新すると、その機能に関するすべての構成情報と履歴情報が保持されます。これには、カスタムスケジュール、アクション、および履歴の予測結果が含まれます。 

## <a name="removing-a-capability"></a>機能の削除
**InsightsCapability**コマンドレットを使用して、System Insights の機能を削除することもできます。 

```PowerShell
Remove-InsightsCapability -Name Sample capability 
```
>[!NOTE]
>既定の予測機能を削除することはできません。

機能を削除すると、その機能と関連付けられているすべての情報 (スケジュール、修復アクション、過去の予測結果など) が完全に削除されます。 

>[!TIP]
>機能に関連付けられているすべての情報を完全に削除する心配がある場合は、機能を削除するのではなく、無効にすることを検討してください。 

## <a name="see-also"></a>参照
System Insights の詳細については、次のリソースを参照してください。

- [System Insights の概要](overview.md)
- [機能について](understanding-capabilities.md)
- [管理機能](managing-capabilities.md)
- [機能の追加と開発](adding-and-developing-capabilities.md)
- [System Insights の FAQ](faq.md)