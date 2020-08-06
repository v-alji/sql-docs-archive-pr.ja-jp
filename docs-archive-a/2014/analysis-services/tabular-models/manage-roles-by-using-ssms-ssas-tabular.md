---
title: SSMS を使用したロールの管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 652faac0-1cfc-438b-8119-2f4b090a2381
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee34d5e75d5d4ce3679d46d29af3215852d2bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712485"
---
# <a name="manage-roles-by-using-ssms-ssas-tabular"></a><span data-ttu-id="2679c-102">SSMS を使用したロールの管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="2679c-102">Manage Roles by using SSMS (SSAS Tabular)</span></span>
  <span data-ttu-id="2679c-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、配置したテーブル モデルのロールの作成、編集、および管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2679c-103">You can create, edit, and manage roles for a deployed tabular model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2679c-104">このトピックのタスク:</span><span class="sxs-lookup"><span data-stu-id="2679c-104">Tasks in this topic:</span></span>  
  
-   [<span data-ttu-id="2679c-105">新しいロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="2679c-105">To create a new role</span></span>](#bkmk_new_role)  
  
-   [<span data-ttu-id="2679c-106">ロールをコピーするには</span><span class="sxs-lookup"><span data-stu-id="2679c-106">To copy a role</span></span>](#bkmk_copy_role)  
  
-   [<span data-ttu-id="2679c-107">ロールを編集するには</span><span class="sxs-lookup"><span data-stu-id="2679c-107">To edit a role</span></span>](#bkmk_edit_role)  
  
-   [<span data-ttu-id="2679c-108">ロールを削除するには</span><span class="sxs-lookup"><span data-stu-id="2679c-108">To delete a role</span></span>](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  <span data-ttu-id="2679c-109">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のロール マネージャーを使用して定義済みロールを含むテーブル モデル プロジェクトを再配置すると、配置済みテーブル モデルに定義されたロールが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="2679c-109">Re-deploying a tabular model project with roles defined by using Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] will overwrite roles defined in a deployed tabular model.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2679c-110">モデル プロジェクトが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で開いているときに、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用してテーブル モデル ワークスペース データベースを管理すると、Model.bim ファイルが破損することがあります。</span><span class="sxs-lookup"><span data-stu-id="2679c-110">Using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage a tabular model workspace database while the model project is open in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] may cause the Model.bim file to become corrupted.</span></span> <span data-ttu-id="2679c-111">テーブル モデル ワークスペース データベースのロールを作成および管理するときは、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のロール マネージャーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="2679c-111">When creating and managing roles for a tabular model workspace database, use Role Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
###  <a name="to-create-a-new-role"></a><a name="bkmk_new_role"></a><span data-ttu-id="2679c-112">新しいロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="2679c-112">To create a new role</span></span>  
  
1.  <span data-ttu-id="2679c-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、新しいロールを作成するテーブル モデル データベースを展開し、 **[ロール]** を右クリックしてから **[新しいロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database for which you want to create a new role, then right click on **Roles**, and then click **New Role**.</span></span>  
  
2.  <span data-ttu-id="2679c-114">**[ロールの作成]** ダイアログ ボックスの [ページの選択] ウィンドウで **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-114">In the **Create Role** dialog box, in the Select a page window, click **General**.</span></span>  
  
3.  <span data-ttu-id="2679c-115">全般設定のウィンドウの **[名前]** フィールドにロールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2679c-115">In the general settings window, in the **Name** field, type a name for the role.</span></span>  
  
     <span data-ttu-id="2679c-116">既定では、既定ロールの名前に番号が付き、新しいロールを作成するたびにその番号が増加します。</span><span class="sxs-lookup"><span data-stu-id="2679c-116">By default, the name of the default role will be incrementally numbered for each new role.</span></span> <span data-ttu-id="2679c-117">Finance Managers や Human Resources Specialists など、メンバーの種類を明確に特定する名前を付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2679c-117">It is recommended you type a name that clearly identifies the member type, for example, Finance Managers or Human Resources Specialists.</span></span>  
  
4.  <span data-ttu-id="2679c-118">**[このロールにデータベースの権限を設定します]** で、次の権限オプションのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="2679c-118">In **Set the database permissions for this role**, select one of the following permissions options:</span></span>  
  
    |<span data-ttu-id="2679c-119">権限</span><span class="sxs-lookup"><span data-stu-id="2679c-119">Permission</span></span>|<span data-ttu-id="2679c-120">説明</span><span class="sxs-lookup"><span data-stu-id="2679c-120">Description</span></span>|  
    |----------------|-----------------|  
    |<span data-ttu-id="2679c-121">**フル コントロール (管理者)**</span><span class="sxs-lookup"><span data-stu-id="2679c-121">**Full control (Administrator)**</span></span>|<span data-ttu-id="2679c-122">メンバーは、モデル スキーマを変更したり、すべてのデータを表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="2679c-122">Members can make modifications to the model schema and can view all data.</span></span>|  
    |<span data-ttu-id="2679c-123">**データベースの処理**</span><span class="sxs-lookup"><span data-stu-id="2679c-123">**Process database**</span></span>|<span data-ttu-id="2679c-124">メンバーは、処理およびすべて処理の各操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="2679c-124">Members can run Process and Process All operations.</span></span> <span data-ttu-id="2679c-125">モデル スキーマを変更することはできませんし、データを表示することもできません。</span><span class="sxs-lookup"><span data-stu-id="2679c-125">Cannot modify the model schema and cannot view data.</span></span>|  
    |<span data-ttu-id="2679c-126">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="2679c-126">**Read**</span></span>|<span data-ttu-id="2679c-127">メンバーは、データを表示できますが (行フィルターに従って)、モデル スキーマを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="2679c-127">Members are allowed to view data (based on row filters) but cannot make any changes to the model schema.</span></span>|  
  
5.  <span data-ttu-id="2679c-128">**[ロールの作成]** ダイアログ ボックスの [ページの選択] ウィンドウで **[メンバーシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-128">In the **Create Role** dialog box, in the Select a page window, click **Membership**.</span></span>  
  
6.  <span data-ttu-id="2679c-129">メンバーシップ設定ウィンドウで **[追加]** をクリックし、 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、メンバーとして追加する Windows ユーザーまたはグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="2679c-129">In the membership settings window, click **Add**, and then in the **Select Users or Groups** dialog box, add the Windows users or groups you want to add as members.</span></span>  
  
7.  <span data-ttu-id="2679c-130">作成しているロールに読み取り権限がある場合、DAX 数式を使用してテーブルに行フィルターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="2679c-130">If the role you are creating has Read permissions, you can add row filters for any table using a DAX formula.</span></span> <span data-ttu-id="2679c-131">行フィルターを追加するには、[**ロール \<rolename> のプロパティ-** ] ダイアログボックスの [**ページの選択**] で、[**行フィルター**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-131">To add row filters, in the **Role Properties - \<rolename>** dialog box, in **Select a page**, click on **Row Filters**.</span></span>  
  
8.  <span data-ttu-id="2679c-132">行フィルターウィンドウでテーブルを選択し、[ **Dax フィルター** ] フィールドをクリックします。次に、[ **dax \<tablename> フィルター** ] フィールドに dax 数式を入力します。</span><span class="sxs-lookup"><span data-stu-id="2679c-132">In the row filters window, select a table, then click on the **DAX Filter** field, and then in the **DAX Filter - \<tablename>** field, type a DAX formula.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2679c-133">[DAX フィルター \<tablename> ] フィールドに、オートコンプリートクエリエディターまたは関数の挿入機能が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="2679c-133">The DAX Filter - \<tablename> field does not contain an AutoComplete query editor or insert function feature.</span></span> <span data-ttu-id="2679c-134">DAX 数式を作成するときにオートコンプリート機能を使用するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の DAX 数式エディターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2679c-134">To use AutoComplete when writing a DAX formula, you must use a DAX formula editor in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
9. <span data-ttu-id="2679c-135">**[OK]** をクリックして、ロールを保存します。</span><span class="sxs-lookup"><span data-stu-id="2679c-135">Click **Ok** to save the role.</span></span>  
  
###  <a name="to-copy-a-role"></a><a name="bkmk_copy_role"></a><span data-ttu-id="2679c-136">ロールをコピーするには</span><span class="sxs-lookup"><span data-stu-id="2679c-136">To copy a role</span></span>  
  
1.  <span data-ttu-id="2679c-137">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、コピーするロールを含むテーブル モデル データベースを展開し、 **[ロール]** を展開してから、ロールを右クリックして **[複製]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-137">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to copy, then expand **Roles**, then right click on the role, and then click **Duplicate**.</span></span>  
  
###  <a name="to-edit-a-role"></a><a name="bkmk_edit_role"></a><span data-ttu-id="2679c-138">ロールを編集するには</span><span class="sxs-lookup"><span data-stu-id="2679c-138">To edit a role</span></span>  
  
-   <span data-ttu-id="2679c-139">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、編集するロールを含むテーブル モデル データベースを展開し、 **[ロール]** を展開してから、ロールを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-139">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to edit, then expand **Roles**, then right click on the role, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="2679c-140">[**ロールのプロパティ** \<rolename> ] ダイアログボックスでは、権限の変更、メンバーの追加または削除、および行フィルターの追加と編集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2679c-140">In the **Role Properties** \<rolename> dialog box, you can change permissions, add or remove members, and add/edit row filters.</span></span>  
  
###  <a name="to-delete-a-role"></a><a name="bkmk_deletet_role"></a><span data-ttu-id="2679c-141">ロールを削除するには</span><span class="sxs-lookup"><span data-stu-id="2679c-141">To delete a role</span></span>  
  
-   <span data-ttu-id="2679c-142">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、削除するロールを含むテーブル モデル データベースを展開し、 **[ロール]** を展開してから、ロールを右クリックして **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2679c-142">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the tabular model database that contains the role you want to delete, then expand **Roles**, then right click on the role, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2679c-143">参照</span><span class="sxs-lookup"><span data-stu-id="2679c-143">See Also</span></span>  
 [<span data-ttu-id="2679c-144">ロール (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="2679c-144">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
