---
title: スケジュール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- schedules [Reporting Services]
- schedules [Reporting Services], about schedules
- published reports [Reporting Services], schedules
- reports [Reporting Services], scheduling
- subscriptions [Reporting Services], scheduling
- automatic report processing
ms.assetid: ecccd16b-eba9-4e95-b55d-f15c621e003f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99bcfbf6559c0f3b59bede54eae6224b4973797b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739132"
---
# <a name="schedules"></a>スケジュール
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、レポートの処理および配信の制御を支援する共有スケジュールとレポート固有スケジュールが用意されています。 これら 2 種類のスケジュールでは、定義、格納、管理の方法が異なります。 2 種類のスケジュールの内部の構成は同じです。 すべてのスケジュールでは、毎月、毎週、または毎日という定期実行の種類を指定します。 定期実行の種類では、イベントが発生する頻度を表す間隔と範囲を設定します。 定期的な実行パターンの種類とパターンの指定方法は、共有スケジュールとレポート固有スケジュールのいずれを作成する場合でも同じです。  
  
 このトピックの内容:  
  
-   [スケジュールで実行できる操作](#bkmk_whatyoucando)  
  
-   [共有スケジュールとレポート固有スケジュールの比較](#bkmk_compare)  
  
-   [データソースを構成する](#bkmk_configuredatasources)  
  
-   [資格情報と処理アカウントの保存](#bkmk_credentials)  
  
-   [スケジュールおよび配信処理のしくみ](#bkmk_how_scheduling_works)  
  
-   [サーバーの依存関係](#bkmk_serverdependencies)  
  
-   [SQL Server エージェントを停止した場合の影響](#bkmk_stoppingagent)  
  
-   [レポートサーバーサービスを停止した場合の影響](#bkmk_stoppingservice)  
  
  
##  <a name="what-you-can-do-with-schedules"></a><a name="bkmk_whatyoucando"></a> スケジュールに対して実行できる操作  
 ネイティブ モードのレポート マネージャーおよび SharePoint モードの SharePoint サイト管理ページを使用して、スケジュールの作成と管理を行うことができます。 次のようにすることができます。  
  
-   標準のサブスクリプションまたはデータ ドリブン サブスクリプションでのレポート配信スケジュール  
  
-   一定間隔でレポート履歴に新しいスナップショットを追加するレポート履歴のスケジュール  
  
-   レポート スナップショットのデータ更新時期のスケジュール  
  
-   共有データセットのデータ更新時期のスケジュール  
  
-   キャッシュされたレポートまたは共有データセットを続けて更新できるように、キャッシュされたレポートまたは共有データセットの有効期限が事前に定義した時間に切れるスケジュール  
  
 多くのレポートまたはサブスクリプションで同じスケジュール情報を使用する場合は、共有スケジュールを作成できます。 共有スケジュールは個別に定義され、スケジュール情報を必要とするレポート、共有データセット、およびサブスクリプションから参照されます。  
  
 スケジュールを作成すると、レポートによってスケジュール情報がレポート サーバー データベース (SharePoint モードの場合はサーバー アプリケーション データベース) に保存されます。 レポート サーバーでは、スケジュールを開始するために使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブも作成されます。 スケジュール処理は、スケジュールを含むレポート サーバーのローカル時間に基づいています。 時刻の形式は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows オペレーティング システムの標準に従います。  
  
 スケジュールを作成および管理する方法の詳細については、「 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)」を参照してください。  
  
> [!NOTE]  
>  スケジュール操作は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。  
  
##  <a name="comparing-shared-and-report-specific-schedules"></a><a name="bkmk_compare"></a> 共有スケジュールとレポート固有スケジュールの比較  
 どちらの種類のスケジュールも同じ出力を返します。  
  
-   **共有スケジュール** は、すぐに使用できる状態のスケジュール情報を含む、移植可能で多目的に使用できるアイテムです。 共有スケジュールは、システムレベルのアイテムなので、共有スケジュールを作成するにはシステムレベルの権限が必要です。 そのため、通常、レポート サーバー管理者またはコンテンツ管理者がレポート サーバー上で使用可能な共有スケジュールを作成します。 共有スケジュールは、レポート マネージャーまたは SharePoint サイトの設定を使用して、レポート サーバー上に格納して管理します。  
  
     レポート、共有データセット、またはサブスクリプションのプロパティを使って定義する特定のスケジュールと比較すると、次のような特徴を持つ共有スケジュールは、管理と維持を容易に行えます。  
  
    -   共有スケジュールは一元的に管理できるため、スケジュールのプロパティを容易に比較できます。操作のスケジュール設定が近すぎる場合や、サーバーの他の処理と競合している場合に、スケジュールの頻度や繰り返しパターンを簡単に調整できます。  
  
    -   コンピューティング環境の変更にすばやく適応することができます。 たとえば、データ ウェアハウスの更新後、 午前 4 時に一連のレポートを実行するとします。 データの更新操作のスケジュールが変更されたり、遅れたりした場合でも、1 つの共有スケジュールのスケジュール情報を更新するだけで、変更に対応できます。  
  
    -   共有スケジュールのみを使用する場合、スケジュール設定された操作がいつ実行されるのかを正確に把握できます。 これにより、パフォーマンスの問題が発生する前に、容易にサーバーの負荷を予測して対応することができます。 たとえば、コンピューターのバックアップを特定の時間に行うようにスケジュール設定した場合、共有スケジュールを別の時間に実行するように調整できます。  
  
-   **レポート固有スケジュール** は、各レポート、サブスクリプション、またはレポート実行操作のコンテキスト内で定義され、キャッシュの有効期限やスナップショットの更新を決定します。 これらのスケジュールは、サブスクリプションを定義するとき、またはレポート実行のプロパティを設定するときに、インラインで作成されます。 共有スケジュールで必要な頻度または反復パターンが指定されていない場合に、レポート固有スケジュールを作成することができます。 レポートを実行しないようにするには、レポート固有スケジュールを手動で編集する必要があります。 レポート固有スケジュールは、各ユーザーが作成できます。  
  
##  <a name="configure-the-data-sources"></a><a name="bkmk_configuredatasources"></a> データ ソースの構成  
 レポートのデータ処理またはサブスクリプション処理のスケジュールを設定するには、保存された資格情報または自動レポート処理アカウントが使用されるようにレポートのデータ ソースを構成しておく必要があります。 保存されている資格情報を使用する場合、保存できる資格情報は 1 組のみです。レポートを実行するすべてのユーザーに対してこの資格情報が使用されます。 資格情報には、Windows ユーザー アカウントまたはデータベース ユーザー アカウントを指定できます。  
  
 自動レポート処理アカウントは、レポート サーバーで構成する特別な目的のアカウントです。 このアカウントは、スケジュール設定された操作が外部のファイルや処理を必要とする場合に、リモート コンピューターに接続するために使用されます。 このアカウントを構成すれば、レポートにデータを提供する外部データ ソースへの接続に使用できます。  
  
 保存されている資格情報または自動レポート処理アカウントを指定するには、レポートのデータ ソース プロパティを編集します。 共有データ ソースがレポートに使用されている場合は、共有データ ソースを編集します。  
  
##  <a name="store-credentials-and-processing-accounts"></a><a name="bkmk_credentials"></a> 資格情報と処理アカウントの保存  
 スケジュールを使った作業を行う方法は、ロールの割り当ての一部であるタスクによって異なります。 既定のロールを使用する場合、スケジュールを作成および管理できるユーザーはコンテンツ マネージャーとシステム管理者です。 カスタム ロールの割り当てを使用する場合、そのロールの割り当てにはスケジュールが設定された操作をサポートするタスクが含まれている必要があります。  
  
|目的|必要なタスク|ネイティブ モードの定義済みロール|SharePoint モードのグループ|  
|----------------|-----------------------|----------------------------------|----------------------------|  
|共有スケジュールの作成、変更、または削除|共有スケジュールの管理|システム管理者|所有者|  
|共有スケジュールの選択|共有スケジュールの表示|システム ユーザー|メンバー|  
|ユーザー定義サブスクリプションでのレポート固有スケジュールの作成、変更、または削除|個別のサブスクリプションを管理|閲覧者、レポート ビルダー、個人用レポート、コンテンツ マネージャー|閲覧者、メンバー|  
|その他すべてのスケジュール設定された操作用のレポート固有スケジュールの作成、変更、または削除|レポート履歴の管理、すべてのサブスクリプションの管理、レポートの管理|コンテンツ マネージャー|所有者|  
  
 ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のセキュリティの詳細については、「 [定義済みロール](../security/role-definitions-predefined-roles.md)」、「 [ネイティブ モードのレポート サーバーに対する権限の許可](../security/granting-permissions-on-a-native-mode-report-server.md) 」、および「 [タスクと権限](../security/tasks-and-permissions.md)」を参照してください。 SharePoint モードについては、「 [Reporting Services のロールおよびタスクと SharePoint のグループおよび権限の比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)」を参照してください。  
  
##  <a name="how-scheduling-and-delivery-processing-works"></a><a name="bkmk_how_scheduling_works"></a> スケジュール処理および配信処理のしくみ  
 スケジュールおよび配信のプロセッサは、次の機能を提供します。  
  
-   レポート サーバー データベース内のイベントおよび通知のキューを管理します。 スケールアウト配置では、キューは配置しているすべてのレポート サーバーで共有されます。  
  
-   レポート プロセッサを呼び出し、レポートの実行、サブスクリプションの処理、またはキャッシュされたレポートの消去を行います。 スケジュール イベントの結果として生じるすべてのレポート処理は、バックグラウンド プロセスとして実行されます。 SharePoint モードでは、タイマー ジョブを使用します。  
  
-   レポートを配信できるように、サブスクリプションで指定されている配信拡張機能を呼び出します。  
  
 スケジュール設定や配信操作のその他の機能は、スケジュールおよび配信のプロセッサと連動する他のコンポーネントやサービスによって処理されます。 特に、スケジュールおよび配信のプロセッサはレポート サーバー サービスで実行され、SQL Server エージェントをタイマーとして使用して定期的なイベントを生成します。 ここでは、Reporting Services の配置におけるスケジュールされた操作の実行方法について、順を追って説明します。  
  
1.  ユーザーがスケジュールを作成すると、スケジュールされた操作が定義されます。 スケジュールで定義するのは、レポート配信のサブスクリプションのトリガー、スナップショットの更新、キャッシュの期限切れなどに使用する日付と時刻です。  
  
2.  レポート サーバーがスケジュール情報をレポート サーバー データベースに保存します。  
  
3.  レポート サーバーは、指定されたスケジュール情報を含む SQL Server エージェントで、対応するジョブを作成します。 このジョブは、レポート サーバー データベースに対して開いている既存の接続を使用し、ストアド プロシージャを介して作成されます。  
  
4.  SQL Server エージェントが、スケジュールで指定された日付と時刻にジョブを実行します。 ジョブが実行されると、イベントが作成され、Reporting Services で管理するキューに追加されます。  
  
5.  このイベントにより、レポートまたはサブスクリプションの処理が行われます。 キューで検出された時点でイベントが処理され、それに従ってレポートが処理または配信されます。  
  
     イベントの処理前に、スケジュールおよび配信のプロセッサは認証の手順を実行し、サブスクリプション所有者にレポート表示の権限があるかどうかを確認します。  
  
 Reporting Services では、すべてのスケジュールされた操作のイベント キューを管理します。 定期的にキューをポーリングし、新しいイベントがないかどうかを確認します。 既定では、10 秒間隔でキューがスキャンされます。 間隔を変更するには、RSReportServer.config ファイルで `PollingInterval`、`IsNotificationService`、および `IsEventService` の構成設定を変更します。 また、SharePoint モードでは、これらの設定に RSreporserver.config を使用するため、値はすべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに適用されます。 詳しくは、「 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)」をご覧ください。  
  
##  <a name="server-dependencies"></a><a name="bkmk_serverdependencies"></a> サーバーの依存関係  
 スケジュールおよび配信のプロセッサでは、レポート サーバー サービスと SQL Server エージェントが開始されている必要があります。 `ScheduleEventsAndReportDeliveryEnabled`ポリシーベースの管理の Reporting Services ファセットの**セキュリティ構成**のプロパティを使用して、スケジュールおよび配信処理機能を有効にする必要があります。 スケジュールされた操作を実行するには、SQL Server エージェントおよびレポート サーバー サービスの両方が実行されている必要があります。  
  
> [!NOTE]  
>  **[Reporting Services のセキュリティ構成]** ファセットを使用して、一時的または永続的に、スケジュールされた操作を停止させることができます。 カスタム配信拡張機能を作成して配置することはできますが、それだけではスケジュールおよび配信のプロセッサを拡張できません。 イベントおよび通知の管理方法を変更することはできません。 機能を無効にするには、「 **Turn Reporting Services Features On or Off** 」の「 [定期的なイベントおよび配信](../report-server/turn-reporting-services-features-on-or-off.md)」を参照してください。  
  
###  <a name="effects-of-stopping-the-sql-server-agent"></a><a name="bkmk_stoppingagent"></a> SQL Server エージェントの停止の影響  
 スケジュールされたレポート処理では、既定で SQL Server エージェントを使用します。 サービスを停止すると、 <xref:ReportService2010.ReportingService2010.FireEvent%2A> メソッドによりプログラムで追加しない限り、新しい処理要求はキューに追加されません。 サービスを再開すると、レポート処理要求を作成するジョブが再開されます。 SQL Server エージェントがオフラインの間、レポート サーバーは、過去に発生する可能性のあったレポート処理ジョブを再作成しません。 SQL Server エージェントを 1 週間停止する場合、その週のすべてのスケジュールされた操作は失われます。  
  
> [!NOTE]  
>  SQL Server エージェントが Reporting Services に提供する機能を、 <xref:ReportService2010.ReportingService2010.FireEvent%2A> メソッドを使用するカスタム コードに置き換え、キューにスケジュール イベントを追加することができます。  
  
###  <a name="effects-of-stopping-the-report-server-service"></a><a name="bkmk_stoppingservice"></a> レポート サーバー サービスの停止の影響  
 レポート サーバー サービスを停止しても、SQL Server エージェントは引き続きレポート処理要求をキューに追加します。 SQL Server エージェントからの状態情報は、ジョブが成功したことを示します。 ただし、レポート サーバー サービスが停止しているため、実際にはレポート処理は実行されません。 レポート サーバー サービスを再起動するまで、要求はキューに蓄積され続けます。 レポート サーバー サービスを再起動すると、キューにあるすべてのレポート処理要求が順番に処理されます。  
  
## <a name="see-also"></a>参照  
 [レポート履歴のスナップショットの作成、変更および削除](../report-server/create-modify-and-delete-snapshots-in-report-history.md)   
 [サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Data-Driven Subscriptions](data-driven-subscriptions.md)   
 [レポートのキャッシュ &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md)   
 [レポート サーバー コンテンツの管理 &#40;SSRS ネイティブ モード&#41;](../report-server/report-server-content-management-ssrs-native-mode.md)   
 [共有データセットのキャッシュ &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md)  
  
  