﻿---
title: フェデレーション ルートとメディア トラフィックの構成
TOCTitle: フェデレーション ルートとメディア トラフィックの構成
ms:assetid: ed6cb922-7863-453a-adce-2ce0ba761d74
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ721925(v=OCS.15)
ms:contentKeyID: 49887207
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# フェデレーション ルートとメディア トラフィックの構成

 

_**トピックの最終更新日:** 2016-12-08_

フェデレーションとは、別々の組織のユーザーがネットワーク境界を越えて通信することを許可する、複数の SIP ドメイン間での信頼関係のことです。 Lync Server 2013 パイロット プールに移行した後は、 Microsoft Office Communications Server 2007 R2 エッジ サーバーのフェデレーション ルートから Lync Server 2013 エッジ サーバーのフェデレーション ルートに移行する必要があります。

単一のサイト展開の場合、以下で説明する手順を使用して、フェデレーション ルートとメディア トラフィック ルートを Office Communications Server 2007 R2 エッジ サーバーおよびディレクターから Lync Server 2013 エッジ サーバーに移行してください。


> [!IMPORTANT]
> フェデレーション ルートとメディア トラフィック ルートを変更するには、 Lync Server 2013 および Office Communications Server 2007 R2 エッジ サーバーの保守作業を行うためのダウンタイムを計画する必要があります。また、この移行プロセスで機能が停止している間は、フェデレーション アクセスも使用できません。ダウンタイムは、ユーザー アクティビティが最も少ない時間帯に予定してください。また、ダウンタイムが発生することをエンド ユーザーに知らせる必要もあります。組織の事情に応じて停止を計画し、適切に対応してください。




> [!IMPORTANT]
> 従来の Office Communications Server 2007 R2 エッジ サーバーが、アクセス エッジ サービス、Web 電話会議エッジ サービス、および音声ビデオ エッジ サービスと同じ FQDN を使用するように構成されている場合は、このセクションで説明する、フェデレーション設定を Lync Server 2013 エッジ サーバーに移行する手順はサポートされません。従来のエッジ サービスが同じ FQDN を使用するように構成されている場合は、まず、すべてのユーザーを Office Communications Server 2007 R2 から Lync Server 2013 に移行します。次に、Office Communications Server 2007 R2 エッジ サーバーを使用停止にし、その後で、Lync Server 2013 エッジ サーバーのフェデレーションを有効にします。詳細については、次のトピックを参照してください。 
> <UL>
> <LI>
> <P><A href="move-remaining-users-to-lync-server-2013_1.md">残りのユーザーの Lync Server 2013 への移動</A></P>
> <LI>
> <P>「サーバーとサーバーの役割の削除」( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=268790%26clcid=0x411">http://go.microsoft.com/fwlink/?linkid=268790&amp;clcid=0x411</A>)</P></LI></UL>




> [!IMPORTANT]
> XMPP フェデレーションが Lync Server 2013 エッジ サーバー経由でルーティングされる場合は、すべてのユーザーが Lync Server 2013 に移行され、XMPP のポリシーと証明書が構成され、XMPP フェデレーション パートナーが Lync Server 2013 で構成され、そして DNS エントリが更新されるまで、従来の Office Communications Server 2007 R2 のユーザーは XMPP フェデレーション パートナーと通信できなくなります。



サーバーの役割を追加または削除するときにトポロジを正常に公開、有効化、または無効化するには、RTCUniversalServerAdmins および Domain Admins グループのメンバーであるユーザーとしてログインする必要があります。サーバーの役割を追加する適切なユーザー権限とアクセス許可を委任することもできます。詳細については、Standard Edition サーバーまたは Enterprise Edition サーバーの「展開」のドキュメントの「[Lync Server 2013 でのセットアップのアクセス許可の委任](lync-server-2013-delegate-setup-permissions.md)」を参照してください。他の構成変更の場合は、RTCUniversalServerAdmins グループのメンバーシップのみが必要です。

## Lync Server 2013 サイトから従来のフェデレーションの関連付けを削除するには

1.  トポロジ ビルダーを使用してパイロット プールを開きます。

2.  左ウィンドウで、サイト ノードに移動します。

3.  サイトを右クリックし、\[**プロパティの編集**\] をクリックします。

4.  左ウィンドウの \[**フェデレーション ルート**\] を選択します。

5.  \[サイトのフェデレーション ルートの割り当て\] で、\[**SIP フェデレーションの有効化**\] の横のチェック ボックスをオフにして、\[**BackCompatSite**\] を経由するフェデレーション ルートを無効にします。
    
    ![\[プロパティの編集\] ダイアログ ボックス、フェデレーション ルート](images/JJ721925.2a80c103-c0cc-43ed-ba00-420f9add006a(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、フェデレーション ルート")

6.  \[**OK**\] をクリックして、\[プロパティの編集\] ページを閉じます。

7.  \[**トポロジ ビルダー**\] で、最上位ノードの \[**Lync Server**\] を選択します。

8.  \[**操作**\] メニューの \[**トポロジの公開**\] をクリックし、ウィザードを完了します。

## 従来のエッジ サーバーをフェデレーションされていないエッジ サーバーとして構成するには

1.  \[**トポロジ ビルダー**\] の \[**操作**\] メニューの \[**Office Communications Server 2007 R2 トポロジのマージ**\] をクリックします。

2.  \[**次へ**\] をクリックして続行します。

3.  \[**エッジ セットアップの指定**\] で、フェデレーションに現在構成されている \[**エッジ サーバーの内部 FQDN**\] を選択し、\[**変更**\] をクリックします。
    
    ![OCS 2007 R2 トポロジのマージ、\[エッジ セットアップの指定\]](images/JJ721925.42c15aaf-c1ac-4fb1-a086-665835c57b23(OCS.15).jpg "OCS 2007 R2 トポロジのマージ、[エッジ セットアップの指定]")

4.  \[**次へ**\] をクリックし、\[**外部エッジの指定**\] ページが表示されるまで既定値を使用します。
    
    ![トポロジ ビルダー、\[外部エッジの指定\] ページ](images/JJ205243.32e97ce5-92f0-477e-8125-5d2ece237b13(OCS.15).jpg "トポロジ ビルダー、[外部エッジの指定] ページ")

5.  \[**外部エッジの指定**\] で、\[**このエッジ プールは、フェデレーションとパブリック IM 接続に使用します**\] チェック ボックスをオフにします。このチェック ボックスをオフにすると、BackCompatSite とのフェデレーションの関連付けが削除されます。
    

    > [!IMPORTANT]
    > この手順は重要です。従来のフェデレーションの関連付けを削除するには、このチェック ボックスをオフにする必要があります。



6.  \[**次へ**\] をクリックし、ウィザードの残りのページで既定値を使用します。

7.  \[**概要**\] で、\[**次へ**\] をクリックしてトポロジのマージを開始します。

8.  \[**状態**\] 列の値が " **成功**" になっていることを確認し、\[**完了**\] をクリックしてウィザードを閉じます。

9.  \[**操作**\] メニューで \[**トポロジの公開**\] を選択し、\[**次へ**\] をクリックします。

10. **公開ウィザード**の実行が完了したら、\[**完了**\] をクリックしてウィザードを閉じます。
    
    ![トポロジ ビルダー、マージ後に表示されたサイト](images/JJ721925.92b679ad-332f-49aa-b4e2-19f939b711ca(OCS.15).jpg "トポロジ ビルダー、マージ後に表示されたサイト")
    
    前の図に示したように、\[**サイトのフェデレーション ルートの割り当て**\] の \[**SIP federation**\] (SIP フェデレーション) は \[**無効**\] に設定されています。

## Lync Server 2013 エッジ サーバーで証明書を構成するには

1.  従来の Office Communications Server 2007 R2 エッジ サーバーから、アクセス プロキシの外部証明書と秘密キーをエクスポートします。

2.  Lync Server 2013 エッジ サーバーに、前の手順でエクスポートした、アクセス プロキシの外部証明書をインポートします。

3.  アクセス プロキシの外部証明書を、エッジ サーバーの Lync Server 2013 外部インターフェイスに割り当てます。

4.  Lync Server 2013 エッジ サーバーの内部インターフェイス証明書を変更しないでください。

## Office Communications Server 2007 R2 フェデレーション ルートを変更して Lync Server 2013 エッジ サーバーを使用するには

1.  Office Communications Server 2007 R2Standard Edition サーバー または フロント エンド サーバー で、Office Communications Server 2007 R2 管理ツールを開きます。

2.  左ウィンドウで、最上位ノードを展開し、\[**フォレスト**\] ノードを右クリックします。\[**プロパティ**\] を選択し、\[**グローバル プロパティ**\] をクリックします。

3.  \[**フェデレーション**\] タブをクリックします。

4.  チェック ボックスをオンにして、フェデレーションとパブリック IM 接続を有効にします。

5.  Lync Server 2013  エッジ サーバー の FQDN を入力し、\[**OK**\] をクリックします。
    
    ![OCS のグローバル プロパティ、\[フェデレーション\] タブ](images/JJ721925.da633f72-43c6-4dac-8d37-ccd0dcde79c9(OCS.15).jpg "OCS のグローバル プロパティ、[フェデレーション] タブ")

## Lync Server 2013 エッジ サーバーのフェデレーションを有効にするには

1.  トポロジ ビルダーの左ウィンドウで、 Lync Server 2013 の \[**エッジ プール**\] ノードに移動します。

2.  ノードを展開し、一覧内の \[エッジ サーバー\] を右クリックし、\[**プロパティの編集**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>フェデレーションは、単一の エッジ プールに対してのみ有効にできます。複数のエッジ プールがある場合は、フェデレーション エッジ プールとして使用するエッジ プールを 1 つ選択します。</td>
    </tr>
    </tbody>
    </table>


3.  \[**全般**\] ページで、\[**このエッジ プールのフェデレーションの有効化 (ポート 5061)**\] チェック ボックスをオンにします。
    
    ![\[プロパティの編集\]、\[全般\]、エッジ フェデレーションを有効にする](images/JJ688121.cc79a88c-cce4-4cab-80ad-4f70325dc7c4(OCS.15).jpg "[プロパティの編集]、[全般]、エッジ フェデレーションを有効にする")

4.  \[**OK**\] をクリックして、\[プロパティの編集\] ページを閉じます。

5.  次に、サイト ノードに移動します。

6.  サイトを右クリックし、\[**プロパティの編集**\] をクリックします。

7.  左ウィンドウで、\[**フェデレーション ルート**\] をクリックします。

8.  \[**サイトのフェデレーション ルートの割り当て**\] で、\[**SIP フェデレーションの有効化**\] を選択し、ボックスの一覧の \[Lync Server 2013  エッジ サーバー\] をクリックします。

9.  \[**OK**\] をクリックして、\[**プロパティの編集**\] ページを閉じます。
    
    ![\[プロパティの編集\] ダイアログ ボックス、\[全般\]、\[エッジ プールの関連付け\]](images/JJ721925.33d43297-10cd-412e-bf4a-a1d9a84b9009(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、[全般]、[エッジ プールの関連付け]")
    
    マルチサイト展開の場合は、この手順をサイトごとに実行します。

## Lync Server 2013 エッジ サーバーの送信メディア パスを構成するには

1.  \[**トポロジ ビルダー**\] で、\[**Standard Edition フロントエンド サーバー**\] の \[Lync Server 2013 プール\] または \[**Enterprise Edition フロントエンド プール**\] に移動します。

2.  プールを右クリックし、\[**プロパティの編集**\] をクリックします。

3.  \[**関連付け**\] セクションで、\[**エッジ プールの関連付け (メディア コンポーネント用)**\] チェック ボックスをオンにします。

4.  ボックスの一覧の \[Lync Server 2013 エッジ サーバー\] をクリックします。
    
    ![\[プロパティの編集\] ダイアログ ボックス、エッジ プールの関連付け](images/JJ721925.0cb76b08-5923-4972-8d7a-a829cb77136b(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、エッジ プールの関連付け")

5.  \[**OK**\] をクリックして、\[**プロパティの編集**\] ページを閉じます。

## エッジ サーバーの構成の変更を公開するには

1.  \[**トポロジ ビルダー**\] で、最上位ノードの \[**Lync Server**\] を選択します。

2.  \[**操作**\] メニューの \[**トポロジの公開**\] を選択し、ウィザードを完了します。

3.  展開内のすべてのプールに対して Active Directory のレプリケーションが発生するのを待ちます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>次のメッセージが表示されることがあります。<br />
    <strong>警告: 複数のフェデレーション エッジ サーバーがトポロジに含まれています。この状態は、最新バージョンの製品への移行中に発生することがあります。その場合、1 つのエッジ サーバーのみがフェデレーション用に実際に使用されます。外部 DNS SRV レコードが正しいエッジ サーバーを指していることを確認してください。複数のフェデレーション エッジ サーバーを (移行シナリオ以外で) 同時にアクティブにして展開する場合は、すべてのフェデレーション パートナーが Office Communications Server 2007 R2 または Lync Server を使用していることを確認してください。また、外部 DNS SRV レコードにすべてのフェデレーション対応エッジ サーバーがリストされていることを確認してください。</strong><br />
    この警告は予期されるものであり、無視してもかまいません。</td>
    </tr>
    </tbody>
    </table>


## 外部ユーザーのフェデレーションとリモート アクセスを確認するには

1.  Lync Server 2013 フロントエンド サーバーから Lync Server 管理シェル を開きます。

2.  フェデレーションとリモート アクセスの状態を確認するには、コマンド ラインから次のように入力します。
    
        Get-CsAccessEdgeConfiguration

3.  フェデレーションとリモート アクセスを有効化するには、コマンド ラインから次のように入力します。
    
        Set-CsAccessEdgeConfiguration
    
    これらのコマンドレットの詳細については、「[Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)」と「[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)」を参照してください。

4.  レプリケーションが完了するまで待ってから、 Lync Server 2013 エッジ サーバーをオンラインにし、フェデレーションと外部アクセスをテストします。

## Lync Server 2013 エッジ サーバーを構成するには

1.  すべての Lync Server 2013 エッジ サーバーをオンラインにします。

2.  外部ファイアウォールのルーティング ルールまたはロード バランサー機器の設定を更新して、外部アクセス (通常は、ポート 443) およびフェデレーション (通常は、ポート 5061) の各 SIP トラフィックを、従来の エッジ サーバー ではなく、 Lync Server 2013  エッジ サーバー に送信します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>ロード バランサー機器がない場合は、フェデレーションの DNS A レコードを更新して、新しい Lync Server アクセス エッジ サーバーを解決する必要があります。中断を最低限にしてこれを行うためには、外部の Lync Server アクセス エッジ FQDN の TTL 値を下げておきます。すると、DNS が更新されて新しい Lync Server アクセス エッジ サーバーを示すようになったとき、フェデレーションとリモート アクセスが速やかに更新されます。</td>
    </tr>
    </tbody>
    </table>


3.  次に、各 エッジ サーバー コンピューターの \[**Lync Server Server Access Edge**\] (Lync Server サーバー アクセス エッジ) を停止します。

4.  従来の各 エッジ サーバー コンピューターで、\[**管理ツール**\] から \[**サービス**\] アプレットを開きます。

5.  サービス リストで、\[**Office Communications Server アクセス エッジ**\] を見つけます。

6.  サービス名を右クリックし、\[**停止**\] を選択してサービスを停止します。

7.  スタートアップの種類を \[**無効**\] に設定します。

8.  \[**OK**\] をクリックして、\[**プロパティ**\] ウィンドウを閉じます。

## 外部ユーザーの接続と外部アクセスをテストするには

  - 少なくとも 1 つのフェデレーション ドメインのユーザー、 Lync Server 2013 の内部ユーザー、および Office Communications Server 2007 R2 のユーザー。インスタント メッセージング (IM)、プレゼンス、音声ビデオ (A/V)、およびデスクトップ共有をテストします。

  - Lync Server 2013 のユーザーおよび Office Communications Server 2007 R2 のユーザーと通信している、組織がサポート (およびプロビジョニングが完了) している各パブリック IM プロバイダーのユーザー。

  - 匿名ユーザーが会議に参加できることを確認します。

  - リモート ユーザー アクセスを使用する Office Communications Server 2007 R2 でホストされたユーザー (イントラネットの外部から Office Communications Server 2007 R2 にログイン、ただし VPN は不使用) と、 Lync Server 2013 上のユーザーおよび Office Communications Server 2007 R2 上のユーザー。IM、プレゼンス、A/V、およびデスクトップ共有をテストします。

  - リモート ユーザー アクセスを使用する Lync Server 2013 でホストされたユーザー (イントラネットの外部から Lync Server 2013 にログイン、ただし VPN は不使用) と、 Lync Server 2013 上のユーザーおよび Office Communications Server 2007 R2 上のユーザー。IM、プレゼンス、A/V、およびデスクトップ共有をテストします。
