---
ms.assetid: 1df78c2a-5054-4b54-8310-c48ea62e6e0b
title: AD FS サインインページのカスタムエラーメッセージ
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 31da3e65e69910817a78ab1007e897fb5a9ad683
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816435"
---
# <a name="custom-error-messages-for-ad-fs-sign-in-page"></a>AD FS サインインページのカスタムエラーメッセージ  


組織の要件に合わせてカスタム エラー メッセージを構成できます。 次の図に、カスタマイズしたエラー ページの説明と一般エラー メッセージを示します。 エラーメッセージをカスタマイズするには、次の Windows PowerShell コマンドレットを使用します。  
  
![カスタムエラー](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom3.png)  
  
## <a name="customize-the-error-page-description"></a>エラー ページの説明のカスタマイズ  
エラーページの説明をカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  
  

`Set-AdfsGlobalWebContent -ErrorPageDescriptionText "This is Contoso's error page description" ` 

  
## <a name="customize-a-generic-error-message"></a>一般エラー メッセージのカスタマイズ  
一般的なエラーメッセージをカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  
  
 
`Set-AdfsGlobalWebContent -ErrorPageGenericErrorMessage "This is a generic error message.  Contact Contoso IT for assistance." ` 

  
## <a name="customize-an-authorization-error-message"></a>承認エラー メッセージのカスタマイズ  
承認エラーメッセージをカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  
  

    Set-AdfsGlobalWebContent -ErrorPageAuthorizationErrorMessage "You have received an Authorization error.  Contact Contoso IT for assistance."  

  
## <a name="customize-a-device-authentication-error-message"></a>デバイス認証エラー メッセージのカスタマイズ  
デバイス認証エラーメッセージをカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  
  
 
`Set-AdfsGlobalWebContent -ErrorPageDeviceAuthenticationErrorMessage "Your device is not authorized.  Contact Contoso IT for assistance."`  
 
  
## <a name="customize-a-support-email-error-message"></a>サポート電子メール エラー メッセージのカスタマイズ  
AD FS でサポート電子メールアドレスを構成できます。 構成されている場合、AD FS は、エラーの詳細を電子メールで送信するためのリンクをエンドユーザーに自動的に表示します。  
  
サポート電子メールエラーメッセージをカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  
  

    Set-AdfsGlobalWebContent -ErrorPageSupportEmail  "admin@contoso.com"  

  
## <a name="customize-a-relying-party-authorization-message"></a>証明書利用者の承認メッセージのカスタマイズ  
AD FS で、証明書利用者の承認エラーメッセージを構成できます。  
  
証明書利用者のエラーメッセージをカスタマイズするには、次の Windows PowerShell コマンドレットと構文を使用します。  

    Set-AdfsRelyingPartyWebContent -Name fedpassive -ErrorPageAuthorizationErrorMessage "<p> You need to be a member of Security Auditors to access this site. Click <A href='http://accessrequest/'>here</A> for more information.</p>"  


## <a name="additional-references"></a>その他の参照情報 
[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)    
