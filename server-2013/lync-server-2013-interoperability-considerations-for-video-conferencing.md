﻿---
title: ビデオ会議の相互運用性に関する考慮事項
TOCTitle: ビデオ会議の相互運用性に関する考慮事項
ms:assetid: 31ead3b5-ed95-42d4-96e2-7d9403d5c026
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204790(v=OCS.15)
ms:contentKeyID: 48271699
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ビデオ会議の相互運用性に関する考慮事項

 

_**トピックの最終更新日:** 2012-10-02_

このセクションでは、レガシ クライアントと Lync Server 2013 プールの間に、または Lync Server 2013 クライアントとレガシ プールの間に相互運用性がある場合の、移行の共存フェーズ中のユーザー エクスペリエンスについて説明します。

## Lync Server 2013 プール

レガシ クライアントが Lync Server 2013 プールで使用されるとき、ユーザー エクスペリエンスは以下のようになります。

  - 2 者間通話では、ビデオ解像度はレガシ プールと同じです。

  - マルチパーティの電話会議、ビデオ解像度、およびビデオ会議の機能は、レガシ プールと同じです。ギャラリー ビューと高解像度は使用できません。

## レガシ プール

Lync Server 2013 クライアントがレガシ プールで使用されるとき、ユーザー エクスペリエンスは以下のようになります。

  - 2 者間通話では、Lync Server 2013 クライアントは以下の新機能を使用できます。
    
      - 両方の参加者が Lync Server 2013 クライアントを使用している場合は、H.264 を使用できます。
    
      - Lync Server 2013 クライアントは TotalReceiveVideoBitRateKb の既定値を使用します。これは、レガシ サーバーがインバンド準備でこの情報を送信しないことによります。

  - マルチパーティの電話会議、ビデオ解像度、およびビデオ会議の機能は、レガシ プール内のレガシ クライアントでのユーザー エクスペリエンスと同じです。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>レガシ サーバーが Lync Server 2013 クライアントをホストするとき、プール上のすべてのユーザーが低解像度のビデオのみを受信し、高解像度ビデオを送信するように、ビデオ会議帯域幅を構成できます。この例は、メディア構成で MaxVideoRateAllowed が CIF-250K に設定され、会議ポリシーで VideoBitRateKb が 2000 kbps に設定された場合です。この設定では、プール上のユーザーは高解像度を送信できないことになります。<br />
MaxVideoRateAllowed が Lync Server 2013 クライアントでは使用されなくなったことにより、Lync Server 2013 クライアントからの高解像度ビデオの要求を拒否することはできません。その代わりに、すべてのプール上のユーザーの会議ポリシーで VideoBitRateKb を MaxVideoRateAllowed と同じ値に設定します (つまり、CIF が 250 kbps、VGA が 600 kbps、HD が 1500 kbps に設定されます)。</td>
</tr>
</tbody>
</table>
