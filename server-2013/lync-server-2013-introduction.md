﻿---
title: 'Lync Server 2013: 概要'
TOCTitle: Lync Server の概要
ms:assetid: 99dd6b65-e591-421f-852b-ee9fe9588998
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398795(v=OCS.15)
ms:contentKeyID: 48272942
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の概要

 

_**トピックの最終更新日:** 2015-03-09_

Lync Server 2013 および Lync 2013 のようなクライアント ソフトウェアは、ユーザーの物理的な位置に関係なく、ユーザーが新しい方法で接続され、接続された状態を保つことを可能にします。 Lync および Lync Server は、さまざまなユーザーの通信方法を 1 つのクライアント インターフェイスに統合し、統合プラットフォームとして展開され、1 つの管理インフラストラクチャを通じて管理されます。

次の表とセクションでは、Lync Server がユーザーに提供する主な機能セットや*負荷*について説明しています。


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>負荷</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IM とプレゼンス</p></td>
<td><p>インスタント メッセージング (IM) とプレゼンスにより、ユーザーは効率的かつ効果的に相手を見つけて連絡できます。</p>
<p>IM は、会話履歴を備えるインスタント メッセージング プラットフォームを提供し、MSN/Windows Live、Yahoo!、AOL、Google Talk などパブリック IM ネットワーク ユーザーとのパブリック IM 接続をサポートします。</p>
<div class="alert">

> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012 年 9 月 1 日の時点で、Microsoft Lync パブリック IM 接続のユーザー サブスクリプション ライセンス ("PIC USL") を新規または更新契約において購入することができなくなりました。アクティブなライセンスをお持ちのお客様は、サービスの停止日まで Yahoo! Messenger とのフェデレーションを引き続きご利用いただけます。AOL と Yahoo! に関しては、2014 年 6 月の終了日が発表されています。詳細については、「<A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013 でのパブリック インスタント メッセンジャーの接続のサポート</A>」を参照してください。</P>
> <LI>
> <P>PIC USL は、ユーザー単位および月単位のサブスクリプション ライセンスであり、Lync Server または Office Communications Server と Yahoo! Messenger とのフェデレーションを行うにはこのライセンスが必要です。Microsoft がこのサービスを提供できるのは、Yahoo! からのサポートを条件とするものでしたが、その基盤となる契約の終了が近づいてきました。</P>
> <LI>
> <P>Lync は組織間を接続したり世界中のユーザーと接続したりするための、これまで以上の強力なツールとなります。Windows Live Messenger とのフェデレーションを行うのに、Lync Standard CAL を超えてユーザー/デバイス ライセンスを追加する必要はありません。Skype フェデレーションがこのリストに追加されることで、Lync ユーザーは IM および音声を使用して数億のユーザーにアクセスできます。</P></LI></UL>


</div>
<p>プレゼンスは、ユーザーの個人的な空き時間や通話応答の意思を、[<strong>連絡可能</strong>] や [<strong>取り込み中</strong>] などの共通のステータス、さらには [<strong>一時退席中</strong>] や [<strong>応答しない</strong>] といったさらに詳細なステータスを使って明確にし、表示します。この豊富なプレゼンス情報により、他のユーザーは効果的な連絡方法をすばやく選択できます。</p></td>
</tr>
<tr class="even">
<td><p>電話会議</p></td>
<td><p>Lync Server は、予定された会議の場合も緊急の会議の場合も、IM 会議、音声会議、Web 会議、ビデオ会議、およびアプリケーション共有をサポートします。これらの会議の全種類が 1 つのクライアントでサポートされます。また、 Lync Server はダイヤルイン会議もサポートしており、公衆交換電話網 (PSTN) 電話のユーザーが会議の音声部分に参加できます。</p>
<p>会議はリアル タイムでシームレスに変更および拡大できます。たとえば、1 つの会議を数人のユーザー間のインスタント メッセージのみで開始し、デスクトップ共有を使用するより参加者の多い大規模な音声会議へと、会話の流れを遮ることなくすばやく簡単に切り替えることができます。</p></td>
</tr>
<tr class="odd">
<td><p>エンタープライズ VoIP</p></td>
<td><p>エンタープライズ VoIP は、Lync Server で提供するボイス オーバー IP (VoIP) です。従来の構内交換機 (PBX) システムを強化または置き換える音声オプションを提供します。IP PBX のすべてのテレフォニー機能に加え、エンタープライズ VoIP は豊富なプレゼンス、IM、共同作業、および会議と統合されています。通話応答、保留、再開、着信転送、通話転送、リモート転送などの機能が直接サポートされ、また、個人用短縮ダイヤル キーは連絡先リストに置き換えられ、自動インターコムは IM に置き換えられます。</p>
<p>エンタープライズ VoIP は、通話受付管理 (CAC) による高い可用性、ブランチ オフィスの存続性、およびデータ復元性の拡張オプションをサポートします。</p></td>
</tr>
<tr class="even">
<td><p>リモート ユーザーのサポート</p></td>
<td><p><em>エッジ サーバー</em>と呼ばれるサーバーを展開し、組織のファイアウォールの外に現在いるユーザーに Lync Server の完全な機能を提供し、これらのリモート ユーザーに接続を提供できます。これらのリモート ユーザーは、Lync 2013 がインストールされているパーソナル コンピューター、電話機、または Web インターフェイスを使用して会議に接続できます。</p>
<p>エッジ サーバーを展開すると、パートナーやベンダー組織との<em>フェデレーション</em>も有効にできます。フェデレーション関係によって、ユーザーは連絡先リストにフェデレーション ユーザーを追加したり、フェデレーション ユーザーとプレゼンス情報やインスタント メッセージを交換したり、音声通話やビデオ通話、会議にフェデレーション ユーザーを招待したりできます。</p></td>
</tr>
<tr class="odd">
<td><p>モバイル クライアントのサポート</p></td>
<td><p>加えて、 Lync Server モビリティ サービスでは、サポートされている Apple iOS、Android、Windows Phone、または Nokia モバイル デバイスを使用するユーザーが Lync 機能にアクセスでき、インスタント メッセージの送受信、連絡先の表示、プレゼンスの表示といった操作を実行できます。また、クリックして会議に参加、勤務先から通話、同一番号接続、ボイス メール、不在着信など、モバイル デバイスでいくつかのエンタープライズ VoIP 機能がサポートされます。バックグラウンドで実行されるアプリケーションをサポートしないモバイル デバイス用にプッシュ通知もサポートされます。</p></td>
</tr>
<tr class="even">
<td><p>他の製品との統合</p></td>
<td><p>Lync Server はいくつかの他の製品を統合し、ユーザーと管理者に追加の利点を提供します。</p>
<p>Outlook に会議ツールが統合されているため、開催者は会議のスケジューリングや急な会議の開始を 1 回のクリックだけで実行でき、参加者はきわめて簡単に会議に参加できます。</p>
<p>プレゼンス情報が Outlook と SharePoint に統合されています。</p>
<p>Exchange ユニファイド メッセージング (UM) では、いくつかの統合機能を提供します。ユーザーは、 Lync Server 内で新しいボイス メールがあるかどうかを確認できます。Outlook メッセージ内の再生ボタンをクリックして音声ボイス メールを聞いたり、通知メッセージ内でボイス メールのトランスクリプションを表示したりできます。</p>
<p>また、 Lync Server 2013 を Exchange 2013 と共に実行することによって、両方の製品のクライアントがアクセスできる統合連絡先ストアや Exchange 2013 データベースに保存されている連絡先用の高画質の写真など、いくつかの新機能を有効にできます。</p></td>
</tr>
<tr class="odd">
<td><p>簡単な展開</p></td>
<td><p>サーバーやクライアントの計画と展開に役立つよう、 Lync Server は トポロジ ビルダーを提供します。</p>
<p></p>
<p>トポロジ ビルダーは、 Lync Server のインストール コンポーネントです。 トポロジ ビルダーを使用して、計画トポロジを作成、調整、および公開できます。また、サーバーのインストールを開始する前にトポロジを検証します。個別のサーバーに Lync Server をインストールする際、インストール プログラムはトポロジの指示に従ってサーバーを展開します。</p></td>
</tr>
<tr class="even">
<td><p>簡単な管理</p></td>
<td><p>Lync Server を展開した後、強力で効率的な次の管理ツールを提供します。</p>
<ul>
<li><p>構成の集中管理。変更を集中管理して展開全体にすばやくレプリケートできます。</p></li>
<li><p>Lync Server コントロール パネル。管理者用の新しい Web ベースのグラフィカル ユーザー インターフェイスです。この Web ベースの UI を使用して、 Lync Server 管理者は企業ネットワークの任意の場所からシステムを管理できます。管理者のコンピューターに管理専用のソフトウェアをインストールする必要はありません。</p></li>
<li><p>Lync Server 管理シェル コマンド ライン管理ツール。 Windows PowerShell コマンドライン インターフェイス ベースのツールです。製品のすべての状況を管理するための豊富なコマンド セットを提供し、 Lync Server 管理者は使い慣れたツールを使って反復的なタスクを自動化できます。</p></li>
</ul></td>
</tr>
</tbody>
</table>


IM およびプレゼンス機能はすべての Lync Server 展開で自動的にインストールされますが、会議、エンタープライズ VoIP、およびリモート ユーザー アクセスを展開するかどうかは選択でき、組織のニーズに合わせた展開を調整できます。

## このセクション中

  - [Lync Server 2013 IM とプレゼンス](lync-server-2013-im-and-presence.md)

  - [Lync Server 2013 電話会議](lync-server-2013-conferencing.md)

  - [Lync Server 2013 のエンタープライズ VoIP](lync-server-2013-enterprise-voice.md)

  - [Lync Server 2013 のスケーラビリティ](lync-server-2013-scalability.md)

