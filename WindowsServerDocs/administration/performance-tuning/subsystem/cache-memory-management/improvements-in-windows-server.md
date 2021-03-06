---
title: キャッシュとメモリマネージャーの機能強化
description: Windows Server 2016 でのキャッシュとメモリマネージャーの機能強化
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: pavel; atales
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: ef3658ab0f035435f6140c1dfa585de78537d37a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851645"
---
# <a name="cache-and-memory-manager-improvements"></a>キャッシュとメモリマネージャーの機能強化

このトピックでは、Windows Server 2012 および2016でのキャッシュマネージャーとメモリマネージャーの機能強化について説明します。

## <a name="cache-manager-improvements-in-windows-server-2016"></a>Windows Server 2016 でのキャッシュマネージャーの機能強化
キャッシュマネージャーでは、真の非同期キャッシュ読み取りのサポートも追加されました。
これにより、非同期のキャッシュされた読み取りに大きく依存しているアプリケーションのパフォーマンスが向上する可能性があります。  ほとんどのインボックスのファイルシステムでは、非同期キャッシュの読み取りがサポートされていますが、多くの場合、スレッドプールとファイルシステムの内部作業キューの処理に関連するさまざまな設計の選択により、パフォーマンスが制限されていました。  カーネルが適切にサポートされるようになったため、Cache Manager では、ファイルシステムからのスレッドプールとワークキュー管理の複雑さがすべて非表示になり、非同期的にキャッシュされた読み取りを処理しやすくなりました。キャッシュマネージャーには、並列処理を最大化するために (システムでサポートされる最大値) の VHD 入れ子レベルに対して、1つのコントロール datastructures があります。


## <a name="cache-manager-improvements-in-windows-server-2012"></a>Windows Server 2012 でのキャッシュマネージャーの機能強化
シーケンシャルなワークロードの先読みロジックに対するキャッシュマネージャーの機能強化に加えて、新しい API [CcSetReadAheadGranularityEx](https://msdn.microsoft.com/library/windows/hardware/hh406341.aspx)が追加されました。 SMB などのファイルシステムドライバーは、先読みパラメーターを変更できます。 これにより、1つの大規模な先行読み取り要求を送信する代わりに、複数の小さなサイズの先行読み取り要求を送信することで、リモートファイルのシナリオのスループットを向上させることができます。 ファイルシステムドライバーなどのカーネルコンポーネントのみが、ファイルごとにこれらの値をプログラムで構成できます。

## <a name="memory-manager-improvements-in-windows-server-2012"></a>Windows Server 2012 でのメモリマネージャーの機能強化
ページの組み合わせを有効にすると、同じ内容のページがプライベートでページが多数存在するサーバーのメモリ使用量を減らすことができます。 たとえば、同じメモリを集中的に使用するアプリの複数のインスタンスを実行しているサーバーや、非常に反復的なデータを扱う1つのアプリの場合は、ページを結合することをお勧めします。 ページの結合を有効にすることの欠点は、CPU の使用率が高くなることです。

次に、ページの結合によって多くのメリットが得られないサーバーの役割の例をいくつか示します。

-   ファイルサーバー (ほとんどのメモリは、プライベートではなく、そのために組み合わせ可能ではないファイルページによって消費されます)

-   AWE または大規模なページを使用するように構成されている Microsoft SQL Server (ほとんどのメモリはプライベートであり、ページング不可能)

ページの結合は既定で無効になっていますが、 [Enable-MMAgent](https://technet.microsoft.com/library/jj658954.aspx) Windows PowerShell コマンドレットを使用して有効にすることができます。 ページの結合が Windows Server 2012 で追加されました。
