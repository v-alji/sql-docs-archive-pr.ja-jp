---
title: データマイニング構造およびデータマイニングモデルに対する権限の付与 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.miningmodels.f1
helpviewer_keywords:
- data mining [Analysis Services], security
- permissions [Analysis Services], mining models
- mining models [Analysis Services], security
- mining structures [Analysis Services], security
- permissions [Analysis Services], mining structures
- user access rights [Analysis Services], mining structures
- user access rights [Analysis Services], mining models
ms.assetid: a0008004-e2b7-47db-acad-5fe7e12b130f
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0db849551bdb38615f280b123c98f0e9d3053d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718800"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a><span data-ttu-id="77728-102">データ マイニング構造およびデータ マイニング モデルに対する権限の付与 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="77728-102">Grant permissions on data mining structures and models (Analysis Services)</span></span>
  <span data-ttu-id="77728-103">既定では、Analysis Services サーバー管理者にのみ、データベースのデータ マイニング構造またはマイニング モデルを表示する権限があります。</span><span class="sxs-lookup"><span data-stu-id="77728-103">By default, only an Analysis Services server administrator has permissions to view data mining structures or mining models in the database.</span></span> <span data-ttu-id="77728-104">管理者以外のユーザーに権限を付与するには、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="77728-104">Follow the instructions below to grant permissions to non-administrator users.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-structure"></a><span data-ttu-id="77728-105">マイニング構造にアクセスするための権限の設定</span><span class="sxs-lookup"><span data-stu-id="77728-105">Set permissions to access a mining structure</span></span>  
  
1.  <span data-ttu-id="77728-106">SSMS で、Analysis Services に接続します。</span><span class="sxs-lookup"><span data-stu-id="77728-106">In SSMS, connect to Analysis Services.</span></span> <span data-ttu-id="77728-107">手順について不明な点がある場合は、「[クライアント アプリケーションからの接続 &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77728-107">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with the steps.</span></span>  
  
2.  <span data-ttu-id="77728-108">オブジェクト エクスプローラーで **[データベース]** フォルダーを開き、データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="77728-108">Open the **Databases** folder, and select a database in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="77728-109">**[ロール]** を右クリックし、 **[新しいロール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="77728-109">Right-click **Roles** and choose **New Role**.</span></span>  
  
4.  <span data-ttu-id="77728-110">[全般] ページで、名前を入力し、必要に応じて説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="77728-110">In the General page, enter a name, and optionally, a description.</span></span> <span data-ttu-id="77728-111">このページには、フル コントロール、データベースの処理、定義の読み取りなどデータベース権限もいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="77728-111">The page also contains several database permissions, such as Full Control, Process Database, and Read Definition.</span></span> <span data-ttu-id="77728-112">これらのいずれの権限も、データ マイニングのアクセスには必要ありません。</span><span class="sxs-lookup"><span data-stu-id="77728-112">None of these permissions are needed for data mining access.</span></span> <span data-ttu-id="77728-113">データべース権限の詳細については、「[データベース権限の付与 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77728-113">See [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for more information about database permissions.</span></span>  
  
5.  <span data-ttu-id="77728-114">**[マイニング構造]** ペインで、データ マイニング構造ごとに **[読み取り]** または **[読み取り/書き込み]**  を選択します。</span><span class="sxs-lookup"><span data-stu-id="77728-114">In the **Mining Structure** pane, select **Read** or **Read/Write**  for each data mining structure.</span></span>  
  
6.  <span data-ttu-id="77728-115">**[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="77728-115">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
7.  <span data-ttu-id="77728-116">**[OK]** をクリックして、ロールの作成を終了します。</span><span class="sxs-lookup"><span data-stu-id="77728-116">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-model"></a><span data-ttu-id="77728-117">マイニング モデルにアクセスするための権限の設定</span><span class="sxs-lookup"><span data-stu-id="77728-117">Set permissions to access a mining model</span></span>  
 <span data-ttu-id="77728-118">データ マイニング モデルの場合、ロールに **[読み取り]** 権限または **[読み取り/書き込み]** 権限を設定できるほか、 **[ドリルスルー]** 権限および **[定義の読み取り]** 権限を設定して基になるデータの表示および参照を許可することもできます。</span><span class="sxs-lookup"><span data-stu-id="77728-118">For a data mining model, a role can have either **Read** or **Read/Write** permissions, as well as **Drillthrough** and **Read Definition** permissions that allow viewing and browsing the underlying data.</span></span>  
  
 <span data-ttu-id="77728-119">**注** マイニング構造とマイニング モデルの両方についてドリルスルーを有効にした場合、そのマイニング モデルとマイニング構造に対するドリルスルー権限を持つロールのすべてのメンバー ユーザーが、マイニング構造内の列を表示できるようになります。これらの列がマイニング モデルに含まれていなかったとしても同様です。</span><span class="sxs-lookup"><span data-stu-id="77728-119">**Note** If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model and the mining structure can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="77728-120">したがって、機密情報を保護するため、個人情報をマスクするデータ ソース ビューを設定し、マイニング構造に対するドリルスルー アクセスは必要な場合にのみ許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77728-120">Therefore, to protect sensitive information, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
 <span data-ttu-id="77728-121">データベース ロールに読み取り権限または読み取り/書き込み権限を与えるには、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー ロールのメンバーであるか、フル コントロール (管理者) 権限を持つ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="77728-121">To grant read or read/write permissions to a database role, a user must be a member of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server role or a member of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has Full Control (Administrator) permissions.</span></span>  
  
1.  <span data-ttu-id="77728-122">で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のインスタンスに接続し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、オブジェクトエクスプローラーで適切なデータベースの [**ロール**] を展開します。次に、データベースロールをクリックするか、新しいデータベースロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="77728-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="77728-123">**[マイニング構造]** ペインで、 **[マイニング モデル]** ボックスの一覧からマイニング モデルを見つけ、そのマイニング モデルの **[読み取り]**、 **[読み取り/書き込み]**、 **[ドリルスルー]**、または **[参照]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="77728-123">In the **Mining Structure** pane, locate the mining model in the **Mining Models** list, and then select **Read**, **Read/Write**, **Drill Through**, or **Browse** for that mining model.</span></span>  
  
3.  <span data-ttu-id="77728-124">**[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="77728-124">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="77728-125">**[OK]** をクリックして、ロールの作成を終了します。</span><span class="sxs-lookup"><span data-stu-id="77728-125">Click **OK** to finish creating the role.</span></span>  
  
 <span data-ttu-id="77728-126">データ マイニング拡張機能 (DMX) の OPENQUERY 句を使用するドリルスルー クエリでデータ ソースを使用するには、適切なデータ ソース オブジェクトに対する読み取り/書き込み権限もデータベース ロールに与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="77728-126">To use a data source in a drillthrough query that uses the Data Mining Extensions (DMX) OPENQUERY clause, the database role also needs read/write permission on the appropriate data source object.</span></span> <span data-ttu-id="77728-127">詳細については、「[データ ソース オブジェクトに対する権限の付与 &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md)」および[OPENQUERY & #40;DMX& #41;](/sql/dmx/source-data-query-openquery)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77728-127">For more information, see [Grant permissions on a data source object &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) and [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77728-128">既定では、OPENROWSET を使った DMX クエリの送信が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="77728-128">By default, the submission of DMX queries by using OPENROWSET is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77728-129">参照</span><span class="sxs-lookup"><span data-stu-id="77728-129">See Also</span></span>  
 <span data-ttu-id="77728-130">[サーバー管理者のアクセス許可を付与 &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="77728-130">[Grant Server Administrator Permissions &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="77728-131">[キューブまたはモデルの権限を &#40;Analysis Services に付与する&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="77728-131">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 <span data-ttu-id="77728-132">[ディメンションデータへのカスタムアクセス権の付与 &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="77728-132">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 [<span data-ttu-id="77728-133">セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="77728-133">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
