---
title: ダイナミック ディスクからベーシック ディスクへの再変換
description: ダイナミック ディスクをベーシック ディスクに再変換する方法について説明します。
ms.date: 12/18/2019
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 8ad14225592d627b6ff88b9e2286b686aa549392
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "75351940"
---
# <a name="change-a-dynamic-disk-back-to-a-basic-disk"></a>ダイナミック ディスクからベーシック ディスクへの再変換

> **適用対象:** Windows 10、Windows 8.1、Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

このトピックでは、ダイナミック ディスク上のすべてのデータを削除し、ベーシック ディスクに変換する方法について説明します。 ダイナミック ディスクは Windows では非推奨となったため、今後使用することはお勧めしません。 ディスクをプールしてより大きいボリュームにする場合は、代わりにベーシック ディスクを使用するか、新しい[記憶域スペース](https://support.microsoft.com/help/12438/windows-10-storage-spaces) テクノロジを使用することをお勧めします。 Windows が起動するボリュームをミラー化する場合、多くのマザーボードに搭載されているような、ハードウェア RAID コントローラーを使用できます。

> [!WARNING]
> ダイナミック ディスクをベーシック ディスクに再変換するには、ディスクからすべてのボリュームを削除し、ディスク上のすべてのデータを完全に消去する必要があります。 操作を開始する前に、保存する必要のあるデータをすべてバックアップしてください。

## <a name="to-change-a-dynamic-disk-back-to-a-basic-disk-by-using-disk-management"></a>ディスクの管理を使用してダイナミック ディスクをベーシック ディスクに戻すには

1.  ダイナミック ディスクからベーシック ディスクに変換するディスク上のすべてのボリュームをバックアップします。

2. 管理者のアクセス許可でディスクの管理を開きます。

   そのための簡単な方法は、タスクバーの検索ボックスに「**コンピューターの管理**」と入力し、 **[コンピューターの管理]** を長押しし (または右クリックし)、 **[管理者として実行]**  >  **[はい]** の順に選択することです。 [コンピューターの管理] が開いたら、 **[ストレージ]**  >  **[ディスク管理]** の順に移動します。

2.  [ディスクの管理] で、ベーシック ディスクに変換するダイナミック ディスク上の各ボリュームを長押しし (または右クリックし)、 **[ボリュームの削除]** をクリックします。

3.  ディスク上のすべてのボリュームが削除されたら、ディスクを右クリックし、 **[ベーシック ディスクに変換する]** をクリックします。

## <a name="to-change-a-dynamic-disk-back-to-a-basic-disk-by-using-a-command-line"></a>コマンド ラインを使用してダイナミック ディスクをベーシック ディスクに戻すには

1.  ダイナミック ディスクからベーシック ディスクに変換するディスク上のすべてのボリュームをバックアップします。

2.  コマンド プロンプトを開き、「`diskpart`」と入力します。

3.  **DISKPART** プロンプトで、「`list disk`」と入力します。 ベーシックに変換するディスクのディスク番号を書き留めておきます。

4.  **DISKPART** プロンプトで、「`select disk <disknumber>`」と入力します。

5.  **DISKPART** プロンプトで、「`detail disk`」と入力します。

6.  ディスク上の各ボリュームについて、**DISKPART** プロンプトで、「`select volume= <volumenumber>`」と入力し、次に「`delete volume`」と入力します。

7.  **DISKPART** プロンプトで、「`select disk <disknumber>`」と入力し、ベーシック ディスクに変換するディスクのディスク番号を指定します。

8.  **DISKPART** プロンプトで、「`convert basic`」と入力します。

| 値  | 説明 |
| --- | --- |
| **list disk**                         | ディスクとディスクに関する情報を一覧表示します。ディスクのサイズ、利用可能な空き領域の容量、ディスクがベーシック ディスクとダイナミック ディスクのどちらであるか、ディスクでマスター ブート レコード (MBR) と GUID パーティション テーブル (GPT) のどちらのパーティション スタイルが使用されているかなどの情報が表示されます。 アスタリスク (*) でマークされているディスクにフォーカスがあります。 |
| **select disk** <em>disknumber</em>   | <em>disknumber</em> がディスク番号である指定されたディスクを選択し、そのディスクにフォーカスを移動します。  |
| **detail disk** <em>disknumber</em>   | 選択したディスクおよびそのディスク上のボリュームのプロパティを表示します。  |
| **select volume** <em>disknumber</em> | <em>disknumber</em> がボリューム番号である指定されたボリュームを選択し、そのボリュームにフォーカスを移動します。 ボリュームが指定されていない場合、**select** コマンドは、フォーカスがある現在のボリュームを一覧表示します。 ボリュームの指定は、番号、ドライブ文字、またはマウント ポイント パスで行うことができます。 ベーシック ディスク上でボリュームを選択すると、対応するパーティションもフォーカスされます。 |
| **delete volume**                     | 選択されたボリュームを削除します。 システム ボリューム、ブート ボリューム、またはアクティブなページング ファイルやクラッシュ ダンプ (メモリ ダンプ) を含んでいるボリュームは削除できません。 |
| **convert basic** | 空のダイナミック ディスクをベーシック ディスクに変換します。  |

## <a name="additional-considerations"></a>その他の考慮事項

-   ディスクをベーシック ディスクに再変換する前に、ディスク上のボリュームやデータをすべて削除しておく必要があります。 データを保持するには、ディスクをベーシック ディスクに変換する前に、データをバックアップするか、別のボリュームに移動します。
-   ダイナミック ディスクをベーシック ディスクに戻すと、そのディスク上にはパーティションおよび論理ドライブしか作成できなくなります。

## <a name="see-also"></a>関連項目

-   [コマンド ライン構文の表記規則](https://technet.microsoft.com/library/cc742449(v=ws.11).aspx)