﻿---
title: 代理トランザクションを実行する監視ノードの構成
TOCTitle: 代理トランザクションを実行する監視ノードの構成
ms:assetid: cedda508-8881-4079-88d5-49798f342ddf
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ205314(v=OCS.15)
ms:contentKeyID: 48273616
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 代理トランザクションを実行する監視ノードの構成

 

_**トピックの最終更新日:** 2015-03-09_

System Center エージェント ファイルがインストールされたら、次に監視ノード自体を構成する必要があります。監視ノードを構成する手順は監視ノードを境界ネットワークの内側に置くか、外側に置くかによって異なります。

監視ノードの構成時には、そのノードが使用する認証方法の種類も選択する必要があります。Lync Server 2013 では、信頼済みサーバーと資格情報認証という 2 つの方法から 1 つを選択することができます。この 2 つの方法の主な違いを次の表にまとめます。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>構成</th>
<th>説明</th>
<th>サポートされる場所</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>信頼済みサーバー</p></td>
<td><p>内部サーバーを偽装する証明書を使用し、認証チャレンジをバイパスします。</p>
<p>この方法は、各監視ノードで多数のユーザー パスワードではなく、1 つの証明書を管理したいと考える管理者にとって便利です。</p></td>
<td><p>エンタープライズの内側。</p>
<p>この方法では、監視ノードが監視対象のプールと同じドメイン内に存在する必要があることに注意してください。監視ノードと監視対象のプールが別のドメインに存在する場合は、この方法ではなく、資格情報認証を使用します。</p></td>
</tr>
<tr class="even">
<td><p>資格情報認証</p></td>
<td><p>ユーザー名とパスワードを各監視ノードの Windows 資格情報マネージャーに保管します。</p>
<p>このモードは、パスワード管理の手間を必要としますが、エンタープライズの外側に位置する監視ノードの場合には唯一の選択肢となります。このような外側に位置する監視ノードを認証の際に信頼済みのエンドポイントとして扱うことはできません。</p></td>
<td><p>エンタープライズの外側。</p>
<p>エンタープライズの内側。</p></td>
</tr>
</tbody>
</table>


また、MonitoringHost.exe と PowerShell.exe の両方について、ファイアウォールに受信規則があることを確認する必要があります。これらのプロセスがファイアウォールによってブロックされている場合、代理トランザクションは 504 (サーバー タイムアウト) エラーになって失敗します。

