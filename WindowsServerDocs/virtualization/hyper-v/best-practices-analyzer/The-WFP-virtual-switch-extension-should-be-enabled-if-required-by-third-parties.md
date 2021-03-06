---
title: 'The WFP virtual switch extension should be enabled if it is required by third party extensions (Hyper-V: サード パーティ製の拡張機能で必要とされている場合、WFP 仮想スイッチ拡張機能を有効にする必要がある)'
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 8aa8a9a5-e3fa-4c9b-8331-ba5a3de22429
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: d4cc23ce638f7b5ee95f80de067b4ad5b360d118
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859305"
---
# <a name="the-wfp-virtual-switch-extension-should-be-enabled-if-it-is-required-by-third-party-extensions"></a>The WFP virtual switch extension should be enabled if it is required by third party extensions (Hyper-V: サード パーティ製の拡張機能で必要とされている場合、WFP 仮想スイッチ拡張機能を有効にする必要がある)

>適用対象: Windows Server 2016

ベストプラクティスとスキャンの詳細については、「[ベストプラクティスアナライザースキャンの実行」および「スキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。  
  
|プロパティ|詳細|  
|-|-|  
|**オペレーティング システム**|Windows Server 2016|  
|**製品/機能**|Hyper-V|  
|**順**|［警告］|  
|**カテゴリ**|構成|  
  
次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。  
  
## <a name="issue"></a>**問題**  
*Windows Filtering Platform (WFP) 仮想スイッチ拡張機能が無効になっています。*  
  
## <a name="impact"></a>**よる**  
*次の仮想スイッチでは、一部のサードパーティの仮想スイッチ拡張機能が正しく動作しない可能性があります。*  
  
仮想マシンの一覧を \<>  
  
## <a name="resolution"></a>**解決方法**  
*Windows PowerShell コマンドレット VMSwitchExtension を使用して、サードパーティ製の拡張機能に必要な場合は Windows フィルタリングプラットフォームを有効にします。*  
  
### <a name="enable-the-windows-filtering-platform-using-windows-powershell"></a>Windows PowerShell を使用して Windows フィルタ リング プラットフォームを有効にします。  
  
1.  Windows PowerShell を開きます。 (デスクトップから **[スタート]** をクリックし、「 **Windows PowerShell**」と入力を開始します)。  
  
2.  右クリック **Windows PowerShell**  をクリック **管理者として実行**します。  
  
3.  外部スイッチの名前の外部を交換した後、このコマンドを実行します。  
  
```  
Enable-VMSwitchExtension -VMSwitchName External -Name Microsoft Windows Filtering Platform  
```  
  
## <a name="see-also"></a>参照  
[VMSwitchExtension](https://technet.microsoft.com/library/hh848541.aspx)  
  


