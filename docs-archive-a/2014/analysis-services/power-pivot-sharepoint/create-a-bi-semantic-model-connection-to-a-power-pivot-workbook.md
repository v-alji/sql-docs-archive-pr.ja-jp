---
title: PowerPivot ブックへの BI セマンティックモデル接続を作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e3f97f-18a8-42b6-9030-b4f818afc3b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ea4ddcc38328acc6ff8cfb5387b13056b689a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643541"
---
# <a name="create-a-bi-semantic-model-connection-to-a-powerpivot-workbook"></a><span data-ttu-id="fd0e5-102">PowerPivot ブックへの BI セマンティック モデル接続の作成</span><span class="sxs-lookup"><span data-stu-id="fd0e5-102">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>
  <span data-ttu-id="fd0e5-103">このトピックでは、同一ファーム内の PowerPivot ブックにリダイレクトする BI セマンティック モデル接続を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-103">Use the information in this topic to set up a BI semantic model connection that redirects to a PowerPivot workbook in the same farm.</span></span>  
  
 <span data-ttu-id="fd0e5-104">BI セマンティック モデル接続を作成して SharePoint 権限を構成したら、その接続を Excel または [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートのデータ ソースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-104">After you create a BI semantic model connection and configure SharePoint permissions, you can use it as a data source for Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span>  
  
 <span data-ttu-id="fd0e5-105">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-105">This topic includes the following sections.</span></span> <span data-ttu-id="fd0e5-106">各タスクは、所定の順序で実行してください。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-106">Perform each task in the order given.</span></span>  
  
 [<span data-ttu-id="fd0e5-107">前提条件の確認</span><span class="sxs-lookup"><span data-stu-id="fd0e5-107">Review Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="fd0e5-108">接続を作成する</span><span class="sxs-lookup"><span data-stu-id="fd0e5-108">Create a Connection</span></span>](#bkmk_create)  
  
 [<span data-ttu-id="fd0e5-109">BI セマンティック モデル接続への SharePoint 権限の構成</span><span class="sxs-lookup"><span data-stu-id="fd0e5-109">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>](#bkmk_permissions)  
  
 [<span data-ttu-id="fd0e5-110">ブックへの SharePoint 権限の構成</span><span class="sxs-lookup"><span data-stu-id="fd0e5-110">Configure SharePoint Permissions on the Workbook</span></span>](#bkmk_userdb)  
  
 [<span data-ttu-id="fd0e5-111">次の手順</span><span class="sxs-lookup"><span data-stu-id="fd0e5-111">Next Steps</span></span>](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="fd0e5-112">前提条件の確認</span><span class="sxs-lookup"><span data-stu-id="fd0e5-112">Review Prerequisites</span></span>  
 <span data-ttu-id="fd0e5-113">BI セマンティック モデル接続ファイルを作成するには、投稿権限以上の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-113">You must have Contribute permissions or above to create a BI semantic model connection file.</span></span>  
  
 <span data-ttu-id="fd0e5-114">BI セマンティック モデル接続のコンテンツ タイプをサポートしているライブラリが必要です。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-114">You must have a library that supports the BI semantic model connection content type.</span></span> <span data-ttu-id="fd0e5-115">詳細については、「 [BI セマンティックモデル接続のコンテンツタイプをライブラリ &#40;PowerPivot for SharePoint&#41;に追加](add-bi-semantic-model-connection-content-type-to-library.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-115">For more information, see [Add a BI Semantic Model Connection Content Type to a Library &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).</span></span>  
  
 <span data-ttu-id="fd0e5-116">BI セマンティックモデル接続を設定する PowerPivot ブックの URL (documents/myworkbook.xlsx など) を把握している必要があり http://adventure-works/shared ます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-116">You must know the URL of the PowerPivot workbook for which you are setting up a BI semantic model connection (for example, http://adventure-works/shared documents/myworkbook.xlsx).</span></span> <span data-ttu-id="fd0e5-117">ブックは、同一ファーム内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-117">The workbook must be in the same farm.</span></span>  
  
 <span data-ttu-id="fd0e5-118">接続シーケンスに参加しているすべてのコンピューターとユーザーは、同じドメインまたは信頼されたドメイン (双方向の信頼関係) に属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-118">All computers and users that participate in the connection sequence must be in the same domain or trusted domain (two-way trust).</span></span>  
  
##  <a name="create-a-connection"></a><a name="bkmk_create"></a><span data-ttu-id="fd0e5-119">接続を作成する</span><span class="sxs-lookup"><span data-stu-id="fd0e5-119">Create a Connection</span></span>  
  
1.  <span data-ttu-id="fd0e5-120">BI セマンティック モデル接続の格納先となるライブラリで、SharePoint リボンの **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-120">In the library that will contain the BI semantic model connection, click **Documents** on the SharePoint ribbon.</span></span> <span data-ttu-id="fd0e5-121">[新しいドキュメント] の下矢印をクリックし、 **[BISM 接続ファイル]** を選択して、[新しい BI セマンティック モデル接続] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-121">Click the down arrow on New Document, and select **BISM Connection File** to open the New BI Semantic Model Connection page.</span></span>  
  
     <span data-ttu-id="fd0e5-122">![SharePoint ライブラリの [新しいドキュメント] サブメニュー](../media/ssas-bismconnection-new.gif "SharePoint ライブラリの [新しいドキュメント] サブメニュー")</span><span class="sxs-lookup"><span data-stu-id="fd0e5-122">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
2.  <span data-ttu-id="fd0e5-123">**サーバー**プロパティを PowerPivot ブックの SharePoint URL ( \*\* http://mysharepoint/shared documents/myWorkbook.xlsx\*\*など) に設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-123">Set the **Server** property to the SharePoint URL of the PowerPivot workbook (for example, **http://mysharepoint/shared documents/myWorkbook.xlsx**.</span></span> <span data-ttu-id="fd0e5-124">PowerPivot for SharePoint の配置では、ファーム内の任意のサーバーにデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-124">In a PowerPivot for SharePoint deployment, data can be loaded on any server in the farm.</span></span> <span data-ttu-id="fd0e5-125">このため、PowerPivot データへのデータ ソース接続では、ブックへのパスだけを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-125">For this reason, data source connections to PowerPivot data specify just the path to the workbook.</span></span> <span data-ttu-id="fd0e5-126">PowerPivot System サービスによって、データを読み込むサーバーが決定されます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-126">The PowerPivot System Service determines which server loads the data.</span></span>  
  
     <span data-ttu-id="fd0e5-127">**データベース**プロパティは使用しないでください。PowerPivot ブックの場所を指定するときには使用されません。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-127">Do not use the **Database** property; it is not used when specifying the location of a PowerPivot workbook.</span></span>  
  
     <span data-ttu-id="fd0e5-128">ページは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-128">Your page should look similar to the following illustration.</span></span>  
  
     <span data-ttu-id="fd0e5-129">![ブックへの URL を示す BISM 接続ページ](../media/ssas-bismconnection-ppvtds.gif "ブックへの URL を示す BISM 接続ページ")</span><span class="sxs-lookup"><span data-stu-id="fd0e5-129">![BISM connection page showing URL to workbook](../media/ssas-bismconnection-ppvtds.gif "BISM connection page showing URL to workbook")</span></span>  
  
     <span data-ttu-id="fd0e5-130">ブックに対する SharePoint 権限を持っている場合は、必要に応じて、その場所が有効であるかどうかを確認するための追加の検証手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-130">Optionally, if you have SharePoint permissions to the workbook, an extra validation step is performed, ensuring that the location is valid.</span></span> <span data-ttu-id="fd0e5-131">データへのアクセス権限がない場合は、検証の応答なしで BI セマンティック モデル接続を保存するオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-131">If you do not have permission to access the data, you are given the option of saving the BI semantic model connection without the validation response.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a><span data-ttu-id="fd0e5-132">BI セマンティックモデル接続に対する SharePoint 権限の構成</span><span class="sxs-lookup"><span data-stu-id="fd0e5-132">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>  
 <span data-ttu-id="fd0e5-133">BI セマンティック モデル接続を Excel ブックまたは Reporting Services レポートのデータ ソースとして使用するには、SharePoint ライブラリ内の BI セマンティック モデル接続アイテムに対する **読み取り** 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-133">Ability to use a BI semantic model connection as a data source for an Excel workbook or Reporting Services report requires **Read** permissions on the BI semantic model connection item in a SharePoint library.</span></span> <span data-ttu-id="fd0e5-134">読み取り権限レベルには、BI セマンティック モデル接続情報を Excel デスクトップ アプリケーションにダウンロードできるようにする **"アイテムを開く"** 権限が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-134">The Read permission level includes the **Open Items** permission that enables downloading BI semantic model connection information to an Excel desktop application.</span></span>  
  
 <span data-ttu-id="fd0e5-135">SharePoint で権限を付与するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-135">There are several ways to grant permissions in SharePoint.</span></span> <span data-ttu-id="fd0e5-136">次の手順では、 **読み取り** 権限レベルを持つ、 **BISM ユーザー** という名前の新しいグループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-136">The following instructions explain how to create a new group called **BISM Users** that have the **Read** permission level.</span></span>  
  
 <span data-ttu-id="fd0e5-137">権限を変更するには、サイト所有者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-137">You must be a site owner to change permissions.</span></span>  
  
1.  <span data-ttu-id="fd0e5-138">[サイトの操作] の **[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-138">In Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="fd0e5-139">**[グループの作成]** をクリックして、新しいグループの名前を「 **BISM ユーザー**」と指定します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-139">Click **Create Group** and name the new group **BISM Users**.</span></span>  
  
3.  <span data-ttu-id="fd0e5-140">**[読み取り]** 権限レベルを選択し、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-140">Choose the **Read** permission level and click **Create**.</span></span>  
  
4.  <span data-ttu-id="fd0e5-141">[ユーザーとグループ] の **[BISM ユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-141">Select **BISM Users** in People and Groups.</span></span>  
  
5.  <span data-ttu-id="fd0e5-142">[新規作成] をポイントして **[ユーザーの追加]** をクリックし、ユーザー アカウントまたはグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-142">Point to New, click **Add Users**, and then add user or group accounts.</span></span>  
  
     <span data-ttu-id="fd0e5-143">これで、追加したユーザーおよびグループに、サイト レベルから権限を継承するすべてのライブラリとリストを含むサイト全体の読み取り権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-143">These users and groups will now have Read permissions throughout the site, including all libraries and lists that inherit permissions from the site level.</span></span> <span data-ttu-id="fd0e5-144">この権限レベルでは高すぎる場合は、必要に応じて特定のライブラリ、リスト、またはアイテムからこのグループを削除できます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-144">If these permissions are too high, you can selectively remove this group from specific libraries, lists, or items.</span></span>  
  
 <span data-ttu-id="fd0e5-145">アイテム レベルで権限を選択的に削除するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-145">To selectively remove permissions at the item level, do the following:</span></span>  
  
1.  <span data-ttu-id="fd0e5-146">ライブラリで、ドキュメントを選択します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-146">In a library, select a document.</span></span> <span data-ttu-id="fd0e5-147">右側の下矢印をクリックし、 **[権限の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-147">Click the right down arrow and then click **Manage Permissions**.</span></span>  
  
2.  <span data-ttu-id="fd0e5-148">既定では、アイテムは権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-148">By default, an item inherits permissions.</span></span> <span data-ttu-id="fd0e5-149">このライブラリ内の個々のドキュメントの権限を変更するには、 **[権限の継承を中止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-149">To change the permissions of individual documents in this library, click **Stop Inheriting Permissions**.</span></span>  
  
3.  <span data-ttu-id="fd0e5-150">**[BISM ユーザー]** の横にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-150">Select the checkbox next to **BISM Users**.</span></span>  
  
4.  <span data-ttu-id="fd0e5-151">**[ユーザー権限の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-151">Click **Remove User Permissions**.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-workbook"></a><a name="bkmk_userdb"></a><span data-ttu-id="fd0e5-152">ブックに対する SharePoint 権限の構成</span><span class="sxs-lookup"><span data-stu-id="fd0e5-152">Configure SharePoint Permissions on the Workbook</span></span>  
 <span data-ttu-id="fd0e5-153">Excel ブック内で PowerPivot データベースを使用している場合、BI セマンティック モデル接続を介したデータ アクセスは Excel ブックに対する SharePoint 権限によって決まります。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-153">If you are using a PowerPivot database inside an Excel workbook, the SharePoint permissions on the Excel workbook determine data access via the BI semantic model connection.</span></span> <span data-ttu-id="fd0e5-154">ブックを外部データ ソースとして使用するには、ブックにアクセスするすべてのユーザーにブックに対する読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-154">All users who access the workbook must have Read permissions on the workbook in order to use it as an external data source.</span></span>  
  
 <span data-ttu-id="fd0e5-155">前のセクションの手順に従って **[BISM ユーザー]** グループを作成した場合は、継承された権限をブックで使用すると想定して、ブックおよび BI セマンティック モデル接続ファイルに対する十分な権限が、 **BISM ユーザー** のメンバーであるユーザー アカウントとグループ アカウントに付与されます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-155">If you created a **BISM Users** group using the instructions in the previous section, user and group accounts that are members of **BISM Users** will have sufficient permission on the workbook as well as the BI semantic model connection file, assuming the workbook uses inherited permissions.</span></span>  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a> <span data-ttu-id="fd0e5-156">次のステップ</span><span class="sxs-lookup"><span data-stu-id="fd0e5-156">Next Steps</span></span>  
 <span data-ttu-id="fd0e5-157">BI セマンティック モデル接続を作成し、セキュリティで保護したら、データ ソースとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-157">After you create and secure a BI semantic model connection, you can specify it as a data source.</span></span> <span data-ttu-id="fd0e5-158">詳細については、「 [Excel または Reporting Services での BI セマンティック モデル接続の使用](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd0e5-158">For more information, see [Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0e5-159">参照</span><span class="sxs-lookup"><span data-stu-id="fd0e5-159">See Also</span></span>  
 <span data-ttu-id="fd0e5-160">[PowerPivot BI セマンティックモデル接続 &#40;。 bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="fd0e5-160">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 <span data-ttu-id="fd0e5-161">[Excel または Reporting Services での BI セマンティックモデル接続の使用](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="fd0e5-161">[Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span></span>  
 [<span data-ttu-id="fd0e5-162">テーブル モデル データベースへの BI セマンティック モデル接続の作成</span><span class="sxs-lookup"><span data-stu-id="fd0e5-162">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
  
