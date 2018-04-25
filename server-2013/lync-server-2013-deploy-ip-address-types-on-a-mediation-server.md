﻿---
title: 'Lync Server 2013: 仲介サーバーに IP アドレス タイプを展開する'
TOCTitle: 仲介サーバーに IP アドレス タイプを展開する
ms:assetid: 689ebed5-96ee-4cd4-b7ae-ee2a86a1d9b3
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204964(v=OCS.15)
ms:contentKeyID: 48272379
ms.date: 07/20/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の仲介サーバーに IP アドレス タイプを展開する

 

_**トピックの最終更新日:** 2016-07-28_

トポロジ ビルダーを使用して次の手順のステップを実行し、IP アドレス タイプを 仲介サーバー に展開します。

## 仲介サーバーに IP アドレス タイプを展開するには

  - トポロジ ビルダーの \[**仲介プール**\] の下で、プール内のサーバーを右クリックし、\[**プロパティの編集**\] を選択します (または、サーバーを選択し、\[**操作**\] メニューの \[**プロパティの編集**\] をクリックします)。

  - \[**プロパティの編集**\] ダイアログ ボックスで、構成する IP アドレス タイプを選択します。デュアル スタック構成の場合は、次の図のように、\[**IPv4 を有効にする**\] および \[**IPv6 を有効にする**\] を選択します。
    
    **仲介サーバー プールの \[プロパティの編集\] ダイアログ ボックス**
    
    ![Lync Server、FQDN を含む全般プロパティ ページ](images/JJ204964.4e650aca-dbff-4a86-b10d-f0162c032539(OCS.15).png "Lync Server、FQDN を含む全般プロパティ ページ")
    
      - \[ **すべての構成済み IP アドレスを使用する**\]。コンピューター上で定義されているすべての IP アドレスの使用を許可する場合は、このオプションを選択します。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>これは、IP version 6 (IPv6) 構成の推奨オプションです。</td>
        </tr>
        </tbody>
        </table>
    
      - \[ **サービスの使用を、指定したアドレスに制限する**\]。新しいサーバーで使用する特定のアドレスを指定する場合は、このオプションを選択します。このオプションを選択する場合は、プライマリ IP アドレスの値を入力する必要があります。
    
      - \[ **プライマリ IP アドレス**\]。公衆交換電話網 (PSTN) 以外のすべての通信でサーバーが使用する IP アドレスを入力します。入力する IP アドレスは、選択されているアドレス タイプの形式に一致している必要があります。
    
      - \[ **PSTN IP アドレス**\]。フロントエンド サーバーで仲介サーバーが共存する場合は、PSTN IP アドレスを定義します。このアドレスは、選択されているアドレス タイプの形式に一致している必要があります。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>追加のネットワーク インターフェイス カード (NIC) を取り付けて Lync Server 2013 の PSTN IP アドレス構成をサポートすることはできません。Lync Server 2013 でサポートされている NIC 構成の詳細については、「<a href="lync-server-2013-server-hardware-platforms.md">Lync Server 2013　用のサーバー ハードウェア プラットフォーム</a>」を参照してください。</td>
        </tr>
        </tbody>
        </table>
