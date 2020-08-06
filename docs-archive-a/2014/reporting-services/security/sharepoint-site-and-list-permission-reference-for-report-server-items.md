---
title: レポート サーバー アイテムの SharePoint サイトおよびリスト アクセス許可のリファレンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
- security [Reporting Services], SharePoint integrated mode
- permission sets [Reporting Services]
ms.assetid: 1fcb27bd-4c4a-43f4-bfff-e42a59c87c49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ff6426a6b1606c682e7cc81b285c2d95ed28cc67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739151"
---
# <a name="sharepoint-site-and-list-permission-reference-for-report-server-items"></a>レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス
  ここでは、SharePoint 統合モードで動作するレポート サーバーに関して、レポート サーバー処理に対するアクセスの許可に使用できる、SharePoint の権限のリファレンス情報を提供します。 このトピックは、カスタム権限レベルを作成する場合に使用する権限を選択するのに役立ちます。  
  
 SharePoint には、コンテンツおよび処理へのアクセスを制御するために使用できる 33 個の権限があります。 これらの権限のすべてではありませんが、その一部は、ドキュメントおよび [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーが関係する処理に適用されます。 この記事の権限リファレンス表を見れば、どの権限で特定のレポート タスクがサポートされているかがわかります。  
  
 それぞれの表の先頭には、SharePoint の権限のリストと説明があります。 個々の権限が定義済みの権限レベルでどのように使用されているかを示す列が 3 つ用意されています。 定義済みの権限レベルには、次のものがあります。  
  
|権限レベル|省略形|  
|----------------------|------------------|  
|フル コントロール|**F**|  
|投稿|**C**|  
|ビジター|**V**|  
  
 レポート サーバーに影響しない権限は除外しています。 また、個人用の設定に使用する権限もすべてこのリファレンス資料から除外しています。 個人用に設定された Web サイトにレポート サーバーのアイテムを含めることは可能ですが、個人用設定の要求や操作がレポート サーバーで直接処理されるわけではありません。  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード &#124; SharePoint 2010 と SharePoint 2013|  
  
## <a name="list-permissions"></a>リスト権限  
 ユーザーがレポート サーバー アイテムにアクセスする方法は、それらのアイテムが格納されているライブラリに設定した権限によって決まります。  
  
|権限|説明|F|C|V|レポート サーバーの処理|  
|----------------|-----------------|-------|-------|-------|-----------------------------|  
|リストの管理|リストの作成と削除、リストの列の追加と削除、およびリストのパブリック ビューの追加と削除を行います。|X|||レポート作成ツールから発行操作を行う際、SharePoint ライブラリにフォルダーを作成します。 レポート履歴の管理にもこの権限が必要です。|  
|[項目の追加]|リストへのアイテムの追加、ドキュメント ライブラリへのドキュメントの追加、および Web ディスカッションのコメントの追加を行います。|X|X||レポート、レポート モデル、共有データ ソース、およびリソース (外部イメージ ファイル) を SharePoint ライブラリに追加します。 共有データ ソースを作成します。 共有データ ソースからレポート モデルを生成します。 レポート ビルダーを起動して新しいレポートを作成するか、レポート ビルダーにモデルを読み込みます。|  
|アイテムの編集|リスト内のアイテムの編集、ドキュメント ライブラリ内のドキュメントの編集、ドキュメント内の Web ディスカッション コメントの編集、ドキュメント ライブラリ内の Web パーツ ページのカスタマイズを行います。<br /><br /> サブスクリプションを作成し、作成したサブスクリプションを編集します。|X|X||レポート履歴スナップショットを含め、ドキュメントの過去のバージョンを表示します。 レポートなどのドキュメントに使用するアイテム プロパティを編集します。 レポート処理オプションを設定します。 レポートに関するパラメーターを設定します。 データ ソースのプロパティを編集します。 レポート履歴スナップショットを作成します。 レポート ビルダーでレポート モデルまたはモデルベースのレポートを開き、変更をファイルに保存します。 クリックスルー レポートをモデルのエンティティに割り当てます。 レポート定義、共有データ ソース、レポート モデル、またはリソースを新しいバージョンに置き換えます (メタデータを残してファイルを置き換えます)。 レポートまたはモデルから参照されている依存アイテムを管理します。 特定のレポートについて、レポート ビューアー Web パーツをカスタマイズします。<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配信拡張機能を使用してレポートをターゲットの場所に配信するサブスクリプションを作成、変更、および削除します。 サブスクリプションの所有者と通知の管理権限を持つユーザーのみが、これらの操作を実行できます。|  
|アイテムの削除|リストのアイテム、ドキュメント ライブラリのドキュメント、およびドキュメントの Web ディスカッション コメントを削除します。|X|X||レポート、レポート モデル、共有データ ソース、およびその他のドキュメントをライブラリから削除します。|  
|アイテムの表示|リストのアイテム、ドキュメント ライブラリのドキュメント、および Web ディスカッション コメントを表示します。|X|X|X|レポート、レポート モデル、およびその他のドキュメントを開いて、レポート サーバーで処理できるようにします。|  
|アイテムを開く|サーバー側のファイル ハンドラーでドキュメントのソースを表示します。|X|X|X|共有データ ソースのリストを表示します。 レポート定義またはレポート モデルのソース ファイルのコピーをダウンロードします。 レポート モデルをデータ ソースとして使用するクリックスルー レポートを表示します。|  
|バージョンの表示|リスト アイテムまたはドキュメントの過去のバージョンを表示します。|X|X|X|ドキュメントおよびレポート スナップショットの過去のバージョンを表示します。|  
|バージョンの削除|リスト アイテムまたはドキュメントの過去のバージョンを削除します。|X|X||ドキュメントおよびレポート スナップショットの過去のバージョンを削除します。|  
  
> [!NOTE]  
>  上記以外のリスト権限には、"チェックアウトのオーバーライド"、"アイテムの承認"、および "アプリケーション ページの表示" があります。 レポート サーバーでは、これらの権限が評価されません。 レポート サーバーでは、これらの操作が処理されません。  
  
## <a name="site-permissions"></a>サイト権限  
 サイト権限は、特定のライブラリに格納されているアイテムには直接関係しない、レポート サーバー処理へのアクセスを決定します。 たとえば、複数のライブラリのアイテムで使用できる共有スケジュールの作成と管理、サイト全体で使用できるレポート ビューアー Web パーツの構成などです。  
  
|権限|説明|F|C|V|レポート サーバーの処理|  
|----------------|-----------------|-------|-------|-------|-----------------------------|  
|権限の管理|Web サイトの権限レベルを作成および変更し、権限をユーザーおよびグループに割り当てます。|X|||すべてのレポート サーバー アイテムおよび処理について権限を変更できます。 モデル アイテム セキュリティを設定できます。|  
|Web サイトの管理|コンテンツの管理に加え、Web サイトのあらゆる管理作業を行います。|X|||共有スケジュールを作成、変更、または削除します。|  
|ページの追加とカスタマイズ|HTML ページまたは Web パーツ ページを追加、変更、または削除します。また、 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]互換のエディターを使用して Web サイトを編集します。|X|||レポート ビューアー Web パーツを追加または削除します。|  
|ユーザー情報の参照|Web サイトのユーザーに関する情報を表示します。|X|X|X|さまざまなサイト、ライブラリ、およびフォルダーに含まれているレポートなどのアイテムを参照します。 ライブラリにレポートなどのアイテムをパブリッシュします。|  
|権限の一覧|Web サイト、リスト、フォルダー、ドキュメント、またはリスト アイテムに対する権限を一覧表示します。|X|||すべてのレポート サーバー アイテムに対する権限を読み取ります。 モデル アイテム セキュリティ設定を含むレポート モデルが使用されているクリックスルー レポートを表示します。|  
|警告の管理|Web サイトのすべてのユーザーに対して通知を管理します。|X|||サイトのサブスクリプションの作成、変更、および削除を行います。|  
|リモート インターフェイスの使用|SOAP、Web DAV、または SharePoint デザイナー インターフェイスを使用して Web サイトにアクセスします。|X|X|X|レポート サーバーに対する URL プロキシ エンドポイントを呼び出すために使用します。|  
|[ファイル]|Web サイト、リスト、またはフォルダーを開き、これらのコンテナー内のアイテムにアクセスします。|X|X|X|スケジュールおよびアイテム プロパティを読み取ります。|  
  
## <a name="see-also"></a>参照  
 [SQL Server Reporting Services と SharePoint グループの役割とタスクの比較とアクセス許可](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)   
 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  