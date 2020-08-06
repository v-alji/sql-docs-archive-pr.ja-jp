---
title: 'レッスン 3 : データ ドリブン サブスクリプションの定義 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1bbc25bdd08b369180e31378a6d25a595badbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742901"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a><span data-ttu-id="eb9f9-102">レッスン 3: データ ドリブン サブスクリプションの定義</span><span class="sxs-lookup"><span data-stu-id="eb9f9-102">Lesson 3: Defining a Data-Driven Subscription</span></span>
  <span data-ttu-id="eb9f9-103">このレッスンでは、データ ドリブン サブスクリプションを使用し、サブスクリプション データ ソースへの接続、サブスクリプション データを取得するクエリの作成、および結果セットとレポート、配信オプションのマッピングを行います。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-103">In this lesson, you use the data-driven subscription pages to connect to a subscription data source, build a query that retrieves subscription data, and map the result set to report and delivery options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb9f9-104">開始する前に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-104">Before you start, verify that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running.</span></span> <span data-ttu-id="eb9f9-105">実行されていない場合は、サブスクリプションを保存できません。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-105">If it is not running, you cannot save the subscription.</span></span>  
  
 <span data-ttu-id="eb9f9-106">このレッスンを行うには、レッスン 1 とレッスン 2 を完了していることと、レポート データ ソースに、保存された資格情報が使用されていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-106">This lesson assumes you completed Lesson 1 and Lesson 2 and that the report data source uses stored credentials.</span></span>  <span data-ttu-id="eb9f9-107">詳細については、「 [レッスン 2: レポート データ ソースのプロパティの変更](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-107">For more information, see [Lesson 2: Modifying the Report Data Source Properties](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)</span></span>  
  
 <span data-ttu-id="eb9f9-108">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="eb9f9-108">In this topic:</span></span>  
  
-   [<span data-ttu-id="eb9f9-109">データドリブンサブスクリプションウィザードの開始</span><span class="sxs-lookup"><span data-stu-id="eb9f9-109">Start the Data-Driven Subscription Wizard</span></span>](#bkmk_startwizard)  
  
-   [<span data-ttu-id="eb9f9-110">ステップ 1 - 説明の定義</span><span class="sxs-lookup"><span data-stu-id="eb9f9-110">Step 1 - Define a description</span></span>](#bkmk_definesubscription)  
  
-   [<span data-ttu-id="eb9f9-111">ステップ 2 - サブスクライバー データ ソースへの接続の定義</span><span class="sxs-lookup"><span data-stu-id="eb9f9-111">Step 2 - Define a Connection to the Subscriber Data Source</span></span>](#bkmk_defineconnectiontosubscriber)  
  
-   [<span data-ttu-id="eb9f9-112">ステップ 3 - サブスクライバー データを取得するためのクエリの定義</span><span class="sxs-lookup"><span data-stu-id="eb9f9-112">Step 3 - Define a Query to Retrieve Subscriber data</span></span>](#bkmk_definequery)  
  
-   [<span data-ttu-id="eb9f9-113">ステップ 4 - 配信オプションの設定</span><span class="sxs-lookup"><span data-stu-id="eb9f9-113">Step 4 - Set Delivery Options</span></span>](#bkmk_set_deliveryoptions)  
  
-   [<span data-ttu-id="eb9f9-114">ステップ 5 - レポート出力を変化させるパラメーター値の構成</span><span class="sxs-lookup"><span data-stu-id="eb9f9-114">Step 5 - Configure a Parameter Value to Very Report Output</span></span>](#bkmk_configure_parameter)  
  
-   [<span data-ttu-id="eb9f9-115">ステップ 6 - サブスクリプションのスケジュールの設定</span><span class="sxs-lookup"><span data-stu-id="eb9f9-115">Step 6 - To Schedule a Subscription</span></span>](#bkmk_schedule_subscription)  
  
##  <a name="start-the-data-driven-subscription-wizard"></a><a name="bkmk_startwizard"></a><span data-ttu-id="eb9f9-116">データドリブンサブスクリプションウィザードの開始</span><span class="sxs-lookup"><span data-stu-id="eb9f9-116">Start the Data-Driven Subscription Wizard</span></span>  
  
1.  <span data-ttu-id="eb9f9-117">レポート マネージャーで **[ホーム]** をクリックして **Sales Orders** レポートのあるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-117">In Report Manager, click **Home**, and navigate to the folder containing the **Sales Orders** report.</span></span>  
  
2.  <span data-ttu-id="eb9f9-118">レポートのショートカット メニューで、 **[管理]** をクリックし、 **[サブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-118">In the context menu of the report, click **Manage**, and then click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="eb9f9-119">[**新しいデータドリブンサブスクリプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-119">Click **New Data-driven Subscription**.</span></span> <span data-ttu-id="eb9f9-120">このボタンが表示されない場合は、コンテンツ マネージャーの権限がありません。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-120">If you do not see this button, you do not have Content Manager permissions.</span></span>  
  
##  <a name="step-1---define-a-description"></a><a name="bkmk_definesubscription"></a><span data-ttu-id="eb9f9-121">手順 1-説明を定義する</span><span class="sxs-lookup"><span data-stu-id="eb9f9-121">Step 1 - Define a description</span></span>  
  
1.  <span data-ttu-id="eb9f9-122">説明に「 **Sales Order delivery** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-122">Type **Sales Order delivery** in description.</span></span>  
  
2.  <span data-ttu-id="eb9f9-123">**[受信者への通知方法を指定します]** で **[Windows ファイル共有]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-123">Select **Windows FileShare** for **Specify how recipients are notified**.</span></span>  
  
3.  <span data-ttu-id="eb9f9-124">**[このサブスクリプションのみを対象とします]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-124">Select **Specify for this subscription only**, and then click **Next**.</span></span>  
  
##  <a name="step-2---define-a-connection-to-the-subscriber-data-source"></a><a name="bkmk_defineconnectiontosubscriber"></a><span data-ttu-id="eb9f9-125">手順 2-サブスクライバーデータソースへの接続を定義する</span><span class="sxs-lookup"><span data-stu-id="eb9f9-125">Step 2 - Define a Connection to the Subscriber Data Source</span></span>  
  
1.  <span data-ttu-id="eb9f9-126">データ ソースの種類として **[Microsoft SQL Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-126">Select **Microsoft SQL Server** as the data source type.</span></span>  
  
2.  <span data-ttu-id="eb9f9-127">[接続文字列] に、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-127">In Connection string, type the following connection string:</span></span>  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb9f9-128"> サブスクライバーはレッスン 1 で作成したデータベースです。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-128">Subscribers is the database you created in lesson 1.</span></span>  
  
3.  <span data-ttu-id="eb9f9-129">**[レポート サーバーに保存され、セキュリティで保護された資格情報]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-129">Click **Credentials stored securely in the report server**.</span></span>  
  
4.  <span data-ttu-id="eb9f9-130">**[ユーザー名]** と **[パスワード]** に、ドメイン ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-130">In **User Name** and **Password**, type your domain user name and password.</span></span> <span data-ttu-id="eb9f9-131">**[ユーザー名]** には、ドメインとユーザー アカウントの両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-131">Include both the domain and user account when specifying **User Name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb9f9-132">サブスクライバー データ ソースへの接続に使用する資格情報は、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]に返されません。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-132">Credentials used to connect to a subscriber data source are not passed back to [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="eb9f9-133">後でサブスクリプションを変更する場合は、データ ソースへの接続に使用するパスワードをこのページで再入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-133">If you modify the subscription later, you must retype the password used to connect to the data source.</span></span>  
  
5.  <span data-ttu-id="eb9f9-134">**[データ ソースへの接続時に Windows 資格情報として使用する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-134">Select **Use as windows credentials when connecting to the data source**, and then click **Next**.</span></span>  
  
##  <a name="step-3---define-a-query-to-retrieve-subscriber-data"></a><a name="bkmk_definequery"></a><span data-ttu-id="eb9f9-135">手順 3-サブスクライバーデータを取得するクエリの定義</span><span class="sxs-lookup"><span data-stu-id="eb9f9-135">Step 3 - Define a Query to Retrieve Subscriber data</span></span>  
  
1.  <span data-ttu-id="eb9f9-136">クエリ ボックスに次のクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-136">In the query box, type the following query:</span></span>  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  <span data-ttu-id="eb9f9-137">30 秒のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-137">Specify a time-out of 30 seconds.</span></span>  
  
3.  <span data-ttu-id="eb9f9-138">**[検証]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-138">Click **Validate**, and then click **Next**.</span></span>  
  
##  <a name="step-4---set-delivery-options"></a><a name="bkmk_set_deliveryoptions"></a><span data-ttu-id="eb9f9-139">手順 4-配信オプションを設定する</span><span class="sxs-lookup"><span data-stu-id="eb9f9-139">Step 4 - Set Delivery Options</span></span>  
  
1.  <span data-ttu-id="eb9f9-140">**[ファイル名]** で、 **[データベースから値を取得]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-140">For **File name**, select **Get the value from the database**.</span></span> <span data-ttu-id="eb9f9-141">**Order**フィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-141">Select the field **Order**.</span></span>  
  
2.  <span data-ttu-id="eb9f9-142">**[パス]** で、 **[静的な値を指定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-142">For **Path**, select **Specify a static value**.</span></span> <span data-ttu-id="eb9f9-143">[値の設定] に、書き込み権限のあるパブリック ファイル共有の名前を入力します (例: `\\mycomputer\public\myreports`)。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-143">In Setting Value, type the name of a public file share for which you have write permissions (for example, `\\mycomputer\public\myreports`).</span></span>  
  
3.  <span data-ttu-id="eb9f9-144">**[表示形式]** で、 **[データベースから値を取得]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-144">For **Render Format**, select **Get the value from the database**.</span></span> <span data-ttu-id="eb9f9-145">[**形式**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-145">Select **Format**.</span></span>  
  
4.  <span data-ttu-id="eb9f9-146">**[書き込みモード]** で、 **[静的な値を指定]** をクリックし、 **[自動増分]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-146">For **Write mode**, select **Specify a static value** and select **AutoIncrement**.</span></span>  
  
5.  <span data-ttu-id="eb9f9-147">**[ファイル拡張子]** で、 **[静的な値を指定]** を選択し、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-147">For **File Extension**, select **Specify a static value** and select **True**.</span></span>  
  
6.  <span data-ttu-id="eb9f9-148">**[ユーザー名]** で、 **[静的な値を指定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-148">For **User name**, select **Specify a static value**.</span></span> <span data-ttu-id="eb9f9-149">ドメイン ユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-149">Type your domain user account.</span></span> <span data-ttu-id="eb9f9-150">`<domain>\<account>`の形式で入力してください。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-150">Enter it in this format: `<domain>\<account>`.</span></span> <span data-ttu-id="eb9f9-151">ユーザー アカウントには、前の手順で構成したパスに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-151">The user account needs to have permissions to the path you configured in the previous steps.</span></span>  
  
7.  <span data-ttu-id="eb9f9-152">**[パスワード]** で、 **[静的な値を指定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-152">For **Password**, select **Specify a static value**.</span></span> <span data-ttu-id="eb9f9-153">パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-153">Type your password.</span></span> <span data-ttu-id="eb9f9-154">パスワードは正確に入力してください。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-154">Be sure that you type the password carefully.</span></span> <span data-ttu-id="eb9f9-155">このウィザードでは、パスワードは検証されません。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-155">The wizard does not validate the password.</span></span>  
  
8.  <span data-ttu-id="eb9f9-156">[**次へ] をクリックします。**</span><span class="sxs-lookup"><span data-stu-id="eb9f9-156">Click **Next.**</span></span>  
  
##  <a name="step-5---configure-a-parameter-value-to-very-report-output"></a><a name="bkmk_configure_parameter"></a><span data-ttu-id="eb9f9-157">手順 5-レポート出力を非常に大きくするようにパラメーター値を構成する</span><span class="sxs-lookup"><span data-stu-id="eb9f9-157">Step 5 - Configure a Parameter Value to Very Report Output</span></span>  
  
1.  <span data-ttu-id="eb9f9-158">**[OrderNumber]** には、 **[データベースから値を取得]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-158">For **OrderNumber**, select **Get the value from the database**.</span></span> <span data-ttu-id="eb9f9-159">[値] で、 **[Order]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-159">In Value, select **Order**.</span></span> <span data-ttu-id="eb9f9-160">[**次へ] をクリックします。**</span><span class="sxs-lookup"><span data-stu-id="eb9f9-160">Click **Next.**</span></span>  
  
##  <a name="step-6---to-schedule-a-subscription"></a><a name="bkmk_schedule_subscription"></a><span data-ttu-id="eb9f9-161">手順 6-サブスクリプションのスケジュールを設定する</span><span class="sxs-lookup"><span data-stu-id="eb9f9-161">Step 6 - To Schedule a Subscription</span></span>  
  
1.  <span data-ttu-id="eb9f9-162">**[このサブスクリプション用に作成されたスケジュールで実行]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-162">Click **On a schedule created for this subscription**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="eb9f9-163">**[スケジュールの詳細]** で、 **[一度だけ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-163">In **Schedule Details**, click **Once**.</span></span>  
  
3.  <span data-ttu-id="eb9f9-164">開始時刻として、現在の時刻から数分後を指定します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-164">Specify a start time that is a few minutes ahead of the current time.</span></span>  
  
4.  <span data-ttu-id="eb9f9-165">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-165">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eb9f9-166">次の手順</span><span class="sxs-lookup"><span data-stu-id="eb9f9-166">Next Steps</span></span>  
 <span data-ttu-id="eb9f9-167">サブスクリプションを実行すると、 *Subscribers* データ ソースの注文ごとに 1 つずつ、4 つのレポート ファイルが、指定したファイル共有に配信されます。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-167">When the subscription runs, four report files will be delivered to the file share you specified, one for each order in the *Subscribers* data source.</span></span> <span data-ttu-id="eb9f9-168">各配信では、データ (注文固有のデータ)、表示形式、ファイル形式がそれぞれ異なっています。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-168">Each delivery should be unique in terms of data (the data should be order-specific), rendering format, and file format.</span></span> <span data-ttu-id="eb9f9-169">各レポートを共有フォルダーから開き、定義したサブスクリプション オプションに基づいて各バージョンがカスタマイズされているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-169">You can open each report from the shared folder to verify that each version is customized based on the subscription options you defined.</span></span>  
  
 <span data-ttu-id="eb9f9-170">![サブスクリプションによって作成されたファイルの一覧](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "サブスクリプションによって作成されたファイルの一覧")</span><span class="sxs-lookup"><span data-stu-id="eb9f9-170">![List of files created by the subscription](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "List of files created by the subscription")</span></span>  
  
 <span data-ttu-id="eb9f9-171">レポート マネージャーのサブスクリプション ページには、サブスクリプションの **[最終実行]** 日付と **[状態]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-171">The subscription page in Report Manager will contain the **Last Run** date and **Status** of the subscription.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb9f9-172">サブスクリプションを実行した後、ページを更新して更新後の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-172">Refresh the page after the subscription runs to see the updated information.</span></span>  
  
 <span data-ttu-id="eb9f9-173">![レポート マネージャーに表示されるサブスクリプションの結果](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "レポート マネージャーに表示されるサブスクリプションの結果")</span><span class="sxs-lookup"><span data-stu-id="eb9f9-173">![Subscription results in Report Manager](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Subscription results in Report Manager")</span></span>  
  
 <span data-ttu-id="eb9f9-174">これで、「データ ドリブン サブスクリプションの定義」のチュートリアルは終了します。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-174">This step concludes the tutorial "Defining a Data-Driven Subscription".</span></span> <span data-ttu-id="eb9f9-175">その他のチュートリアルの詳細につい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ては、 [Reporting Services チュートリアル &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb9f9-175">To learn more about other [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9f9-176">参照</span><span class="sxs-lookup"><span data-stu-id="eb9f9-176">See Also</span></span>  
 <span data-ttu-id="eb9f9-177">[データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="eb9f9-177">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="eb9f9-178">[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="eb9f9-178">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="eb9f9-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="eb9f9-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="eb9f9-180">[データドリブンサブスクリプションの作成、変更、および削除](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="eb9f9-180">[Create, Modify, and Delete a Data-Driven Subscription](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="eb9f9-181">サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;</span><span class="sxs-lookup"><span data-stu-id="eb9f9-181">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
