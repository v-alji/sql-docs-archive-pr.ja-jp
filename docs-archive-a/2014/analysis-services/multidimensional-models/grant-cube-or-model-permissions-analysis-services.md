---
title: キューブ権限またはモデル権限の付与 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.cubes.f1
helpviewer_keywords:
- user access rights [Analysis Services], cubes
- cubes [Analysis Services], security
- read/write permissions
- permissions [Analysis Services], cubes
ms.assetid: 55b1456e-2f6b-4101-b316-c926f40304e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 23e0c5d6c6e70a4ee563ec47562629dd58b0f146
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711114"
---
# <a name="grant-cube-or-model-permissions-analysis-services"></a><span data-ttu-id="a211d-102">キューブ権限またはモデル権限の付与 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a211d-102">Grant cube or model permissions (Analysis Services)</span></span>
  <span data-ttu-id="a211d-103">キューブまたは表形式モデルは、Analysis Services データ モデルの主要なクエリ オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a211d-103">A cube or tabular model is the primary query object in an Analysis Services data model.</span></span> <span data-ttu-id="a211d-104">アドホック データ探索のために Excel から多次元データまたは表形式データに接続する場合、ユーザーは、通常、最初に、ピボット レポート オブジェクトの基礎となるデータ構造として、特定のキューブまたは表形式モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a211d-104">When connecting to multidimensional or tabular data from Excel for ad hoc data exploration, users typically start by selecting a specific cube or tabular model as the data structure behind the Pivot report object.</span></span> <span data-ttu-id="a211d-105">このトピックでは、キューブまたは表形式データへのアクセスに必要な権限を付与する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a211d-105">This topic explains how to grant the necessary permissions for cube or tabular data access.</span></span>  
  
 <span data-ttu-id="a211d-106">既定では、サーバー管理者とデータベース管理者を除いて、データベースのクエリ キューブに対する権限を持ちません。</span><span class="sxs-lookup"><span data-stu-id="a211d-106">By default, no one except a Server Administrator or Database Administrator has permission to query cubes in a database.</span></span> <span data-ttu-id="a211d-107">管理者以外がキューブにアクセスするには、キューブが含まれているデータベースのために作成されたロールでのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="a211d-107">Cube access by a non-administrator requires membership in a role created for the database containing the cube.</span></span> <span data-ttu-id="a211d-108">メンバーシップは、Active Directory またはローカル コンピューターに定義された、Windows ユーザー アカウントまたはグループ アカウントに対してサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a211d-108">Membership is supported for Windows user or group accounts, defined in either Active Directory or on the local computer.</span></span> <span data-ttu-id="a211d-109">開始する前に、作成するロールではどのアカウントにメンバーシップが割り当てられるかを判別します。</span><span class="sxs-lookup"><span data-stu-id="a211d-109">Before you start, identify which accounts will be assigned membership in the roles you are about to create.</span></span>  
  
 <span data-ttu-id="a211d-110">キューブへの `Read` アクセス権には、そのキューブ内のディメンション、メジャー グループ、およびパースペクティブに対する権限も付属します。</span><span class="sxs-lookup"><span data-stu-id="a211d-110">Having `Read` access to a cube also conveys permissions on the dimensions, measure groups, and perspectives within it.</span></span> <span data-ttu-id="a211d-111">ほとんどの管理者は、キューブ レベルで Read 権限を付与し、特定のオブジェクト、関連するデータ、またはユーザー ID に対する権限を制限します。</span><span class="sxs-lookup"><span data-stu-id="a211d-111">Most administrators will grant read permissions at the cube level and then restrict permissions on specific objects, on associated data, or by user identity.</span></span>  
  
 <span data-ttu-id="a211d-112">後続のソリューション配置でもロール定義を保持するには、モデルの不可欠な要素として [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] にロールを定義し、データベースがパブリッシュされた後、データベース管理者が [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にロール メンバーシップを割り当てることがベスト プラクティスとなります。</span><span class="sxs-lookup"><span data-stu-id="a211d-112">To preserve role definitions over successive solution deployments, a best practice is to define roles in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] as an integral part of the model, and then have a database administrator assign role memberships in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] after the database is published.</span></span> <span data-ttu-id="a211d-113">ただし、どちらのツールも両方のタスクに使用できます。</span><span class="sxs-lookup"><span data-stu-id="a211d-113">But you can use either tool for both tasks.</span></span> <span data-ttu-id="a211d-114">手順を簡素化するため、ロール定義とメンバーシップの両方に [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="a211d-114">To simplify the exercise, we'll use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] for both role definition and membership.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a211d-115">サーバー管理者、またはフル コントロール権限を持つデータベース管理者のみが、ソース ファイルからサーバーへのキューブの配置や、ロールの作成とメンバーへの割り当てを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a211d-115">Only server administrators, or database administrators having Full Control permissions, can deploy a cube from source files to a server, or create roles and assign members.</span></span> <span data-ttu-id="a211d-116">これらの権限レベルの詳細については、「 [Analysis Services&#41;&#40;サーバー管理者権限を付与](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md)する」および「 [Analysis Services&#41;にデータベース &#40;権限を付与](grant-database-permissions-analysis-services.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a211d-116">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) and [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for details about these permission levels.</span></span>  
  
#### <a name="step-1-create-the-role"></a><span data-ttu-id="a211d-117">手順 1: ロールの作成</span><span class="sxs-lookup"><span data-stu-id="a211d-117">Step 1: Create the role</span></span>  
  
1.  <span data-ttu-id="a211d-118">SSMS で、Analysis Services に接続します。</span><span class="sxs-lookup"><span data-stu-id="a211d-118">In SSMS, connect to Analysis Services.</span></span> <span data-ttu-id="a211d-119">この手順について不明な点がある場合は、「[クライアント アプリケーションからの接続 (Analysis Services)](../instances/connect-from-client-applications-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-119">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with this step.</span></span>  
  
2.  <span data-ttu-id="a211d-120">オブジェクト エクスプローラーで **[データベース]** フォルダーを開き、データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="a211d-120">Open the **Databases** folder in Object Explorer, and select a database.</span></span>  
  
3.  <span data-ttu-id="a211d-121">**[ロール]** を右クリックし、 **[新しいロール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a211d-121">Right-click **Roles** and choose **New Role**.</span></span> <span data-ttu-id="a211d-122">ロールがデータベース レベルで作成され、データベース内のオブジェクトに適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a211d-122">Notice that roles are created at the database level and apply to objects within it.</span></span> <span data-ttu-id="a211d-123">データベース間でロールを共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="a211d-123">You cannot share roles across databases.</span></span>  
  
4.  <span data-ttu-id="a211d-124">**[全般]** ペインで、名前を入力し、必要に応じて説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="a211d-124">In the **General** pane, enter a name, and optionally, a description.</span></span> <span data-ttu-id="a211d-125">また、このペインには、フル コントロール、データベースの処理、定義の読み取りなど、いくつかのデータベース権限も含まれています。</span><span class="sxs-lookup"><span data-stu-id="a211d-125">This pane also contains several database permissions, such as Full Control, Process Database, and Read Definition.</span></span> <span data-ttu-id="a211d-126">これらのいずれの権限も、キューブまたは表形式モデルに対するクエリの実行には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a211d-126">None of these permissions are needed for querying a cube or tabular model.</span></span> <span data-ttu-id="a211d-127">これらの権限の詳細については、「[データベース権限の付与 (Analysis Services)](grant-database-permissions-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-127">See [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for more information about these permissions.</span></span>  
  
5.  <span data-ttu-id="a211d-128">名前および必要に応じて説明を入力した後、次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="a211d-128">Continue to the next step after entering a name and optional description.</span></span>  
  
#### <a name="step-2-assign-membership"></a><span data-ttu-id="a211d-129">手順 2: メンバーシップの割り当て</span><span class="sxs-lookup"><span data-stu-id="a211d-129">Step 2: Assign Membership</span></span>  
  
1.  <span data-ttu-id="a211d-130">**[メンバーシップ]** ペインで、 **[追加]** をクリックして、このロールを使用してキューブにアクセスする Windows ユーザー アカウントまたはグループ アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="a211d-130">In the **Membership** pane, click **Add** to enter the Windows user or group accounts that will be accessing the cube using this role.</span></span> <span data-ttu-id="a211d-131">Analysis Services では、Windows セキュリティ ID のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a211d-131">Analysis Services only supports Windows security identities.</span></span> <span data-ttu-id="a211d-132">この手順ではデータベース ログインを作成しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a211d-132">Notice that you are not creating database logins in this step.</span></span> <span data-ttu-id="a211d-133">Analysis Services では、ユーザーは Windows アカウントで接続します。</span><span class="sxs-lookup"><span data-stu-id="a211d-133">In Analysis Services, users connect through Windows accounts.</span></span>  
  
2.  <span data-ttu-id="a211d-134">次の手順に進み、キューブ権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="a211d-134">Continue to the next step, setting cube permissions.</span></span>  
  
     <span data-ttu-id="a211d-135">データ ソース ペインをスキップしていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a211d-135">Notice that we are skipping the Data Source pane.</span></span> <span data-ttu-id="a211d-136">Analysis Services データの通常のコンシューマーのほとんどには、データ ソース オブジェクトに対する権限は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a211d-136">Most regular consumers of Analysis Services data do not need permissions on the data source object.</span></span> <span data-ttu-id="a211d-137">これらの権限レベルの詳細については、「 [データ ソース オブジェクトに対する権限の付与 (Analysis Services)](grant-permissions-on-a-data-source-object-analysis-services.md) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-137">See [Grant permissions on a data source object &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) for details on when you might set this permission.</span></span>  
  
#### <a name="step-3-set-cube-permissions"></a><span data-ttu-id="a211d-138">手順 3: キューブ権限の設定</span><span class="sxs-lookup"><span data-stu-id="a211d-138">Step 3: Set Cube Permissions</span></span>  
  
1.  <span data-ttu-id="a211d-139">[**キューブ**] ペインで、キューブを選択し、[ `Read` または**読み取り/書き込み**アクセス] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a211d-139">In the **Cubes** pane, select a cube, and then click `Read` or **Read/Write** access.</span></span>  
  
     <span data-ttu-id="a211d-140">`Read`ほとんどの操作にはアクセスが十分です。</span><span class="sxs-lookup"><span data-stu-id="a211d-140">`Read` access is sufficient for most operations.</span></span> <span data-ttu-id="a211d-141">**[読み取り/書き込み]** は、処理ではなく書き戻しにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="a211d-141">**Read/Write** is used only for writeback, not processing.</span></span> <span data-ttu-id="a211d-142">この機能の詳細については、「 [パーティションの書き戻しの設定](set-partition-writeback.md) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-142">See [Set Partition Writeback](set-partition-writeback.md) for more information about this capability.</span></span>  
  
     <span data-ttu-id="a211d-143">複数のキューブのほか、[ロールの作成] ダイアログ ボックスで使用可能なその他のオブジェクトも選択できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a211d-143">Notice that you can select multiple cubes, as well as other objects available in the Create Role dialog box.</span></span> <span data-ttu-id="a211d-144">キューブに対する権限を付与すると、そのキューブに関連付けられたディメンションおよびパースペクティブへのアクセスが承認されます。</span><span class="sxs-lookup"><span data-stu-id="a211d-144">Granting permissions to a cube authorizes access to the dimensions and perspectives associated with the cube.</span></span> <span data-ttu-id="a211d-145">キューブに既に表されているオブジェクトを手動で追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a211d-145">It's not necessary to manually add objects already represented in the cube.</span></span>  
  
     <span data-ttu-id="a211d-146">特定のメジャーを使用できないようにするなどの目的で、オブジェクトまたはユーザーによって承認方法を変化させる必要がある場合、特定のオブジェクトやセルに対するアクセスをアトミックに許可または拒否できます。</span><span class="sxs-lookup"><span data-stu-id="a211d-146">If you need to vary authorization by objects or user, for example to make certain measures unavailable, you can allow or deny access atomically on specific objects, even on cells.</span></span> <span data-ttu-id="a211d-147">詳細については、「[ディメンション データへのカスタム アクセス権の付与 (Analysis Services)](grant-custom-access-to-dimension-data-analysis-services.md)」および「[セル データへのカスタム アクセス権の付与 (Analysis Services)](grant-custom-access-to-cell-data-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-147">See [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) and [Grant custom access to cell data &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md) for details.</span></span>  
  
2.  <span data-ttu-id="a211d-148">この時点で **[OK]** をクリックすると、このロールのすべてのメンバーが、指定した権限レベルでキューブにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a211d-148">At this point, after you click **OK**, all members of this role have access to the cubes, at the permission levels you specified.</span></span>  
  
     <span data-ttu-id="a211d-149">**[キューブ]** ペインでは、 **[ドリルスルーとローカル キューブ]** を使用してサーバー キューブからローカル キューブを作成するための権限をユーザーに付与したり、 **[ドリルスルー]** 権限を使用してドリルスルーのみを許可したりできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a211d-149">Notice that on the **Cubes** pane, you can grant users permission to create local cubes from a server cube via **Drillthrough and Local Cube**, or allow drillthrough only, via the **Drillthrough** permission.</span></span>  
  
     <span data-ttu-id="a211d-150">さらに、このペインでは、キューブに対する **[データベースの処理]** 権限を付与して、このロールのすべてのメンバーがこのキューブのデータを処理できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a211d-150">Finally, this pane lets you grant **Process Database** rights on the cube to give all members of this role the ability to process data for this cube.</span></span> <span data-ttu-id="a211d-151">処理は通常制限付きの操作であるため、そのタスクを管理者に委ねるか、または特にそのタスク用に別途ロールを定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a211d-151">Because processing is typically a restricted operation, we recommend that you leave that task to the administrators, or define separate roles specifically for that task.</span></span> <span data-ttu-id="a211d-152">処理権限のベスト プラクティスの詳細については、「[処理権限の付与 (Analysis Services)](grant-process-permissions-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-152">See [Grant process permissions &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) for more information about processing permission best practices.</span></span>  
  
#### <a name="step-4-test"></a><span data-ttu-id="a211d-153">手順 4: テスト</span><span class="sxs-lookup"><span data-stu-id="a211d-153">Step 4: Test</span></span>  
  
1.  <span data-ttu-id="a211d-154">Excel を使用して、キューブのアクセス権をテストします。</span><span class="sxs-lookup"><span data-stu-id="a211d-154">Use Excel to test cube access permissions.</span></span> <span data-ttu-id="a211d-155">また、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用すると、次に説明するのと同じ方法に従って、管理者以外のユーザーとしてアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a211d-155">You can also use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], following the same technique described next ─ running the application as a non-administrator user.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a211d-156">Analysis Services 管理者の場合、管理者権限がより権限の小さいロールと結合されるため、個別にロール権限をテストするのが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="a211d-156">If you are an Analysis Services administrator, administrator permissions will be combined with roles having lesser permissions, making it difficult to test role permissions in isolation.</span></span> <span data-ttu-id="a211d-157">テストを簡素化するため、テスト対象のロールに割り当てられたアカウントを使用して、SSMS の 2 番目のインスタンスを開くことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a211d-157">To simplify testing, we suggest that you open a second instance of SSMS, using the account assigned to the role you are testing.</span></span>  
  
2.  <span data-ttu-id="a211d-158">Shift キーを押したまま **[Excel]** を右クリックして、 **[別のユーザーとして実行]** オプションにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a211d-158">Hold-down the Shift key and right-click the **Excel** shortcut to access the **Run as different user** option.</span></span> <span data-ttu-id="a211d-159">このロールにメンバーシップがある Windows ユーザー アカウントまたはグループ アカウントの 1 つを入力します。</span><span class="sxs-lookup"><span data-stu-id="a211d-159">Enter one of the Windows user or group accounts having membership in this role.</span></span>  
  
3.  <span data-ttu-id="a211d-160">Excel が開いたら、[データ] タブを使用して Analysis Services に接続します。</span><span class="sxs-lookup"><span data-stu-id="a211d-160">When Excel opens, use the Data tab to connect to Analysis Services.</span></span> <span data-ttu-id="a211d-161">別の Windows ユーザーとして Excel を実行しているため、ロールをテストする際には **[Windows 認証を使用する]** オプションが適切な資格情報の種類です。</span><span class="sxs-lookup"><span data-stu-id="a211d-161">Because you are running Excel as a different Windows user, the **Use Windows Authentication** option is the right credential type to use when testing roles.</span></span> <span data-ttu-id="a211d-162">この手順について不明な点がある場合は、「[クライアント アプリケーションからの接続 (Analysis Services)](../instances/connect-from-client-applications-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-162">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with this step.</span></span>  
  
     <span data-ttu-id="a211d-163">接続に関するエラーが表示された場合は、Analysis Services のポート構成を確認し、サーバーがリモート接続に対応していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a211d-163">If you get errors on the connection, check the port configuration for Analysis Services and verify that the server accepts remote connections.</span></span> <span data-ttu-id="a211d-164">ポートの構成については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-164">See [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) for port configuration.</span></span>  
  
#### <a name="step-5-script-role-definition-and-assignments"></a><span data-ttu-id="a211d-165">手順 5: スクリプト ロールの定義と割り当て</span><span class="sxs-lookup"><span data-stu-id="a211d-165">Step 5: Script role definition and assignments</span></span>  
  
1.  <span data-ttu-id="a211d-166">最後の手順として、作成したロール定義をキャプチャするスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="a211d-166">As a final step, you should generate a script that captures the role definition you just created.</span></span>  
  
     <span data-ttu-id="a211d-167">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] からプロジェクトを再配置すると、プロジェクト内に定義されていないロールまたはロール メンバーシップが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="a211d-167">Redeploying a project from [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite any roles or role memberships that are not defined inside the project.</span></span> <span data-ttu-id="a211d-168">再配置後にロールおよびロール メンバーシップを最も速く再構築する方法は、スクリプトを使用することです。</span><span class="sxs-lookup"><span data-stu-id="a211d-168">The quickest way to rebuild roles and role membership after redeployment is through script.</span></span>  
  
2.  <span data-ttu-id="a211d-169">SSMS で、 **[ロール]** フォルダーに移動し、既存のロールを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="a211d-169">In SSMS, navigate to the **Roles** folder and right-click an existing role.</span></span>  
  
3.  <span data-ttu-id="a211d-170">CREATE TO file**として [スクリプトロール**] を選択し  |  **CREATE TO**  |  **file**ます。</span><span class="sxs-lookup"><span data-stu-id="a211d-170">Select **Script Role as** | **CREATE TO** | **file**.</span></span>  
  
4.  <span data-ttu-id="a211d-171">拡張子を .xmla にしてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="a211d-171">Save the file with an .xmla file extension.</span></span> <span data-ttu-id="a211d-172">スクリプトをテストするには、現在のロールを削除し、SSMS でファイルを開き、F5 キーを押してスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a211d-172">To test the script, delete the current role, open the file in SSMS, and press F5 to execute the script.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a211d-173">次のステップ</span><span class="sxs-lookup"><span data-stu-id="a211d-173">Next step</span></span>  
 <span data-ttu-id="a211d-174">セルまたはディメンション データへのアクセスを制限するようにキューブ権限を調整できます。</span><span class="sxs-lookup"><span data-stu-id="a211d-174">You can refine cube permissions to restrict access to cell or dimension data.</span></span> <span data-ttu-id="a211d-175">詳細については、「[ディメンション データへのカスタム アクセス権の付与 (Analysis Services)](grant-custom-access-to-dimension-data-analysis-services.md)」および「[セル データへのカスタム アクセス権の付与 (Analysis Services)](grant-custom-access-to-cell-data-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a211d-175">See [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) and [Grant custom access to cell data &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a211d-176">参照</span><span class="sxs-lookup"><span data-stu-id="a211d-176">See Also</span></span>  
 <span data-ttu-id="a211d-177">[Analysis Services によってサポートされる認証方法](../instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a211d-177">[Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="a211d-178">[データマイニング構造およびデータマイニングモデルに対する権限の許可 &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a211d-178">[Grant permissions on data mining structures and models &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md) </span></span>  
 [<span data-ttu-id="a211d-179">データ ソース オブジェクトに対する権限の付与 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a211d-179">Grant permissions on a data source object &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
  