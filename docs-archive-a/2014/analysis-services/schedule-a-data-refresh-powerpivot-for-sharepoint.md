---
title: データ更新のスケジュール (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 8571208f-6aae-4058-83c6-9f916f5e2f9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d6078cf59c27c15ead8f22047ba9add20757be7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633379"
---
# <a name="schedule-a-data-refresh-powerpivot-for-sharepoint"></a><span data-ttu-id="90615-102">データ更新のスケジュール (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="90615-102">Schedule a Data Refresh (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="90615-103">データ更新をスケジュールすると、SharePoint サイトにパブリッシュした Excel ブック内の PowerPivot データが自動更新されるようになります。</span><span class="sxs-lookup"><span data-stu-id="90615-103">You can schedule data refresh to get automatic updates to PowerPivot data inside an Excel workbook that you published to a SharePoint site.</span></span>  
  
 <span data-ttu-id="90615-104">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="90615-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="90615-105">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="90615-105">**In this topic:**</span></span>  
  
 [<span data-ttu-id="90615-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="90615-106">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="90615-107">データ更新の概要</span><span class="sxs-lookup"><span data-stu-id="90615-107">Data Refresh Overview</span></span>](#intro)  
  
 [<span data-ttu-id="90615-108">データ更新の有効化とスケジュール</span><span class="sxs-lookup"><span data-stu-id="90615-108">Enable and schedule data refresh</span></span>](#drenablesched)  
  
 [<span data-ttu-id="90615-109">データ更新の確認</span><span class="sxs-lookup"><span data-stu-id="90615-109">Verify Data Refresh</span></span>](#drverify)  
  
> [!NOTE]  
>  <span data-ttu-id="90615-110">PowerPivot データ更新は、SharePoint ファーム内の Analysis Services サーバー インスタンスによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="90615-110">PowerPivot data refresh is performed by Analysis Services server instances in the SharePoint farm.</span></span> <span data-ttu-id="90615-111">Excel Services のデータ更新機能とは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="90615-111">It is not related to the data refresh feature that is provided in Excel Services.</span></span> <span data-ttu-id="90615-112">PowePivot スケジュールのデータ更新機能では、PowerPivot 以外のデータは更新されません。</span><span class="sxs-lookup"><span data-stu-id="90615-112">The PowePivot Schedule data refresh feature will not refresh non PowerPivot data.</span></span>  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="90615-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="90615-113">Prerequisites</span></span>  
 <span data-ttu-id="90615-114">データ更新スケジュールを作成するには、ブックの投稿レベル以上の権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-114">You must have Contribute level of permission or greater on the workbook to create a data refresh schedule.</span></span>  
  
 <span data-ttu-id="90615-115">データ更新時にアクセスされる外部データ ソースが使用可能であること、およびスケジュールに指定した資格情報がそれらのデータ ソースにアクセスする権限を持っていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-115">External data sources that are accessed during data refresh must be available and the credentials you specify in the schedule must have permission to access those data sources.</span></span> <span data-ttu-id="90615-116">スケジュールされたデータ更新には、ネットワーク接続を介してアクセスできるデータ ソースの場所が必要になります (たとえば、ワークステーションのローカル フォルダーではなく、ネットワーク ファイル共有など)。</span><span class="sxs-lookup"><span data-stu-id="90615-116">Scheduled data refresh requires a data source location that is accessible over a network connection (for example, from a network file share rather than a local folder on your workstation).</span></span>  
  
 <span data-ttu-id="90615-117">データ ソースには、Office ドキュメントまたは Access データベースを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="90615-117">The data source cannot be an Office document or Access database.</span></span> <span data-ttu-id="90615-118">Office では、サーバー環境での Office データ接続コンポーネントの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="90615-118">Office does not support the use of the Office data connectivity components in a server environment.</span></span> <span data-ttu-id="90615-119">ブックにそれらのソースからのデータが含まれている場合は、データ更新スケジュールのデータ ソースの一覧からそれらのソースを削除してください。</span><span class="sxs-lookup"><span data-stu-id="90615-119">If your workbook contains data from these sources, be sure to remove those sources from the data source list in your data refresh schedule.</span></span>  
  
 <span data-ttu-id="90615-120">ブックは [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] のバージョンであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-120">The workbook must be a [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] version.</span></span> <span data-ttu-id="90615-121">以前のリリースの PowerPivot for Excel で作成されたブックを使用する場合、データベースを最新のバージョンにアップグレードしないと、データ更新のスケジュールが正常に機能しません。</span><span class="sxs-lookup"><span data-stu-id="90615-121">If you use workbooks that were created in the previous release of PowerPivot for Excel, schedule data refresh will not work unless you upgrade the database to the most recent version.</span></span>  
  
 <span data-ttu-id="90615-122">更新操作の終了時に、ブックがチェックインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-122">The workbook must be checked in at the time the refresh operation is finished.</span></span> <span data-ttu-id="90615-123">ブックに対するロックは、データ更新の最後に、ファイルに対して行われます (更新の開始時ではなく、ファイルが保存されるときに実行されます)。</span><span class="sxs-lookup"><span data-stu-id="90615-123">A lock on the workbook is placed on the file at the end of data refresh, when the file is saved, rather than when refresh starts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90615-124">データ更新の進行中に、サーバーによってブックがロックされることはありません。</span><span class="sxs-lookup"><span data-stu-id="90615-124">The server does not lock the workbook while the data refresh is in progress.</span></span> <span data-ttu-id="90615-125">ただし、更新されたファイルをチェックインするために、ファイルはデータ更新の終了時にロックされます。</span><span class="sxs-lookup"><span data-stu-id="90615-125">However, it does lock the file at the end of data refresh for the purpose of checking in the updated file.</span></span> <span data-ttu-id="90615-126">この時点で、ファイルが別のユーザーにチェックアウトされると、更新されたデータが破棄されます。同様に、ファイルがチェックインされているが、データ更新の開始時にサーバーによって取得されたコピーと大幅に異なる場合、更新されたデータは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="90615-126">If at this time, the file is checked out to another user, the refreshed data will be thrown out. Similarly, if the file is checked in, but it is significantly different from the copy retrieved by the server at the start of data refresh, the refreshed data will be discarded.</span></span>  
  
##  <a name="data-refresh-overview"></a><a name="intro"></a><span data-ttu-id="90615-127">データ更新の概要</span><span class="sxs-lookup"><span data-stu-id="90615-127">Data Refresh Overview</span></span>  
 <span data-ttu-id="90615-128">Excel ブックの PowerPivot データは、リモート サーバーやネットワーク ファイル共有からアクセスされる外部のデータベースやデータ ファイルなど、複数の外部データ ソースから取得できます。</span><span class="sxs-lookup"><span data-stu-id="90615-128">PowerPivot data in an Excel workbook can originate from multiple external data sources, including external databases or data files that you access from remote servers or network file shares.</span></span> <span data-ttu-id="90615-129">接続された外部データ ソースからインポートされたデータを含む PowerPivot ブックの場合は、データ更新を構成して、元のソースで更新されたデータを自動的にインポートするようにスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="90615-129">For PowerPivot workbooks that contain imported data from connected or external data sources, you can configure data refresh to schedule an automatic import of updated data from those original sources.</span></span>  
  
 <span data-ttu-id="90615-130">外部データ ソースには、PowerPivot クライアント アプリケーションを使用してブックに元のデータをインポートしたときに指定した、埋め込まれた接続文字列、URL、または UNC パスを通してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="90615-130">An external data source is accessed through an embedded connection string, URL, or UNC path that you specified when you imported the original data into the workbook using the PowerPivot client application.</span></span> <span data-ttu-id="90615-131">PowerPivot ブックに格納された元の接続情報が、その後のデータ更新操作に再利用されます。</span><span class="sxs-lookup"><span data-stu-id="90615-131">Original connection information that is stored in the PowerPivot workbook is reused for subsequent data refresh operations.</span></span> <span data-ttu-id="90615-132">データ ソースへの接続に使用される資格情報を上書きできますが、データ更新の目的で接続文字列を上書きすることはできません。既存の接続情報のみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="90615-132">Although you can overwrite credentials used to connect to data sources, you cannot overwrite connection strings for data refresh purposes; only existing connection information is used.</span></span>  
  
 <span data-ttu-id="90615-133">各ブックには、データ更新スケジュール ページが 1 つだけあり、そのページにすべてのスケジュール情報が指定されています。</span><span class="sxs-lookup"><span data-stu-id="90615-133">There is only one data refresh schedule page for each workbook, and all schedule information is specified on that page.</span></span> <span data-ttu-id="90615-134">通常は、ブックの作成者がスケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="90615-134">Typically, the person who authored the workbook defines the schedule.</span></span>  
  
 <span data-ttu-id="90615-135">スケジュール所有者として、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="90615-135">As the schedule owner, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="90615-136">既定のスケジュールを定義する。</span><span class="sxs-lookup"><span data-stu-id="90615-136">Define the default schedule.</span></span> <span data-ttu-id="90615-137">これは、データ ソース レベルで定義されているスケジュールがない場合に使用されるスケジュールです。</span><span class="sxs-lookup"><span data-stu-id="90615-137">This is the schedule that is used if there are no scheduled defined at the data source level.</span></span>  
  
-   <span data-ttu-id="90615-138">データ更新の実行に使用される資格情報を指定する。</span><span class="sxs-lookup"><span data-stu-id="90615-138">Specify the credentials used to run data refresh</span></span>  
  
-   <span data-ttu-id="90615-139">どのデータ ソースを更新操作に含めるかを選択する。</span><span class="sxs-lookup"><span data-stu-id="90615-139">Choose which data sources to include in the refresh operation.</span></span>  
  
-   <span data-ttu-id="90615-140">必要に応じて、データ更新時に照会される各データ ソースの個別のスケジュールと資格情報をインラインで指定します。</span><span class="sxs-lookup"><span data-stu-id="90615-140">Optionally, specify in-line, individual schedules and credentials for each data source that is queried during data refresh.</span></span> <span data-ttu-id="90615-141">各データ ソースは、個別に更新できます。</span><span class="sxs-lookup"><span data-stu-id="90615-141">Each data source can be refreshed independently.</span></span> <span data-ttu-id="90615-142">すべてのデータ ソースにカスタム スケジュールを作成すると、既定のスケジュールは無視されます。</span><span class="sxs-lookup"><span data-stu-id="90615-142">If you create custom schedules for every data source, the default schedule is ignored.</span></span>  
  
 <span data-ttu-id="90615-143">個々のデータ ソースに対して詳細なスケジュールを作成することで、外部データ ソースでの変動に合わせた更新スケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="90615-143">Creating granular schedules for individual data sources enables you to match the refresh schedule to fluctuations in the external data sources.</span></span> <span data-ttu-id="90615-144">たとえば、1 日をとおして生成されるトランザクション データが含まれる外部データ ソースに対しては、更新された情報を毎晩取得するようなデータ更新スケジュールを個別に作成できます。</span><span class="sxs-lookup"><span data-stu-id="90615-144">For example, if an external data source contains transactional data that is generated throughout the day, you can create an individual data refresh schedule for that data source to get its updated information nightly.</span></span>  
  
##  <a name="enable-and-schedule-data-refresh"></a><a name="drenablesched"></a><span data-ttu-id="90615-145">データ更新の有効化とスケジュール</span><span class="sxs-lookup"><span data-stu-id="90615-145">Enable and schedule data refresh</span></span>  
 <span data-ttu-id="90615-146">SharePoint ライブラリにパブリッシュした Excel ブック内の PowerPivot データ用にデータ更新をスケジュールするには、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="90615-146">Use the following instructions to schedule data refresh for PowerPivot data in an Excel workbook that is published to a SharePoint library.</span></span>  
  
1.  <span data-ttu-id="90615-147">ブックが含まれているライブラリで、ブックを選択して下矢印をクリックし、コマンドの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="90615-147">In the library that contains the workbook, select the workbook and then click the down arrow to display a list of commands.</span></span>  
  
2.  <span data-ttu-id="90615-148">**[PowerPivot データ更新の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90615-148">Click **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="90615-149">データ更新スケジュールが既に定義されている場合は、代わりに [データ更新履歴の表示] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90615-149">If a data refresh schedule is already defined, you will see the View Data Refresh history page instead.</span></span> <span data-ttu-id="90615-150">**[データ更新の構成]** をクリックすると、スケジュール定義ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="90615-150">You can click **Configure data refresh** to open the schedule definition page.</span></span>  
  
3.  <span data-ttu-id="90615-151">スケジュール定義ページで、 **[有効]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="90615-151">In the schedule definition page, select the **Enable** checkbox.</span></span>  
  
4.  <span data-ttu-id="90615-152">[スケジュールの詳細] で、スケジュールの種類とその詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="90615-152">In Schedule Details, specify the type of schedule and specify its details.</span></span> <span data-ttu-id="90615-153">この手順では、既定のスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="90615-153">This step creates the default schedule.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="90615-154">**[さらに、できるだけ早く更新を行います]** チェック ボックスをオンにしてください。</span><span class="sxs-lookup"><span data-stu-id="90615-154">Be sure to select the **Also refresh as soon as possible** checkbox.</span></span> <span data-ttu-id="90615-155">これにより、このブックに対してデータ更新が機能していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="90615-155">Doing so lets you verify that data refresh is operational for this workbook.</span></span> <span data-ttu-id="90615-156">スケジュールを保存した後、データ更新が開始するまで最大 1 分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="90615-156">Note that after you save schedule, it can take up to a minute for data refresh to start.</span></span>  
  
5.  <span data-ttu-id="90615-157">[最も早い開始時刻] で、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="90615-157">In Earliest Start Time, choose one of the following:</span></span>  
  
    1.  <span data-ttu-id="90615-158">**[営業時間後]** は、営業時間外の処理期間を示します。これは、その日の営業時間に生成された最新のデータがデータベース サーバーに保存されている可能性が高い期間です。</span><span class="sxs-lookup"><span data-stu-id="90615-158">**After business hours** specifies an off-hours processing period when database servers are more likely to have current data that was generated throughout the business day.</span></span>  
  
    2.  <span data-ttu-id="90615-159">**[特定の最も早い開始時刻]** は、データ更新要求が処理キューに追加される最も早い開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="90615-159">**Specific earliest start time** is the hour and minutes of the earliest time of day the data refresh request is added to a process queue.</span></span> <span data-ttu-id="90615-160">15 分間隔で指定できます。</span><span class="sxs-lookup"><span data-stu-id="90615-160">You can specify minutes in 15-minute intervals.</span></span> <span data-ttu-id="90615-161">この設定は、現在の日付や将来の日付に適用されます。</span><span class="sxs-lookup"><span data-stu-id="90615-161">The setting applies to the current day as well as future dates.</span></span> <span data-ttu-id="90615-162">たとえば、午前 6 時 30 分の値を指定して</span><span class="sxs-lookup"><span data-stu-id="90615-162">For example, if you specify a value of 6:30 A.M.</span></span> <span data-ttu-id="90615-163">現在の時間が午後 4 時 30 分である場合、午後 4 時 30 分は午前 6 時 30 分の後であるため、更新要求は現在の日付のキューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="90615-163">and the current time is 4:30 P.M., the refresh request will be added to the queue in the current day because 4:30 P.M.</span></span> <span data-ttu-id="90615-164">午前6:30 時より後</span><span class="sxs-lookup"><span data-stu-id="90615-164">is after 6:30 A.M.</span></span>  
  
     <span data-ttu-id="90615-165">最も早い開始時刻は、要求が処理キューに追加される時間を表します。</span><span class="sxs-lookup"><span data-stu-id="90615-165">Earliest start time defines when a request is added to the process queue.</span></span> <span data-ttu-id="90615-166">実際の処理は、データ処理の開始に適したリソースがサーバーに存在する時点で行われます。</span><span class="sxs-lookup"><span data-stu-id="90615-166">Actual processing occurs when the server has adequate resources to begin data processing.</span></span> <span data-ttu-id="90615-167">処理完了後に、実際の処理時間がデータ更新の履歴に記録されます。</span><span class="sxs-lookup"><span data-stu-id="90615-167">Actual processing time will be recorded in data refresh history after processing is complete.</span></span>  
  
6.  <span data-ttu-id="90615-168">**[さらに、できるだけ早く更新を行います]** チェック ボックスをオンにして、データ更新をサーバーが処理できるようになったらすぐに実行します。</span><span class="sxs-lookup"><span data-stu-id="90615-168">Select the checkbox **Also refresh as soon as possible** to run data refresh as soon as the server can process it.</span></span> <span data-ttu-id="90615-169">データ更新ジョブが成功したら、データ ソースが利用可能であり、権限とサーバー構成が正しく設定されていることが確認できます。</span><span class="sxs-lookup"><span data-stu-id="90615-169">A successful outcome of a data refresh job verifies that the data sources are available and that permissions and server configuration are set correctly.</span></span>  
  
7.  <span data-ttu-id="90615-170">[電子メール通知] に、処理エラーの発生時に通知するユーザーの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="90615-170">In E-mail notifications, enter the e-mail address of the person who should be notified in the event of a processing error.</span></span>  
  
8.  <span data-ttu-id="90615-171">[資格情報] では、データ更新ジョブの実行に使用するアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="90615-171">In Credentials, specify an account used to run the data refresh job.</span></span> <span data-ttu-id="90615-172">データ更新のためにブックを開くことができるように、このアカウントにはブックに対する投稿権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-172">The account must have Contribute permissions on the workbook so that it can open the workbook to refresh its data.</span></span> <span data-ttu-id="90615-173">また、Windows ドメイン ユーザー アカウントであることも必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-173">It must be a Windows domain user account.</span></span> <span data-ttu-id="90615-174">多くの場合、このアカウントにはデータ更新時に使用される外部データ ソースに対する読み取り権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-174">In many cases, this account must also have read permissions on the external data sources used during data refresh.</span></span> <span data-ttu-id="90615-175">特に、最初に [Windows 認証を使用する] オプションを使用してデータをインポートした場合、現在のユーザーの Windows 資格情報を使用する接続文字列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="90615-175">Specifically, if you originally imported the data using the Use Windows Authentication option, then the connection string is built to use the Windows credentials of the current user.</span></span> <span data-ttu-id="90615-176">現在のユーザーがデータ更新アカウントの場合、データ更新を成功させるためには、そのアカウントに外部データ ソースに対する読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-176">If the current user is the data refresh account, that account must have read permissions on the external data source in order for data refresh to succeed.</span></span> <span data-ttu-id="90615-177">次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="90615-177">Choose one of the following options:</span></span>  
  
    1.  <span data-ttu-id="90615-178">PowerPivot 自動データ更新アカウントを使用してデータ更新操作を処理する場合は、 **[管理者によって構成されたデータ更新アカウントを使用します]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90615-178">Choose **Use the data refresh account configured by the administrator** to process the data refresh operation using the PowerPivot unattended data refresh account.</span></span>  
  
    2.  <span data-ttu-id="90615-179">ユーザー名とパスワードを入力する場合は、 **[次の Windows ユーザー資格情報を使用して接続する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90615-179">Choose **Connect using the following Windows user credentials** if you want to enter a user name and password.</span></span> <span data-ttu-id="90615-180">アカウント情報は、"ドメイン\ユーザー" の形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="90615-180">Enter the account information in domain\user format.</span></span>  
  
    3.  <span data-ttu-id="90615-181">使用する保存済みの資格情報を含んでいる対象アプリケーションの ID がわかっている場合は、 **[Secure Store Service で保存した資格情報を使用して接続する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="90615-181">Choose **Connect using the credentials saved in Secure Store Service** if you know the ID of a target application that contains previously stored credentials you want to use.</span></span>  
  
     <span data-ttu-id="90615-182">これらのオプションの詳細については、「[Power Pivot データ更新用の保存された資格情報の構成&#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)」および「[Power Pivot 自動データ更新アカウントの構成 &#40;PowerPivot for SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90615-182">For more information about these options, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) and [Configure the PowerPivot Unattended Data Refresh Account &#40;PowerPivot for SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md).</span></span>  
  
9. <span data-ttu-id="90615-183">データ更新で更新前のすべてのデータ ソースに対してクエリを再実行する場合は、[データ ソース] の **[すべてのデータ ソース]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="90615-183">In Data Sources, select the **All data sources** checkbox if you want data refresh to re-query all of the original data sources.</span></span>  
  
     <span data-ttu-id="90615-184">このオプションをオンにすると、PowerPivot データを提供するすべての外部データ ソースが自動的に更新に含まれます。ブックにデータを提供するデータ ソースの追加や削除に伴ってデータ ソースの一覧が変更されても、影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="90615-184">If you select this option, any external data source that provides PowerPivot data is automatically included in the refresh, even if the list of data sources changes over time as you add or remove data sources that provide data to the workbook.</span></span>  
  
     <span data-ttu-id="90615-185">更新に含めるデータ ソースを手動で選択する場合は、[データ ソース] の **[すべてのデータ ソース]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="90615-185">Clear the **All data sources** checkbox if you want to manually select which data sources to include.</span></span> <span data-ttu-id="90615-186">後で新しいデータ ソースを追加してブックを変更する場合は、スケジュールのデータ ソースの一覧を更新してください。</span><span class="sxs-lookup"><span data-stu-id="90615-186">If you later modify the workbook by adding a new data source, be sure to update the data source list in the schedule.</span></span> <span data-ttu-id="90615-187">この操作を実行しないと、新しいデータ ソースが更新操作に含まれません。</span><span class="sxs-lookup"><span data-stu-id="90615-187">Otherwise, newer data sources will not be included in the refresh operation.</span></span>  
  
     <span data-ttu-id="90615-188">選択に使用できるデータ ソースの一覧は、ブックの [PowerPivot データ更新の管理] ページを開いたときに、PowerPivot ブックから取得されます。</span><span class="sxs-lookup"><span data-stu-id="90615-188">The list of data sources that you can choose from is retrieved from the PowerPivot workbook when you open the Manage PowerPivot Data Refresh page for the workbook.</span></span>  
  
     <span data-ttu-id="90615-189">次の条件を満たすデータ ソースのみを選択します。</span><span class="sxs-lookup"><span data-stu-id="90615-189">Be sure to select only those data sources that meet the following criteria:</span></span>  
  
    -   <span data-ttu-id="90615-190">データ ソースは、データ更新時に指定の場所に存在し、使用可能になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-190">The data source must be available at the time that data refresh occurs and at the stated location.</span></span> <span data-ttu-id="90615-191">元のデータ ソースが、ブックを作成したユーザーのローカル ディスク ドライブにある場合は、そのデータ ソースをデータ更新操作から除外するか、何らかの方法でそのデータ ソースをネットワーク接続経由でアクセス可能な場所にパブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-191">If the original data source is on a local disk drive of the person who authored the workbook, you must either exclude that data source from the data refresh operation, or find a way to publish that data source to a location that is accessible through a network connection.</span></span> <span data-ttu-id="90615-192">データ ソースをネットワーク上の場所に移動する場合は、 [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] でブックを開いて、データ ソースの接続情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="90615-192">If you move a data source to a network location, be sure to open the workbook in [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] and update the data source connection information.</span></span> <span data-ttu-id="90615-193">この操作は、PowerPivot ブックに格納された接続情報を再確立するために必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-193">This is necessary to re-establish the connection information that is stored in the PowerPivot workbook.</span></span>  
  
    -   <span data-ttu-id="90615-194">データ ソースへのアクセスには、PowerPivot ブックに埋め込まれている資格情報、またはスケジュールに指定されている資格情報を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-194">The data source must be accessed using the credential information that is embedded in the PowerPivot workbook or that is specified in the schedule.</span></span> <span data-ttu-id="90615-195">埋め込みの資格情報は、PowerPivot for Excel を使用してデータをインポートするときに、PowerPivot ブックに格納されます。</span><span class="sxs-lookup"><span data-stu-id="90615-195">Embedded credential information is stored in the PowerPivot workbook when you import data using PowerPivot for Excel.</span></span> <span data-ttu-id="90615-196">通常、埋め込みの資格情報は SSPI=IntegratedSecurity または SSPI=TrustedConnection です。これは、現在のユーザーの資格情報を使用して、データ ソースに接続することを表します。</span><span class="sxs-lookup"><span data-stu-id="90615-196">Embedded credential information is often SSPI=IntegratedSecurity or SSPI=TrustedConnection, which means use the credentials of the current user to connect to the data source.</span></span> <span data-ttu-id="90615-197">データ更新スケジュールの資格情報をオーバーライドする場合は、定義済みの保存された資格情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="90615-197">If you want to override the credential information in your data refresh schedule, you can specify predefined, stored credentials.</span></span> <span data-ttu-id="90615-198">詳細については、「[PowerPivot データ更新用の保存された資格情報の構成 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90615-198">For more information, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).</span></span>  
  
    -   <span data-ttu-id="90615-199">データ更新は、指定したすべてのデータ ソースに対して成功する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-199">Data refresh must succeed for all of the data sources that you specify.</span></span> <span data-ttu-id="90615-200">成功しなかった場合、更新されたデータは破棄され、最後に保存したバージョンのブックが維持されます。</span><span class="sxs-lookup"><span data-stu-id="90615-200">Otherwise, the refreshed data is discarded, leaving you with the last saved version of the workbook.</span></span> <span data-ttu-id="90615-201">確実でないデータ ソースは除外してください。</span><span class="sxs-lookup"><span data-stu-id="90615-201">Exclude any data sources that you are not sure about.</span></span>  
  
    -   <span data-ttu-id="90615-202">ブック内の他のデータを無効にするようなデータ更新を行わないでください。</span><span class="sxs-lookup"><span data-stu-id="90615-202">Data refresh must not invalidate other data in your workbook.</span></span> <span data-ttu-id="90615-203">データのサブセットを更新するときは、時期の異なる静的データと新しいデータを集計してもブックが引き続き有効になるかどうかの判断が重要になります。</span><span class="sxs-lookup"><span data-stu-id="90615-203">When you refresh a subset of your data, it is important that you understand whether the workbook is still valid once newer data is aggregated with static data that is not from the same time period.</span></span> <span data-ttu-id="90615-204">データの依存関係を理解し、データ更新がブックにとって適切かどうかを確認するのは、ブック作成者の責任です。</span><span class="sxs-lookup"><span data-stu-id="90615-204">As a workbook author, it is up to you to know your data dependencies and ensure that data refresh is appropriate for the workbook itself.</span></span>  
  
10. <span data-ttu-id="90615-205">必要に応じて、特定のデータ ソースに個別のスケジュールを定義できます。</span><span class="sxs-lookup"><span data-stu-id="90615-205">Optionally, you can define individual schedules for specific data sources.</span></span> <span data-ttu-id="90615-206">これは、元のデータ ソースもスケジュールに基づいて更新される場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="90615-206">This is useful if you have original data sources that are themselves updated on a schedule.</span></span> <span data-ttu-id="90615-207">たとえば、毎週月曜日の 2 時に更新されるデータ マートのデータを PowerPivot データ ソースで使用している場合、そのデータ マートに対して、更新されたデータを毎週月曜日の 4 時に取得するインライン スケジュールを定義できます。</span><span class="sxs-lookup"><span data-stu-id="90615-207">For example, if a PowerPivot data source uses data from a data mart that is refreshed every Monday at 02:00 hours, you can define an inline schedule for the data mart to retrieve its refreshed data every Monday at 04:00 hours.</span></span>  
  
11. <span data-ttu-id="90615-208">**[OK]** をクリックして、スケジュールを保存します。</span><span class="sxs-lookup"><span data-stu-id="90615-208">Click **OK** to save your schedule.</span></span>  
  
##  <a name="verify-data-refresh"></a><a name="drverify"></a><span data-ttu-id="90615-209">データ更新の確認</span><span class="sxs-lookup"><span data-stu-id="90615-209">Verify Data Refresh</span></span>  
 <span data-ttu-id="90615-210">データ更新を確認する最善の方法は、データ更新をすぐに実行し、履歴ページを確認して、データ更新が正常に完了したかどうかを確認することです。</span><span class="sxs-lookup"><span data-stu-id="90615-210">The best way to verify data refresh is to execute data refresh right away and then review the history page to see whether it completed successfully.</span></span> <span data-ttu-id="90615-211">スケジュールの **[さらに、できるだけ早く更新を行います]** チェック ボックスをオンにすると、データ更新が動作することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="90615-211">Selecting the **Also refresh as soon as possible** checkbox on your schedule will provide the verification that data refresh is operational.</span></span>  
  
 <span data-ttu-id="90615-212">データ更新操作の現在と過去のレコードは、ブックの [データ更新の履歴] ページで表示できます。</span><span class="sxs-lookup"><span data-stu-id="90615-212">You can view the current and past record of data refresh operations in the Data Refresh History page for the workbook.</span></span> <span data-ttu-id="90615-213">このページは、ブックにデータ更新がスケジュールされている場合にだけ表示されます。</span><span class="sxs-lookup"><span data-stu-id="90615-213">This page only appears if data refresh has been scheduled for a workbook.</span></span> <span data-ttu-id="90615-214">データ更新スケジュールがない場合は、代わりにスケジュール定義ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90615-214">If there is no data refresh schedule, the schedule definition page appears instead.</span></span>  
  
 <span data-ttu-id="90615-215">データ更新の履歴を表示するには、投稿権限以上の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="90615-215">You must have Contribute permissions or greater to view data refresh history.</span></span>  
  
1.  <span data-ttu-id="90615-216">SharePoint サイトで、PowerPivot ブックを含んだライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="90615-216">On a SharePoint site, open the library that contains a PowerPivot workbook.</span></span>  
  
     <span data-ttu-id="90615-217">SharePoint ライブラリ内のどのブックに PowerPivot データが含まれているかを、外観で判別することはできません。</span><span class="sxs-lookup"><span data-stu-id="90615-217">There is no visual indicator that identifies which workbooks in a SharePoint library contain PowerPivot data.</span></span> <span data-ttu-id="90615-218">更新可能な PowerPivot データが含まれているブックを、あらかじめ調べておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-218">You must know in advance which workbooks contain refreshable PowerPivot data.</span></span>  
  
2.  <span data-ttu-id="90615-219">ドキュメントを選択し、右側にある下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90615-219">Select the document, and then click the down arrow that appears to the right.</span></span>  
  
3.  <span data-ttu-id="90615-220">**[PowerPivot データ更新の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90615-220">Select **Manage PowerPivot Data Refresh**.</span></span>  
  
 <span data-ttu-id="90615-221">履歴ページが開き、現在の Excel ブック内の PowerPivot データに関するすべての更新操作の完全な記録が表示されます。最新のデータ更新操作の状態も表示されます。</span><span class="sxs-lookup"><span data-stu-id="90615-221">The history page appears, showing a complete record for all refresh activity for PowerPivot data in the current Excel workbook, including the status of the most recent data refresh operation.</span></span>  
  
 <span data-ttu-id="90615-222">場合によっては、表示される実際の処理時間が、指定した時間とは異なることもあります。</span><span class="sxs-lookup"><span data-stu-id="90615-222">In some cases, you might see actual processing times that differ from the time you specified.</span></span> <span data-ttu-id="90615-223">これは、サーバーの処理負荷が高い場合に起こります。</span><span class="sxs-lookup"><span data-stu-id="90615-223">This will occur if there is a heavy processing load on the server.</span></span> <span data-ttu-id="90615-224">負荷が高い場合、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] サービス インスタンスは十分なシステム リソースが空くまで待機してから、データ更新を開始します。</span><span class="sxs-lookup"><span data-stu-id="90615-224">Under heavy load, the [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] service instance will wait until enough system resources are free before it begins a data refresh.</span></span>  
  
 <span data-ttu-id="90615-225">更新操作の終了時に、ブックがチェックインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90615-225">The workbook must be checked in when the refresh operation is finished.</span></span> <span data-ttu-id="90615-226">このときに、更新されたデータがブックに保存されます。</span><span class="sxs-lookup"><span data-stu-id="90615-226">The workbook will be saved with the refreshed data at that time.</span></span> <span data-ttu-id="90615-227">ファイルがチェックアウトされている場合、データ更新は、次回の予定時刻までスキップされます。</span><span class="sxs-lookup"><span data-stu-id="90615-227">If the file is checked out, data refresh is skipped until the next scheduled time.</span></span>  
  
 <span data-ttu-id="90615-228">予期しない状態メッセージ (更新操作の失敗や取り消しなど) が表示される場合は、問題の調査のため、権限やサーバーが使用できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="90615-228">If you see a status message that is unexpected (for example, a refresh operation failed or was cancelled), you can investigate the problem by checking permissions and server availability.</span></span>  
  
 <span data-ttu-id="90615-229">データ更新の問題の解決方法については、TechNet wiki の PowerPivot データ更新のトラブルシューティングのページをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="90615-229">Review the PowerPivot data refresh troubleshooting page on the TechNet WIKI for help on resolving data refresh problems.</span></span> <span data-ttu-id="90615-230">詳細については、「 [PowerPivot データ更新のトラブルシューティング](https://go.microsoft.com/fwlink/?LinkId=251594)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90615-230">For more information see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/?LinkId=251594).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90615-231">SharePoint 管理者は、サーバーの全体管理で PowerPivot 管理ダッシュボードにある統合データ更新レポートを表示して、データ更新の問題をトラブルシューティングできます。</span><span class="sxs-lookup"><span data-stu-id="90615-231">SharePoint administrators can help you troubleshoot data refresh problems by viewing the consolidated data refresh reports in the PowerPivot Management Dashboard in Central Administration.</span></span> <span data-ttu-id="90615-232">詳細については、「 [PowerPivot Management Dashboard and Usage Data](power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="90615-232">For more information, see [PowerPivot Management Dashboard and Usage Data](power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90615-233">参照</span><span class="sxs-lookup"><span data-stu-id="90615-233">See Also</span></span>  
 <span data-ttu-id="90615-234">[SharePoint 2010 での PowerPivot データ更新](powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="90615-234">[PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 <span data-ttu-id="90615-235">[データ更新履歴の表示 &#40;PowerPivot for SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="90615-235">[View Data Refresh History &#40;PowerPivot for SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="90615-236">PowerPivot データ更新用の保存された資格情報を構成する &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="90615-236">Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
  