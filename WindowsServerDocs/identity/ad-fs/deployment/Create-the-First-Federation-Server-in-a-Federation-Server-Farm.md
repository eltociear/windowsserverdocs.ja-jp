---
ms.assetid: 5e334c4e-75a7-453c-83e8-5ab4243cc685
title: フェデレーション サーバー ファーム内に最初のフェデレーション サーバーを作成する
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 0fe5c3160f661357536ef3bd60762873063c8ed0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855475"
---
# <a name="create-the-first-federation-server-in-a-federation-server-farm"></a>フェデレーション サーバー ファーム内に最初のフェデレーション サーバーを作成する

フェデレーションサービスの役割サービスをインストールし、必要な証明書をコンピューターに構成したら、コンピューターをフェデレーションサーバーになるように構成することができます。 AD FS フェデレーションサーバー構成ウィザードを使用して、新しいフェデレーションサーバーファームの最初のフェデレーションサーバーになるようにコンピューターをセットアップするには、次の手順を実行します。  
  
ファーム内に最初のフェデレーション サーバーを作成する作業では、新しいフェデレーション サービスを作成し、このコンピューターをプライマリ フェデレーション サーバーにする作業も行います。 つまり、このコンピューターは、AD FS 構成データベースの読み取り\/書き込みコピーを使用して構成されます。 このファーム内の他のすべてのフェデレーションサーバーは、プライマリフェデレーションサーバーに対して行われたすべての変更を、ローカルに格納されている AD FS 構成データベースのコピーのみを読み取り\-レプリケートする必要があります。 このレプリケーション プロセスの詳細については、「[AD FS 構成データベースの役割](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)」を参照してください。  
  
> [!NOTE]  
> SSO\) 設計 \(でフェデレーション Web シングル\-署名\-については、アカウントパートナー組織に少なくとも1つのフェデレーションサーバーがあり、リソースパートナー組織に少なくとも1つのフェデレーションサーバーが必要です。 詳細については、「[フェデレーション サーバーの配置場所](https://technet.microsoft.com/library/dd807127.aspx)」を参照してください。  
  
この手順を実行するには、Domain Admins グループのメンバーシップ、または Active Directory 内のプログラム データ コンテナーへの書き込みアクセス権を付与されている委任されたドメイン アカウントが最低限必要です。  
  
### <a name="to-create-the-first-federation-server-in-a-federation-server-farm"></a>フェデレーション サーバー ファーム内に最初のフェデレーション サーバーを作成するには  
  
1.  AD FS フェデレーション サーバー構成ウィザードを開始するには 2 つの方法があります。 ウィザードを開始するには、次のいずれかを実行します。  
  
    -   フェデレーションサービスの役割サービスのインストールが完了したら、の AD FS 管理スナップイン\-を開き、 **[概要]** ページまたは **[操作]** ウィンドウの **[AD FS フェデレーションサーバー構成ウィザード]** リンクをクリックします。  
  
    -   セットアップウィザードが完了したらいつでも、Windows エクスプローラーを開き、 **C:\\windows\\ADFS**フォルダーに移動して、 **[fsconfigwizard .exe]** をダブル\-クリックします。  
  
2.  **[ようこそ]** ページで、 **[新しいフェデレーション サービスの作成]** が選択されているのを確認し、 **[次へ]** をクリックします。  
  
3.  [**スタンド\-アロンまたはファームの展開の選択**] ページで、 **[新しいフェデレーションサーバーファーム]** をクリックし、 **[次へ]** をクリックします。  
  
4.  **[フェデレーション サービス名の指定]** ページで、表示されている **[SSL 証明書]** が正しいことを確認します。 これが正しい証明書でない場合は、 **[SSL 証明書]** 一覧から適切な証明書を選択します。  
  
    この証明書は、既定の Web サイトの Secure Sockets Layer \(SSL\) 設定から生成されます。 既定の Web サイトで SSL 証明書が 1 つしか構成されていない場合、その証明書が表示され、自動的に選択して使われます。 既定の Web サイトに対して複数の SSL 証明書が構成されている場合、そのすべての証明書がここに表示されます。ユーザーはその中から選択する必要があります。 既定の Web サイトに対して SSL 設定が構成されていない場合、ローカル コンピューター上の個人の証明書ストアで使用可能な証明書から一覧が生成されます。  
  
    > [!NOTE]  
    > IIS に対して SSL 証明書が構成されていない場合、証明書をオーバーライドすることはできません。 そのため、対象となる SSL 証明書用の以前の IIS 構成が保持されます。 この制限を回避するには、証明書を削除するか、IIS 管理コンソールを使って証明書を手動で再構成することができます。  
  
5.  選択した AD FS データベースが既に存在する場合、 **[既存の AD FS 構成データベースの検出]** ページが表示されます。 このページが表示された場合は、 **[データベースの削除]** をクリックし、 **[次へ]** をクリックします。  
  
    > [!CAUTION]  
    > このオプションを選択するのは、AD FS データベース内のこのデータが重要でないか、実稼働フェデレーション サーバー ファームで使用されていないことが明らかな場合のみにしてください。  
  
6.  **[サービス アカウントを指定します]** ページで、 **[参照]** をクリックします。 **[参照]** ダイアログ ボックスで、この新しいフェデレーション サーバー ファームでサービス アカウントとして使用するドメイン アカウントを見つけ、 **[OK]** をクリックします。 このアカウントのパスワードを入力し、確認して、 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    > フェデレーションサーバーファームのサービスアカウントを指定する方法の詳細については、「[フェデレーションサーバーファームのサービスアカウントを手動で構成](Manually-Configure-a-Service-Account-for-a-Federation-Server-Farm.md)する」を参照してください。 フェデレーションサーバーファーム内の各フェデレーションサーバーは、ファームが動作するために同じサービスアカウントを指定する必要があります。 たとえば、作成されたサービスアカウントが contoso\\ADFS2SVC の場合、フェデレーションサーバーの役割を構成し、同じファームに参加する各コンピューターは、フェデレーションサーバー構成ウィザードのこの手順で contoso\\ADFS2SVC を指定する必要があります。  
  
7.  **[設定の適用準備]** ページで、詳細を確認します。 設定が正しいと思われる場合は、 **[次へ]** をクリックして、これらの設定で AD FS の構成を開始します。  
  
8.  **[構成結果]** ページで作業内容を確認します。 すべての構成手順が終了したら、 **[閉じる]**  をクリックしてウィザードを終了します。  
  
    > [!IMPORTANT]  
    > デプロイを安全に行うため、AD FS フェデレーション サーバー構成ウィザードを使って、フェデレーション サーバー ファームを構成する場合に、アーティファクトの解像度と応答検出が無効になります。 このウィザードは、サービス構成データを保存するための Windows 内部データベースを自動構成します。 ただし、AD FS 管理スナップ\-の **[エンドポイント]** ノード、または Windows PowerShell の Enable\-enable-adfsendpoint コマンドレットのいずれかを使用してアーティファクト解決エンドポイントを有効にすることで、この変更を誤って元に戻すことができます。 フェデレーション サーバー ファームと Windows 内部データベースを併用する場合、このエンドポイントが無効のままに維持されるように、既定の設定を再構成しないように注意してください。  
  
## <a name="additional-references"></a>その他の参照情報  
[チェックリスト: フェデレーションサーバーのセットアップ](Checklist--Setting-Up-a-Federation-Server.md)  
  

