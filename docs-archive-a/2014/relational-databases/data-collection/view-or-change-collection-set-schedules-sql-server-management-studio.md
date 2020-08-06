---
title: コレクション セットのスケジュールの表示または変更 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.collectionsetprop.uploads.f1
- sql12.swb.dc.collectionsetprop.general.f1
- sql12.swb.dc.collectionsetprop.description.f1
helpviewer_keywords:
- collection sets [SQL Server], changing schedules
- schedules [SQL Server], changing collection set
- collection sets [SQL Server], viewing schedules
- schedules [SQL Server], viewing collection set
ms.assetid: 26336c98-78c5-414f-8d6a-574fc3af60c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2eb1acf0346b3e16bd1d54829abbc070e1d9d63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643972"
---
# <a name="view-or-change-collection-set-schedules-sql-server-management-studio"></a><span data-ttu-id="110b5-102">コレクション セットのスケジュールの表示または変更 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="110b5-102">View or Change Collection Set Schedules (SQL Server Management Studio)</span></span>
  <span data-ttu-id="110b5-103">コレクション セットのスケジュールは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-103">You can view or change collection set schedules by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="110b5-104">コレクション モードをキャッシュと非キャッシュのどちらにするかで、スケジュールをどのように変更できるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="110b5-104">The collection mode, cached or non-cached, determines how you can make changes to a schedule.</span></span> <span data-ttu-id="110b5-105">キャッシュ モードでは、コレクションとアップロードに別々のスケジュールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-105">Cached mode uses separate schedules for collection and upload.</span></span> <span data-ttu-id="110b5-106">非キャッシュ モードでは、コレクションとアップロードに同じスケジュールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-106">Non-cached mode uses the same schedule for collection and upload.</span></span> <span data-ttu-id="110b5-107">それぞれのシステム データ コレクション セットで使用されるコレクション モードの種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="110b5-107">The type of collection mode for each of the System Datacollection sets is as follows:</span></span>  
  
-   <span data-ttu-id="110b5-108">**ディスク使用量** では非キャッシュ コレクション モードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-108">**Disk Usage** uses non-cached collection mode.</span></span>  
  
-   <span data-ttu-id="110b5-109">**クエリ統計情報** ではキャッシュ コレクション モードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-109">**Query Statistics** uses cached collection mode.</span></span>  
  
-   <span data-ttu-id="110b5-110">**サーバー利用状況** ではキャッシュ コレクション モードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-110">**Server Activity** uses cached collection mode.</span></span>  
  
### <a name="to-view-collection-set-schedules"></a><span data-ttu-id="110b5-111">コレクション セットのスケジュールを表示するには</span><span class="sxs-lookup"><span data-stu-id="110b5-111">To view collection set schedules</span></span>  
  
1.  <span data-ttu-id="110b5-112">オブジェクト エクスプローラーで、 **[管理]** ノード、 **[データ コレクション]** 、 **[システム データ コレクション セット]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="110b5-112">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="110b5-113">コレクション セット名を右クリックし、 **[プロパティ]** をクリックして [[データ コレクション セットのプロパティ]](#CollectionSet) ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-113">Right-click a collection set name, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
### <a name="to-change-the-schedules-for-a-cached-mode-collection-set"></a><span data-ttu-id="110b5-114">キャッシュ モードのコレクション セットのスケジュールを変更するには</span><span class="sxs-lookup"><span data-stu-id="110b5-114">To change the schedules for a cached mode collection set</span></span>  
  
1.  <span data-ttu-id="110b5-115">オブジェクト エクスプローラーで、 **[管理]** ノード、 **[データ コレクション]** 、 **[システム データ コレクション セット]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="110b5-115">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="110b5-116">**[クエリ統計情報]** などのキャッシュ モードを使用するコレクション セットを右クリックし、 **[プロパティ]** をクリックして、 [[データ コレクション セットのプロパティ]](#CollectionSet) ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-116">Right-click a collection set that uses cached mode, such as **Query Statistics**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
3.  <span data-ttu-id="110b5-117">**[全般]** ページで収集頻度を変更できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-117">You can change the collection frequency on the **General** page.</span></span> <span data-ttu-id="110b5-118">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="110b5-118">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="110b5-119">詳細ペインで、 **[コレクション アイテム]** テーブルの **[収集頻度 (秒)]** 列に表示されている数値をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-119">In the details pane, double-click the number that is displayed for the **Collection Frequency (sec)** column in the **Collection items** table.</span></span>  
  
    2.  <span data-ttu-id="110b5-120">より小さな数値を入力して収集頻度を増加させるか、またはより大きな数値を入力して収集頻度を減少させ、&lt;localizedText&gt;Enter&lt;/localizedText&gt; キーを押して新しい値を格納します。</span><span class="sxs-lookup"><span data-stu-id="110b5-120">To increase or decrease the collection frequency, type a lower or higher number, and then press ENTER to store the new value.</span></span>  
  
4.  <span data-ttu-id="110b5-121">コレクション セットの既存のアップロード スケジュールを変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="110b5-121">To change the existing upload schedule for the collection set, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="110b5-122">**[アップロード]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-122">Click the **Uploads** page.</span></span>  
  
    2.  <span data-ttu-id="110b5-123">詳細ペインで **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-123">In the details pane, click **Pick**.</span></span>  
  
         <span data-ttu-id="110b5-124">**[ジョブのスケジュール選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-124">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="110b5-125">利用可能なスケジュールがテーブルとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-125">The available schedules appear as a table.</span></span>  
  
    3.  <span data-ttu-id="110b5-126">変更するスケジュールを持つ行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-126">Click the row with the schedule that you want.</span></span> <span data-ttu-id="110b5-127">たとえば、スケジュールを 5 分ごとの頻度に変更するには、スケジュール名が **[CollectorSchedule_Every_5min]** である行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-127">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min.**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="110b5-128">選択したスケジュールのプロパティを表示および編集するには、 **[プロパティ]** をクリックして、このスケジュールの **[ジョブ スケジュールのプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-128">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="110b5-129">このダイアログ ボックスを使用して、頻度などのスケジュール情報を変更できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-129">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
        >   
        >  <span data-ttu-id="110b5-130">既存のスケジュールを変更する代わりに、 **[アップロード]** ページの **[新規作成]** をクリックして新しいアップロード スケジュールを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="110b5-130">As an alternative to modifying an existing schedule, you can create a new upload schedule by clicking **New** on the **Uploads** page.</span></span> <span data-ttu-id="110b5-131">この操作を行うと、 **[新しいジョブ スケジュール]** ダイアログ ボックスが開きます。このページでは、カスタム スケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-131">This action opens the **New Job Schedule** dialog box, which you can use to create a custom schedule.</span></span>  
  
    4.  <span data-ttu-id="110b5-132">スケジュールの構成が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-132">When you are finished configuring the schedule, click **OK**.</span></span>  
  
         <span data-ttu-id="110b5-133">加えた変更が **[アップロード]** ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-133">The changes that you made appear on the **Uploads** page.</span></span>  
  
5.  <span data-ttu-id="110b5-134">**[OK]** をクリックして、収集頻度とアップロード スケジュールの変更を保存し、 **[データ コレクション セットのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="110b5-134">Click **OK** to save the changes to the collection frequency and the upload schedule, and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
### <a name="to-change-the-schedule-for-a-non-cached-mode-collection-set"></a><span data-ttu-id="110b5-135">非キャッシュ モードのコレクション セットのスケジュールを変更するには</span><span class="sxs-lookup"><span data-stu-id="110b5-135">To change the schedule for a non-cached mode collection set</span></span>  
  
1.  <span data-ttu-id="110b5-136">オブジェクト エクスプローラーで、 **[管理]** ノード、 **[データ コレクション]** 、 **[システム データ コレクション セット]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="110b5-136">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="110b5-137">**[ディスク使用量]** などのキャッシュ モードを使用しないコレクション セットを右クリックし、 **[プロパティ]** をクリックして、 [[データ コレクション セットのプロパティ]](#CollectionSet) ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-137">Right-click a collection set that uses non-cached mode, such as **Disk Usage**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
     <span data-ttu-id="110b5-138">**[データ コレクション セットのプロパティ]** ダイアログ ボックスが開き、コレクション セットのプロパティがページ ビューで表示されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-138">The **Data Collection Set Properties** dialog box displays a paged view of the collection set properties.</span></span>  
  
3.  <span data-ttu-id="110b5-139">コレクション セットのスケジュールを変更するには、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-139">To change the schedule for the collection set, click **Pick**.</span></span>  
  
     <span data-ttu-id="110b5-140">**[ジョブのスケジュール選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-140">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="110b5-141">利用可能なスケジュールがテーブルとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-141">The available schedules are displayed as a table.</span></span>  
  
4.  <span data-ttu-id="110b5-142">変更するスケジュールを持つ行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-142">Click the row with the schedule that you want.</span></span> <span data-ttu-id="110b5-143">たとえば、スケジュールを 5 分ごとの頻度に変更するには、スケジュール名が **[CollectorSchedule_Every_5min]** である行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-143">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="110b5-144">選択したスケジュールのプロパティを表示および編集するには、 **[プロパティ]** をクリックして、このスケジュールの **[ジョブ スケジュールのプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-144">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="110b5-145">このダイアログ ボックスを使用して、頻度などのスケジュール情報を変更できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-145">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
    >   
    >  <span data-ttu-id="110b5-146">既存のスケジュールを変更する代わりに、 **[全般]** ページの **[新規作成]** をクリックして新しい収集頻度とアップロード スケジュールを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="110b5-146">As an alternative to modifying an existing schedule, you can create a new collect and upload schedule by clicking **New** on the **General** page.</span></span> <span data-ttu-id="110b5-147">この操作を行うと、 **[新しいジョブ スケジュール]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="110b5-147">This action opens the **New Job Schedule** dialog box.</span></span>  
  
5.  <span data-ttu-id="110b5-148">スケジュールの構成が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-148">When you are finished configuring the schedule, click **OK**.</span></span>  
  
6.  <span data-ttu-id="110b5-149">**[OK]** をクリックして、変更を保存し、 **[データ コレクション セットのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="110b5-149">Click **OK** to save the changes and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
####  <a name="data-collection-set-properties-dialog-box"></a><a name="CollectionSet"></a> <span data-ttu-id="110b5-150">[データ コレクション セットのプロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="110b5-150">Data Collection Set Properties Dialog Box</span></span>  
 <span data-ttu-id="110b5-151">**[全般] ページ**</span><span class="sxs-lookup"><span data-stu-id="110b5-151">**General Page**</span></span>  
  
 <span data-ttu-id="110b5-152">このページを使用すると、データの収集方法とアップロード方法を構成し、スケジュールを構成し、管理データ ウェアハウスでのデータ保持期間を構成できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-152">Use this page to configure how data is collected and uploaded, configure schedules, and configure data retention periods in the management data warehouse.</span></span> <span data-ttu-id="110b5-153">このページでは、コレクター型や収集頻度などコレクション セットに関する情報や、コレクション セットに使用される入力パラメーターの情報も提供します。</span><span class="sxs-lookup"><span data-stu-id="110b5-153">This page also provides information about collection sets, such as collector types and collection frequencies, as well as the input parameters that are used for a collection set.</span></span>  
  
 <span data-ttu-id="110b5-154">**名前**</span><span class="sxs-lookup"><span data-stu-id="110b5-154">**Name**</span></span>  
 <span data-ttu-id="110b5-155">このページが参照するコレクション セットの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="110b5-155">Displays the name of the collection set that this page refers to.</span></span>  
  
 <span data-ttu-id="110b5-156">**[データの収集およびアップロード]**</span><span class="sxs-lookup"><span data-stu-id="110b5-156">**Data collection and upload**</span></span>  
 <span data-ttu-id="110b5-157">データを収集して管理データ ウェアハウスにアップロードする方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="110b5-157">Specifies how data is collected and uploaded to the management data warehouse.</span></span> <span data-ttu-id="110b5-158">以下のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="110b5-158">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="110b5-159">**キャッシュしない - データを同じスケジュールで収集およびアップロードします。**</span><span class="sxs-lookup"><span data-stu-id="110b5-159">**Non-cached. Collection and data upload on the same schedule.**</span></span>|<span data-ttu-id="110b5-160">選択した場合、次のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="110b5-160">When selected, specify one of the following:</span></span><br /><br /> <span data-ttu-id="110b5-161">**[要求時]** :</span><span class="sxs-lookup"><span data-stu-id="110b5-161">**On-demand**.</span></span> <span data-ttu-id="110b5-162">データは要求時に収集およびアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="110b5-162">Data is collected and uploaded on demand.</span></span><br /><br /> <span data-ttu-id="110b5-163">**[スケジュール]** :</span><span class="sxs-lookup"><span data-stu-id="110b5-163">**Schedule**.</span></span> <span data-ttu-id="110b5-164">データはスケジュールに従って収集およびアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="110b5-164">Data is collected and uploaded according to a schedule.</span></span> <span data-ttu-id="110b5-165">**[選択]** をクリックしてスケジュールを定義済み一覧から選択するか、 **[新規作成]** をクリックして新しいスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="110b5-165">Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>|  
|<span data-ttu-id="110b5-166">**キャッシュする - 一定の収集頻度でデータを収集およびキャッシュして、別途設定されたスケジュールでキャッシュされたデータをアップロードします。**</span><span class="sxs-lookup"><span data-stu-id="110b5-166">**Cached. Collect and cache data at a set of collection frequencies. Upload cached data on a separate schedule.**</span></span>|<span data-ttu-id="110b5-167">指定された収集頻度でデータを収集およびキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="110b5-167">Collect and cache data for a specified collection frequency.</span></span> <span data-ttu-id="110b5-168">収集したデータを、別途設定されたスケジュールでアップロードします。</span><span class="sxs-lookup"><span data-stu-id="110b5-168">Upload the collected data on a separate schedule.</span></span>|  
  
 <span data-ttu-id="110b5-169">**[収集頻度 (秒)]**</span><span class="sxs-lookup"><span data-stu-id="110b5-169">**Collection items**</span></span>  
 <span data-ttu-id="110b5-170">コレクション セット内のコレクション アイテムを表示します。</span><span class="sxs-lookup"><span data-stu-id="110b5-170">Displays the collection items in the collection set.</span></span> <span data-ttu-id="110b5-171">コレクション アイテムごとに次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="110b5-171">The following information is provided for each collection item:</span></span>  
  
-   <span data-ttu-id="110b5-172">**名前**</span><span class="sxs-lookup"><span data-stu-id="110b5-172">**Name**</span></span>  
  
-   <span data-ttu-id="110b5-173">**[コレクターの種類]**</span><span class="sxs-lookup"><span data-stu-id="110b5-173">**Collector Type**</span></span>  
  
-   <span data-ttu-id="110b5-174">**[収集頻度]** (秒)。</span><span class="sxs-lookup"><span data-stu-id="110b5-174">**Collection Frequency** (secs).</span></span> <span data-ttu-id="110b5-175">このフィールドは、 **[データの収集およびアップロード]** がキャッシュするように構成されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-175">This field is editable if **Data collection and upload** is configured as cached.</span></span> <span data-ttu-id="110b5-176">収集頻度を設定するには、このセルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="110b5-176">Double-click this cell to set the collection frequency.</span></span>  
  
 <span data-ttu-id="110b5-177">**入力パラメーター。**</span><span class="sxs-lookup"><span data-stu-id="110b5-177">**Input parameters**</span></span>  
 <span data-ttu-id="110b5-178">コレクション セットに使用される入力パラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="110b5-178">Displays the input parameters used for the collection set.</span></span>  
  
 <span data-ttu-id="110b5-179">**[実行するアカウント名]**</span><span class="sxs-lookup"><span data-stu-id="110b5-179">**Run as**</span></span>  
 <span data-ttu-id="110b5-180">コレクション セットの実行に使用するアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="110b5-180">Specifies the account used to run the collection set.</span></span> <span data-ttu-id="110b5-181">既定は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスのアカウントです。</span><span class="sxs-lookup"><span data-stu-id="110b5-181">By default this is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service Account.</span></span> <span data-ttu-id="110b5-182">プロキシ アカウントが定義されている場合、この一覧には、使用可能なプロキシ アカウントの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="110b5-182">If proxy accounts are defined, this list includes the names of the available proxy accounts.</span></span>  
  
 <span data-ttu-id="110b5-183">**[収集したデータを管理データ ウェアハウスに保持する期間を設定します。]**</span><span class="sxs-lookup"><span data-stu-id="110b5-183">**Set how long collected data will be retained in the management data warehouse.**</span></span>  
 <span data-ttu-id="110b5-184">収集したデータを保持する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="110b5-184">Specifies how long collected data is retained.</span></span> <span data-ttu-id="110b5-185">以下のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="110b5-185">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="110b5-186">**[データ保持日数]**</span><span class="sxs-lookup"><span data-stu-id="110b5-186">**Retain data for**</span></span>|<span data-ttu-id="110b5-187">このオプションは既定で選択されます。既定の保持期間は 14 日間です。</span><span class="sxs-lookup"><span data-stu-id="110b5-187">This option is selected by default, and the default retention period is 14 days.</span></span>|  
|<span data-ttu-id="110b5-188">**[データを無期限に保持]**</span><span class="sxs-lookup"><span data-stu-id="110b5-188">**Retain data indefinitely**</span></span>|<span data-ttu-id="110b5-189">データを保持する期間に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="110b5-189">There is no time limit on the length of time that data is retained.</span></span>|  
  
 <span data-ttu-id="110b5-190">**[アップロード] ページ**</span><span class="sxs-lookup"><span data-stu-id="110b5-190">**Uploads Page**</span></span>  
  
 <span data-ttu-id="110b5-191">このページを使用すると、このコレクション セットによって収集されるデータのアップロード スケジュールを構成できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-191">Use this page to configure the upload schedule for data that is collected by this collection set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="110b5-192">このタブは、 **[キャッシュする]** オプションが **[データの収集およびアップロード]** に対して構成されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-192">This tab is only enabled if the **Cached** option is configured for **Data collection and upload**.</span></span>  
  
 <span data-ttu-id="110b5-193">**サーバー**</span><span class="sxs-lookup"><span data-stu-id="110b5-193">**Server**</span></span>  
 <span data-ttu-id="110b5-194">管理データ ウェアハウスをホストするサーバーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="110b5-194">Displays the name of the server that hosts the management data warehouse.</span></span> <span data-ttu-id="110b5-195">詳細については、「[管理データ ウェアハウスの構成 &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="110b5-195">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="110b5-196">**[管理データ ウェアハウス]**</span><span class="sxs-lookup"><span data-stu-id="110b5-196">**Management data warehouse**</span></span>  
 <span data-ttu-id="110b5-197">管理データ ウェアハウスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="110b5-197">Displays the name of the management data warehouse.</span></span> <span data-ttu-id="110b5-198">詳細については、「[管理データ ウェアハウスの構成 &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="110b5-198">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="110b5-199">**[最終アップロード]**</span><span class="sxs-lookup"><span data-stu-id="110b5-199">**Last upload**</span></span>  
 <span data-ttu-id="110b5-200">コレクション セットに対して実行された最終アップロードの日付と時刻に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="110b5-200">Displays date and time information for the last upload done for the collection set.</span></span>  
  
 <span data-ttu-id="110b5-201">**[アップロード スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="110b5-201">**Upload schedule**</span></span>  
 <span data-ttu-id="110b5-202">コレクション セットのアップロード スケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="110b5-202">Specifies the upload schedule for the collection set.</span></span> <span data-ttu-id="110b5-203">有効になっている場合は、 **[選択]** をクリックしてスケジュールを定義済み一覧から選択するか、 **[新規作成]** をクリックして新しいスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="110b5-203">If enabled, Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>  
  
 <span data-ttu-id="110b5-204">**[説明] ページ'**</span><span class="sxs-lookup"><span data-stu-id="110b5-204">**Description Page**</span></span>  
  
 <span data-ttu-id="110b5-205">このページを使用すると、このプロパティ ページが参照するコレクション セットの説明を表示できます。</span><span class="sxs-lookup"><span data-stu-id="110b5-205">Use this page to view a description of the collection set that this properties page refers to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110b5-206">参照</span><span class="sxs-lookup"><span data-stu-id="110b5-206">See Also</span></span>  
 <span data-ttu-id="110b5-207">[データ コレクションの管理](manage-data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="110b5-207">[Manage Data Collection](manage-data-collection.md) </span></span>  
 <span data-ttu-id="110b5-208">[[データ コレクション]](data-collection.md)</span><span class="sxs-lookup"><span data-stu-id="110b5-208">[Data Collection](data-collection.md)</span></span>  
  
  
