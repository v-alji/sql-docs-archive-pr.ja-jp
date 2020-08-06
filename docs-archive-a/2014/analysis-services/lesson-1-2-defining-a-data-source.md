---
title: データソースの定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdf00b47360341e2b9a99654482d65be83b86503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631314"
---
# <a name="defining-a-data-source"></a><span data-ttu-id="d797c-102">データ ソースの定義</span><span class="sxs-lookup"><span data-stu-id="d797c-102">Defining a Data Source</span></span>
  <span data-ttu-id="d797c-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを作成した後は、通常、そのプロジェクトで使用するデータ ソースを 1 つ以上定義します。</span><span class="sxs-lookup"><span data-stu-id="d797c-103">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you generally start working with the project by defining one or more data sources that the project will use.</span></span> <span data-ttu-id="d797c-104">データ ソースを定義するときは、データ ソースへの接続に使用する接続文字列情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="d797c-104">When you define a data source, you are defining the connection string information that will be used to connect to the data source.</span></span> <span data-ttu-id="d797c-105">詳細については、「 [データ ソースの作成 &#40;SSAS 多次元&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d797c-105">For more information, see [Create a Data Source &#40;SSAS Multidimensional&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md).</span></span>  
  
 <span data-ttu-id="d797c-106">次の実習では、AdventureWorksDWSQLServer2012 サンプル データベースを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトのデータ ソースとして定義します。</span><span class="sxs-lookup"><span data-stu-id="d797c-106">In the following task, you define the AdventureWorksDWSQLServer2012 sample database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="d797c-107">チュートリアル用にサンプル データベースはローカル コンピューターに保存されていますが、ソース データベースから 1 つ以上のリモート コンピューターをホストすることもしばしばあります。</span><span class="sxs-lookup"><span data-stu-id="d797c-107">While this database is located on your local computer for the purposes of this tutorial, source databases are frequently hosted on one or more remote computers.</span></span>  
  
### <a name="to-define-a-new-data-source"></a><span data-ttu-id="d797c-108">新しいデータ ソースを定義するには</span><span class="sxs-lookup"><span data-stu-id="d797c-108">To define a new data source</span></span>  
  
1.  <span data-ttu-id="d797c-109">ソリューション エクスプローラー (Microsoft Visual Studio ウィンドウの右側) で、 **[データ ソース]** を右クリックし、 **[新しいデータ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d797c-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Sources**, and then click **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="d797c-110">**データ ソース ウィザード** の **[データ ソース ウィザードへようこそ]** ページで、 **[次へ]** をクリックして **[接続の定義方法を選択します]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="d797c-110">On the **Welcome to the Data Source Wizard** page of the **Data Source Wizard**, click **Next** to open the **Select how to define the connection** page.</span></span>  
  
3.  <span data-ttu-id="d797c-111">**[接続の定義方法を選択します]** ページでは、新しい接続、既存の接続、または以前に定義したデータ ソース オブジェクトに基づいて、データ ソースを定義できます。</span><span class="sxs-lookup"><span data-stu-id="d797c-111">On the **Select how to define the connection** page, you can define a data source based on a new connection, based on an existing connection, or based on a previously defined data source object.</span></span> <span data-ttu-id="d797c-112">ここでは、新しい接続に基づいてデータ ソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="d797c-112">In this tutorial, you define a data source based on a new connection.</span></span> <span data-ttu-id="d797c-113">**[既存の接続または新しい接続に基づいてデータ ソースを作成する]** が選択されていることを確認し、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d797c-113">Verify that **Create a data source based on an existing or new connection** is selected, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="d797c-114">**[接続マネージャー]** ダイアログ ボックスで、データ ソースの接続のプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="d797c-114">In the **Connection Manager** dialog box, you define connection properties for the data source.</span></span> <span data-ttu-id="d797c-115">**[プロバイダー]** ボックスの一覧で、 **[ネイティブ OLE DB\SQL Server Native Client 11.0]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d797c-115">In the **Provider** list box, verify that **Native OLE DB\SQL Server Native Client 11.0** is selected.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="d797c-116">では、 **[プロバイダー]** ボックスの一覧に表示されるその他のプロバイダーもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d797c-116">also supports other providers, which are displayed in the **Provider** list.</span></span>  
  
5.  <span data-ttu-id="d797c-117">[**サーバー名**] テキストボックスに、「」と入力 `localhost` します。</span><span class="sxs-lookup"><span data-stu-id="d797c-117">In the **Server name** text box, type `localhost`.</span></span>  
  
     <span data-ttu-id="d797c-118">ローカルコンピューター上の名前付きインスタンスに接続するには、 **localhost \\<インスタンス \> 名**を入力します。</span><span class="sxs-lookup"><span data-stu-id="d797c-118">To connect to a named instance on your local computer, type **localhost\\<instance name\>**.</span></span> <span data-ttu-id="d797c-119">ローカル コンピューターではなく指定のコンピューターに接続するには、コンピューター名または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d797c-119">To connect to the specific computer instead of the local computer, type the computer name or IP address.</span></span>  
  
6.  <span data-ttu-id="d797c-120">**[Windows 認証を使用]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d797c-120">Verify that **Use Windows Authentication** is selected.</span></span> <span data-ttu-id="d797c-121">**[データベースの選択または入力]** ボックスの一覧で、 **[AdventureWorksDW2012]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d797c-121">In the **Select or enter a database name** list, select **AdventureWorksDW2012**.</span></span>  
  
7.  <span data-ttu-id="d797c-122">**[接続テスト]** をクリックして、データベースへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="d797c-122">Click **Test Connection** to test the connection to the database.</span></span>  
  
8.  <span data-ttu-id="d797c-123">[**OK**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d797c-123">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="d797c-124">ウィザードの **[権限借用情報]** ページでは、データ ソースへの接続時に使用する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のセキュリティ資格情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="d797c-124">On the **Impersonation Information** page of the wizard, you define the security credentials for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use to connect to the data source.</span></span> <span data-ttu-id="d797c-125">権限借用は、Windows 認証が選択されている場合に、データ ソースへの接続に使用される Windows アカウントに関連する機能です。</span><span class="sxs-lookup"><span data-stu-id="d797c-125">Impersonation affects the Windows account used to connect to the data source when Windows Authentication is selected.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="d797c-126">では、OLAP オブジェクトを処理するための権限借用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d797c-126">does not support impersonation for processing OLAP objects.</span></span> <span data-ttu-id="d797c-127">**[サービス アカウントを使用する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d797c-127">Select **Use the service account**, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="d797c-128">**[ウィザードの完了]** ページで、既定の名前である **Adventure Works DW 2012**をそのまま使用して、 **[完了]** をクリックします。新しいデータ ソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d797c-128">On the **Completing the Wizard** page, accept the default name, **Adventure Works DW 2012**, and then click **Finish** to create the new data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d797c-129">作成後にデータ ソースのプロパティを変更するには、 **[データ ソース]** フォルダー内のデータ ソースをダブルクリックします。 **[データ ソース デザイナー]** にデータ ソースのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d797c-129">To modify the properties of the data source after it has been created, double-click the data source in the **Data Sources** folder to display the data source properties in **Data Source Designer**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d797c-130">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="d797c-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d797c-131">データ ソース ビューの定義</span><span class="sxs-lookup"><span data-stu-id="d797c-131">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a><span data-ttu-id="d797c-132">参照</span><span class="sxs-lookup"><span data-stu-id="d797c-132">See Also</span></span>  
 [<span data-ttu-id="d797c-133">データ ソースの作成 &#40;SSAS 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="d797c-133">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
  
