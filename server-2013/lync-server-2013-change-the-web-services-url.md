﻿---
title: Web サービス URL の変更
TOCTitle: Web サービス URL の変更
ms:assetid: 4cee37c0-3b99-4207-997f-bf4229d760c0
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg520992(v=OCS.15)
ms:contentKeyID: 48272027
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Web サービス URL の変更

 

_**トピックの最終更新日:** 2015-11-16_

フロントエンド プールと Standard Edition サーバーをセットアップする際には、オプションで外部 Web ファームの完全修飾ドメイン名 (FQDN) と関連するポートを構成します。Lync Server 展開ウィザード の実行時にこの URL を構成しなかった場合は、これらの設定を手動で構成する必要があります。 これらは推奨されている既定ポートであるため、管理者は通常この設定を変更する必要はありません。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>次のスクリーン ショットは Standard Edition サーバーを構成中の画面なので、[FQDN のオーバーライド] オプションは無効になっています。このオプションは、フロント エンド プールの Enterprise Edition サーバーを構成するときに有効になります。</td>
</tr>
</tbody>
</table>


![Web サービスのプール設定の編集](images/Gg520992.fbdf5cc9-479a-463f-bb1d-53575ecdfc9d(OCS.15).jpg "Web サービスのプール設定の編集")

## Web サービスを構成する

1.  トポロジ ビルダーがインストールされているコンピューターに、Domain Admins グループおよび RTCUniversalServerAdmins グループのメンバーとしてログオンします。

2.  トポロジ ビルダーを以下の手順で起動します。\[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Server トポロジ ビルダー**\] の順にクリックします。

3.  トポロジ ビルダー では、\[**Standard Edition フロントエンド サーバー**\]、\[**Enterprise Edition フロントエンド プール**\]、および \[**ディレクトリ プール**\] の下のコンソール ツリーでプール名を選択します。 プール名を右クリックして \[**プロパティの編集**\] をクリックし、\[**Web サービス**\] をクリックします。

4.  \[**外部 Web サービスの FQDN**\] を追加または編集し、\[**OK**\] をクリックします。
    

    > [!WARNING]
    > 複数のフロント エンド プールまたはフロント エンド サーバーがある場合は、外部 Web サービスの FQDN は一意でなければなりません。たとえばフロント エンド サーバーの外部 Web サービスの FQDN を <STRONG>pool01.contoso.com</STRONG> に定義した場合、別のフロント エンド プールまたはフロント エンド サーバーには <STRONG>pool01.contoso.com</STRONG> を使用できません。またディレクターも展開する場合は、ディレクターまたはディレクター プールに指定されている外部 Web サービスの FQDN は、他のディレクターまたはディレクター プール、さらにフロント エンド プールまたはフロント エンド サーバーとは別のものでなければなりません。



5.  ご使用の環境でリッスン ポートと公開ポートが正しく構成されていることを確認します。

6.  ご使用の環境のすべての Standard Edition サーバー、フロントエンド プール、およびディレクター プールでこのステップを繰り返します。

7.  コンソール ツリーで \[**Lync Server 2013**\] をクリックし、次に \[**操作**\] ウィンドウで \[**トポロジの公開**\] をクリックします。

リッスン ポートと公開ポートを構成する際には、次の要件に注意する必要があります。

  - 表示されるリッスン ポートは、各フロントエンド サーバー上のインターネット インフォメーション サービス (IIS) 用に構成されているポートです。

  - IIS では、内部と外部のリッスン ポートが異なる必要があります。 外部のリッスン ポートの場合、これらは通常同じです。1 つが内部 Web トラフィックのハードウェア ロード バランサーを表し、もう 1 つが外部 Web トラフィックのリバース プロキシ サーバーを表すためです。

  - フロント エンド プール、ディレクター、またはディレクター プールの内部 Web サービスを上書きして、独自の FQDN を定義できます。
    

    > [!WARNING]
    > 独自に定義した FQDN で内部 Web サービスを上書きする場合は、各 FQDN は他のフロント エンド プール、ディレクター、またはディレクター プールとは別のものにする必要があります。



  - 公開ポートは、リバース プロキシまたはハードウェア ロード バランサー上で、リッスン ポートとして構成する必要があります。

  - フロントエンド プールの場合 (例には表示されていません)、内部 SIP プールの FQDN は内部 Web サービスの FQDN と異なる必要があります。これは、ハードウェア ロード バランサー経由の Web トラフィックと内部 SIP プールのトラフィックが、DNS ロード バランサー経由でやり取りされるためです。 この要件を満たす必要があります。

  - Lync Server Standard Edition の展開の場合、内部 Web サービスの FQDN の上書きは不要で許可されません。このサーバーは負荷分散できないためです。

  - ご使用の環境に、内部 SIP トラフィックと Web トラフィックの両方で使用するハードウェア ロード バランサーがあると、トポロジ ビルダーでは区別できません。
    
    Web サービスの FQDN は、互いに簡単に区別できる必要があります。そうすることで、URL リダイレクションはクライアントのために適切なサーバーを指すようにできます。たとえば、2 つの FQDN の一方の名前を meeting.contoso.com、他方を conferencing.contoso.com にするとします。それでは、さらに似た名前の FQDN (meet1.contoso.com と meet2.contoso.com など) がある場合に、リダイレクションに問題が発生する可能性があります。

境界ネットワークでは、外部 Web サービスがリバース プロキシと共に機能します。クライアントはこのような Web サービスを使用して、外部アクセスを提供します。ここで構成される FQDN は、クライアントのログイン時にクライアントに送信され、リモート接続時にリバース プロキシに再度 HTTPS 接続するために使用されます。 リバース プロキシ サーバーは、外部 Web サービスの FQDN を内部のハードウェア ロード バランサーに転送するか、プールに直接転送します。リバース プロキシでは、外部 Web サービスの FQDN を内部 Web サーバーの IP アドレスに解決できる必要があります。外部 Web サービスの FQDN は、公衆インターネットに解決できる必要があります。

内部サーバーが Standard Edition サーバー である場合、内部 FQDN は Standard Edition サーバー の FQDN です。内部サーバーがフロントエンド プールの場合、FQDN は内部 Web ファーム サーバーを負荷分散するハードウェア ロード バランサーの仮想 IP (VIP) です。複数の Enterprise Edition サーバーが含まれるフロントエンド プールには、ハードウェア ロード バランサーが必要です。Standard Edition サーバーまたは単一の Enterprise Edition フロントエンド サーバーには、ロード バランサーは不要です。

