---
ms.assetid: ef91f1d8-2991-4d90-b687-5fa189737c88
title: AD FS サーバーの容量計画
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 984579813a843e6c39bd85bb9aa07cdddfcfc067
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858635"
---
# <a name="planning-for-ad-fs-server-capacity"></a>AD FS サーバーの容量計画


  
> [!NOTE]  
> このトピックに記載されている内容には、Windows Server 2012 を実行しているサーバーで実際に実行されたテストは反映されていません。 このトピックは、必要なテストの実行が完了したら更新される予定です。  
  
Active Directory フェデレーションサービス (AD FS) \(AD FS\) のキャパシティプランニングは、フェデレーションサービスのピーク時の使用状況を予測し、それらの負荷要件を満たすために\-サーバーのデプロイを計画または拡張するプロセスです。  
  
このセクションでは、フェデレーションサーバーとフェデレーションサーバープロキシの両方の役割の展開ガイドラインについて説明します。これは、Microsoft の AD FS 製品チームによって実行されたラボテストに基づいています。 このコンテンツの目的は、次の作業に役立てていただくことです。  
  
-   AD FS サーバーの数など、組織固有の AD FS 展開に必要なハードウェアのニーズを厳密に見積もることができます。  
  
-   要求内の\-に署名するために予想されるピーク時の使用量を正確にプロジェクトし、増加を計画し、AD FS の展開がその予想されるピーク時の使用量を処理できることを確認します。  
  
キャパシティ プランニングに関するこのコンテンツを読み始める前に、次の 2 つの表のタスクを、ここに示した順序で実行することをお勧めします。 最初の表には、ここで説明するキャパシティ プランニングに関連する背景情報を知るうえで役立つタスクへのリンクがあります。  
  
|推奨されるタスク|説明|参照|  
|--------------------|---------------|-------------|  
|AD FS フェデレーションサーバーとフェデレーションサーバープロキシを展開するための要件を理解する|フェデレーション サーバーとフェデレーション サーバー プロキシを展開するために必要な、ハードウェアとソフトウェアに関する重要な要件を確認します。|[付録 A: AD FS の要件の確認](Appendix-A--Reviewing-AD-FS-Requirements.md)|  
|組織に展開する AD FS 構成データベースの種類を選択します|このセクションでキャパシティプランニングデータの使用を開始する前に、まず、展開する AD FS 構成データベースの種類 (Windows Internal Database \(WID\) または構造化照会言語 \(SQL\) データベースのどちらかを決定する必要があります。|[AD FS 構成データベースの役割](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)。<p>[AD FS 展開トポロジに関する考慮事項](AD-FS-Deployment-Topology-Considerations.md)|  
|選択した新しい AD FS 構成データベースと共に使用するトポロジ レイアウトのタイプを決定する|展開内で使用する AD FS 構成データベースのタイプを決定したら、運用環境内でのフェデレーション サーバーとフェデレーション サーバー プロキシの配置に関して、どの展開トポロジが最も要望に近いかを検討する必要があります。|[AD FS 展開トポロジの決定](Determine-Your-AD-FS-Deployment-Topology.md)|  
|主要 AD FS 関連のキャパシティプランニングの用語を理解する|AD FS 容量計画に関するディスカッションで使用される、一般的な容量計画の用語の定義を確認します。|このトピックの「[AD FS キャパシティ プランニングの用語](Planning-for-AD-FS-Server-Capacity.md#bk_terms)」をご覧ください。|  
  
前の表に示したコンテンツの確認が完了したら、次の表に示す、前提条件となるタスクを行ってください。  
  
|前提条件となるタスク|説明|参照|  
|---------------------|---------------|-------------|  
|AD FS 容量計画のサイジングスプレッドシートをダウンロードする|AD FS 容量計画のサイジングスプレッドシートは、AD FS のフェデレーションサーバーファームの展開に必要なフェデレーションサーバーの数を判断するのに役立ちます。 このスプレッドシートの使い方は、次のタスクの下に示したリンク先にあります。|[AD FS キャパシティプランニングスプレッドシート](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacityPlanning.xlsx)|  
|\(SSO\) 対象の要求\-認識アプリケーションに対するシングルサイン\-オンを必要とするユーザーの数に関するデータと、このアクセスに関連する予想されるピーク時の使用期間に関するデータを収集します。|ここで集めるユーザー データは、AD FS キャパシティ プランニング サイジング スプレッドシートの入力値として使用します。|[組織のフェデレーションサーバーの数を推定する](Planning-for-Federation-Server-Capacity.md#bk_estimatefs)|  
|Windows Server 2016 の AD FS キャパシティプランニングスプレッドシート|Windows Server 2016 用に更新された計画ワークシート|[AD FS Windows Server 2016 の容量計画](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx)  
  
## <a name="ad-fs-capacity-planning-terms"></a><a name="bk_terms"></a>AD FS 容量計画の使用条件  
次の表では、AD FS 設計ガイドのこの容量計画のセクションでよく使用される重要な用語について説明します。 AD FS の用語の完全な一覧については、「[キー AD FS の概念につい](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)て」を参照してください。  
  
|用語|Definition|  
|--------|--------------|  
|同時実行ユーザー数|サービスへの要求を送信するユーザーの数の、所定の時間当たりの見積もり。通常はピーク アクティビティ期間の数値です。|  
|アクティブ ユーザー数|システム上でアクティブであるユーザー (要求を送信するとは限らない) の数の、所定の時間当たりのおおよその平均値。|  
|定義済みユーザー数|理論上の最大ユーザー数。通常は、そのシステム内でアカウントが定義済みであるユーザーの数に基づいています。|  
|1 秒あたりの要求数|サーバーのスループットについて話すときに、クライアントによって送信された要求の \(\) \(数については、1秒あたり\) サーバーのスループットについて説明します。 この数値は、サーバー プロセッサとメモリのキャパシティの計画を立てるときに使用します。|  
|サーバーの応答性と使用率の目標値|許容されるサーバー パフォーマンスの範囲を規定する数値。 一般的に、応答性が目標値を下回ったときや使用率が目標値を上回ったときは、システムが過負荷であると見なされ、キャパシティ拡大が必要になります。|  
|Windows Internal Database \(WID\)|特定の AD FS の展開で SQL Server の代替手段として使用できる既定の AD FS 構成データベース。|  
  
## <a name="configuration-environment-used-during-ad-fs-testing"></a>AD FS テスト時に使用される構成環境  
このセクションでは、AD FS 製品チームがテストを実行するために使用した構成環境について説明します。 フェデレーション サーバーのテストにおいてパフォーマンスと拡張性のデータを収集するのに使用されたコンピューター ハードウェア、ソフトウェア、およびネットワーク構成は次のとおりです。  
  
-   デュアル Quad コア2.27 ギガヘルツ \(GHz\) \(8 コア\)  
  
-   16\-GB RAM  
  
-   Windows Server 2008 R2 Enterprise Edition  
  
-   ギガビット ネットワーク  
  
> [!NOTE]  
> テスト中にフェデレーションサーバーで 16 GB の RAM が使用されていましたが、ほとんどの AD FS の展開では、フェデレーションサーバーあたり 4 GB の RAM など、より適度なメモリサイズを使用できます。 この AD FS 容量計画のコンテンツに記載されている推奨事項は、AD FS キャパシティプランニングスプレッドシートによって得られる結果と共に、各フェデレーションサーバーがほとんどの AD FS 運用環境で約 4GB's RAM を使用するという前提に基づいています。  
  
フェデレーション サーバー プロキシのテストでパフォーマンスと拡張性のデータを収集するのに使用された構成は次のとおりです。  
  
-   デュアル Quad コア 2.24 GHz \(4 コア\)  
  
-   4\-GB の RAM  
  
-   Windows Server 2008 R2 Enterprise Edition  
  
-   ギガビット ネットワーク  
  
> [!NOTE]  
> AD FS サーバーの容量に関する推奨事項は、特定の環境で使用するハードウェアおよびネットワーク構成に対して選択した仕様によって、大きく異なる場合があります。 参考までに、このコンテンツで示すサイジングのガイダンスでは、前述のコンピューターでの使用率目標を 80% としています。  
  
## <a name="measure-ad-fs-server-capacity"></a>AD FS サーバーのキャパシティを測定する  
一般的に、ハードウェア コンポーネントのうち、サーバーのパフォーマンスと拡張性に影響を及ぼすのは、CPU、メモリ、ディスク、ネットワーク アダプターです。 幸いなことに、各 AD FS コンポーネントでは、メモリとディスク領域に対する要求がほとんど必要ありません。 ネットワーク接続は明らかに要件の 1 つです。 したがって、負荷テストをフェデレーション サーバーとフェデレーション サーバー プロキシに対して実行するときは、次の 2 つの主要領域にしぼってサーバー キャパシティを測定することになります。  
  
-   **1 秒あたりのピーク AD FS 要求数:** フェデレーションサーバーで1秒間に処理される要求の署名\-数。 この測定値は、1 つのサーバーに同時にサインインできるユーザーの数を特定するのに役立ちます。 この測定値を CPU 使用量の測定値と組み合わせると、この測定値がパフォーマンスに及ぼす影響を理解するのに役立ちます。  
  
-   **CPU 使用量:** CPU 容量を測定する割合。 この測定値は、1秒あたりの要求で受信した署名\-の数に基づいて発生した全体的な CPU 負荷を特定するのに役立ちます。  
  
## <a name="continue-reading-more-about-ad-fs-capacity-planning"></a>AD FS キャパシティ プランニングに関して次に参照するコンテンツ  
前提条件となるタスクを完了し、関連する用語とハードウェアの要件を理解したら、次の追加容量計画のコンテンツを使用して、展開に必要な AD FS サーバーの推奨数を判断できます。  
  
-   [フェデレーション サーバーの容量計画](Planning-for-Federation-Server-Capacity.md)  
  
-   [フェデレーション サーバー プロキシの容量計画](Planning-for-Federation-Server-Proxy-Capacity.md)  
  
## <a name="see-also"></a>参照
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
