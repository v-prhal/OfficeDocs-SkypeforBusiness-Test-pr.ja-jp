﻿---
title: 'Lync Server 2013: 通話受付管理のベスト プラクティス'
TOCTitle: 通話受付管理のベスト プラクティス
ms:assetid: 97173cca-8175-4ae2-a247-eb7ef809da93
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398770(v=OCS.15)
ms:contentKeyID: 48272907
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の通話受付管理のベスト プラクティス

 

_**トピックの最終更新日:** 2012-09-22_

パフォーマンスの向上と展開の簡略化を実現するには、通話受付管理を展開するときに次のベスト プラクティスを適用します。

  - 現在のメディア トラフィックと予測されるメディア トラフィックに対して WAN が十分にプロビジョニングされていることを確認します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>帯域幅制限にバッファーを考慮することをお勧めします。合計使用帯域幅に影響し、帯域幅制限の超過を招く可能性のある競合状態が発生する場合があります。たとえば、メディア トラフィックが帯域幅制限に近づいているときに 2 つの通話を開始しようとすると、一方の通話の方が早く開始されたためにもう一方の通話が拒否されることがあります。</td>
    </tr>
    </tbody>
    </table>


  - 最適な CAC 設定を選択し、ネットワークの使用状況の変化に合わせて CAC 設定を更新できるように、ネットワークの使用状況と通話詳細記録を監視します。

  - CAC 帯域幅ポリシーを使用して QoS 設定を補完します。

  - ブロックされた通話を PSTN に再ルーティングする場合、PSTN の機能と処理能力を確認します。詳細については、「[Lync Server 2013 での発信音声ルーティングの計画](lync-server-2013-planning-outbound-voice-routing.md)」を参照してください。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>処理能力は、潜在的な PSTN の再ルーティングをサポートするために開く必要のあるポート数を表します。</td>
    </tr>
    </tbody>
    </table>

