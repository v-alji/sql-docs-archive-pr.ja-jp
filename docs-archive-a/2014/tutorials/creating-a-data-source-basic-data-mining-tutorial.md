---
title: データソースの作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d8d5974c3685476f5d7a5751fb71bfa98384cf36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634746"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a><span data-ttu-id="de0f7-102">データ ソースの作成 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="de0f7-102">Creating a Data Source (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="de0f7-103">*データソース*は、プロジェクトに保存および管理され、データベースに配置されるデータ接続です [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="de0f7-103">A *data source* is a data connection that is saved and managed in your project and deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="de0f7-104">データ ソースには、ソース データが存在するサーバーとデータベースの名前、および接続に必要なその他のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="de0f7-104">The data source contains the names of the server and database where your source data resides, in addition to any other required connection properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de0f7-105">データベースの名前は [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="de0f7-105">The name of the database is [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="de0f7-106">このデータベースをまだインストールしていない場合は、 [MICROSOFT SQL サンプルデータベース](https://go.microsoft.com/fwlink/?LinkId=88417)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de0f7-106">If you have not already installed this database, see the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page.</span></span>  
  
### <a name="to-create-a-data-source"></a><span data-ttu-id="de0f7-107">データ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="de0f7-107">To create a data source</span></span>  
  
1.  <span data-ttu-id="de0f7-108">**ソリューションエクスプローラー**で、[**データソース**] フォルダーを右クリックし、[**新しいデータソース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0f7-108">In **Solution Explorer**, right-click the **Data Sources** folder and select **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="de0f7-109">**[データ ソース ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0f7-109">On the **Welcome to the Data Source Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="de0f7-110">[**接続の定義方法を選択**します] ページで、[**新規**] をクリックしてデータベースに接続を追加し [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="de0f7-110">On the **Select how to define the connection** page, click **New** to add a connection to the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="de0f7-111">[**接続マネージャー**] の [**プロバイダー** ] ボックスの一覧で、[**ネイティブ OLE Db\ SQL Server native Client 11.0**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de0f7-111">In the **Provider** list in **Connection Manager**, select **Native OLE DB\SQL Server Native Client 11.0**.</span></span>  
  
5.  <span data-ttu-id="de0f7-112">[**サーバー名**] ボックスに、をインストールしたサーバーの名前を入力または選択し [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="de0f7-112">In the **Server name** box, type or select the name of the server on which you installed [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span>  
  
     <span data-ttu-id="de0f7-113">たとえば、データベースがローカルサーバーでホストされている場合は、「 **localhost** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="de0f7-113">For example, type **localhost** if the database is hosted on the local server.</span></span>  
  
6.  <span data-ttu-id="de0f7-114">[**サーバーにログオン**する] で、[ **Windows 認証を使用する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de0f7-114">In the **Log onto the server** group, select **Use Windows Authentication**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="de0f7-115">Windows 認証は SQL Server 認証よりも安全性に優れているので、実装時はできる限り Windows 認証を使用してください。</span><span class="sxs-lookup"><span data-stu-id="de0f7-115">Whenever possible, implementers should use Windows Authentication, as it provides a more secure authentication method than SQL Server Authentication.</span></span> <span data-ttu-id="de0f7-116">SQL Server 認証は旧バージョンとの互換性を維持するために提供されています。</span><span class="sxs-lookup"><span data-stu-id="de0f7-116">However, SQL Server Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="de0f7-117">認証方法の詳細については、「[データベースエンジンの構成-アカウントの準備](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de0f7-117">For more information about authentication methods, see [Database Engine Configuration - Account Provisioning](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).</span></span>  
  
7.  <span data-ttu-id="de0f7-118">[**データベース名の選択または入力**] ボックスの一覧で、を選択し、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0f7-118">In the **Select or enter a database name** list, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="de0f7-119">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0f7-119">Click **Next**.</span></span>  
  
9. <span data-ttu-id="de0f7-120">[**権限借用情報**] ページで、[**サービスアカウントを使用する**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0f7-120">On the **Impersonation Information** page, click **Use the service account**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="de0f7-121">[**ウィザードの完了**] ページで、既定では、データソースの名前が ADVENTURE works DW 2012 になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="de0f7-121">On the **Completing the Wizard** page, notice that, by default, the data source is named Adventure Works DW 2012.</span></span>  
  
10. <span data-ttu-id="de0f7-122">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de0f7-122">Click **Finish**.</span></span>  
  
     <span data-ttu-id="de0f7-123">新しいデータソース Adventure Works DW 2012 がソリューションエクスプローラーの [**データソース**] フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="de0f7-123">The new data source, Adventure Works DW 2012, appears in the **Data Sources** folder in Solution Explorer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="de0f7-124">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="de0f7-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="de0f7-125">データソースビューの作成基本的なデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="de0f7-125">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="de0f7-126">このレッスンの前の作業</span><span class="sxs-lookup"><span data-stu-id="de0f7-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="de0f7-127">基本的なデータマイニングチュートリアル &#40;Analysis Services プロジェクトの作成&#41;</span><span class="sxs-lookup"><span data-stu-id="de0f7-127">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="de0f7-128">参照</span><span class="sxs-lookup"><span data-stu-id="de0f7-128">See Also</span></span>  
 <span data-ttu-id="de0f7-129">[SSAS 多次元&#41;&#40;データソースを作成する](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="de0f7-129">[Create a Data Source &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span></span>  
 <span data-ttu-id="de0f7-130">[データソースの定義](../analysis-services/lesson-1-2-defining-a-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="de0f7-130">[Defining a Data Source](../analysis-services/lesson-1-2-defining-a-data-source.md) </span></span>  
 [<span data-ttu-id="de0f7-131">権限借用オプションの設定 &#40;SSAS - 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="de0f7-131">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional)  
  
  
