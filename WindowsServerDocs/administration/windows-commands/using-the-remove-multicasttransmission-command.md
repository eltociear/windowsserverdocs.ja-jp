---
title: /Get-multicasttransmission
description: /Get-multicasttransmission の Windows コマンドに関するトピック。イメージのマルチキャスト転送を無効にします。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9a7f5c31-bfbf-425d-9129-a6f9173fe83d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36bb666b841c4c0c33f12c5ca766e619afc176ef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830335"
---
# <a name="using-the-remove-multicasttransmission-command"></a>/Remove-multicasttransmission コマンドを使用してください。

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージのマルチキャスト転送を無効にします。 **/Force**を指定しない限り、既存のクライアントはイメージの転送を完了しますが、新しいクライアントは参加できません。

## <a name="syntax"></a>構文
**Windows Server 2008**
```
wdsutil /remove-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image Group>] [/Filename:<File name>] [/force]
```
**Windows Server 2008 R2**ブートイメージ:
```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
\x20    [/Server:<Server name>]
\x20  mediatype:Boot
\x20    /Architecture:{x86 | ia64 | x64}
\x20    [/Filename:<File name>]
```
インストールイメージの場合:
```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group
        [/Filename:<File name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
メディア:<Image name>|イメージの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|
メディアの種類: {インストール&#124;ブート}|イメージの種類を指定します。 このオプションに設定する必要があります **インストール** Windows Server 2008 用です。|
|/アーキテクチャ: {x86 & #124; ia64 & #124; x64}|転送の開始に関連付けられているブート イメージのアーキテクチャを指定します。 さまざまなアーキテクチャでブート イメージで同じイメージの名前を指定することも可能であるために、正しい転送が使用されるようにするアーキテクチャを指定してください。|
|\mediaGroup:<Image group name>]|イメージを含むイメージ グループを指定します。 イメージ グループ名が指定されていないサーバーに 1 つだけのイメージ グループが存在する場合は、そのイメージ グループを使用します。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループ名を指定するこのオプションを使用する必要があります。|
|[/ファイル名:<File name>]|ファイル名を指定します。 場合は、ソース イメージは、名前によって一意に識別できない、ファイル名を指定するこのオプションを使用する必要があります。|
|/force|転送を削除し、すべてのクライアントを終了します。 **/Force**オプションの値を指定しない限り、既存のクライアントはイメージの転送を完了できますが、新しいクライアントは参加できません。|
## <a name="examples"></a><a name=BKMK_examples></a>例
名前空間を停止する (現在のクライアントは、送信、完了は新しいクライアントは参加できません) の種類。
```
wdsutil /remove-MulticastTransmissiomedia:Vista with Office
/Imagetype:Install
```
```
wdsutil /remove-MulticastTransmissiomedia:x64 Boot Image
/Imagetype:Boot /Architecture:x64
```
すべてのクライアントの終了時に、次のように入力します。
```
wdsutil /remove-MulticastTransmission /Server:MyWDSServer
/Image:Vista with Officemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /force
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のポイント](command-line-syntax-key.md)
[get AllMulticastTransmissions コマンドを使用して](using-the-get-allmulticasttransmissions-command.md)
[/get-multicasttransmission コマンドを使用して](using-the-get-multicasttransmission-command.md)
[MulticastTransmission 新しいコマンドを使用して](using-the-new-multicasttransmission-command.md)
[サブコマンド:/start-multicasttransmission](subcommand-start-multicasttransmission.md)
