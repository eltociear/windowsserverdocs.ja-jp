---
title: Scwcmd の構成
description: '* * * * のリファレンストピック'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6528b9dc-3d82-4228-b734-ed717458d74c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54f488eea2478c0b38f7ed9bea5ec15c0db3538f
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820982"
---
# <a name="scwcmd-configure"></a>Scwcmd: 構成

> 適用対象: Windows Server 2012 R2、Windows Server 2012

コンピューターには、セキュリティ構成ウィザード SCW によって生成されたセキュリティ ポリシーを適用します。 このコマンド ライン ツールでは、入力としてコンピューター名の一覧も受け取ります。

## <a name="syntax"></a>構文

```
scwcmd configure [[[/m:<ComputerName> | /ou:<OuName>] /p:<Policy>] | /i:<ComputerList>] [/u:<UserName>] [/pw:<Password>] [/t:<Threads>]
```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|/m: \< ComputerName>|NetBIOS 名、DNS 名、または構成するコンピューターの IP アドレスを指定します。 場合、 **/m** パラメーターが指定されている、 **/p** パラメーターも指定する必要があります。|
|/ou: \< ouname>|Active Directory ドメイン サービスでは、組織単位 (OU) の完全修飾ドメイン名 (FQDN) を指定します。 場合、 **/ou** パラメーターが指定されている、 **/p** パラメーターも指定する必要があります。 指定したポリシーに従って、OU 内のすべてのコンピューターが分析されます。|
|/p: \< ポリシー>|構成の実行に使用する .xml ポリシー ファイルのパスとファイル名を指定します。|
|/i: \< computerlist>|予想されるポリシー ファイルと共にコンピューターの一覧を含む .xml ファイルのパスとファイル名を指定します。 .Xml ファイル内のすべてのコンピューターは、対応するポリシー ファイルに基づいて構成されます。 サンプルの .xml ファイルは、%windir%\security\samplemachinelist.xml です。|
|/u: \< ユーザー名>|リモート コンピューターを構成するときに使用する、代替のユーザー資格情報を指定します。 既定値は、ユーザーには、ログオンしています。|
|/pw: \< パスワード>|リモート コンピューターを構成するときに使用する、代替のユーザー資格情報を指定します。 既定値は、ログオン ユーザーのパスワードです。|
|/t: \< スレッド>|構成処理中に保守する必要が未処理の構成の同時操作の数を指定します (既定値 = 40、MinValue = 1、最大値 = 1000)。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈

Scwcmd.exe は Windows Server 2008 R2、Windows Server 2008 または Windows Server 2003 を実行するコンピューターにできるだけです。

## <a name="examples"></a>例

ファイル webpolicy.xml に対してセキュリティ ポリシーを構成するには、次のように入力します。
```
scwcmd configure /p:webpolicy.xml
```
コンピューターのセキュリティ ポリシーを構成ファイル webpolicy.xml に対して 172.16.0.0 を webadmin アカウントの資格情報を使用して、次のように入力します。
```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```
セキュリティ ポリシーを構成する、最大 100 個のスレッドのリスト campusmachines.xml 上のすべてのコンピューターで、次のように入力します。
```
scwcmd configure /i:campusmachines.xml /t:100
```
DomainAdmin アカウントの資格情報を使用して、ファイル webpolicy.xml に対してウェブサーバ OU 内のすべてのコンピューターにセキュリティ ポリシーを構成するには、次のように入力します。
```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)