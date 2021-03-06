---
title: DirectAccess の展開の前提条件
description: このトピックでは、Windows Server 2016 での DirectAccess 展開の前提条件について説明します。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 57c7e039-42ef-4909-867a-b5f669c9e74e
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 5916c5bb87d7bdb10bcc32e24647923d434de2e7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857450"
---
# <a name="prerequisites-for-deploying-directaccess"></a>DirectAccess の展開の前提条件

>適用対象: Windows Server (半期チャネル)、Windows Server 2016

次の表は、構成ウィザードを使用して DirectAccess を展開するために必要な前提条件を示しています。  
  
|||  
|-|-|  
|シナリオ|前提条件|  
|[はじめにウィザードを使用して単一の DirectAccess サーバーを展開する](../../remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md)|-すべてのプロファイルで Windows ファイアウォールを有効にする必要があります。<p>-Windows 10&reg;を実行しているクライアントでのみサポートされています。 <br />              Windows&reg; 8、Windows&reg; 8.1 Enterprise。<p>-公開キー基盤は必要ありません。<p>-2 要素認証の展開ではサポートされていません。 認証にはドメインの資格情報が必要です。<p>-現在のドメイン内のすべてのモバイルコンピューターに DirectAccess を自動的に展開します。<p>-インターネットへのトラフィックは、DirectAccess を経由しません。 強制トンネルの構成はサポートされません。<p>-DirectAccess サーバーは、ネットワークロケーションサーバーです。<p>-ネットワークアクセス保護 (NAP) はサポートされていません。<p>-DirectAccess 管理コンソールまたは Windows PowerShell コマンドレット以外の機能を使用してポリシーを変更することはできません。<p>-マルチサイト構成の場合、または今後は、 [「詳細設定を使用した単一の DirectAccess サーバーの展開](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)」のガイダンスに従ってください。|  
|[詳細設定を使用して単一の DirectAccess サーバーを展開する](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)|-公開キー基盤を展開する必要があります。<br />    詳細については、「[テストラボガイドミニモジュール: Windows Server 2012 用の基本的な PKI](https://social.technet.microsoft.com/wiki/contents/articles/7862.test-lab-guide-mini-module-basic-pki-for-windows-server-2012.aspx)」を参照してください。<p>-すべてのプロファイルで Windows ファイアウォールを有効にする必要があります。<p>次のサーバーオペレーティングシステムでは、DirectAccess がサポートされています。<p>-Windows Server 2016 のすべてのバージョンを DirectAccess クライアントまたは DirectAccess サーバーとして展開できます。<br />-Windows Server 2012 R2 のすべてのバージョンを DirectAccess クライアントまたは DirectAccess サーバーとして展開できます。<br />-Windows Server 2012 のすべてのバージョンを DirectAccess クライアントまたは DirectAccess サーバーとして展開できます。<br />-Windows Server 2008 R2 のすべてのバージョンを DirectAccess クライアントまたは DirectAccess サーバーとして展開できます。<p>次のクライアントオペレーティングシステムでは、DirectAccess がサポートされています。<p>-Windows 10&reg; Enterprise<br />-Windows 10&reg; Enterprise 2015 Long Term Servicing Branch (LTSB)<br />-Windows&reg; 8 および 8.1 Enterprise<br />-Windows&reg; 7 Ultimate<br />-Windows&reg; 7 Enterprise<p>-Force トンネルの構成は、KerbProxy 認証ではサポートされていません。<p>-DirectAccess 管理コンソールまたは Windows PowerShell コマンドレット以外の機能を使用してポリシーを変更することはできません。<p>-NAT64/DNS64 と IPHTTPS サーバーロールを別のサーバーに分離することはサポートされていません。|  
  


