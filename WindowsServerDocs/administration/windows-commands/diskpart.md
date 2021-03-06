---
title: diskpart
description: Diskpart コマンドインタープリターのリファレンストピック。コンピューターのドライブを管理するのに役立ちます。
ms.prod: windows-server
ms.technology: storage
author: jasongerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: 8b6d36e428daaefd7cf26e42170442373fc7551c
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992572"
---
# <a name="diskpart"></a>diskpart

> 適用対象: Windows 10、Windows 8.1、Windows 8、Windows 7、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、windows server 2008 R2、Windows Server 2008

Diskpart コマンドインタープリターを使用すると、コンピューターのドライブ (ディスク、パーティション、ボリューム、または仮想ハードディスク) を管理できます。

**Diskpart**コマンドを使用するには、まず、オブジェクトを一覧表示してから、フォーカスを与えるオブジェクトを選択する必要があります。 オブジェクトにフォーカスがあると、入力した diskpart コマンドがそのオブジェクトに対して動作します。

## <a name="list-available-objects"></a>使用可能なオブジェクトの一覧表示

次のように使用して、使用可能なオブジェクトの一覧を表示し、オブジェクトの番号またはドライブ文字を特定することができます。

- `list disk`-コンピューター上のすべてのディスクを表示します。

- `list volume`-コンピューター上のすべてのボリュームを表示します。

- `list partition`-コンピューターにフォーカスがあるディスク上のパーティションを表示します。

- `list vdisk`-コンピューター上のすべての仮想ディスクを表示します。

**リスト**コマンドを実行すると、フォーカスがあるオブジェクトの横にアスタリスク (*) が表示されます。

## <a name="determine-focus"></a>フォーカスの決定

オブジェクトを選択すると、別のオブジェクトを選択するまで、フォーカスはそのオブジェクトに残ります。 たとえば、フォーカスがディスク0に設定されていて、ディスク2で [ボリューム 8] を選択した場合、フォーカスはディスク0からディスク2のボリューム8に移ります。

一部のコマンドでは、フォーカスが自動的に変更されます。 たとえば、新しいパーティションを作成すると、フォーカスは自動的に新しいパーティションに切り替わります。

選択したディスクのパーティションにのみフォーカスを移すことができます。 パーティションにフォーカスがある場合、関連するボリューム (存在する場合) にもフォーカスがあります。 ボリュームにフォーカスがあると、関連するディスクとパーティションには、ボリュームが1つの特定のパーティションにマップされている場合にもフォーカスがあります。 そうでない場合は、ディスクとパーティションにフォーカスが失われます。

## <a name="syntax"></a>構文

Diskpart コマンドインタープリターを起動するには、コマンドプロンプトで次のように入力します。

```
diskpart <parameter>
```

> [!IMPORTANT]
> Diskpart を実行するには、ローカルの**Administrators**グループ、または同様のアクセス許可を持つグループに存在する必要があります。

### <a name="parameters"></a>パラメーター

Diskpart コマンドインタープリターから次のコマンドを実行できます。

| command | 説明 |
| ------- | ----------- |
| [active](active.md) | フォーカスがあるディスクのパーティションをアクティブとしてマークします。 |
| [add](add.md) | フォーカスのあるシンプル ボリュームを、指定されたディスクにミラー化します。 |
| [assign](assign.md) | フォーカスがあるボリュームに、ドライブ文字またはマウント ポイントを割り当てます。 |
| [vdisk のアタッチ](attach-vdisk.md) | 仮想ハードディスク (VHD) を接続します。これにより、ホストコンピューターにローカルハードディスクドライブとして表示されます。 |
| [attributes](attributes.md) | ディスクまたはボリュームの属性を表示、設定、またはクリアします。 |
| [automount](automount.md) | 自動マウント機能を有効または無効にします。 |
| [break](break.md) | フォーカスのあるミラー ボリュームを 2 つのシンプル ボリュームに分割します。 |
| [clean](clean.md) | フォーカスがあるディスクから、パーティション フォーマットまたはボリューム フォーマットをすべて削除します。 |
| [compact vdisk](compact-vdisk.md) | 容量可変の拡張バーチャルハードディスク (VHD) ファイルの物理サイズを小さくします。 |
| [convert](convert.md) | ファイルアロケーションテーブル (FAT) および FAT32 ボリュームを NTFS ファイルシステムに変換し、既存のファイルとディレクトリをそのまま残します。 |
| [create](create.md) | ディスク上のパーティション、1つまたは複数のディスク上のボリューム、または仮想ハードディスク (VHD) を作成します。 |
| [delete](delete.md) | パーティションまたはボリュームを削除します。 |
| [vdisk のデタッチ](detach-vdisk.md) | 選択した仮想ハードディスク (VHD) がホストコンピューター上のローカルハードディスクドライブとして表示されなくなります。 |
| [データ](detail.md) | 選択したディスク、パーティション、ボリューム、または仮想ハードディスク (VHD) に関する情報を表示します。 |
| [exit](exit.md) | Diskpart コマンドインタープリターを終了します。 |
| [vdisk を展開する](expand-vdisk.md) | 仮想ハードディスク (VHD) を指定されたサイズに拡張します。 |
| [extend](extend.md) | フォーカスがあるボリュームまたはパーティションを、そのファイルシステムと共に、ディスク上の空き領域 (未割り当て) に拡張します。 |
| [ファイルシステム](filesystems.md) | フォーカスがあるボリュームの現在のファイルシステムに関する情報を表示し、ボリュームのフォーマットがサポートされているファイルシステムの一覧を表示します。 |
| [format](format.md) | Windows ファイルを受け入れるようにディスクをフォーマットします。 |
| [gpt](gpt.md) | ベーシック GUID パーティションテーブル (gpt) ディスクにフォーカスがあるパーティションに gpt 属性を割り当てます。 |
| [help](help.md) | 使用可能なコマンドの一覧、または指定したコマンドの詳細なヘルプ情報を表示します。 |
| [import](import.md) | 外部ディスクグループをローカルコンピューターのディスクグループにインポートします。 |
| [稼動](inactive.md) | 基本マスターブートレコード (MBR) ディスクで、フォーカスがあるシステムパーティションまたはブートパーティションを非アクティブとしてマークします。 |
| [list](list.md) | ディスクのパーティション、ディスク内のボリューム、またはバーチャルハードディスク (Vhd) のディスクの一覧を表示します。 |
| [マージ vdisk](merge-vdisk.md) | 差分仮想ハード_ディスク (VHD)、対応する親 VHD をマージします。 |
| [なっ](offline.md) | オンラインのディスクまたはボリュームをオフライン状態にかかります。 |
| [オンライン](online.md) | オフラインのディスクまたはボリュームをオンライン状態にかかります。 |
| [recover](recover.md) | ディスクグループ内のすべてのディスクの状態を更新し、無効なディスクグループのディスクを回復します。また、古いデータを保持しているミラーボリュームと RAID-5 ボリュームを再同期します。 |
| [rem](rem.md) | スクリプトにコメントを追加できます。 |
| [remove](remove.md) | ボリュームからドライブ文字またはマウントポイントを削除します。 |
| [回復](repair.md) | 障害が発生したディスク領域を指定されたダイナミックディスクに交換することで、フォーカスのある RAID-5 ボリュームを修復します。 |
| [再スキャン](rescan.md) | コンピューターに追加された新しいディスクを検索します。 |
| [日数](retain.md) | ブートとして使用する既存のダイナミック シンプル ボリュームまたはシステム ボリュームを準備します。 |
| [san](san.md) | オペレーティングシステムの記憶域ネットワーク (san) ポリシーを表示または設定します。 |
| [select](select.md) | フォーカスを移動すると、ディスク、パーティション、ボリューム、またはバーチャル ハード_ディスク (VHD) します。 |
| [id の設定](set-id.md) | フォーカスのあるパーティションの [パーティションの種類] フィールドを変更します。 |
| [shrink](shrink.md) | 指定した量だけ、選択したボリュームのサイズが小さくなります。 |
| [uniqueid](uniqueid.md) | フォーカスがあるディスクの GUID パーティションテーブル (GPT) 識別子またはマスターブートレコード (MBR) 署名を表示または設定します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ディスク管理の概要](https://docs.microsoft.com/windows-server/storage/disk-management/overview-of-disk-management)

- [Storage Cmdlets in Windows PowerShell (Windows PowerShell の記憶域コマンドレット)](https://docs.microsoft.com/powershell/module/storage/)
