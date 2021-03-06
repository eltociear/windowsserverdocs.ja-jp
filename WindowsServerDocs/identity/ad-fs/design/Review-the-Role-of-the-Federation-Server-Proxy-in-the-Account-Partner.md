---
ms.assetid: 1b3a03c0-5558-4177-9b2f-e9d6ce3271cd
title: アカウント パートナー内のフェデレーション サーバー プロキシの役割を確認する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: cd04c8e73cb2b8da69d6ab0cf0e8117f51536abf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858565"
---
# <a name="review-the-role-of-the-federation-server-proxy-in-the-account-partner"></a>アカウント パートナー内のフェデレーション サーバー プロキシの役割を確認する

Active Directory フェデレーションサービス (AD FS) \(AD FS\) のアカウントパートナー組織の境界ネットワークにおけるフェデレーションサーバープロキシの主要な役割は、インターネット経由でログオンするクライアントコンピューターから認証資格情報を収集し、それらの資格情報を、アカウントパートナー組織の企業ネットワーク内にあるフェデレーションサーバーに渡すことです。 クライアントコンピューターのアカウントは、アカウントパートナーの属性ストアに格納されます。  
  
フェデレーションサーバープロキシは、アカウントパートナー組織のニーズに合わせてどのように構成するかに応じて、次の役割の1つまたは複数で機能させることもできます。  
  
-   セキュリティトークンのリレー: フェデレーションサーバーは、フェデレーションサーバープロキシにセキュリティトークンを発行し、次にそのトークンをクライアントコンピューターにリレーします。 セキュリティ トークンは、そのクライアント コンピューターから特定の証明書利用者にアクセスするために使用されます。  
  
-   資格情報の収集—フェデレーションサーバープロキシは、clientlogon .aspx\) \(既定のクライアントログオン Web フォームを使用して、フォーム\-ベースの認証を通じてパスワード\-ベースの資格情報を収集します。 ただし、このフォームをカスタマイズして、Secure Sockets Layer \(SSL\) クライアント認証など、サポートされているその他の種類の認証を受け入れることができます。 このページをカスタマイズする方法の詳細については、「 [http:\/\/go.microsoft.com\/fwlink\/?」 \(「クライアントログオンとホーム領域検出ページのカスタマイズ」を参照してください。LinkId\=104275](https://go.microsoft.com/fwlink/?LinkId=104275)\)。 フェデレーションサーバープロキシは、Windows 統合認証を通じて資格情報を受け入れません。  
  
要約すると、アカウントパートナーのフェデレーションサーバープロキシは、企業ネットワーク内に配置されているフェデレーションサーバーへのクライアントログオンのプロキシとして機能します。 また、フェデレーションサーバープロキシを使用すると、証明書利用者に送信されるインターネットクライアントにセキュリティトークンを配布することも容易になります。  
  
> [!CAUTION]  
> アカウントパートナーのエクストラネットでフェデレーションサーバープロキシを公開すると、インターネットにアクセスできるすべてのユーザーがクライアントログオン Web フォームにアクセスできるようになります。 これにより、組織は、AD DS\)\(企業 Active Directory Domain Services に格納されているユーザーアカウントのアカウントロックアウトをトリガーする可能性があるパスワード\-ベースの攻撃やブルートフォース攻撃など、一部のパスワードベースの攻撃に対して脆弱になる可能性があります。  
  

## <a name="see-also"></a>参照
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
