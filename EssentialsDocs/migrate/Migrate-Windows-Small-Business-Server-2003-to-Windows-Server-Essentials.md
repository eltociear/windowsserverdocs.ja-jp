---
title: Windows Small Business Server 2003 から Windows Server Essentials への移行
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 119a7fbc-2c76-4aa3-8a7f-c7073d461b5b
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f7dfa203f999e23b52c8fcf1f861a59f4f399d95
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852525"
---
# <a name="migrate-windows-small-business-server-2003-to-windows-server-essentials"></a>Windows Small Business Server 2003 から Windows Server Essentials への移行

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

このガイドでは、既存の Windows SBS 2003 ドメインを新しいハードウェア上の Windows Server&reg; 2012 Essentials に移行してから、設定とデータを移行する方法について説明します。 このガイドでは、移行の完了後に Windows Server Essentials ネットワークから既存のサーバーを削除する方法についても説明します。  
  
> [!IMPORTANT]
>   Windows Server Essentials には64ビット環境が必要です。  Windows Server Essentials では、32ビット環境はサポートされていません。  
> 
> [!NOTE]
>  移行中の問題を回避するために、Windows Server Essentials 製品開発チームでは、移行を開始する前にこのドキュメントを読むことを強くお勧めします。  
> 
> [!NOTE]
> 
>  サーバーデータを最新バージョンの Windows Server Essentials に移行する方法については、「 [Windows Server essentials への移行](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)」を参照してください。  
> 
>  サーバーデータを最新バージョンの Windows Server Essentials に移行する方法については、「 [Windows Server essentials への移行](../migrate/Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)」を参照してください。  

  
## <a name="additional-resources"></a>その他のリソース  
 移行プロセスを実行するために役立つその他の情報、ツール、およびコミュニティリソースへのリンクについては、「 [Windows Small Business Server の移行](https://go.microsoft.com/fwlink/?LinkId=217520)」 web サイトを参照してください。  
  
## <a name="terms-and-definitions"></a>用語と定義  
 **移行元サーバー:** 設定とデータの移行元の既存のサーバー。  
  
 **移行先サーバー:** 設定とデータの移行先となる新しいサーバー。  
  
## <a name="migration-process-summary"></a>移行プロセスの概要  
 この移行ガイドには次の手順が含まれます。  
  

1.  [Windows Server Essentials への移行のために移行元サーバーを準備](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md)します。  移行元サーバーおよびネットワークが、移行できる状態になっていることを確認する必要があります。 ここでは、移行元サーバーのバックアップ、移行元サーバーのシステム正常性の評価、最新のサービス パックと修正プログラムのインストール、およびネットワーク構成の確認について詳しく説明します。  
  
2.  [Windows Server Essentials を移行モードでインストール](Install-Windows-Server-Essentials-in-migration-mode.md)します。  ここでは、移行先サーバーに Windows Server Essentials を移行モードでインストールするために実行する手順について説明します。  
  
3.  [新しい Windows Server Essentials ネットワークにコンピューターを参加](Join-computers-to-the-new-Windows-Server-Essentials-network.md)させます。  このセクションでは、クライアントコンピューターを新しい Windows Server Essentials ネットワークに参加させ、グループポリシーの設定を更新する方法について説明します。  
  
4.  [SBS 2003 の設定とデータを移行先サーバーに移動](Move-Windows-SBS-2003-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md)します。  ここでは、移行元サーバーからのデータと設定の移行について説明します。  
  
5.  [Windows Server Essentials の移行先サーバーでフォルダーリダイレクトを有効に](Enable-folder-redirection-on-the-Windows-Server-Essentials-Destination-Server.md)します。  移行元サーバーでフォルダー リダイレクトが有効になっている場合は、移行先サーバーでフォルダー リダイレクトを有効にしてから、以前のフォルダー リダイレクト グループ ポリシー設定を削除できます。  
  
6.  [新しい Windows Server Essentials ネットワークから移行元サーバーを降格し、削除](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md)します。  移行元サーバーをネットワークから削除する前に、グループ ポリシーの更新を強制し、移行元サーバーを降格する必要があります。  
  
7.  [Windows Server Essentials への移行のために移行後のタスクを実行](Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md)します。  すべての設定とデータを Windows Server Essentials に移行したら、許可されたコンピューターをユーザーアカウントにマップすることができます。  
  
8.  [Windows Server Essentials ベストプラクティスアナライザーを実行](Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md)します。  Windows Server Essentials への設定とデータの移行が完了したら、Windows Server Essentials BPA をダウンロードして実行する必要があります。   

  
 いくつかの移行手順では、管理者としてコマンド プロンプト ウィンドウを開く必要があります。  
  
###  <a name="to-open-a-command-prompt-window-on-the-source-server-as-an-administrator"></a><a name="BKMK_OpenACommandPromptAsAdmin"></a>移行元サーバーで管理者としてコマンドプロンプトウィンドウを開くには  
  
1.  [スタート] をクリックします。  
  
2.  検索ボックスに「cmd」と入力します。  
  
3.  結果一覧で [cmd] を右クリックし、[管理者として実行] をクリックします。  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>移行先サーバーで管理者としてコマンド プロンプト ウィンドウを開くには  
  
1.  **[スタート]** 画面で、検索ボックスに「**cmd**」と入力します。  
  
2.  結果一覧で **[cmd]** を右クリックし、 **[管理者として実行]** をクリックします。
