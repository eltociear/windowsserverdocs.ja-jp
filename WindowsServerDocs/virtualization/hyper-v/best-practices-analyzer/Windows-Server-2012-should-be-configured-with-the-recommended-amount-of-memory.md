---
title: Windows Server 2012 には推奨されるメモリ量を構成します。
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 12d0b473-cf6a-4746-b03d-2ceeb701c5d0
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 634e36fe4b871ef33d2b2a3f024521901fffe437
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860985"
---
# <a name="windows-server-2012-should-be-configured-with-the-recommended-amount-of-memory"></a>Windows Server 2012 には推奨されるメモリ量を構成します。

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
*Windows Server 2012 を実行している仮想マシンは、推奨される RAM 容量 (2 GB) 未満で構成されています。*  
  
## <a name="impact"></a>**よる**  
*ゲストオペレーティングシステムとアプリケーションが正常に動作しない可能性があります。複数のアプリケーションを同時に実行するのに十分なメモリがない可能性があります。これは、次の仮想マシンに影響します。*  
  
仮想マシンの一覧を \<>  
  
## <a name="resolution"></a>**解決方法**  
*Hyper-v マネージャーを使用して、この仮想マシンに割り当てられているメモリを少なくとも 2 GB に増やします。*  
  
### <a name="increase-the-memory-using-hyper-v-manager"></a>Hyper-v マネージャーを使用してメモリを増やす  
  
1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、 **[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。  
  
2.  結果ウィンドウで  **仮想マシン**, 、構成する仮想マシンを選択します。 バーチャルマシンの状態は **オフ (オフ**)」と表示されます。 そうでない場合は、バーチャルマシンを右クリックし、 **[シャットダウン]** をクリックします。  
  
3.  **[操作]** ウィンドウで、仮想マシン名の下の **[設定]** をクリックします。  
  
4.  ナビゲーションウィンドウで、 **[メモリ]** をクリックします。  
  
5.  **[メモリ]** ページで、**スタートアップ RAM**を 2 GB 以上に設定し、[ **OK]** をクリックします。  
  
### <a name="increase-the-memory-using-windows-powershell"></a>Windows PowerShell を使用してメモリを増やす  
  
1.  Windows PowerShell を開きます。 (デスクトップから **[スタート]** をクリックし、「 **Windows PowerShell**」と入力を開始します)。  
  
2.  右クリック **Windows PowerShell**  をクリック **管理者として実行**します。  
  
3.  \<MyVM > を仮想マシンの名前に置き換えた後、次のコマンドを実行します。  
  
```  
Set-VMMemory <MyVM> -StartupBytes 2GB  
```  
  
## <a name="see-also"></a>参照  
[設定-VMMemory](https://technet.microsoft.com/library/hh848572.aspx)  
  


