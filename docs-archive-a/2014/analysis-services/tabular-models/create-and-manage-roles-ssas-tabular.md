---
title: ロールの作成と管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 335e0e311d97ea452449cd0c5d6550f6dbcca4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632753"
---
# <a name="create-and-manage-roles-ssas-tabular"></a><span data-ttu-id="45197-102">ロールの作成および管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="45197-102">Create and Manage Roles (SSAS Tabular)</span></span>
  <span data-ttu-id="45197-103">テーブル モデルでは、ロールはあるモデルのメンバー アクセス許可を定義します。</span><span class="sxs-lookup"><span data-stu-id="45197-103">Roles, in tabular models, define member permissions for a model.</span></span> <span data-ttu-id="45197-104">モデル プロジェクトのロールは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [ロール マネージャー] ダイアログ ボックスを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="45197-104">Roles are defined for a model project by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="45197-105">モデルが配置されると、データベース管理者は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してロールを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="45197-105">When a model is deployed, database administrators can manage roles by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="45197-106">このトピックのタスクでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で [ロール マネージャー] ダイアログ ボックスを使用して、モデル作成時にロールを作成し管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45197-106">The tasks in this topic describe how to create and manage roles during model authoring by using the Role Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="45197-107">配置済みモデル データベースでのロールの管理については、「[テーブル モデル ロール &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="45197-107">For information about managing roles in a deployed model database, see [Tabular Model Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="45197-108">タスク</span><span class="sxs-lookup"><span data-stu-id="45197-108">Tasks</span></span>  
 <span data-ttu-id="45197-109">ロールの作成、編集、コピー、削除の各操作を実行するには、 **[ロール マネージャー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="45197-109">To create, edit, copy, and delete roles, you will use the **Role Manager** dialog box.</span></span> <span data-ttu-id="45197-110">**[ロール マネージャー]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[ロール マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45197-110">To view the **Role Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="45197-111">新しいロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="45197-111">To create a new role</span></span>  
  
1.  <span data-ttu-id="45197-112">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[ロール マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45197-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Role Manager**.</span></span>  
  
2.  <span data-ttu-id="45197-113">**[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45197-113">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="45197-114">新しいロールが [ロール] リストに追加され、強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="45197-114">A new highlighted role is added to the Roles list.</span></span>  
  
3.  <span data-ttu-id="45197-115">**[ロール]** リストの **[名前]** フィールドに、ロールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="45197-115">In the **Roles** list, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="45197-116">既定では、既定ロールの名前に番号が付き、新しいロールを作成するたびにその番号が増加します。</span><span class="sxs-lookup"><span data-stu-id="45197-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="45197-117">Finance Managers や Human Resources Specialists など、メンバーの種類を明確に特定する名前を付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45197-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="45197-118">**[権限]** フィールドで下矢印をクリックしてから、次の権限の種類から 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="45197-118">In the **Permissions** field, click the down arrow and then select one of the following permission types:</span></span>  
  
    |<span data-ttu-id="45197-119">権限</span><span class="sxs-lookup"><span data-stu-id="45197-119">Permission</span></span>|<span data-ttu-id="45197-120">説明</span><span class="sxs-lookup"><span data-stu-id="45197-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="45197-121">**なし**</span><span class="sxs-lookup"><span data-stu-id="45197-121">**None**</span></span>|<span data-ttu-id="45197-122">メンバーは、モデル スキーマを変更したり、データをクエリしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="45197-122">Members cannot make any modifications to the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="45197-123">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="45197-123">**Read**</span></span>|<span data-ttu-id="45197-124">メンバーは、(行フィルターに基づいて) データをクエリできますが、モデル スキーマを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="45197-124">Members are allowed to query data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="45197-125">**読み取りと処理**</span><span class="sxs-lookup"><span data-stu-id="45197-125">**Read and Process**</span></span>|<span data-ttu-id="45197-126">メンバーは、(行レベル フィルターに基づいて) データをクエリでき、処理およびすべて処理の各操作も実行できますが、モデル スキーマを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="45197-126">Members are allowed to query data (based on row-level filters) and run Process and Process All operations, but cannot make any changes to the model schema.</span></span>|  
    |<span data-ttu-id="45197-127">**処理**</span><span class="sxs-lookup"><span data-stu-id="45197-127">**Process**</span></span>|<span data-ttu-id="45197-128">メンバーは、処理およびすべて処理の各操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="45197-128">Members can run Process and Process All operations.</span></span> <span data-ttu-id="45197-129">モデル スキーマを変更することはできませんし、データをクエリすることもできません。</span><span class="sxs-lookup"><span data-stu-id="45197-129">Cannot modify the model schema and cannot query data.</span></span>|  
    |<span data-ttu-id="45197-130">**管理者**</span><span class="sxs-lookup"><span data-stu-id="45197-130">**Administrator**</span></span>|<span data-ttu-id="45197-131">メンバーは、モデル スキーマを変更したり、すべてのデータをクエリしたりできます。</span><span class="sxs-lookup"><span data-stu-id="45197-131">Members can make modifications to the model schema and can query all data.</span></span>|  
  
5.  <span data-ttu-id="45197-132">ロールの説明を入力するには、 **[説明]** フィールドをクリックして説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="45197-132">To enter a description for the role, click the **Description** field, and then type a description.</span></span>  
  
6.  <span data-ttu-id="45197-133">作成しているロールに読み取りまたは読み取りと処理の権限がある場合、DAX 式を使用して行フィルターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="45197-133">If the role you are creating has Read or Read and Process permission, you can add row filters using a DAX formula.</span></span> <span data-ttu-id="45197-134">行フィルターを追加するには、 **[行フィルター]** タブをクリックし、テーブルを選択してから、 **[DAX フィルター]** フィールドをクリックし、DAX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="45197-134">To add row filters, click the **Row Filters** tab, then select a table, then click the **DAX Filter** field, and then type a DAX formula.</span></span>  
  
7.  <span data-ttu-id="45197-135">このロールにメンバーを追加するには、 **[メンバー]** タブをクリックし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45197-135">To add members to the role, click the **Members** tab, and then click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45197-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、配置済みモデルにロール メンバーを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="45197-136">Role members can also be added to a deployed model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="45197-137">詳しくは、「[SSMS を使用したロールの管理 &#40;SSAS テーブル&#41;](manage-roles-by-using-ssms-ssas-tabular.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="45197-137">For more information, see [Manage Roles by using SSMS &#40;SSAS Tabular&#41;](manage-roles-by-using-ssms-ssas-tabular.md).</span></span>  
  
8.  <span data-ttu-id="45197-138">**[ユーザーまたはグループの選択]** ダイアログ ボックスで、メンバーとして Windows ユーザーまたは Windows グループ オブジェクトを入力します。</span><span class="sxs-lookup"><span data-stu-id="45197-138">In the **Select Users or Groups** dialog box, enter Windows user or Windows group objects as members.</span></span>  
  
9. <span data-ttu-id="45197-139">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45197-139">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45197-140">参照</span><span class="sxs-lookup"><span data-stu-id="45197-140">See Also</span></span>  
 <span data-ttu-id="45197-141">[SSAS 表形式のロール &#40;&#41;](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="45197-141">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 <span data-ttu-id="45197-142">[SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="45197-142">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 <span data-ttu-id="45197-143">[Excel での分析 &#40;SSAS 表形式&#41;](analyze-in-excel-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="45197-143">[Analyze in Excel &#40;SSAS Tabular&#41;](analyze-in-excel-ssas-tabular.md) </span></span>  
 <span data-ttu-id="45197-144">[ユーザー名関数 &#40;DAX&#41;](/dax/username-function-dax) </span><span class="sxs-lookup"><span data-stu-id="45197-144">[USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) </span></span>  
 [<span data-ttu-id="45197-145">CUSTOMDATA 関数 &#40;DAX&#41;</span><span class="sxs-lookup"><span data-stu-id="45197-145">CUSTOMDATA Function &#40;DAX&#41;</span></span>](/dax/customdata-function-dax)  
  
  
