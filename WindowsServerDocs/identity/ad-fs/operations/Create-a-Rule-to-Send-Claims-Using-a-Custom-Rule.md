---
ms.assetid: 38eb3726-e97b-484e-9926-67e8a046b0c5
title: カスタム規則を使用して要求を送信する規則を作成する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 81a1fbbd703a5d452c437b089b822e227f55af82
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816695"
---
# <a name="create-a-rule-to-send-claims-using-a-custom-rule"></a>カスタム規則を使用して要求を送信する規則を作成する


Active Directory フェデレーションサービス (AD FS) (AD FS) の**カスタム規則**テンプレートを使用して要求を送信することによって、標準の規則テンプレートが組織の要件を満たしていない状況に対して、カスタムの要求規則を作成できます。 カスタム要求規則は、要求規則言語で記述されているため、**カスタム規則**のテキストボックスにコピーしてから、規則セットで使用する必要があります。 高度なルールの構文を構築する方法については、「[要求規則言語の役割](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)」を参照してください。  
  
で AD FS 管理スナップ\-を使用して要求規則を作成するには、次の手順に従います。  
  
この手順を実行するには、ローカルコンピューターの**Administrators**、またはそれと同等のメンバーシップが最低限必要です。  適切なアカウントの使用方法の詳細を確認し、グループ メンバーシップ [ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477)します。



## <a name="to-create-a-rule-to-pass-through-or-filter-an-incoming-claim-on-a-relying-party-trust-in-windows-server-2016"></a>Windows Server 2016 で証明書利用者信頼に対して入力方向の要求をパススルーまたはフィルター処理する規則を作成するには 

1.  サーバーマネージャーで、 **[ツール]** をクリックし、 **[AD FS の管理]** を選択します。  
  
2.  コンソールツリーの  **AD FS**で、**証明書利用者の信頼** をクリックします。 
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG) を作成 ![には  
  
3.  選択した信頼を右\-クリックし、 **[要求の発行ポリシーの編集]** をクリックします。
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG) を作成 ![には   
  
4.  **[要求発行ポリシーの編集]** ダイアログボックスの **[発行変換規則]** で、 **[規則の追加]** をクリックして規則ウィザードを開始します。 
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG) を作成 ![には    

5.  **[規則テンプレートの選択]** ページの **[要求規則テンプレート]** で、 **[カスタム規則を使用して要求を送信]** する を一覧から選択し、 **[次へ]** をクリックします。  
ルール](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom3.PNG) を作成 ![には   
  
6.  **[規則の構成]** ページの **[要求規則名]** に、この規則の表示名を入力します。 **[カスタム規則]** で、この規則に必要な要求規則言語の構文を入力するか、貼り付けます。  
ルール](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom4.PNG) を作成 ![には     

7.  **[完了]** をクリックします。  
  
8.  **[要求規則の編集]** ダイアログボックスで、 **[OK]** をクリックして規則を保存します。   
  
## <a name="to-create-a-rule-to-pass-through-or-filter-an-incoming-claim-on-a-claims-provider-trust-in-windows-server-2016"></a>Windows Server 2016 の要求プロバイダー信頼に対して入力方向の要求をパススルーまたはフィルター処理する規則を作成するには 
  
1.  サーバーマネージャーで、 **[ツール]** をクリックし、 **[AD FS の管理]** を選択します。  
  
2.  コンソールツリーの  **AD FS**で、**要求プロバイダー信頼** をクリックします。 
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG) を作成 ![には  
  
3.  選択した信頼を右\-クリックし、 **[要求規則の編集]** をクリックします。
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG) を作成 ![には   
  
4.  **[要求規則の編集]** ダイアログボックスの **[受け入れ変換規則]** で、 **[規則の追加]** をクリックして規則ウィザードを開始します。
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG) を作成 ![には    

5.  **[規則テンプレートの選択]** ページの **[要求規則テンプレート]** で、 **[カスタム規則を使用して要求を送信]** する を一覧から選択し、 **[次へ]** をクリックします。  
ルール](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom3.PNG) を作成 ![には   
  
6.  **[規則の構成]** ページの **[要求規則名]** に、この規則の表示名を入力します。 **[カスタム規則]** で、この規則に必要な要求規則言語の構文を入力するか、貼り付けます。  
ルール](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom4.PNG) を作成 ![には     

7.  **[完了]** をクリックします。  
  
8.  **[要求規則の編集]** ダイアログボックスで、 **[OK]** をクリックして規則を保存します。   

















   
  
## <a name="to-create-a-rule-to-send-claims-by-using-a-custom-claim-in-windows-server-2012-r2"></a>Windows Server 2012 R2 でカスタム要求を使用して要求を送信するための規則を作成するには 
  
1.  サーバーマネージャーで、 **[ツール]** をクリックし、 **[AD FS の管理]** をクリックします。  
  
2.  コンソールツリーの [ **AD FS\\の信頼関係**] で、 **[要求プロバイダー信頼]** または **[証明書利用者信頼]** をクリックし、この規則を作成する一覧内の特定の信頼をクリックします。  
  
3.  選択した信頼を右\-クリックし、 **[要求規則の編集]** をクリックします。  
ルール](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG) を作成 ![には 
  
4.  **[要求規則の編集]** ダイアログボックスで、次のいずれかのタブを選択します。このタブは、編集している信頼と、この規則を作成する規則セットによって異なります。次に、 **[規則の追加]** をクリックして、その規則セットに関連付けられている規則ウィザードを開始します。  
  
    -   **受け入れ変換規則**  
  
    -   **発行変換規則**  
  
    -   **発行承認規則**  
  
    -   **委任の承認規則**  
ルール](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG) を作成 ![には
  
5.  **[規則テンプレートの選択]** ページの **[要求規則テンプレート]** で、 **[カスタム規則を使用して要求を送信]** する を一覧から選択し、 **[次へ]** をクリックします。  
ルール](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom1.PNG) を作成 ![には   
  
6.  **[規則の構成]** ページの **[要求規則名]** に、この規則の表示名を入力します。 **[カスタム規則]** で、この規則に必要な要求規則言語の構文を入力するか、貼り付けます。  
ルール](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom2.PNG) を作成 ![には     

7.  **[完了]** をクリックします。  
  
8.  **[要求規則の編集]** ダイアログボックスで、 **[OK]** をクリックして規則を保存します。  

## <a name="additional-references"></a>その他の参照情報 
[要求規則を構成する](Configure-Claim-Rules.md)  
 
[チェックリスト: 証明書利用者信頼の要求規則を作成する](https://technet.microsoft.com/library/ee913578.aspx)  

[チェックリスト: 要求プロバイダー信頼の要求規則を作成する](https://technet.microsoft.com/library/ee913564.aspx)  
  
[承認要求規則を使用する場合](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)  

[要求の役割](../../ad-fs/technical-reference/The-Role-of-Claims.md)  
  
[要求規則の役割](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md) 
