---
title: ホットプラグとホットプラグを使用できるように、SCSI コントローラーでバーチャルマシンを構成する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 511e1172-aeef-463d-b5dd-2bffae411ff1
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: bd49a911d278a1f07fe9630f39798204d760dd88
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80862155"
---
# <a name="configure-a-virtual-machine-with-a-scsi-controller-to-be-able-to-hot-plug-and-hot-unplug-storage"></a>ホットプラグとホットプラグを使用できるように、SCSI コントローラーでバーチャルマシンを構成する

>適用対象: Windows Server 2016


  
*ベストプラクティスとスキャンの詳細については、「ベストプラクティスアナライザー」を参照してください* [Best Practices Analyzer](https://go.microsoft.com/fwlink/?LinkId=122786)。  
  
|プロパティ|詳細|  
|-|-|  
|**オペレーティング システム**|Windows Server 2016|  
|**製品/機能**|Hyper-V|  
|**順**|［警告］|  
|**カテゴリ**|構成|  
  
次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。  
  
## <a name="issue"></a>問題  
  
*SCSI コントローラーが構成されていない仮想マシンが見つかりました。*  
  
## <a name="impact"></a>影響  
  
*次の仮想マシンのストレージをホットプラグまたはホットプラグで取り外すことはできません。*  
  
仮想マシン名の \<一覧 >  
  
ホットプラグまたはホットプラグを切断する機能により、仮想マシンの記憶域のニーズを管理しやすくなります。ダウンタイムは必要ありません。 記憶域を追加または削除する前に、SCSI コントローラーのない仮想マシンをシャットダウンする必要があります。  
  
## <a name="resolution"></a>解決方法  
  
*この仮想マシンに対してホットプラグまたはホットプラグを使用する必要がない場合は、何もする必要はありません。それ以外の場合は、仮想マシンをシャットダウンし、構成に SCSI コントローラーを追加します。*  
  
SCSI コントローラーをホットプラグとホットプラグを使用して記憶域を取り外すには、ゲストオペレーティングシステムが現在のバージョンの integration services を実行している必要があります。  
  


