---
title: レポートマネージャー | を使用してモデルを作成します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59ce278a22ec9797b001ca37a0bde576483cf5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719694"
---
# <a name="create-a-model-using-report-manager"></a><span data-ttu-id="6745a-102">レポート マネージャーを使用してモデルを作成する</span><span class="sxs-lookup"><span data-stu-id="6745a-102">Create a Model Using Report Manager</span></span>
  <span data-ttu-id="6745a-103">レポート マネージャーを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のキューブ、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のデータベース、Oracle のデータベースからモデルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6745a-103">You can generate models from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, or an Oracle database using Report Manager.</span></span> <span data-ttu-id="6745a-104">レポート モデルは、レポート サーバーにパブリッシュされている共有データ ソースから生成されます。</span><span class="sxs-lookup"><span data-stu-id="6745a-104">Report models are generated from shared data sources that are published on the report server.</span></span> <span data-ttu-id="6745a-105">まだ共有データ ソースがない場合は、作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6745a-105">If you do not already have a shared data source, you must create one.</span></span>  
  
 <span data-ttu-id="6745a-106">生成されるレポート モデルは、共有データ ソースのスキーマに完全に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6745a-106">The report model that you generate is based entirely on the schema of the shared data source.</span></span> <span data-ttu-id="6745a-107">データ ソースのどの部分をモデルに含めるかを選択したり、生成されるモデルのルールやメタデータを編集したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6745a-107">You cannot choose which parts of the data source are included in the model, nor can you edit the rules or metadata of a generated model.</span></span> <span data-ttu-id="6745a-108">ただし、モデルが生成された後でモデルのプロパティを設定したり、モデル全体またはモデルの一部へのアクセスを制限するロールの割り当てを定義したりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="6745a-108">However, you can set properties on the model after it is generated and define role assignments that restrict access to all or part of the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6745a-109">レポートマネージャーまたは2007を使用して生成された Oracle ベースのモデルには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] [!INCLUDE[SPS2010](../includes/sps2010-md.md)] oracle データソースへの接続に使用するユーザーアカウントのスキーマの一部であるデータベースオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6745a-109">An Oracle-based model generated using Report Manager or [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 [!INCLUDE[SPS2010](../includes/sps2010-md.md)] will include database objects that are a part of the schema for the user account used to connect to the Oracle data source.</span></span> <span data-ttu-id="6745a-110">ユーザー アカウント名は、データ ソース プロパティの資格情報で指定されます。</span><span class="sxs-lookup"><span data-stu-id="6745a-110">The user account name is specified in the data source properties credentials.</span></span>  
  
### <a name="to-create-a-new-data-source-for-a-report-model-using-report-manager"></a><span data-ttu-id="6745a-111">レポート マネージャーを使用してレポート モデルの新しいデータ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="6745a-111">To create a new data source for a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="6745a-112">Web ブラウザーで、アドレス バーにレポート サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="6745a-112">In your Web browser, type the URL for your report server in the address bar.</span></span>  
  
2.  <span data-ttu-id="6745a-113">**[新しいデータ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6745a-113">Click **New Data Source**.</span></span>  
  
3.  <span data-ttu-id="6745a-114">**[名前]** ボックスに、データ ソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6745a-114">In the **Name** box, enter a name for the data source.</span></span>  
  
4.  <span data-ttu-id="6745a-115">必要に応じて、 **[説明]** ボックスにモデルの簡単な説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="6745a-115">Optionally, enter a brief description of the mode in the **Description** text box.</span></span>  
  
5.  <span data-ttu-id="6745a-116">**[このデータ ソースを有効にする]** チェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6745a-116">Verify that the **Enable this data source** check box is selected.</span></span>  
  
6.  <span data-ttu-id="6745a-117">**[接続の種類]** ボックスの一覧で、接続先のデータ ソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="6745a-117">In the **Connection type** list, select the data source type to which you want to connect.</span></span> <span data-ttu-id="6745a-118">接続の種類は、 **[Oracle]**、 **[Microsoft SQL Server]** 、 **[Microsoft SQL Server Analysis Services]** のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6745a-118">The connection type must be one of the following: **Oracle**, **Microsoft SQL Server** or **Microsoft SQL Server Analysis Services**.</span></span>  
  
7.  <span data-ttu-id="6745a-119">**[接続文字列]** ボックスに、データベースを指す接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="6745a-119">In the **Connection string** box, enter the connection string that points to the database.</span></span>  
  
8.  <span data-ttu-id="6745a-120">レポート ビルダーのユーザーがデータベースに接続するために使用する必要のある接続方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="6745a-120">Select the connection method that Report Builder users will need to use to connect to the database.</span></span>  
  
    -   <span data-ttu-id="6745a-121">Windows 認証 : オペレーティング システムで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザーを認証する場合には、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="6745a-121">Windows Authentication: Select this option when you want the operating system to authenticate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] users.</span></span> <span data-ttu-id="6745a-122">このオプションを選択すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、パスワードの暗号化などの Windows のセキュリティ機能を使用してユーザーを認証します。</span><span class="sxs-lookup"><span data-stu-id="6745a-122">This option allows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use Windows security features, such as password encryption, to authenticate users.</span></span> <span data-ttu-id="6745a-123">このオプションを選択することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6745a-123">It is strongly recommended that you select this option.</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="6745a-124">認証: ユーザーが作成したログインアカウントを使用する場合は、このオプションを選択し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6745a-124">Authentication: Select this option when you want users to use a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account that you created.</span></span> <span data-ttu-id="6745a-125">ユーザーは、正しい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログイン名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6745a-125">Users must supply a valid [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login name and password.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="6745a-126">可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="6745a-126">Whenever possible, use Windows Authentication.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-report-model-using-report-manager"></a><span data-ttu-id="6745a-127">レポート マネージャーを使用してレポート モデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="6745a-127">To create a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="6745a-128">レポート マネージャーで、モデルに使用するデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="6745a-128">In Report Manager, select the data source that you want to use for your model.</span></span>  
  
     <span data-ttu-id="6745a-129">[プロパティ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6745a-129">The Properties page is displayed.</span></span>  
  
2.  <span data-ttu-id="6745a-130">データ ソースに対して指定したオプションが必要かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6745a-130">Verify that you want to use the options specified for the data source.</span></span>  
  
3.  <span data-ttu-id="6745a-131">**[モデルの生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6745a-131">Click **Generate Model**.</span></span>  
  
     <span data-ttu-id="6745a-132">データ ソースの [全般] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6745a-132">The General page is displayed for the data source.</span></span>  
  
4.  <span data-ttu-id="6745a-133">**[名前]** ボックスに、レポート モデルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6745a-133">In the **Name** box, enter a name for the report model.</span></span>  
  
5.  <span data-ttu-id="6745a-134">**[説明]** ボックスに、モデルの簡単な説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="6745a-134">In the **Description** box, enter a brief description of the model.</span></span>  
  
6.  <span data-ttu-id="6745a-135">レポート モデルの保存先として新しい場所を指定するには、 **[場所の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6745a-135">To specify a new location to save the report model to, click **Change Location**.</span></span>  
  
     <span data-ttu-id="6745a-136">既定では、レポート モデルはレポート マネージャーの [ホーム] に保存されます。</span><span class="sxs-lookup"><span data-stu-id="6745a-136">By default, the report model is saved to Report Manager Home.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="6745a-137">レポート モデルが作成され、指定した場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="6745a-137">The report model is created and saved to the location that you specified.</span></span> <span data-ttu-id="6745a-138">レポート マネージャーを使用して、このモデルに権限を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="6745a-138">You can assign permissions to this model by using Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6745a-139">参照</span><span class="sxs-lookup"><span data-stu-id="6745a-139">See Also</span></span>  
 <span data-ttu-id="6745a-140">[ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="6745a-140">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="6745a-141">[Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="6745a-141">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="6745a-142">[[新しいデータ ソース] ページ &#40;レポート マネージャー&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="6745a-142">[New Data Source Page &#40;Report Manager&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md)</span></span>  
  
  
