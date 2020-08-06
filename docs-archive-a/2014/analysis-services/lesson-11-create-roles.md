---
title: 'レッスン 12: ロールの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 962cd19726a5404de81e20a2209b25b9cc277e21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631295"
---
# <a name="lesson-12-create-roles"></a><span data-ttu-id="77831-102">レッスン 12:ロールの作成</span><span class="sxs-lookup"><span data-stu-id="77831-102">Lesson 12: Create Roles</span></span>
  <span data-ttu-id="77831-103">このレッスンでは、ロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="77831-103">In this lesson, you will create roles.</span></span> <span data-ttu-id="77831-104">ロールを使用すると、ロール メンバーである Windows ユーザーのみにアクセスを制限することで、モデル データベース オブジェクトとデータにセキュリティを提供できます。</span><span class="sxs-lookup"><span data-stu-id="77831-104">Roles provide model database object and data security by limiting access to only those Windows users which are role members.</span></span> <span data-ttu-id="77831-105">各ロールには､1 つの許可 (なし､読み取り､読み取りと処理､処理､管理者のいずれか) のみ定義します｡</span><span class="sxs-lookup"><span data-stu-id="77831-105">Each role is defined with a single permission: None, Read, Read and Process, Process, or Administrator.</span></span> <span data-ttu-id="77831-106">モデルのロールは、モデルの作成時に [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の [ロール マネージャー] ダイアログ ボックスを使用して定義できます。</span><span class="sxs-lookup"><span data-stu-id="77831-106">Roles can be defined during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="77831-107">モデルを配置した後は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用してロールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="77831-107">After a model has been deployed, you can manage roles by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="77831-108">詳細については、「[ロール (SSAS テーブル)](tabular-models/roles-ssas-tabular.md)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77831-108">To learn more, see [Roles &#40;SSAS Tabular&#41;](tabular-models/roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77831-109">このチュートリアルでは､ロールの作成は必須のレッスンではありません｡</span><span class="sxs-lookup"><span data-stu-id="77831-109">Creating roles is not necessary to complete this tutorial.</span></span> <span data-ttu-id="77831-110">既定では､現在のログインに使用したアカウントがモデルの管理者権限を保有します｡</span><span class="sxs-lookup"><span data-stu-id="77831-110">By default, the account you are currently logged in with will have Administrator privileges on the model.</span></span> <span data-ttu-id="77831-111">ただし、組織内の他のユーザーがレポート クライアント アプリケーションを使用してモデルを参照できるようにするには、読み取り権限を持ったロールを少なくとも 1 つ作成し、それらのユーザーをメンバーとして追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77831-111">However, to allow other users in your organization to browse the model by using a reporting client application, you must create at least one role with Read permissions and add those users as members.</span></span>  
  
 <span data-ttu-id="77831-112">3 つのルールを作成します｡</span><span class="sxs-lookup"><span data-stu-id="77831-112">You will create three roles:</span></span>  
  
-   <span data-ttu-id="77831-113">Sales Manager-このロールには、すべてのモデルオブジェクトとデータに対する読み取り権限を付与する組織内のユーザーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="77831-113">Sales Manager - This role can include users in your organization for which you want to have Read permission to all model objects and data.</span></span>  
  
-   <span data-ttu-id="77831-114">販売アナリストの米国-このロールには、米国での売上に関連するデータのみを参照できるようにする組織内のユーザーを含めることができます (米国)。</span><span class="sxs-lookup"><span data-stu-id="77831-114">Sales Analyst US - This role can include users in your organization for which you want only to be able to browse data related to sales in the US (United States).</span></span> <span data-ttu-id="77831-115">このロールに対しては、DAX 式を使用して *行フィルター*を定義することにより、メンバーが米国のデータのみを参照できるように制限します。</span><span class="sxs-lookup"><span data-stu-id="77831-115">For this role, you will use a DAX formula to define a *Row Filter*, which restricts members to browse data only for the United States.</span></span>  
  
-   <span data-ttu-id="77831-116">管理者-このロールには、管理者権限を付与するユーザーを含めることができます。これにより、モデルデータベースに対する管理タスクを実行するための無制限のアクセス権と権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="77831-116">Administrator - This role can include users for which you want to have Administrator permission, which allows unlimited access and permissions to perform administrative tasks on the model database.</span></span>  
  
 <span data-ttu-id="77831-117">社内の Windows ユーザー アカウントとグループ アカウントは一意であるため､特定のアカウントをメンバーに追加できます｡</span><span class="sxs-lookup"><span data-stu-id="77831-117">Because Windows user and group accounts in your organization are unique, you can add accounts from your particular organization to members.</span></span> <span data-ttu-id="77831-118">しかし、このチュートリアルでは、メンバーを空白のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="77831-118">However, for this tutorial, you can also leave the members blank.</span></span> <span data-ttu-id="77831-119">各ロールの影響は、後の「レッスン 12: Excel での分析」でもテストできます。</span><span class="sxs-lookup"><span data-stu-id="77831-119">You will still be able to test the effect of each role later in Lesson 12: Analyze in Excel.</span></span>  
  
 <span data-ttu-id="77831-120">このレッスンの推定所要時間: **15 分**</span><span class="sxs-lookup"><span data-stu-id="77831-120">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="77831-121">前提条件</span><span class="sxs-lookup"><span data-stu-id="77831-121">Prerequisites</span></span>  
 <span data-ttu-id="77831-122">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77831-122">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="77831-123">このレッスンの実習を行う前に、前のレッスン「 [レッスン 11: パーティションの作成](lesson-10-create-partitions.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="77831-123">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="create-roles"></a><span data-ttu-id="77831-124">ロールの作成</span><span class="sxs-lookup"><span data-stu-id="77831-124">Create Roles</span></span>  
  
#### <a name="to-create-a-sales-manager-user-role"></a><span data-ttu-id="77831-125">Sales Manager ユーザー ロールを作成する</span><span class="sxs-lookup"><span data-stu-id="77831-125">To create a Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="77831-126">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="77831-127">**[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-127">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="77831-128">"なし" 権限を設定された新しいロールがリストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77831-128">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="77831-129">新しいロールをクリックし、[**名前**] 列でロールの名前をに変更し `Internet Sales Manager` ます。</span><span class="sxs-lookup"><span data-stu-id="77831-129">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Manager`.</span></span>  
  
4.  <span data-ttu-id="77831-130">**[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。</span><span class="sxs-lookup"><span data-stu-id="77831-130">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="77831-131">任意: **[メンバー]** タブをクリックし、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-131">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="77831-132">**Select Users また Groups** ダイアログ ボックスでこのロールに含める社内 Windows ユーザーまたはグループを入力します｡</span><span class="sxs-lookup"><span data-stu-id="77831-132">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
7.  <span data-ttu-id="77831-133">選択内容を確認し、[ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-133">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a><span data-ttu-id="77831-134">Sales Analyst US ユーザー ロールを作成する</span><span class="sxs-lookup"><span data-stu-id="77831-134">To create a Sales Analyst US user role</span></span>  
  
1.  <span data-ttu-id="77831-135">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="77831-136">**[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-136">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="77831-137">"なし" 権限を設定された新しいロールがリストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77831-137">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="77831-138">新しいロールをクリックし、[**名前**] 列でロールの名前をに変更し `Internet Sales US` ます。</span><span class="sxs-lookup"><span data-stu-id="77831-138">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales US`.</span></span>  
  
4.  <span data-ttu-id="77831-139">**[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。</span><span class="sxs-lookup"><span data-stu-id="77831-139">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="77831-140">行フィルターをクリックし、 **Geography** テーブルに対してのみ、[DAX フィルター] 列に次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="77831-140">Click on the Row Filters tab, and then for the **Geography** table only, in the DAX Filter column, type the following formula:</span></span>  
  
     `=Geography[Country Region Code] = "US"`  
  
     <span data-ttu-id="77831-141">Row Filter 式の結果は ブール値 (真/偽) をとる必要があります｡</span><span class="sxs-lookup"><span data-stu-id="77831-141">A Row Filter formula must resolve to a Boolean (TRUE/FALSE) value.</span></span> <span data-ttu-id="77831-142">この数式では、国の地域コード値が "US" である行のみがユーザーに表示されるように指定しています。</span><span class="sxs-lookup"><span data-stu-id="77831-142">With this formula, you are specifying that only rows with the Country Region Code value of "US" be visible to the user.</span></span>  
  
     <span data-ttu-id="77831-143">数式の入力が終了したら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="77831-143">When you have finished building the formula, press ENTER.</span></span>  
  
6.  <span data-ttu-id="77831-144">任意: **[メンバー]** タブをクリックし、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-144">Optional: Click on the **Members** tab, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="77831-145">**Select Users また Groups** ダイアログ ボックスでこのロールに含める社内 Windows ユーザーまたはグループを入力します｡</span><span class="sxs-lookup"><span data-stu-id="77831-145">In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
8.  <span data-ttu-id="77831-146">選択内容を確認し、[ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-146">Verify your selections, and then click **OK**</span></span>  
  
#### <a name="to-create-an-administrator-role"></a><span data-ttu-id="77831-147">Administrator ロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="77831-147">To create an Administrator role</span></span>  
  
1.  <span data-ttu-id="77831-148">**[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-148">In the **Role Manager** dialog box, click **New**.</span></span>  
  
2.  <span data-ttu-id="77831-149">新しいロールをクリックし、[**名前**] 列でロールの名前をに変更し `Internet Sales Administrator` ます。</span><span class="sxs-lookup"><span data-stu-id="77831-149">Click on the new role, and then in the **Name** column, rename the role to `Internet Sales Administrator`.</span></span>  
  
3.  <span data-ttu-id="77831-150">**[権限]** 列で、ドロップダウン リストをクリックし、 **[管理者]** 権限を選択します。</span><span class="sxs-lookup"><span data-stu-id="77831-150">In the **Permissions** column, click the dropdown list, and then select the **Administrator** permission.</span></span>  
  
4.  <span data-ttu-id="77831-151">**[メンバー]** タブをクリックし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-151">Click on the **Members** tab, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="77831-152">(省略可能) **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。</span><span class="sxs-lookup"><span data-stu-id="77831-152">Optional: In the **Select Users or Groups** dialog box, enter the Windows users or groups from your organization you want to include in the role.</span></span>  
  
6.  <span data-ttu-id="77831-153">選択内容を確認し、[ **OK** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="77831-153">Verify your selections, and then click **OK**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="77831-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="77831-154">Next Steps</span></span>  
 <span data-ttu-id="77831-155">このチュートリアルを続行するには、次のレッスン「 [レッスン 13: Excel での分析](lesson-12-analyze-in-excel.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="77831-155">To continue this tutorial, go to the next lesson: Lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
  
