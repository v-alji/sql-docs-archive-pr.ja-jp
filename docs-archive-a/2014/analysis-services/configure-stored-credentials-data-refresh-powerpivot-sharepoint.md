---
title: PowerPivot データ更新用の保存された資格情報の構成 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a1350c5d776891397401e9d3127b7849281b106
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633495"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a><span data-ttu-id="793ca-102">PowerPivot データ更新用の保存された資格情報の構成 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="793ca-102">Configure Stored Credentials for PowerPivot Data Refresh (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="793ca-103">使用する資格情報を保存するために、対象アプリケーションを Secure Store Service で作成してあれば、PowerPivot データ更新ジョブは任意の Windows ユーザー アカウントで実行できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-103">PowerPivot data refresh jobs can run under any Windows user account as long as you create a target application in Secure Store Service to store the credentials you want to use.</span></span> <span data-ttu-id="793ca-104">同様に、PowerPivot for Excel のデータを最初にインポートするときに使用するものとは異なるデータベース ログインを提供する場合は、その資格情報を Secure Store Service の対象アプリケーションにマップし、データ更新スケジュールでその対象アプリケーションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-104">Similarly, if you want to provide a database login that varies from the one used to originally import the data in PowerPivot for Excel, you can map those credentials to a Secure Store Service target application, and then specify that target application in a data refresh schedule.</span></span>  
  
 <span data-ttu-id="793ca-105">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="793ca-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="793ca-106">このトピックの手順に従うと、PowerPivot データ更新スケジュール ページで次の資格情報オプションを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="793ca-106">After you follow the instructions in this topic, you will be able to use the following credentials option in the PowerPivot data refresh schedule page:</span></span>  
  
 <span data-ttu-id="793ca-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span><span class="sxs-lookup"><span data-stu-id="793ca-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span></span>  
  
 <span data-ttu-id="793ca-108">このトピックでは、SharePoint 2010 ファーム内の PowerPivot データの更新操作に使用するユーザー名とパスワードの設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="793ca-108">This topic explains how to set up the user names and passwords that are used for PowerPivot data refresh in a SharePoint 2010 farm.</span></span> <span data-ttu-id="793ca-109">この手順を使用するには、あらかじめ、Secure Store Service を有効にし、マスター キーを生成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-109">Before you can use these steps, you must have enabled Secure Store Service and generated a master key.</span></span> <span data-ttu-id="793ca-110">詳細については、「 [SharePoint 2010 での PowerPivot データ更新](powerpivot-data-refresh-with-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-110">For more information, see [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span></span>  
  
 <span data-ttu-id="793ca-111">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="793ca-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="793ca-112">データ更新用の Windows アカウントの構成</span><span class="sxs-lookup"><span data-stu-id="793ca-112">Configure any Windows account for data refresh</span></span>](#configAny)  
  
 [<span data-ttu-id="793ca-113">外部やサードパーティのデータ ソースにアクセスするための定義済みアカウントの構成</span><span class="sxs-lookup"><span data-stu-id="793ca-113">Configure a predefined account for accessing external or third-party data sources</span></span>](#config3rd)  
  
 <span data-ttu-id="793ca-114">データ更新の構成または使用に関する問題が発生した場合は、TechNet wiki の「 [PowerPivot データ更新のトラブルシューティング](https://go.microsoft.com/fwlink/?LinkID=223279)」ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-114">If you have problems configuring or using data refresh, refer to the [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/?LinkID=223279) page on the TechNet wiki for possible solutions.</span></span>  
  
##  <a name="configure-any-windows-account-for-data-refresh"></a><a name="configAny"></a><span data-ttu-id="793ca-115">データ更新用の Windows アカウントを構成する</span><span class="sxs-lookup"><span data-stu-id="793ca-115">Configure any Windows account for data refresh</span></span>  
 <span data-ttu-id="793ca-116">SharePoint ユーザーがデータ更新スケジュールを定義するときには、データ更新の実行に使用するユーザー ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-116">When a SharePoint user defines a data refresh schedule, he or she must specify the user identity under which data refresh is performed.</span></span> <span data-ttu-id="793ca-117">オプションとしては、PowerPivot 自動データ更新アカウントを選択する方法、ユーザー自身の Windows ドメイン ユーザー アカウントを入力する方法、またはデータ更新の目的に使用できるその他の Windows ユーザー アカウントを入力する方法があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-117">Options include selecting the PowerPivot unattended data refresh account, entering his or her Windows domain user account, or entering some other Windows user account that is valid for data refresh purposes.</span></span> <span data-ttu-id="793ca-118">ここでは、最後のオプション (その他の Windows アカウントを指定する方法) の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="793ca-118">The steps in this section are for the last option: specifying some other Windows account.</span></span>  
  
 <span data-ttu-id="793ca-119">この方法は、PowerPivot 自動データ更新アカウント (SharePoint 上のすべての PowerPivot ユーザーが利用可能) の使用またはブック所有者の資格情報の使用に代わる方法が必要な場合に選択できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-119">You might choose this approach if you want an alternative to using the PowerPivot unattended data refresh account (available to all PowerPivot users on SharePoint) or the credentials of the workbook owner.</span></span> <span data-ttu-id="793ca-120">たとえば、組織レベルでのデータ更新操作の追跡および管理が容易になるように、ワークグループに応じて一連のデータ更新アカウントを利用可能にすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-120">For example, you might want to make a series of data refresh accounts available to different workgroups to help you track and manage data refresh activity at the organizational level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="793ca-121">この対象アプリケーション (および保存される資格情報) を使用するユーザーとアプリケーションは、アプリケーションのメンバーとして表示される必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-121">People and applications that use this target application (and the credentials that it stores) must be listed as members of the application.</span></span> <span data-ttu-id="793ca-122">また、対象アプリケーション、Windows アカウント、およびデータ更新スケジュールでこの対象アプリケーションを指定するユーザーのグループやユーザー アカウントを使用する、PowerPivot サービス アプリケーションの各 ID を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-122">You must add the identity of each PowerPivot service application that will use the target application, your Windows account, and the group or user accounts of people who will be specifying this target application in their data refresh schedules.</span></span> <span data-ttu-id="793ca-123">これらのアカウントは、対象アプリケーションを作成するときにすべて指定できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-123">You can specify all of these accounts when you create the target application.</span></span> <span data-ttu-id="793ca-124">このアプリケーションにアクセスする必要があるユーザー アカウントとグループ アカウントがわからない場合は、対象アプリケーションを作成した後で追加できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-124">If you do not know all of the user and group accounts that will require access to this application, you can add them later after the target application is created.</span></span>  
  
 <span data-ttu-id="793ca-125">データ更新用の保存された資格情報の構成には次の 4 つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-125">There are 4 parts to configuring stored credentials for data refresh:</span></span>  
  
-   <span data-ttu-id="793ca-126">資格情報を保存する対象アプリケーションを作成する。</span><span class="sxs-lookup"><span data-stu-id="793ca-126">Create the target application that stores the credentials.</span></span>  
  
-   <span data-ttu-id="793ca-127">アカウントに投稿権限を付与する。</span><span class="sxs-lookup"><span data-stu-id="793ca-127">Grant Contribute permissions to the account.</span></span>  
  
-   <span data-ttu-id="793ca-128">データ更新中に外部データ ソースにアクセスするための読み取り権限をアカウントに付与する。</span><span class="sxs-lookup"><span data-stu-id="793ca-128">Grant the account read permissions to access external data sources during data refresh.</span></span>  
  
-   <span data-ttu-id="793ca-129">この対象アプリケーションをデータ更新スケジュールで指定した場合にデータ更新が動作することを確認する。</span><span class="sxs-lookup"><span data-stu-id="793ca-129">Verify that data refresh works when you specify this target application in a data refresh schedule.</span></span>  
  
### <a name="step-1-create-a-target-application"></a><span data-ttu-id="793ca-130">手順 1: 対象アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="793ca-130">Step 1: Create a target application</span></span>  
  
1.  <span data-ttu-id="793ca-131">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-131">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="793ca-132">[ **Secure Store Service**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-132">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="793ca-133">[ターゲットアプリケーションの管理] で、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-133">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="793ca-134">[対象アプリケーション ID] に、テキスト文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-134">In Target application ID, type a text string.</span></span> <span data-ttu-id="793ca-135">文字列は一意であることが必要ですが、覚えやすい文字列を指定してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-135">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="793ca-136">ユーザーがこのアプリケーションに保存された資格情報を使用する場合は、データ更新スケジュール ページでこの文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-136">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="793ca-137">[表示名] に、わかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-137">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="793ca-138">この名前は表示にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="793ca-138">This name is used for display purposes only.</span></span> <span data-ttu-id="793ca-139">データ更新スケジュールで対象アプリケーションを指定する場合には使用されません。</span><span class="sxs-lookup"><span data-stu-id="793ca-139">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="793ca-140">[連絡先の電子メール] に、自分の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-140">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="793ca-141">[ターゲットアプリケーションの種類] で、[**グループ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="793ca-141">In Target Application Type, select **Group**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="793ca-142">[グループ] アカウントの種類を選択すると、資格情報へのアクセスを要求するすべてのユーザーおよびサービス アカウントを指定できるため、このアカウントの種類を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-142">Choosing a Group account type is necessary because it allows you to specify all of the user and service accounts requesting access to the credentials.</span></span> <span data-ttu-id="793ca-143">要求ごとに、PowerPivot System サービスは要求元が対象アプリケーションのメンバーかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="793ca-143">For each request, PowerPivot System Service verifies whether the requestor is a member of the target application.</span></span>  
  
8.  <span data-ttu-id="793ca-144">[対象アプリケーションのページ URL] はスキップします。</span><span class="sxs-lookup"><span data-stu-id="793ca-144">Skip Target Application Page URL.</span></span> <span data-ttu-id="793ca-145">PowerPivot データ更新では使用されません。</span><span class="sxs-lookup"><span data-stu-id="793ca-145">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="793ca-146">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-146">Click **Next**.</span></span>  
  
10. <span data-ttu-id="793ca-147">[ **Secure Store のターゲットアプリケーションの資格情報フィールドの指定**] ページで、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="793ca-147">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values.</span></span> <span data-ttu-id="793ca-148">フィールドの名前と種類は、Windows ユーザー名と Windows パスワードにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-148">Field names and types should be Windows User Name and Windows Password.</span></span>  
  
11. <span data-ttu-id="793ca-149">[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-149">Click Next.</span></span>  
  
12. <span data-ttu-id="793ca-150">[ターゲット アプリケーションの管理者] で、ターゲット アプリケーション設定に対する管理アクセス権 (たとえば、[メンバー] ボックスの一覧でアカウントを追加または削除する機能) を必要とする SharePoint ユーザーの Windows ドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="793ca-150">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to target application settings (for example, the ability to add or remove accounts from the Members list).</span></span>  
  
13. <span data-ttu-id="793ca-151">[メンバー] で、次のユーザー アカウントとグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-151">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="793ca-152">アプリケーションの作成者として、自分の Windows ユーザー アカウントを [メンバー] ボックスの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-152">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="793ca-153">スケジュールによってデータ更新が実行されるときに資格情報を取得できるように、PowerPivot サービス アプリケーションのアプリケーション プール ID を追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-153">Add the application pool identity of the PowerPivot service application so that it can retrieve the credentials when data refresh is scheduled to run.</span></span> <span data-ttu-id="793ca-154">アプリケーションプール id を表示するには、[**サービスアプリケーションの管理**] にアクセスし、名前の横にある空白部分をクリックして PowerPivot サービスアプリケーションを選択します (これにより行が選択されます)。次に、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-154">To view the application pool identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="793ca-155">このページに表示されるセキュリティ アカウントが、対象アプリケーションのメンバーとして追加するアカウントになります。</span><span class="sxs-lookup"><span data-stu-id="793ca-155">The security account that appears on this page is the account to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="793ca-156">データ更新スケジュールにこの対象アプリケーションを登録する Windows ユーザー アカウントとグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-156">Add Windows user and group accounts that will be entering this target application in data refresh schedules.</span></span>  
  
14. <span data-ttu-id="793ca-157">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-157">Click **OK**.</span></span>  
  
15. <span data-ttu-id="793ca-158">先ほど作成したターゲットアプリケーションを選択し、下矢印をクリックして、[**資格情報の設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="793ca-158">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="793ca-159">[資格情報の所有者] の資格情報の所有者の一覧は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="793ca-159">In Credential Owner, notice that the list of credential owners is read-only.</span></span> <span data-ttu-id="793ca-160">資格情報の所有権を持つアカウントは、対象アプリケーションのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="793ca-160">The accounts who have ownership over the credentials are the members of the target application.</span></span> <span data-ttu-id="793ca-161">資格情報の所有者を追加または削除するには、対象アプリケーションのメンバーの一覧でアカウントを追加または削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-161">To add or remove a credential owner, you must add or remove accounts from the target application members list.</span></span>  
  
     <span data-ttu-id="793ca-162">[Windows ユーザー名] および [Windows パスワード] に、データ更新の実行に使用する Windows ユーザー アカウントの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-162">In Windows User Name and Windows Password, type credentials of Windows user account that will be used to run data refresh.</span></span>  
  
17. <span data-ttu-id="793ca-163">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-163">Click **OK**.</span></span>  
  
###  <a name="step-2-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a><span data-ttu-id="793ca-164">手順 2: アカウントに投稿権限を付与する</span><span class="sxs-lookup"><span data-stu-id="793ca-164">Step 2: Grant Contribute permissions to the account</span></span>  
 <span data-ttu-id="793ca-165">保存された資格情報を使用する前に、使用するすべての PowerPivot ブックで、このアカウントに投稿権限を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-165">Before you can use the stored credentials, the account must be assigned Contribute permissions on any PowerPivot workbook for which it is used.</span></span> <span data-ttu-id="793ca-166">この権限レベルは、ライブラリからブックを開き、データの更新後に再度ライブラリに保存するために必要です。</span><span class="sxs-lookup"><span data-stu-id="793ca-166">This permission level is necessary to open the workbook from a library and then save it back to the library after the data is refreshed.</span></span>  
  
 <span data-ttu-id="793ca-167">権限の割り当ては、サイト コレクションの管理者が実行する手順です。</span><span class="sxs-lookup"><span data-stu-id="793ca-167">Assigning permissions is a step that is performed by the site collection administrator.</span></span> <span data-ttu-id="793ca-168">SharePoint の権限は、ルート サイト コレクションで割り当てるか、ルート サイト コレクションより下位の任意のレベル (個々のドキュメントやアイテムを含む) で割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="793ca-168">SharePoint permissions can be assigned at the root site collection or at any level below that, including on individual documents and items.</span></span> <span data-ttu-id="793ca-169">権限の設定方法は、権限をどのくらい細かく設定する必要があるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="793ca-169">How you set permissions will vary depending on how granular you need them to be.</span></span> <span data-ttu-id="793ca-170">次の手順は、権限を付与する方法の一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="793ca-170">The following steps show you one approach for granting permissions.</span></span>  
  
1.  <span data-ttu-id="793ca-171">SharePoint サイトで、[サイトの操作] の [**サイトの権限**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-171">On a SharePoint site, in Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="793ca-172">**[アクセス許可の付与]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-172">Click **Grant Permissions**.</span></span>  
  
3.  <span data-ttu-id="793ca-173">[ユーザーの選択] に、対象アプリケーションで指定した Windows ドメイン ユーザー アカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-173">In Select users, type the name of the Windows domain user account that you specified in the target application.</span></span>  
  
4.  <span data-ttu-id="793ca-174">[アクセス許可の付与] で、[**ユーザーにアクセス許可を直接付与**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="793ca-174">In Grant Permissions, select **Grant users permission directly**.</span></span>  
  
5.  <span data-ttu-id="793ca-175">[**投稿**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-175">Select **Contribute**, and then click **OK**.</span></span>  
  
###  <a name="step-3-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a><span data-ttu-id="793ca-176">手順 3: データ更新で使用される外部データソースにアクセスするための読み取り権限を付与する</span><span class="sxs-lookup"><span data-stu-id="793ca-176">Step 3: Grant read permissions to access external data sources used in data refresh</span></span>  
 <span data-ttu-id="793ca-177">データを PowerPivot ブックにインポートする場合、通常、外部データへの接続は、信頼関係接続か、(現在のユーザーの ID を使用してデータ ソースに接続する) 権限を借用した接続に基づきます。</span><span class="sxs-lookup"><span data-stu-id="793ca-177">When importing data into a PowerPivot workbook, connections to external data are often based on trusted connections or impersonated connections that use the identity of the current user to connect to the data source.</span></span> <span data-ttu-id="793ca-178">これらの種類の接続は、現在のユーザーがインポートする対象のデータに対する読み取り権限を持つ場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="793ca-178">These types of connections work only when the current user has permission to read the data that he or she is importing.</span></span>  
  
 <span data-ttu-id="793ca-179">データ更新シナリオでは、データをインポートするために使用された接続文字列が、データを更新するために再利用されます。</span><span class="sxs-lookup"><span data-stu-id="793ca-179">In a data refresh scenario, the same connection string that was used to import data is now reused to refresh the data.</span></span> <span data-ttu-id="793ca-180">接続文字列が現在のユーザーを想定している (たとえば、Integrated_Security=SSPI を含む文字列) 場合、PowerPivot System サービスは、対象アプリケーションで指定したユーザー ID を現在のユーザーとして渡します。</span><span class="sxs-lookup"><span data-stu-id="793ca-180">If the connection string assumes the current user (for example, a string that includes Integrated_Security=SSPI), then the PowerPivot System Service will pass the user identity specified in the target application as the current user.</span></span> <span data-ttu-id="793ca-181">この接続は、外部データ ソースに対する読み取り権限がアカウントに付与されている場合にのみ成功します。</span><span class="sxs-lookup"><span data-stu-id="793ca-181">This connection will only succeed if the account has read permissions on the external data source.</span></span>  
  
 <span data-ttu-id="793ca-182">このため、アカウントには、データ更新中に使用されるすべての外部データ ソースに対する読み取り専用権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-182">For this reason, you must grant the account read-only permissions on all of the external data sources that are used during data refresh.</span></span>  
  
 <span data-ttu-id="793ca-183">組織で使用しているデータ ソースの管理者であれば、ログインを作成し、必要な権限を付与することができます。</span><span class="sxs-lookup"><span data-stu-id="793ca-183">If you are an administrator of the data sources used in your organization, you can create a login and assign the necessary permissions.</span></span> <span data-ttu-id="793ca-184">管理者でない場合は、データの所有者に対してアカウント情報を連絡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-184">Otherwise, you must contact the data owners and provide the account information.</span></span> <span data-ttu-id="793ca-185">対象アプリケーションにマップされる Windows ドメイン ユーザー アカウントを必ず指定してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-185">Be sure to specify the Windows domain user account that maps to the target application.</span></span> <span data-ttu-id="793ca-186">これは、このトピックの「手順 1: ターゲットアプリケーションを作成する」で指定したアカウントです。</span><span class="sxs-lookup"><span data-stu-id="793ca-186">This is the account you specified in "Step 1: Create a target application" in this topic.</span></span>  
  
###  <a name="step-4-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a><span data-ttu-id="793ca-187">手順 4: データ更新構成ページでアカウントの可用性を確認する</span><span class="sxs-lookup"><span data-stu-id="793ca-187">Step 4: Verify account availability in data refresh configuration pages</span></span>  
  
1.  <span data-ttu-id="793ca-188">PowerPivot データが含まれているパブリッシュ済みのブックのデータ更新構成ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="793ca-188">Open a data refresh configuration page for a published workbook that contains PowerPivot data.</span></span> <span data-ttu-id="793ca-189">ページを開く方法については、「 [PowerPivot for SharePoint&#41;&#40;データ更新をスケジュールする](schedule-a-data-refresh-powerpivot-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-189">For instructions on how to open the page, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="793ca-190">[データ更新の構成] ページで [ **Secure Store Service (SSS) に保存された資格情報を使用してデータソースにログオン**します] オプションが有効になっていることを確認し、ターゲットアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-190">Verify that the **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source** option is enabled in the data refresh configuration page, and then enter the name of the target application.</span></span>  
  
3.  <span data-ttu-id="793ca-191">[**直ちに更新**する] チェックボックスをオンにし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-191">Select the **Also refresh as soon as possible** checkbox, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="793ca-192">ブックが格納されているライブラリで、ブックを選択し、右側に表示される下矢印をクリックして、[ **PowerPivot データ更新の管理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="793ca-192">In the library that contains the workbook, select the workbook, click the down arrow that appears to right, and then select **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="793ca-193">データ更新ジョブが返すデータ量が多い場合は、数分待つことが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="793ca-193">You might need to wait several minutes if the data refresh job is returning a large amount of data.</span></span>  
  
 <span data-ttu-id="793ca-194">エラーが発生した場合は、[データ更新の履歴] ページで [**スケジュールの構成**] をクリックして、別の資格情報を試すことができます。</span><span class="sxs-lookup"><span data-stu-id="793ca-194">If an error occurs, you can click **Configure schedule** in the data refresh history page to try different credentials.</span></span> <span data-ttu-id="793ca-195">元のブックのデータ ソース接続情報を調べて、データ更新時に使用される接続文字列を表示することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="793ca-195">You might also need to inspect the data source connection information in the original workbook to view the connection string that is used during data refresh.</span></span> <span data-ttu-id="793ca-196">接続文字列は、問題のトラブルシューティングに使用できるサーバーの場所とデータベースに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="793ca-196">The connection string will provide information about the server location and database that you can use to troubleshoot the problem.</span></span>  
  
 <span data-ttu-id="793ca-197">トラブルシューティングの詳細については、TechNet Wiki の「 [PowerPivot データ更新のトラブルシューティング](https://go.microsoft.com/fwlink/p/?LinkID=223279)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-197">For more information about troubleshooting, see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/p/?LinkID=223279) on the TechNet Wiki.</span></span>  
  
##  <a name="configure-a-predefined-account-for-accessing-external-or-third-party-data-sources"></a><a name="config3rd"></a><span data-ttu-id="793ca-198">外部またはサードパーティのデータソースにアクセスするための定義済みアカウントの構成</span><span class="sxs-lookup"><span data-stu-id="793ca-198">Configure a predefined account for accessing external or third-party data sources</span></span>  
 <span data-ttu-id="793ca-199">多くの場合、データベース サーバーには独自の認証方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="793ca-199">Database servers often come with their own authentication methods.</span></span> <span data-ttu-id="793ca-200">データ更新時に外部データ ソースへアクセスするためにデータベース資格情報を必要とする PowerPivot ブックがある場合は、資格情報の対象アプリケーション ID を作成し、[データ更新のスケジュール] ページの [データ ソース] セクションで、対象アプリケーションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-200">If you have a PowerPivot workbook that requires database credentials to access an external data source during data refresh, you can create a target application ID for the credentials, and then specify the target application in the Data Sources section of the schedule data refresh page.</span></span>  
  
 <span data-ttu-id="793ca-201">この手順は、PowerPivot ブックに既に埋め込まれているデータベース資格情報をオーバーライドするオプションをユーザーに提供する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="793ca-201">This step is only necessary if you want to provide users with an option of overriding the database credentials that are already embedded in the PowerPivot workbook.</span></span>  
  
 <span data-ttu-id="793ca-202">この手順は、接続文字列にユーザー名とパスワードが既に含まれている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="793ca-202">This step only works if the connection string already includes a user name and password.</span></span> <span data-ttu-id="793ca-203">接続文字列に資格情報があることは比較的少ないため、このオプションを利用する機能はある程度制限されています。</span><span class="sxs-lookup"><span data-stu-id="793ca-203">Note that having credentials in the connection string is relatively uncommon, so your ability to make use of this option is somewhat limited.</span></span> <span data-ttu-id="793ca-204">データベース認証を使用してデータ ソースに接続する場合は、接続文字列にユーザー ID とパスワードだけを使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="793ca-204">In most cases, you will only have a user ID and password in the connection string if you are using database authentication to connect to the data source.</span></span> <span data-ttu-id="793ca-205">接続文字列にユーザー ID とパスワードが含まれているかどうかを確認する方法の詳細については、「 [SharePoint 2010 での PowerPivot データ更新](powerpivot-data-refresh-with-sharepoint-2010.md)」の「スケジュールを作成し、外部データにアクセスするためのアクセス許可を付与する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-205">For more information about how to check the connection string to see if it includes a User ID and password, see the "Grant permissions to create schedules and access external data" section in [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).</span></span>  
  
1.  <span data-ttu-id="793ca-206">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-206">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="793ca-207">[ **Secure Store Service**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-207">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="793ca-208">[ターゲットアプリケーションの管理] で、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-208">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="793ca-209">[対象アプリケーション ID] に、テキスト文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-209">In Target application ID, type a text string.</span></span> <span data-ttu-id="793ca-210">文字列は一意であることが必要ですが、覚えやすい文字列を指定してください。</span><span class="sxs-lookup"><span data-stu-id="793ca-210">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="793ca-211">ユーザーがこのアプリケーションに保存された資格情報を使用する場合は、データ更新スケジュール ページでこの文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-211">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="793ca-212">[表示名] に、わかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-212">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="793ca-213">この名前は表示にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="793ca-213">This name is used for display purposes only.</span></span> <span data-ttu-id="793ca-214">データ更新スケジュールで対象アプリケーションを指定する場合には使用されません。</span><span class="sxs-lookup"><span data-stu-id="793ca-214">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="793ca-215">[連絡先の電子メール] に、自分の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-215">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="793ca-216">[ターゲットアプリケーションの種類] で、[**グループ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="793ca-216">In Target Application Type, select **Group**.</span></span>  
  
8.  <span data-ttu-id="793ca-217">[対象アプリケーションのページ URL] はスキップします。</span><span class="sxs-lookup"><span data-stu-id="793ca-217">Skip Target Application Page URL.</span></span> <span data-ttu-id="793ca-218">PowerPivot データ更新では使用されません。</span><span class="sxs-lookup"><span data-stu-id="793ca-218">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="793ca-219">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-219">Click **Next**.</span></span>  
  
10. <span data-ttu-id="793ca-220">[ **Secure Store のターゲットアプリケーションの資格情報フィールドの指定**] ページで、データソースが Windows 認証を使用している場合に限り、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="793ca-220">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values only if the data source uses Windows authentication.</span></span> <span data-ttu-id="793ca-221">それ以外の場合は、データ ソースに対して有効なフィールドの種類を選択し、その種類に合わせてフィールド名を編集します。</span><span class="sxs-lookup"><span data-stu-id="793ca-221">Otherwise, choose the field types that are valid for your data source, and then edit the field names to match the type.</span></span>  
  
     <span data-ttu-id="793ca-222">たとえば、フィールド名に SQL Server ユーザー名と SQL Server ユーザー パスワードを指定し、フィールドの種類に [ユーザー名] と [パスワード] を選択できます。</span><span class="sxs-lookup"><span data-stu-id="793ca-222">For example, you might specify SQL Server User Name and SQL Server User Password for field names, and then choose User Name and Password for field types.</span></span>  
  
11. <span data-ttu-id="793ca-223">[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-223">Click Next.</span></span>  
  
12. <span data-ttu-id="793ca-224">[対象アプリケーションの管理者] で、アプリケーション設定に対する管理アクセス権を必要とする SharePoint ユーザーの Windows ドメイン ユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="793ca-224">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to the application settings.</span></span>  
  
13. <span data-ttu-id="793ca-225">[メンバー] で、次のユーザー アカウントとグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-225">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="793ca-226">アプリケーションの作成者として、自分の Windows ユーザー アカウントを [メンバー] ボックスの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-226">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="793ca-227">保存した資格情報にアクセスするために対象アプリケーションを使用する各 PowerPivot サービス アプリケーションのアプリケーション プール ID を追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-227">Add the application pool identity of each PowerPivot service application that will be using the target application to access its stored credentials.</span></span> <span data-ttu-id="793ca-228">Id を表示するには、[**サービスアプリケーションの管理**] にアクセスし、名前の横にある空白部分をクリックして PowerPivot サービスアプリケーションを選択し (これにより行が選択されます)、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-228">To view the identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="793ca-229">このページに表示されるセキュリティアカウントは、対象アプリケーションのメンバーとして追加するアカウントです。</span><span class="sxs-lookup"><span data-stu-id="793ca-229">The security account that appears on this page is the account that you want to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="793ca-230">データ更新スケジュール ページのデータ ソース セクションにこの対象アプリケーションを登録する Windows ユーザー アカウントとグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="793ca-230">Add Windows user and group accounts that will be entering this target application in the data sources section of a data refresh schedule page.</span></span>  
  
14. <span data-ttu-id="793ca-231">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-231">Click **OK**.</span></span>  
  
15. <span data-ttu-id="793ca-232">先ほど作成したターゲットアプリケーションを選択し、下矢印をクリックして、[**資格情報の設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="793ca-232">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="793ca-233">データ ソースへの接続に使用される資格情報 (たとえば、SQL Server ログインのユーザー名とパスワード) を入力します。</span><span class="sxs-lookup"><span data-stu-id="793ca-233">Enter the credentials that will be used to connect to the data source (for example, the user name and password of a SQL Server login).</span></span>  
  
17. <span data-ttu-id="793ca-234">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="793ca-234">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793ca-235">参照</span><span class="sxs-lookup"><span data-stu-id="793ca-235">See Also</span></span>  
 <span data-ttu-id="793ca-236">[データ更新 &#40;PowerPivot for SharePoint をスケジュールする&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="793ca-236">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="793ca-237">SharePoint 2010 での PowerPivot データ更新</span><span class="sxs-lookup"><span data-stu-id="793ca-237">PowerPivot Data Refresh with SharePoint 2010</span></span>](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
