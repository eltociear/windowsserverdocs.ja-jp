---
ms.assetid: 74ef34c8-e13f-499b-b2bb-952ad7036622
title: フェデレーション サーバーの名前解決の要件
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b455596910e1b04569e087843da8b88f9f020137
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853035"
---
# <a name="name-resolution-requirements-for-federation-servers"></a>フェデレーション サーバーの名前解決の要件

企業ネットワーク上のクライアントコンピューターが Active Directory フェデレーションサービス (AD FS) \(\)AD FS によって保護されているアプリケーションまたは Web サービスにアクセスしようとすると、まずフェデレーションサーバーに対して認証を行う必要があります。 認証する方法の 1 つでは、会社のネットワーク クライアントが Windows 統合認証を通じて、ローカルのフェデレーション サーバーにアクセスします。  
  
## <a name="configure-corporate-dns"></a>企業 DNS を構成する  
ローカルのフェデレーション サーバーで Windows 統合認証を通じて正常な名前解決を実行、ドメイン ネーム システム \(DNS\) アカウントの企業ネットワーク内には、新しいホストのパートナーを構成 \(A\) 完全修飾ドメイン名を解決するリソース レコード \(FQDN\) フェデレーション サーバー クラスターの IP アドレスにフェデレーション サーバーのホスト名です。  
  
次の図を見ると、特定のシナリオでのこのタスクの実現方法がわかります。 この場合は、Microsoft Network Load Balancing \(NLB\) 既存のフェデレーション サーバー ファームの 1 つのクラスターの FQDN 名と 1 つのクラスター IP アドレスを提供します。  
  
![名の要件](media/adfs2_deploy_single_fs.gif)  
  
NLB を使用する FQDN をクラスターまたはクラスターの IP アドレスを構成する方法については、次を参照してください。 [クラスター パラメーターを指定して](https://go.microsoft.com/fwlink/?LinkId=75282)します。  
  
会社の DNS にフェデレーション サーバーを構成する方法については、次を参照してください [ホストと #40; を追加します。(&) #41 です。フェデレーション サーバー用の会社の DNS リソース レコード](../../ad-fs/deployment/Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md)します。  
  
境界ネットワーク内のフェデレーション サーバー プロキシを構成する方法については、次を参照してください。 [フェデレーション サーバー プロキシの名前解決要件](Name-Resolution-Requirements-for-Federation-Server-Proxies.md)します。  
  

## <a name="see-also"></a>参照
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
