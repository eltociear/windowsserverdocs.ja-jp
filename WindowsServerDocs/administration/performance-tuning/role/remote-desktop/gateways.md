---
title: リモートデスクトップゲートウェイのパフォーマンスチューニング
description: リモートデスクトップゲートウェイのパフォーマンスチューニングに関する推奨事項
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: hammadbu; vladmis
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 3794b47e7226a905944495dd7c31f3196a33d0d5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851735"
---
# <a name="performance-tuning-remote-desktop-gateways"></a>リモートデスクトップゲートウェイのパフォーマンスチューニング

> [!NOTE]
> Windows 8 以降および Windows Server 2012 R2 以降では、リモートデスクトップゲートウェイ (RD ゲートウェイ) は TCP、UDP、およびレガシ RPC トランスポートをサポートしています。 次のデータのほとんどは、レガシ RPC トランスポートに関するものです。 レガシ RPC トランスポートが使用されていない場合、このセクションは適用されません。

このトピックでは、顧客のデプロイのパフォーマンスを向上させるためのパフォーマンス関連のパラメーターと、顧客のネットワーク使用パターンに依存するチューニングについて説明します。

主要な RD ゲートウェイは、リモートデスクトップ接続インスタンスと、顧客のネットワーク内の RD セッションホストサーバーインスタンスの間で、多数のパケット転送操作を実行します。

> [!NOTE]
> 次のパラメーターは、RPC トランスポートにのみ適用されます。

インターネットインフォメーションサービス (IIS) と RD ゲートウェイは、RD ゲートウェイのシステムパフォーマンスを向上させるために、次のレジストリパラメーターをエクスポートします。

**スレッドチューニング**

-   **Maxiothreads**

    ``` syntax
    HKLM\Software\Microsoft\Terminal Server Gateway\Maxiothreads (REG_DWORD)
    ```

    このアプリ固有のスレッドプールは、受信要求を処理するために RD ゲートウェイによって作成されるスレッドの数を指定します。 このレジストリ設定が存在する場合は、有効になります。 スレッド数は、論理プロセスの数と同じです。 論理プロセッサの数が5未満の場合、既定値は5スレッドになります。

-   **MaxPoolThreads**

    ``` syntax
    HKLM\System\CurrentControlSet\Services\InetInfo\Parameters\MaxPoolThreads (REG_DWORD)
    ```

    このパラメーターは、論理プロセッサごとに作成する IIS プールスレッドの数を指定します。 IIS プールのスレッドは、ネットワークで要求を監視し、すべての受信要求を処理します。 **Maxpoolthreads**カウントには RD ゲートウェイ使用するスレッドは含まれません。 既定値は 4 です。

**RD ゲートウェイのリモートプロシージャコールチューニング**

次のパラメーターを使用して、リモートデスクトップ接続および RD ゲートウェイコンピューターが受信するリモートプロシージャコール (RPC) を調整できます。 Windows を変更すると、各接続を介して送信されるデータの量を調整し、RPC over HTTP v2 のシナリオでパフォーマンスを向上させることができます。

-   **ServerReceiveWindow**

    ``` syntax
    HKLM\Software\Microsoft\Rpc\ServerReceiveWindow (REG_DWORD)
    ```

    既定値は 64 KB です。 この値は、サーバーが RPC プロキシから受信するデータに使用するウィンドウを指定します。 最小値は 8 KB に設定され、最大値は 1 GB に設定されます。 値が存在しない場合は、既定値が使用されます。 この値に変更が加えられると、変更を有効にするために IIS を再起動する必要があります。

-   **ServerReceiveWindow**

    ``` syntax
    HKLM\Software\Microsoft\Rpc\ServerReceiveWindow (REG_DWORD)
    ```

    既定値は 64 KB です。 この値は、クライアントが RPC プロキシから受信するデータに使用するウィンドウを指定します。 最小値は 8 KB、最大値は 1 GB です。 値が存在しない場合は、既定値が使用されます。

## <a name="monitoring-and-data-collection"></a>監視とデータ収集

次のパフォーマンスカウンターの一覧は、RD ゲートウェイのリソース使用率を監視するときに、カウンターの基本セットと見なされます。

-   \\ターミナルサービスゲートウェイ\\\*

-   \\RPC/HTTP プロキシ\\\*

-   サーバーごとに RPC/HTTP プロキシを \\\\\*

-   \\Web サービス\\\*

-   \\W3SVC\_w3wp.exe\\\*

-   \\IPv4\\\*

-   \\メモリ\\\*

-   \\ネットワークインターフェイス (\*)\\\*

-   \\プロセス (\*)\\\*

-   \\プロセッサ情報 (\*)\\\*

-   \\同期 (\*)\\\*

-   \\システム\\\*

-   \\TCPv4\\\*

次のパフォーマンスカウンターは、レガシ RPC トランスポートにのみ適用されます。

-   rpc/HTTP プロキシ\\の \\\* RPC

-   rpc/HTTP プロキシをサーバーごとに \\\\\* RPC

-   \\Web サービス\\\* RPC

-   \\W3SVC\_w3wp.exe\\\* RPC

> [!NOTE]
> 該当する場合は、\\IPv6\\\* および \\TCPv6\\\* オブジェクトを追加します。ReplaceThisText

