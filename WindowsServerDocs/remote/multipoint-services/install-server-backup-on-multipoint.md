---
title: MultiPoint server にサーバーバックアップをインストールする
description: バックアップと回復ツールをインストールする手順について説明します。
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: e4331370-ba07-4529-92ab-db14a41bfc3b
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: f8fe5ac8b57105d421af431b12c8dc17250b622d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80820335"
---
# <a name="install-server-backup-on-your-multipoint-server"></a>MultiPoint server にサーバーバックアップをインストールする
MultiPoint サーバーのバックアップと回復の計画について検討することをお勧めします。
  
任意のサイズの環境では、適切なバックアップと回復の計画が重要です。 Windows Server バックアップは、Windows Server 2016 の機能です。この機能を使用すると、ウィザードやその他のツールを使用して、インストールされているサーバーの基本的なバックアップおよび回復タスクを実行できます。 Windows Server バックアップを使用して、サーバー全体 (すべてのボリューム)、選択したボリューム、システム状態、または特定のファイルやフォルダーをバックアップし、システムの再構築に使用できるバックアップを作成できます。  
  
また、ボリューム、フォルダー、ファイル、特定のアプリケーション、およびシステム状態を回復できます。 また、ハードディスク障害などの障害については、ゼロから、または代替ハードウェアを使用して、システムを再構築することができます。 これを行うには、完全なサーバーのバックアップ、またはオペレーティングシステムファイルと Windows 回復環境を含むボリュームのみをバックアップする必要があります。 これにより、システム全体が古いシステムまたは新しいハードディスクに復元されます。  
  
Windows Server バックアップの重要な機能は、バックアップを自動的に実行するようにスケジュールする機能です。  
  
必要なバックアップの種類を設定するには、次の手順に従います。  
  
## <a name="install-backup-and-recovery-tools"></a>バックアップと回復ツールのインストール  
  
1.  **[スタート]** 画面で、 **[サーバーマネージャー]** を開きます。  
  
2.  **[役割と機能の追加]** をクリックして、役割の追加ウィザードを開始します。 **[次へ]** をクリックしてから、メモを**開始する前に**を確認します。  
  
3.  **[役割ベースまたは機能ベースのインストール]** オプションを選択し、 **[次へ]** をクリックします。  
  
4.  管理しているローカルコンピューターを選択し、 **[次へ]** をクリックします。  
  
    [ 機能の追加ウィザード ] が開きます。  
  
5.  **機能の選択** ページで Windows Server バックアップ機能 を展開し、 **Windows Server バックアップ**および**コマンドラインツール**のチェックボックスをオンにして、**次へ** をクリックします。  
  
    > [!NOTE]  
    > また、スナップインと Wbadmin コマンドラインツールをインストールするだけの場合は、 **[Windows Server バックアップの機能]** を展開し、 **[Windows Server バックアップ]** チェックボックスのみをオンにして、 **[コマンドラインツール]** チェックボックスがオフになっていることを確認します。  
  
6.  **[インストールオプションの確認]** ページで、選択した内容を確認し、 **[インストール]** をクリックします。  
  
    インストール中にエラーが発生した場合は、 **[インストールの結果]** ページにエラーが記録されます。  
  
7.  インストールが正常に完了すると、次のバックアップおよび回復ツールにアクセスできるようになります。  
  
    -   Windows Server バックアップスナップインを開くには、**スタート**画面で「 **Backup**」と入力し、結果で **[Windows Server バックアップ]** をクリックします。  
  
    -   コマンドの Wbadmin ツールとビュー構文を開始するには、**スタート**画面で「 **command**」と入力します。 結果で、 **[コマンドプロンプト]** を右クリックし、ページの下部にある **[管理者として実行]** をクリックして、確認プロンプトで **[はい]** をクリックします。 コマンドプロンプトで、「 **wbadmin/?** 」と入力します。 enter キーを押します。 ツールのコマンド構文と説明が表示されます。  
  
## <a name="configure-backups-using-windows-server-backup"></a>Windows Server バックアップを使用したバックアップの構成  
  
-   [サーバーのバックアップ](https://technet.microsoft.com/library/cc753528.aspx)に関するガイダンスに従ってください。 