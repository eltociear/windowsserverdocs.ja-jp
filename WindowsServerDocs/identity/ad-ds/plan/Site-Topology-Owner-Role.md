---
ms.assetid: af76ddbe-83a2-4a62-9989-873e3bb1c772
title: サイト トポロジの所有者の役割
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 1e90c88db6a40de48444e047628abcee6cc3673b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80821825"
---
# <a name="site-topology-owner-role"></a>サイト トポロジの所有者の役割

>適用対象: Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サイトトポロジを管理する管理者は、サイトトポロジの所有者と呼ばれます。 サイトトポロジの所有者は、サイト間のネットワークの条件を理解し、Active Directory Domain Services (AD DS) の設定を変更してサイトトポロジへの変更を実装する権限を持っています。 サイトトポロジの変更は、レプリケーショントポロジの変更に影響します。 サイトトポロジの所有者の責任は次のとおりです。  
  
-   ネットワーク接続が変更された場合に、サイトトポロジの変更を制御する。  
  
-   ネットワークグループからのネットワーク接続とルーターに関する情報の取得と管理。 サイトトポロジの所有者は、サブネットアドレス、サブネットマスク、およびそれぞれが属する場所の一覧を管理する必要があります。 サイトトポロジの所有者は、サイトのトポロジに影響を与えるネットワーク速度と容量に関する問題も理解して、サイトリンクのコストを効果的に設定する必要があります。  
  
-   ドメインコントローラーの IP アドレスが別のサイトの別のサブネットに変更された場合、またはサブネット自体が別のサイトに割り当てられている場合は、サイト間のドメインコントローラーを表す Active Directory サーバーオブジェクトを移動します。 どちらの場合も、サイトトポロジ所有者は、ドメインコントローラーの Active Directory サーバーオブジェクトを新しいサイトに手動で移動する必要があります。  
  


