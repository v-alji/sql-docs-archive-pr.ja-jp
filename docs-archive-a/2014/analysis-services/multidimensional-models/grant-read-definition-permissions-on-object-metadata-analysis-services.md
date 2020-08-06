---
title: オブジェクトメタデータに対する定義の読み取り権限の付与 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- permissions [Analysis Services], read metadata
- read metadata permissions
ms.assetid: c857e48e-64b0-4ffe-900d-a0a3ddafcefb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e3b18b913ed4b678baf0969b006f1386ba748e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641899"
---
# <a name="grant-read-definition-permissions-on-object-metadata-analysis-services"></a><span data-ttu-id="666c2-102">オブジェクト メタデータに対する定義の読み取り権限の付与 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="666c2-102">Grant read definition permissions on object metadata (Analysis Services)</span></span>
  <span data-ttu-id="666c2-103">管理者は、選択したオブジェクトのオブジェクト定義またはメタデータを読み取る権限を使用して、オブジェクトの定義の変更、オブジェクトの構造の変更、またはオブジェクトの実際のデータの表示を行う権限を付与することなく、オブジェクト情報を表示する権限を付与できます。</span><span class="sxs-lookup"><span data-stu-id="666c2-103">Permission to read an object definition, or metadata, on selected objects lets an administrator grant permission to view object information, without also granting permission to modify the object's definition, modify the object's structure, or view the actual data for the object.</span></span> <span data-ttu-id="666c2-104">`Read Definition`権限は、データベース、データソース、ディメンション、マイニング構造、およびマイニングモデルレベルで許可できます。</span><span class="sxs-lookup"><span data-stu-id="666c2-104">`Read Definition` permissions can be granted at the database, data source, dimension, mining structure, and mining model levels.</span></span> <span data-ttu-id="666c2-105">キューブに対する権限が必要な場合は、 `Read Definition` データベースに対してを有効にする必要があり `Read Definition` ます。アクセス許可は付加的なものであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="666c2-105">If you require `Read Definition` permissions for a cube, you must enable `Read Definition` for the database.Remember that permissions are additive.</span></span> <span data-ttu-id="666c2-106">たとえば、あるロールではキューブのメタデータを読み取るための権限を付与し、別のロールでは同じユーザーにディメンションのメタデータを読み取るための権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="666c2-106">For example, one role grants permission to read the metadata for a cube, while a second role grants the same user permission to read the metadata for a dimension.</span></span> <span data-ttu-id="666c2-107">これら 2 つの異なるロールの権限は組み合わされ、キューブのメタデータを読み取る権限と、そのデータベース内のディメンションのメタデータを読み取る権限をユーザーに与えることになります。</span><span class="sxs-lookup"><span data-stu-id="666c2-107">The permissions from the two different roles combine to give the user permission to both read metadata for the cube and the metadata for the dimension within that database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="666c2-108">データベースのメタデータを読み取る権限は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースに接続するために必要な最小限の権限です。</span><span class="sxs-lookup"><span data-stu-id="666c2-108">Permission to read a database's metadata is the minimum permission required to connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database using either [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="666c2-109">また、メタデータを読み取る権限を持つユーザーは、DISCOVER_XML_METADATA スキーマ行セットを使用して、オブジェクトのクエリを行い、そのメタデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="666c2-109">A user who has permission to read metadata can also use the DISCOVER_XML_METADATA schema rowset to query the object and view its metadata.</span></span> <span data-ttu-id="666c2-110">詳細については、「 [DISCOVER_XML_METADATA 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="666c2-110">For more information, see [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).</span></span>  
  
## <a name="set-read-definition-permissions-on-a-database"></a><span data-ttu-id="666c2-111">データベースに対する定義の読み取り権限の設定</span><span class="sxs-lookup"><span data-stu-id="666c2-111">Set read definition permissions on a database</span></span>  
 <span data-ttu-id="666c2-112">データベース メタデータを読み取る権限を付与すると、データベース内のすべてのオブジェクトのメタデータを読み取るための権限も付与されます。</span><span class="sxs-lookup"><span data-stu-id="666c2-112">Granting permission to read database metadata also grants permission to read the metadata of all objects in the database.</span></span>  
  
 <span data-ttu-id="666c2-113">`Read Definition`専用の処理のためにロールを設定するときは常に、データベースレベルで権限を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="666c2-113">We suggest that you include the `Read Definition` permission at the database level whenever you are setting up roles for dedicated processing.</span></span> <span data-ttu-id="666c2-114">では、 `Read Definition` 管理者以外のユーザーがでモデルのオブジェクト階層を表示 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] し、後続の処理のために個々のオブジェクトに移動できます。</span><span class="sxs-lookup"><span data-stu-id="666c2-114">Having `Read Definition` allows non-administrators to view a model's object hierarchy in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and navigate to individual objects for subsequent processing.</span></span>  
  
1.  <span data-ttu-id="666c2-115">で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のインスタンスに接続し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、オブジェクトエクスプローラーで適切なデータベースの [**ロール**] を展開します。次に、データベースロールをクリックするか、新しいデータベースロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="666c2-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="666c2-116">[**全般**] タブで、オプションを選択し `Read Definition` ます。</span><span class="sxs-lookup"><span data-stu-id="666c2-116">On the **General** tab, select the `Read Definition` option.</span></span>  
  
3.  <span data-ttu-id="666c2-117">**[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="666c2-117">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="666c2-118">**[OK]** をクリックして、ロールの作成を終了します。</span><span class="sxs-lookup"><span data-stu-id="666c2-118">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-read-definition-permissions-on-individual-objects"></a><span data-ttu-id="666c2-119">個々のオブジェクトに対する定義の読み取り権限の設定</span><span class="sxs-lookup"><span data-stu-id="666c2-119">Set read definition permissions on individual objects</span></span>  
  
1.  <span data-ttu-id="666c2-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、 **[データベース]** フォルダーを開き、データベースを選択します。オブジェクト エクスプローラーでそのデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、または新しいデータベース ロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="666c2-120">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the **Databases** folder, select a database, expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="666c2-121">**[全般**] ペインで、のデータベース権限を消去し `Read Definition` ます。</span><span class="sxs-lookup"><span data-stu-id="666c2-121">In the **General** pane, clear the database permission for `Read Definition`.</span></span> <span data-ttu-id="666c2-122">この手順によって、権限継承が削除され、個々のオブジェクトに対する権限を設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="666c2-122">This step removes permission inheritance so that you can set permissions on individual objects.</span></span>  
  
3.  <span data-ttu-id="666c2-123">プロパティを指定するオブジェクトを選択し `Read Definition` ます。</span><span class="sxs-lookup"><span data-stu-id="666c2-123">Select the object for which you are specifying `Read Definition` properties:</span></span>  
  
    -   <span data-ttu-id="666c2-124">[**データソース**] ペインで、 `Read Definition` そのデータソースのチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="666c2-124">In the **Data Sources** pane, click the `Read Definition` check box for that data source.</span></span> <span data-ttu-id="666c2-125">ロール メンバーは、サーバー名や場合によってはユーザー名も含め、データ ソースの接続文字列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="666c2-125">Role members can view the connection string to the data source, including the server name and possibly the user name.</span></span> <span data-ttu-id="666c2-126">接続文字列を変更する権限やその他のオブジェクトの定義を表示する権限は付与しないで、接続文字列情報を提供する場合に、この権限が使用できます。</span><span class="sxs-lookup"><span data-stu-id="666c2-126">This permission is available in case you want to provide connection string information, without also granting permission to modify the connection string or view the definitions of any other objects.</span></span>  
  
    -   <span data-ttu-id="666c2-127">[**ディメンション**] ペインで、 `Read Definition` そのディメンションのチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="666c2-127">In the **Dimensions** pane, click the `Read Definition` check box for that dimension.</span></span> <span data-ttu-id="666c2-128">熟練したアナリストおよび開発者が、変更権限のない定義を表示したり、他のオブジェクト (他のディメンション、キューブ オブジェクト、マイニング構造、マイニング モデルなど) の定義を表示したりすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="666c2-128">Experienced analysts and developers may need to view the definition without permission to modify it or view the definitions of other objects (such as other dimensions, cube objects, or mining structures and models).</span></span>  
  
    -   <span data-ttu-id="666c2-129">[マイニング構造] ペインで、 `Read Definition` データマイニング構造またはデータマイニングモデルのチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="666c2-129">In the Mining Structures pane, click the `Read Definition` check box for data mining structures or models.</span></span> <span data-ttu-id="666c2-130">`Read Definition`データモデルを参照するには、が必要です。</span><span class="sxs-lookup"><span data-stu-id="666c2-130">`Read Definition` is required for browsing the data model.</span></span> <span data-ttu-id="666c2-131">詳細については、「[データ マイニング構造およびデータ マイニング モデルに対する権限の付与 &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="666c2-131">See [Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) for details.</span></span>  
  
4.  <span data-ttu-id="666c2-132">**[メンバーシップ]** ペインで、このロールを使用して Analysis Services に接続する Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="666c2-132">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
5.  <span data-ttu-id="666c2-133">**[OK]** をクリックして、ロールの作成を終了します。</span><span class="sxs-lookup"><span data-stu-id="666c2-133">Click **OK** to finish creating the role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666c2-134">参照</span><span class="sxs-lookup"><span data-stu-id="666c2-134">See Also</span></span>  
 <span data-ttu-id="666c2-135">[Analysis Services &#40;データベースのアクセス許可を付与&#41;](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="666c2-135">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="666c2-136">処理権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="666c2-136">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
  
