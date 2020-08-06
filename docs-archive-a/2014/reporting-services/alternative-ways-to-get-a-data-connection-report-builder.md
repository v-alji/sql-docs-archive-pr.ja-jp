---
title: 別の方法でデータ接続を取得する (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2be693469318172b2a55fbcb17b33e1deaaed3df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633001"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a><span data-ttu-id="dd4c3-102">別の方法でデータ接続を取得する (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="dd4c3-102">Alternative Ways to Get a Data Connection (Report Builder)</span></span>
  <span data-ttu-id="dd4c3-103">データ接続には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースなどの外部データ ソースに接続するときに必要な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-103">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="dd4c3-104">通常、使用する接続情報と資格情報の種類はデータ ソースの所有者から提供されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-104">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span>  
  
 <span data-ttu-id="dd4c3-105">データ接続を指定するには、レポート サーバーの共有データ ソースを使用するか、特定のレポートでのみ使用する埋め込みデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-105">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in a specific report.</span></span>  
  
 <span data-ttu-id="dd4c3-106">ほとんどのチュートリアルでは埋め込みデータ ソースを使用しますが、共有データ ソースにアクセスできる場合は、代わりに共有データ ソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-106">In most tutorials you use embedded data sources, but if you have access to shared data sources, then you can use them instead.</span></span>  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a><span data-ttu-id="dd4c3-107">共有データ ソースのデータ接続の取得</span><span class="sxs-lookup"><span data-stu-id="dd4c3-107">Getting a Data Connection From a Shared Data Source</span></span>  
 <span data-ttu-id="dd4c3-108">レポート サーバーに使用可能な共有データ ソースがあり、それらを使用する権限がある場合は、埋め込みデータ ソースの代わりにそれらの共有データ ソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-108">If the report server has available shared data source that you have permissions to use, you can use them instead of an embedded data source.</span></span> <span data-ttu-id="dd4c3-109">共有データ ソースを探し、それらを使用するために必要な資格情報を指定する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-109">The following procedures tell how to locate the shared data sources and provide any credentials needed to use them.</span></span>  
  
 <span data-ttu-id="dd4c3-110">共有データ ソースを使用するには、レポート サーバーを参照して共有データ ソースを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-110">To use a shared data source, you must browse to a report server and select one.</span></span> <span data-ttu-id="dd4c3-111">通常、レポート サーバーの URL はレポート サーバー管理者から提供されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-111">Usually, you get the report server URL from the report server administrator.</span></span>  
  
#### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a><span data-ttu-id="dd4c3-112">共有データ ソースの一覧からデータ接続を指定するには</span><span class="sxs-lookup"><span data-stu-id="dd4c3-112">To specify a data connection from a list of shared data sources</span></span>  
  
1.  <span data-ttu-id="dd4c3-113">**[データセットの選択]** ページで **[データセットを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-113">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="dd4c3-114">**[データ ソースへの接続の選択]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-114">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="dd4c3-115">データ ソースの一覧から、アクセスする権限があるデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-115">From the list of data sources, select a data source that you have permission to access.</span></span>  
  
3.  <span data-ttu-id="dd4c3-116">データ ソースに接続できることを確認するために、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-116">To verify that you can connect to the data source, click **Test Connection**.</span></span> <span data-ttu-id="dd4c3-117">"接続が正常に作成されました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-117">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="dd4c3-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="dd4c3-119">必要に応じて、資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-119">If necessary, enter your credentials.</span></span> <span data-ttu-id="dd4c3-120">資格情報をローカルに保存するには、 **[接続時にパスワードを保存する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-120">To save the credentials locally, select **Save password with connection**.</span></span> <span data-ttu-id="dd4c3-121">このオプションを選択しない場合、レポートを実行するたびに資格情報が要求されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-121">If you not select this option, you will be prompted for credentials every time that you run the report</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a><span data-ttu-id="dd4c3-122">レポート サーバーの共有データ ソースを参照してデータ接続を指定するには</span><span class="sxs-lookup"><span data-stu-id="dd4c3-122">To specify a data connection by browsing to a shared data source on a report server</span></span>  
  
1.  <span data-ttu-id="dd4c3-123">**[データセットの選択]** ページで **[データセットを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-123">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="dd4c3-124">**[データ ソースへの接続の選択]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-124">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="dd4c3-125">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-125">Click **Browse**.</span></span> <span data-ttu-id="dd4c3-126">**[データ ソースの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-126">The **Select Data Source** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="dd4c3-127">**[検索対象]** ドロップダウン リストから **[最近使ったサイトとサーバー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-127">From the **Look in** drop-down list, select **Recent Sites and Servers**.</span></span> <span data-ttu-id="dd4c3-128">データ ソース ウィンドウでサーバーの URL をクリックし、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-128">In the data source pane, click the URL for your server, and then click **Open**.</span></span>  
  
     <span data-ttu-id="dd4c3-129">データ ソースまたはモデルの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-129">The list of data sources or models appears.</span></span>  
  
4.  <span data-ttu-id="dd4c3-130">または、 **[名前]** にレポート サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-130">Alternatively, in **Name**, type the URL to the report server.</span></span> <span data-ttu-id="dd4c3-131">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-131">Click **Open**.</span></span>  
  
     <span data-ttu-id="dd4c3-132">レポート ビルダーがレポート サーバーに接続され、ルート フォルダーにある使用可能なデータ ソースが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-132">Report Builder connects to the report server and loads the data sources that are available at the root folder.</span></span>  
  
5.  <span data-ttu-id="dd4c3-133">接続するための必要な権限があるデータ ソースが格納されたフォルダーに移動し、データ ソースを選択して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-133">Navigate to a folder that contains a data source that you have sufficient permissions to connect to, select the data source, and then click **Open**.</span></span>  
  
     <span data-ttu-id="dd4c3-134">**[データ ソースへの接続の選択]** ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-134">You are back on the **Choose a connection to a data source** page.</span></span>  
  
6.  <span data-ttu-id="dd4c3-135">データ ソースに接続できることを確認するために、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-135">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="dd4c3-136">"接続が正常に作成されました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-136">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="dd4c3-137">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-137">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="dd4c3-138">ユーザー名とパスワードを要求された場合は、資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-138">If you are prompted for a user name and password, enter your credentials.</span></span> <span data-ttu-id="dd4c3-139">資格情報をローカルに保存するには、 **[接続時にパスワードを保存する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dd4c3-139">To save the credentials locally, select **Save password with connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd4c3-140">参照</span><span class="sxs-lookup"><span data-stu-id="dd4c3-140">See Also</span></span>  
 <span data-ttu-id="dd4c3-141">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dd4c3-141">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="dd4c3-142">チュートリアル &#40;レポートビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="dd4c3-142">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
