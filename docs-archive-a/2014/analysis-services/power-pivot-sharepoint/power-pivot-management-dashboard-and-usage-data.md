---
title: PowerPivot 管理ダッシュボードと使用状況データ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 541c8b1f-c6c2-423d-a97d-65c379967e0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581ed571661d54b1cfe9a63224b05f4f8b0267e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641287"
---
# <a name="powerpivot-management-dashboard-and-usage-data"></a><span data-ttu-id="18f98-102">PowerPivot 管理ダッシュボードと使用状況データ</span><span class="sxs-lookup"><span data-stu-id="18f98-102">PowerPivot Management Dashboard and Usage Data</span></span>
  <span data-ttu-id="18f98-103">PowerPivot 管理ダッシュボードとは、SQL Server PowerPivot for SharePoint の配置の管理に役立つ SharePoint サーバーの全体管理の定義済みのレポートおよび Web パーツのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="18f98-103">PowerPivot Management Dashboard is a collection of predefined reports and web parts in SharePoint Central Administration that help you administer a SQL Server PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="18f98-104">管理ダッシュボードでは、サーバーの状態、ブックの利用状況、およびデータ更新に関連する情報が示されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-104">The Management Dashboard provides information related to server health, workbook activity, and data refresh.</span></span> <span data-ttu-id="18f98-105">ダッシュボードは、SharePoint 使用状況データ コレクションのデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="18f98-105">The dashboard uses data from the SharePoint usage data collection.</span></span>  
  
 [<span data-ttu-id="18f98-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="18f98-106">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="18f98-107">ダッシュボードのセクションの概要</span><span class="sxs-lookup"><span data-stu-id="18f98-107">Overview of the sections of the Dashboard</span></span>](#items)  
  
 [<span data-ttu-id="18f98-108">PowerPivot 管理ダッシュボードを開く</span><span class="sxs-lookup"><span data-stu-id="18f98-108">Open PowerPivot Management Dashboard</span></span>](#open)  
  
 [<span data-ttu-id="18f98-109">ダッシュボードのソース データ</span><span class="sxs-lookup"><span data-stu-id="18f98-109">Source Data in Dashboards</span></span>](#sourcedata)  
  
 [<span data-ttu-id="18f98-110">PowerPivot 管理ダッシュボードの編集</span><span class="sxs-lookup"><span data-stu-id="18f98-110">Edit PowerPivot Dashboard</span></span>](#edit)  
  
 [<span data-ttu-id="18f98-111">PowerPivot 管理ダッシュボード用カスタム レポートの作成</span><span class="sxs-lookup"><span data-stu-id="18f98-111">Create Custom Reports for PowerPivot Management Dashboard</span></span>](#reports)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="18f98-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="18f98-112">Prerequisites</span></span>  
 <span data-ttu-id="18f98-113">管理する PowerPivot サービス アプリケーションの PowerPivot 管理ダッシュボードを開くには、サービス管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="18f98-113">You must be a service administrator to open PowerPivot Management Dashboard for a PowerPivot service application that you manage.</span></span>  
  
##  <a name="overview-of-the-sections-of-the-dashboard"></a><a name="items"></a><span data-ttu-id="18f98-114">ダッシュボードのセクションの概要</span><span class="sxs-lookup"><span data-stu-id="18f98-114">Overview of the sections of the Dashboard</span></span>  
 <span data-ttu-id="18f98-115">PowerPivot 管理ダッシュボードには、特定の情報カテゴリにドリル ダウンする Web パーツおよび埋め込みレポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="18f98-115">PowerPivot Management Dashboard contains Web Parts and embedded reports that drill down into specific information categories.</span></span> <span data-ttu-id="18f98-116">ダッシュボードの各部分の説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="18f98-116">The following list describes each part of the dashboard:</span></span>  
  
|<span data-ttu-id="18f98-117">ダッシュボード</span><span class="sxs-lookup"><span data-stu-id="18f98-117">Dashboard</span></span>|<span data-ttu-id="18f98-118">説明</span><span class="sxs-lookup"><span data-stu-id="18f98-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18f98-119">インフラストラクチャ - サーバーの状態</span><span class="sxs-lookup"><span data-stu-id="18f98-119">Infrastructure - Server Health</span></span>|<span data-ttu-id="18f98-120">CPU 使用率、メモリ消費量、およびクエリ応答時間の時間の経過に伴う変化の傾向を表示し、システム リソースが最大容量に近づいていないかどうか、または使用率が低くなっていないかどうかを評価できるようにします。</span><span class="sxs-lookup"><span data-stu-id="18f98-120">Shows trends in CPU usage, memory consumption, and query response times over time so that you can assess whether system resources are nearing maximum capacity or are under utilized.</span></span>|  
|<span data-ttu-id="18f98-121">Actions</span><span class="sxs-lookup"><span data-stu-id="18f98-121">Actions</span></span>|<span data-ttu-id="18f98-122">現在のサービス アプリケーション、サービス アプリケーションの一覧、および使用状況ログを含む、サーバーの全体管理内の他のページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="18f98-122">Contains links to other pages in Central Administration including the current service application, a list of service applications, and usage logging.</span></span>|  
|<span data-ttu-id="18f98-123">ブックの利用状況 - グラフ</span><span class="sxs-lookup"><span data-stu-id="18f98-123">Workbook Activity - Chart</span></span>|<span data-ttu-id="18f98-124">データ アクセスの頻度をレポートします。</span><span class="sxs-lookup"><span data-stu-id="18f98-124">Reports on frequency of data access.</span></span> <span data-ttu-id="18f98-125">PowerPivot データ ソースへの接続が発生する頻度を日単位または週単位で確認できます。</span><span class="sxs-lookup"><span data-stu-id="18f98-125">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="18f98-126">ブックの利用状況 - リスト</span><span class="sxs-lookup"><span data-stu-id="18f98-126">Workbook Activity - Lists</span></span>|<span data-ttu-id="18f98-127">データ アクセスの頻度をレポートします。</span><span class="sxs-lookup"><span data-stu-id="18f98-127">Reports on frequency of data access.</span></span> <span data-ttu-id="18f98-128">PowerPivot データ ソースへの接続が発生する頻度を日単位または週単位で確認できます。</span><span class="sxs-lookup"><span data-stu-id="18f98-128">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="18f98-129">データ更新 - 最近の利用状況</span><span class="sxs-lookup"><span data-stu-id="18f98-129">Data Refresh - Recent Activity</span></span>|<span data-ttu-id="18f98-130">データ更新ジョブの状態をレポートします (実行に失敗したジョブを含む)。</span><span class="sxs-lookup"><span data-stu-id="18f98-130">Reports on the status of data refresh jobs, including jobs that failed to run.</span></span> <span data-ttu-id="18f98-131">このレポートは、データ更新操作をアプリケーション レベルで総合的に理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="18f98-131">This report provides a composite view into data refresh operations at the application level.</span></span> <span data-ttu-id="18f98-132">管理者は、PowerPivot サービス アプリケーション全体に対して定義されているデータ更新ジョブの数が一目でわかります。</span><span class="sxs-lookup"><span data-stu-id="18f98-132">Administrators can see at a glance the number of data refresh jobs that are defined for the entire PowerPivot service application.</span></span>|  
|<span data-ttu-id="18f98-133">データ更新 - 最近のエラー</span><span class="sxs-lookup"><span data-stu-id="18f98-133">Data Refresh - Recent Failures</span></span>|<span data-ttu-id="18f98-134">データ更新が正常に完了しなかった PowerPivot ブックを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="18f98-134">Lists the PowerPivot workbooks that did not complete data refresh successfully.</span></span>|  
|<span data-ttu-id="18f98-135">Reports</span><span class="sxs-lookup"><span data-stu-id="18f98-135">Reports</span></span>|<span data-ttu-id="18f98-136">Excel で開くことができるレポートへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="18f98-136">Contains links to reports that you can open in Excel.</span></span>|  
  
##  <a name="open-powerpivot-management-dashboard"></a><a name="open"></a><span data-ttu-id="18f98-137">PowerPivot 管理ダッシュボードを開く</span><span class="sxs-lookup"><span data-stu-id="18f98-137">Open PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="18f98-138">ダッシュボードには、一度に 1 つの PowerPivot サービス アプリケーションの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-138">The dashboard shows information for one PowerPivot service application at a time.</span></span> <span data-ttu-id="18f98-139">管理ダッシュボードは、異なる 2 つの場所から開くことができます。</span><span class="sxs-lookup"><span data-stu-id="18f98-139">You can open the management dashboard from two different locations.</span></span>  
  
### <a name="open-the-dashboard-from-general-application-settings"></a><span data-ttu-id="18f98-140">[アプリケーションの全般設定] からダッシュボードを開く</span><span class="sxs-lookup"><span data-stu-id="18f98-140">Open the dashboard from General Application Settings</span></span>  
  
1.  <span data-ttu-id="18f98-141">サーバーの全体管理の **[アプリケーションの全般設定]** グループで **[PowerPivot 管理ダッシュボード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-141">In Central Administration, in the **General Application Settings** group, click **PowerPivot Management Dashboard**.</span></span>  
  
2.  <span data-ttu-id="18f98-142">メイン ページで、業務データを表示する PowerPivot サービス アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="18f98-142">On the main page, select the PowerPivot service application for which you want to view operations data.</span></span>  
  
### <a name="open-the-dashboard-from-a-powerpivot-service-application"></a><span data-ttu-id="18f98-143">PowerPivot サービス アプリケーションからダッシュボードを開く</span><span class="sxs-lookup"><span data-stu-id="18f98-143">Open the dashboard from a PowerPivot service application</span></span>  
  
1.  <span data-ttu-id="18f98-144">サーバーの全体管理で、[**アプリケーション管理**] の [**サービスアプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-144">In Central Administration, in **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="18f98-145">PowerPivot サービス アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-145">Click the name of the PowerPivot service application.</span></span> <span data-ttu-id="18f98-146">PowerPivot 管理ダッシュボードに、現在のサービス アプリケーションの業務データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-146">The PowerPivot Management Dashboard displays operational data for the current service application.</span></span>  
  
### <a name="change-the-current-service-application"></a><span data-ttu-id="18f98-147">現在のサービス アプリケーションを変更する</span><span class="sxs-lookup"><span data-stu-id="18f98-147">Change the current service application.</span></span>  
 <span data-ttu-id="18f98-148">管理ダッシュボードで現在の PowerPivot サービス アプリケーションを変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="18f98-148">To change current PowerPivot service application in the management dashboard:</span></span>  
  
1.  <span data-ttu-id="18f98-149">PowerPivot 管理ダッシュボードの上部に、現在のサービスアプリケーションの名前 (**既定の Powerpivot サービスアプリケーション**など) があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f98-149">At the top of the PowerPivot management dashboard, note the name of the current service application, for example **Default PowerPivot Service Application**.</span></span>  
  
2.  <span data-ttu-id="18f98-150">**[アクション]** ダッシュボードで、 **[サービス アプリケーションの一覧を表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-150">In the **Actions** dashboard, click **List Service Applications**.</span></span>  
  
3.  <span data-ttu-id="18f98-151">管理ダッシュボードのレポートを表示する PowerPivot サービス アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-151">Click the name of the PowerPivot Service application for which you want to see management dashboard reports.</span></span>  
  
##  <a name="source-data-in-dashboards"></a><a name="sourcedata"></a><span data-ttu-id="18f98-152">ダッシュボードのソースデータ</span><span class="sxs-lookup"><span data-stu-id="18f98-152">Source Data in Dashboards</span></span>  
 <span data-ttu-id="18f98-153">ダッシュボード、レポート、および Web パーツでは、システムおよび PowerPivot アプリケーション データベースからデータを取り出す内部データ モデルのデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-153">Dashboards, reports and web parts show data from an internal data model that pulls data from the system and PowerPivot application databases.</span></span> <span data-ttu-id="18f98-154">内部データ モデルは、サーバーの全体管理サイトでホストされている PowerPivot ブックに埋め込まれています。</span><span class="sxs-lookup"><span data-stu-id="18f98-154">The internal data model is embedded in a PowerPivot workbook hosted in the Central Administration site.</span></span> <span data-ttu-id="18f98-155">データ モデルの構造は固定されています。</span><span class="sxs-lookup"><span data-stu-id="18f98-155">The structure of the data model is fixed.</span></span> <span data-ttu-id="18f98-156">PowertPivot ブックをデータ ソースとして使用して新しいレポートを作成できますが、構造は変更しないでください。変更すると、その構造を使用する定義済みのレポートが壊れます。</span><span class="sxs-lookup"><span data-stu-id="18f98-156">Although you can use the PowertPivot workbook as a data source to create new reports, you must not modify the structure in a way that breaks the predefined reports that use it.</span></span>  
  
 <span data-ttu-id="18f98-157">データの収集方法の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18f98-157">For more information about how data is collected, see the following:</span></span>  
  
-   [<span data-ttu-id="18f98-158">PowerPivot 使用状況データ収集</span><span class="sxs-lookup"><span data-stu-id="18f98-158">PowerPivot Usage Data Collection</span></span>](power-pivot-usage-data-collection.md)  
  
-   [<span data-ttu-id="18f98-159">&#40;PowerPivot for SharePoint の使用状況データ収集の構成</span><span class="sxs-lookup"><span data-stu-id="18f98-159">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 <span data-ttu-id="18f98-160">PowerPivot サーバー システムに関するデータをキャプチャするために、イベント メッセージング、データ更新の履歴、およびその他の使用状況履歴が各 PowerPivot サービス アプリケーションに対して有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18f98-160">To capture data about the PowerPivot server system, verify event messaging, data refresh history, and other usage history is enabled for each PowerPivot service application.</span></span> <span data-ttu-id="18f98-161">通常のサーバー操作中に収集されるサーバーおよび使用状況のデータは、最終的に、内部データ モデルに格納されるソース データになります。</span><span class="sxs-lookup"><span data-stu-id="18f98-161">The server and usage data gathered during normal server operations is the source data that ends up in the internal data model.</span></span> <span data-ttu-id="18f98-162">**注:** イベントまたは使用状況履歴を無効にすると、複合レポートは不完全またはエラーになります。</span><span class="sxs-lookup"><span data-stu-id="18f98-162">**Note:** If you turn off events or usage history, the composite reports will be incomplete or erroneous.</span></span>  
  
##  <a name="edit-powerpivot-dashboard"></a><a name="edit"></a><span data-ttu-id="18f98-163">PowerPivot ダッシュボードの編集</span><span class="sxs-lookup"><span data-stu-id="18f98-163">Edit PowerPivot Dashboard</span></span>  
 <span data-ttu-id="18f98-164">ダッシュボードの開発またはカスタマイズに関する専門知識がある場合は、ダッシュボードを編集して新しい Web パーツを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="18f98-164">If you have expertise in dashboard development or customization, you can edit the dashboard to include new web parts.</span></span> <span data-ttu-id="18f98-165">また、ダッシュボードに含まれる Web パーツのプロパティも編集できます。</span><span class="sxs-lookup"><span data-stu-id="18f98-165">You can also edit the web part properties that are included in the dashboard.</span></span>  
  
##  <a name="create-custom-reports-for-powerpivot-management-dashboard"></a><a name="reports"></a><span data-ttu-id="18f98-166">PowerPivot 管理ダッシュボードのカスタムレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="18f98-166">Create Custom Reports for PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="18f98-167">レポートを作成するため、PowerPivot の使用状況データと履歴は、ダッシュボードと共に作成および構成される内部の PowerPivot ブックに保持されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-167">For reporting purposes, PowerPivot usage data and history is kept in an internal PowerPivot workbook that is created and configured along with the dashboard.</span></span> <span data-ttu-id="18f98-168">必要な情報が既定のレポートに含まれていない場合は、ブックに基づいて Excel でカスタム レポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18f98-168">If the default reports do not provide the information you require, you can create custom reports in Excel based on the workbook.</span></span> <span data-ttu-id="18f98-169">後で PowerPivot ソリューション ファイルをアップグレードまたはアンインストールした場合、ブックと作成したカスタム レポートは両方とも保持されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-169">Both the workbook and any custom reports that you create will be preserved if you upgrade or uninstall the PowerPivot solution files later.</span></span> <span data-ttu-id="18f98-170">ブックとレポートは、サーバーの全体管理サイト内の PowerPivot 管理ライブラリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-170">The workbook and reports are stored in the PowerPivot Management library within the Central Administration site.</span></span> <span data-ttu-id="18f98-171">このライブラリは既定では表示されませんが、[サイトの操作] にある [すべてのサイト コンテンツの表示] 操作を使用すると表示できます。</span><span class="sxs-lookup"><span data-stu-id="18f98-171">This library is not visible by default, but you can view the library using the View All Site Content action under Site Actions.</span></span>  
  
 <span data-ttu-id="18f98-172">カスタム レポートでの作業を簡単に開始できるように、PowerPivot 管理ダッシュボードには、ソースのブックに接続するための Office データ接続 (.odc) ファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="18f98-172">To help you get started with custom reporting, PowerPivot Management Dashboard provides an Office Data Connection (.odc) file to connect to the source workbook.</span></span> <span data-ttu-id="18f98-173">たとえば、.odc ファイルを Excel で使用して、追加のレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18f98-173">Dor example, you can use the .odc file in Excel to create additional reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18f98-174">Excel で .odc ファイルを使用しようとしたときに "データ ソースの初期化に失敗しました" というエラーが表示されないように、ファイルを編集してください。</span><span class="sxs-lookup"><span data-stu-id="18f98-174">Edit the file to avoid the following error when attempting to use the .odc file in Excel: "Initialization of the data source failed".</span></span> <span data-ttu-id="18f98-175">自動生成される .odc ファイルには、MSOLAP OLE DB プロバイダーでサポートされていないパラメーターが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="18f98-175">The auto-generated .odc file includes a parameter that are not supported by the MSOLAP OLE DB provider.</span></span> <span data-ttu-id="18f98-176">次の手順では、これらのパラメーターを削除する回避策について説明します。</span><span class="sxs-lookup"><span data-stu-id="18f98-176">The following instructions provide the workaround for removing the parameters.</span></span>  
  
 <span data-ttu-id="18f98-177">PowerPivot ブックに基づいて全体管理でレポートを作成するには、ファーム管理者またはサービス管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="18f98-177">You must be a farm or service administrator to build reports that are based on the PowerPivot workbook in Central Administration.</span></span>  
  
1.  <span data-ttu-id="18f98-178">PowerPivot 管理ダッシュボードを開きます。</span><span class="sxs-lookup"><span data-stu-id="18f98-178">Open the PowerPivot Management Dashboard.</span></span>  
  
2.  <span data-ttu-id="18f98-179">ページの下部にある **[レポート]** セクションまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="18f98-179">Scroll to the **Reports** section at the bottom of the page.</span></span>  
  
3.  <span data-ttu-id="18f98-180">**[PowerPivot 管理データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-180">Click **PowerPivot Management Data**.</span></span>  
  
4.  <span data-ttu-id="18f98-181">.odc ファイルをローカル フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="18f98-181">Save the .odc file to a local folder.</span></span>  
  
5.  <span data-ttu-id="18f98-182">テキスト エディターで .odc ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="18f98-182">Open the .odc file in a text editor.</span></span>  
  
6.  <span data-ttu-id="18f98-183">`<odc:ConnectionString>` 要素で、行の最後までスクロールし、`Embedded Data=False` を削除してから `Edit Mode=0` を削除します。</span><span class="sxs-lookup"><span data-stu-id="18f98-183">In the `<odc:ConnectionString>` element, scroll to the end of the line and remove `Embedded Data=False`, and then remove `Edit Mode=0`.</span></span> <span data-ttu-id="18f98-184">文字列の最後の文字がセミコロンである場合は、ここで削除します。</span><span class="sxs-lookup"><span data-stu-id="18f98-184">If the last character in the string is a semicolon, remove it now.</span></span>  
  
7.  <span data-ttu-id="18f98-185">このファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="18f98-185">Save the File.</span></span> <span data-ttu-id="18f98-186">残りの手順は、使用している PowerPivot と Excel のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="18f98-186">The remaining steps depend on which version of PowerPivot and Excel you are using.</span></span>  
  
8.  1.  <span data-ttu-id="18f98-187">Excel 2013 を起動します。</span><span class="sxs-lookup"><span data-stu-id="18f98-187">Start Excel 2013</span></span>  
  
    2.  <span data-ttu-id="18f98-188">**PowerPivot** リボンで、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-188">In the **PowerPivot** ribbon, click **Manage**.</span></span>  
  
    3.  <span data-ttu-id="18f98-189">**[外部データの取り込み]** をクリックし、 **[既存の接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-189">Click **Get External Data** and then click **Existing connections**.</span></span>  
  
    4.  <span data-ttu-id="18f98-190">.ODC ファイルが表示されている場合はそのファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-190">Click the .ODC file if you see it.</span></span> <span data-ttu-id="18f98-191">.ODC ファイルが表示されない場合は、 **[参照]** をクリックし、ファイル パスで .odc ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="18f98-191">If you do not see the .ODC file, click **Browse for More** and then in the file path, specify the .odc file.</span></span>  
  
    5.  <span data-ttu-id="18f98-192">[**開く**] をクリック</span><span class="sxs-lookup"><span data-stu-id="18f98-192">Click **Open**</span></span>  
  
    6.  <span data-ttu-id="18f98-193">**[接続のテスト]** をクリックして、接続に成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f98-193">Click **Test Connection** to verify the connection succeeds.</span></span>  
  
    7.  <span data-ttu-id="18f98-194">接続の名前を指定して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-194">Click type a name for the connection and then click **Next**.</span></span>  
  
    8.  <span data-ttu-id="18f98-195">[MDX クエリの指定] で、[**デザイン**] をクリックして mdx クエリデザイナーを開き、[編集モードのプロパティ名が正しく書式設定されていません。] という**エラーメッセージが表示**された場合に、操作するデータをアセンブルします。.ODC ファイル。</span><span class="sxs-lookup"><span data-stu-id="18f98-195">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with **If you see the error message** "The Edit Mode property name is not formatted correctly.", verify you edits the .ODC file.</span></span>  
  
    9. <span data-ttu-id="18f98-196">[ **OK]** をクリックし、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-196">Click **OK** and then click **Finish**.</span></span>  
  
    10. <span data-ttu-id="18f98-197">ピボットテーブル レポートまたはピボットグラフ レポートを作成して、データを Excel で表示します。</span><span class="sxs-lookup"><span data-stu-id="18f98-197">Create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
9. 1.  <span data-ttu-id="18f98-198">Excel 2010 を起動します。</span><span class="sxs-lookup"><span data-stu-id="18f98-198">Start Excel 2010.</span></span>  
  
    2.  <span data-ttu-id="18f98-199">PowerPivot リボンで、 **[PowerPivot ウィンドウの起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-199">On the PowerPivot ribbon, click **Launch PowerPivot Window**.</span></span>  
  
    3.  <span data-ttu-id="18f98-200">PowerPivot ウィンドウのデザイン リボンで、 **[既存の接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-200">On the Design ribbon in the PowerPivot window, click **Existing Connections**.</span></span>  
  
    4.  <span data-ttu-id="18f98-201">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-201">Click **Browse for More**.</span></span>  
  
    5.  <span data-ttu-id="18f98-202">ファイル パスで、.odc ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="18f98-202">In the file path, specify the .odc file.</span></span>  
  
    6.  <span data-ttu-id="18f98-203">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-203">Click **Open**.</span></span> <span data-ttu-id="18f98-204">使用状況データを含む PowerPivot ブックへの接続文字列を使用して、テーブルのインポート ウィザードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="18f98-204">The Table Import Wizard starts, using the connection string to the PowerPivot workbook that contains usage data.</span></span>  
  
    7.  <span data-ttu-id="18f98-205">**[接続テスト]** をクリックして、アクセス権があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18f98-205">Click **Test Connection** to verify that you have access.</span></span>  
  
    8.  <span data-ttu-id="18f98-206">接続の表示名を入力し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18f98-206">Enter a friendly name for the connection, and then click **Next**.</span></span>  
  
    9. <span data-ttu-id="18f98-207">[MDX クエリの指定] で、 **[デザイン]** をクリックして MDX クエリ デザイナーを開き、操作するデータを収集してから、ピボットテーブル レポートまたはピボットグラフ レポートを作成して、データを Excel で表示します。</span><span class="sxs-lookup"><span data-stu-id="18f98-207">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with, and then create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f98-208">参照</span><span class="sxs-lookup"><span data-stu-id="18f98-208">See Also</span></span>  
 <span data-ttu-id="18f98-209">[SharePoint 2010 での PowerPivot データ更新](../powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="18f98-209">[PowerPivot Data Refresh with SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 [<span data-ttu-id="18f98-210">&#40;PowerPivot for SharePoint の使用状況データ収集の構成</span><span class="sxs-lookup"><span data-stu-id="18f98-210">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
