﻿---
title: 'Lync Server 2013: セキュリティ構成ウィザードで IIS のポートを閉じた後にサーバーを再アクティブ化する'
TOCTitle: セキュリティ構成ウィザードで IIS のポートを閉じた後にサーバーを再アクティブ化する
ms:assetid: cb8e17cf-f8c1-4099-b63b-c242d656c26a
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398851(v=OCS.15)
ms:contentKeyID: 48273587
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# セキュリティ構成ウィザードで IIS のポートを閉じた後にサーバーを再アクティブ化する

 

_**トピックの最終更新日:** 2012-10-01_

一部の Lync Server 2013 役割は、 Web サービスを インターネット インフォメーション サービス (IIS) ポート 4443 で実行します。 Lync Server 展開ウィザード Bootstrapper.exe を実行するか、 **Enable-CsComputer** コマンドレットを実行すると、ファイアウォールで例外が作成され、そのポートが開かれます。その後、 Windows Server 2008 R2 のセキュリティ構成ウィザード (または他の堅牢性向上スクリプト) を実行すると、ポート 4443 がブロックされ、外部クライアントは Web サービスにアクセスできなくなります。ポートを開くには、ファイアウォールの例外を直接変更するか、サーバーを再アクティブ化します。

## 展開ウィザードを使用してサーバーを再アクティブ化するには

1.  Lync Server 展開ウィザードページで、\[**手順 2: Lync Server コンポーネントの設定または削除**\] の横の \[**実行**\] をクリックします。

2.  \[**Lync Server コンポーネントの設定**\] ページで、\[**次へ**\] をクリックします。

3.  \[**コマンドの実行**\] ページで、タスク状態が完了と表示されたら、\[**完了**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>bootstrapper.exe または <strong>Enable-CsComputer</strong> を使用して、サーバーを再アクティブ化することもできます。</td>
    </tr>
    </tbody>
    </table>

