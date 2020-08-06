---
title: プロセスのアクセス許可を付与する (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e41e8710bc167ef53eb2aad2cbf678019b96e0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718794"
---
# <a name="grant-process-permissions-analysis-services"></a><span data-ttu-id="41bbb-102">処理権限の付与 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="41bbb-102">Grant process permissions (Analysis Services)</span></span>
  <span data-ttu-id="41bbb-103">管理者は、Analysis Services 処理操作専用のロールを作成して、その特定のタスクを他のユーザーまたは自動スケジューリング処理用のアプリケーションに委任できます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-103">As an administrator, you can create a role dedicated to Analysis Services processing operations, allowing you to delegate that particular task to other users, or to applications used for unattended scheduled processing.</span></span> <span data-ttu-id="41bbb-104">処理権限はデータベース、キューブ、ディメンション、およびマイニング構造レベルで許可することができます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-104">Process permissions can be granted at the database, cube, dimension, and mining structure levels.</span></span> <span data-ttu-id="41bbb-105">非常に大きなキューブまたは表形式データベースで作業している場合を除き、相互に依存関係にあるものなどすべてのオブジェクトを含めて、データベース レベルで処理権限を付与することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-105">Unless you are working with a very large cube or tabular database, we recommend granting processing rights at the database level, inclusive of all objects, including those having dependencies on each other.</span></span>  
  
 <span data-ttu-id="41bbb-106">権限は、オブジェクトを権限および Windows ユーザーアカウントまたはグループ アカウントに関連付けるロールによって付与されます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-106">Permissions are granted through roles that associate objects with permissions and Windows user or group accounts.</span></span> <span data-ttu-id="41bbb-107">権限は加算的であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="41bbb-107">Remember that permissions are additive.</span></span> <span data-ttu-id="41bbb-108">あるロールによってキューブを処理する権限が付与され、別のロールによって同じユーザーにディメンションを処理する権限が付与される場合、この 2 種類のロールによる権限が組み合わされ、キューブを処理する権限とそのデータベース内の指定のディメンションを処理する権限の両方がユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-108">If one role grants permission to process a cube, while a second role gives the same user permission to process a dimension, the permissions from the two different roles combine to give the user permission to both process the cube and process the specified dimension within that database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="41bbb-109">ロールによって処理権限のみが付与されているユーザーは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に接続したり、オブジェクトを処理したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="41bbb-109">A user whose role only has Process permissions will be unable to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and process objects.</span></span> <span data-ttu-id="41bbb-110">これらのツールを使用するには、オブジェクト メタデータにアクセスするための`Read Definition`権限が必要となります。</span><span class="sxs-lookup"><span data-stu-id="41bbb-110">These tools require the `Read Definition` permission to access object metadata.</span></span> <span data-ttu-id="41bbb-111">どちらのツールも使用できない場合は、XMLA スクリプトを使用して処理操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41bbb-111">Without the ability to use either tool, XMLA script must be used to execute a processing operation.</span></span>  
>   
>  <span data-ttu-id="41bbb-112">また、テスト目的で`Read Definition`権限も付与することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-112">We suggest you also grant `Read Definition` permissions for testing purposes.</span></span> <span data-ttu-id="41bbb-113">`Read Definition`権限と`Process Database`権限の両方を持つユーザーは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で対話的にオブジェクトを処理できます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-113">A user having both `Read Definition` and `Process Database` permissions can process objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], interactively.</span></span> <span data-ttu-id="41bbb-114">「 [オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41bbb-114">See [Grant read definition permissions on object metadata &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) for details.</span></span>  
  
## <a name="set-processing-permissions-at-the-database-level"></a><span data-ttu-id="41bbb-115">データベース レベルでの処理権限の設定</span><span class="sxs-lookup"><span data-stu-id="41bbb-115">Set processing permissions at the database level</span></span>  
 <span data-ttu-id="41bbb-116">ここでは、管理者以外のユーザーがデータベース内のすべてのキューブ、ディメンション、マイニング構造、およびマイニング モデルを処理できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-116">This section explains how to enable processing by non-administrators, for all cubes, dimensions, mining structures, and mining models in the database.</span></span>  
  
1.  <span data-ttu-id="41bbb-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="41bbb-118">[**ロール**] [  |  **新しいロール**] を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-118">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="41bbb-119">名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-119">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="41bbb-120">**[全般**] ペインで、チェックボックスをオンにし `Process Database` ます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-120">In the **General** pane, select the `Process Database` check box.</span></span> <span data-ttu-id="41bbb-121">また、などの `Read Definition` SQL Server ツールのいずれかを使用して対話型の処理を有効にすることもでき [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-121">Additionally, select `Read Definition` to also enable interactive processing through one of the SQL Server tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
4.  <span data-ttu-id="41bbb-122">**[メンバーシップ]** ペインで、このデータベースのすべてのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-122">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="41bbb-123">**[OK]** をクリックすると、ロール定義が完了します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-123">Click **OK** to complete the role definition.</span></span>  
  
## <a name="set-processing-permissions-on-individual-objects"></a><span data-ttu-id="41bbb-124">個々のオブジェクトに対する処理権限の設定</span><span class="sxs-lookup"><span data-stu-id="41bbb-124">Set processing permissions on individual objects</span></span>  
 <span data-ttu-id="41bbb-125">個々のキューブ、ディメンション、データ マイニング構造、またはデータ マイニング モデルに対する処理権限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-125">You can set processing permissions on individual cubes, dimensions, data mining structures or models.</span></span>  
  
 <span data-ttu-id="41bbb-126">一緒に処理する必要があるオブジェクトを誤って除外した場合は、処理が失敗することがあります (たとえば、キューブに対する処理は有効にしたものの、その関連するディメンションに対する処理は有効にしなかった場合)。</span><span class="sxs-lookup"><span data-stu-id="41bbb-126">Processing can fail if you inadvertently exclude objects that need to be processed together (for example, if you enable processing on a cube, but not on its related dimensions).</span></span> <span data-ttu-id="41bbb-127">オブジェクトの依存関係は見落とされやすいため、個々のオブジェクトに対する処理権限を設定するときには、徹底的にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="41bbb-127">Because it can be easy to miss object dependencies, thorough testing is essential when setting processing permissions on individual objects.</span></span>  
  
1.  <span data-ttu-id="41bbb-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="41bbb-129">[**ロール**] [  |  **新しいロール**] を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-129">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="41bbb-130">名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-130">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="41bbb-131">**[全般**] ペインで、チェックボックスをオフにし `Process Database` ます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-131">In the **General** pane, clear the `Process Database` check box.</span></span> <span data-ttu-id="41bbb-132">データベース権限によって、ロールのオプションがグレー表示されるか選択不可になることで、下位レベルのオブジェクトに対する権限の設定機能がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-132">Database permissions override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
     <span data-ttu-id="41bbb-133">技術的には、専用の処理ロール用にデータベース権限は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="41bbb-133">Technically, no database permissions are needed for dedicated processing roles.</span></span> <span data-ttu-id="41bbb-134">ただし、 `Read Definition` データベースレベルでは、でデータベースを表示することはできない [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ため、テストが困難になります。</span><span class="sxs-lookup"><span data-stu-id="41bbb-134">But without `Read Definition` at the database level, you cannot view the database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], making testing more difficult.</span></span>  
  
4.  <span data-ttu-id="41bbb-135">処理する個々のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-135">Select individual objects to process:</span></span>  
  
    -   <span data-ttu-id="41bbb-136">**[キューブ]** ペインで、各キューブの **[処理]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-136">In the **Cubes** pane, select the **Process** check box for each cube.</span></span>  
  
    -   <span data-ttu-id="41bbb-137">**[ディメンション]** ペインで、 **[すべてのデータベース ディメンション]** を選択し、各ディメンションの **[処理]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-137">In the **Dimensions** pane, select **All database dimensions**, and then **Process** check box for each dimension.</span></span> <span data-ttu-id="41bbb-138">あるいは、すべての行を選択し、シフトクリックを使用してチェック ボックスの選択を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-138">Or, select all rows, then use shift-click to toggle the check box selections.</span></span>  
  
5.  <span data-ttu-id="41bbb-139">**[メンバーシップ]** ペインで、これらのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-139">In the **Membership** pane, add the Windows user and group accounts having permission to process these objects.</span></span>  
  
6.  <span data-ttu-id="41bbb-140">**[OK]** をクリックすると、ロール定義が完了します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-140">Click **OK** to complete the role definition.</span></span>  
  
## <a name="test-processing"></a><span data-ttu-id="41bbb-141">処理のテスト</span><span class="sxs-lookup"><span data-stu-id="41bbb-141">Test processing</span></span>  
  
1.  <span data-ttu-id="41bbb-142">Shift キーを押したまま [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を右クリックし、 **[別のユーザーとして実行する]** を選択し、テスト対象のロールに割り当てられた Windows アカウントを使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-142">Hold down the shift-key and right-click [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select **Run as a different user** and connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using a Windows account assigned to the role you are testing.</span></span>  
  
2.  <span data-ttu-id="41bbb-143">[データベース] フォルダーを開き、データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-143">Open the Databases folder, and select a database.</span></span> <span data-ttu-id="41bbb-144">アカウントにメンバーシップが付与されているロールで表示可能なデータベースのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-144">You will only see the databases that are visible to the roles for which your account has membership.</span></span>  
  
3.  <span data-ttu-id="41bbb-145">キューブまたはディメンションを右クリックし、 **[処理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-145">Right-click a cube or dimension and select **Process**.</span></span> <span data-ttu-id="41bbb-146">処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-146">Choose a processing option.</span></span> <span data-ttu-id="41bbb-147">オブジェクトのすべての組み合わせについて、すべてのオプションをテストします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-147">Test all of the options, for all combinations of objects.</span></span> <span data-ttu-id="41bbb-148">オブジェクトが見つからないためにエラーが発生した場合は、そのオブジェクトをロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-148">If errors occur due to missing objects, add the objects to the role.</span></span>  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a><span data-ttu-id="41bbb-149">データ マイニング構造に対する処理権限の設定</span><span class="sxs-lookup"><span data-stu-id="41bbb-149">Set processing permissions on a data mining structure</span></span>  
 <span data-ttu-id="41bbb-150">データ マイニング構造を処理するための権限を付与するロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-150">You can create a role granting permission to process data mining structures.</span></span> <span data-ttu-id="41bbb-151">これには、すべてのマイニング モデルの処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-151">This includes the processing of all mining models.</span></span>  
  
 <span data-ttu-id="41bbb-152">**Drill Through** `Read Definition` マイニングモデルとマイニング構造の参照に使用されるドリルスルーと権限はアトミックであり、同じロールに追加することも、別のロールに分割することもできます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-152">**Drill Through** and `Read Definition` permissions used for browsing a mining model and structure are atomic and can be added to the same role, or separated out into a different role.</span></span>  
  
1.  <span data-ttu-id="41bbb-153">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、[データベース] フォルダーを開いてデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-153">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="41bbb-154">[**ロール**] [  |  **新しいロール**] を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-154">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="41bbb-155">名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-155">Enter a name and description.</span></span> <span data-ttu-id="41bbb-156">**[全般]** ペインで、データベース権限のチェック ボックスがオフであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-156">In the **General** pane, make sure that the database permission check boxes are clear.</span></span> <span data-ttu-id="41bbb-157">データベース権限によって、ロールのオプションがグレー表示されるか選択不可になることで、下位レベルのオブジェクトに対する権限の設定機能がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="41bbb-157">Database permissions will override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
3.  <span data-ttu-id="41bbb-158">**[マイニング構造]** ペインで、各マイニング構造の **[処理]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="41bbb-158">In the **Mining Structures** pane, select the **Process** check box for each mining structure.</span></span>  
  
4.  <span data-ttu-id="41bbb-159">**[メンバーシップ]** ペインで、このデータベースのすべてのオブジェクトを処理する権限のある Windows ユーザー アカウントおよびグループ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-159">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="41bbb-160">**[OK]** をクリックすると、ロール定義が完了します。</span><span class="sxs-lookup"><span data-stu-id="41bbb-160">Click **OK** to complete the role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bbb-161">参照</span><span class="sxs-lookup"><span data-stu-id="41bbb-161">See Also</span></span>  
 <span data-ttu-id="41bbb-162">[データベース、テーブル、またはパーティションの処理](../tabular-models/process-database-table-or-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="41bbb-162">[Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) </span></span>  
 <span data-ttu-id="41bbb-163">[多次元モデルオブジェクトの処理](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="41bbb-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="41bbb-164">[Analysis Services &#40;データベースのアクセス許可を付与&#41;](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="41bbb-164">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="41bbb-165">オブジェクト メタデータに対する定義の読み取り権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="41bbb-165">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  
