---
title: Finance の名前ポリシーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 44ffff45f126d2ad9b73c5b8410b8f89ad2b0604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632419"
---
# <a name="create-the-finance-name-policy"></a><span data-ttu-id="51ffb-102">Finance の名前ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="51ffb-102">Create the Finance Name Policy</span></span>
  <span data-ttu-id="51ffb-103">ここでは、Finance という名前のデータベースを作成し、すべてのテーブルが文字列 **fintbl**で始まることを必須とする条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-103">In this task, you will create a database named Finance, and then create a condition that requires all tables to start with the letters **fintbl**.</span></span> <span data-ttu-id="51ffb-104">さらに、Finance データベース内のテーブルに名前付け基準を適用するためのポリシーとポリシー カテゴリを作成します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-104">Then, you will create a policy and policy category to enforce a naming standard for tables in the Finance database.</span></span>  
  
### <a name="to-create-the-finance-database"></a><span data-ttu-id="51ffb-105">Finance データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="51ffb-105">To create the Finance database</span></span>  
  
1.  <span data-ttu-id="51ffb-106">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でクエリ ウィンドウを開き、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-106">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window and execute the following statement:</span></span>  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  <span data-ttu-id="51ffb-107">オブジェクト エクスプローラーで、 **[データベース]** をクリックし、F5 キーを押してデータベースの一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-107">In Object Explorer, click **Databases**, and then press F5 to refresh the list of databases.</span></span>  
  
### <a name="to-create-the-finance-tables-condition"></a><span data-ttu-id="51ffb-108">Finance のテーブルの条件を作成するには</span><span class="sxs-lookup"><span data-stu-id="51ffb-108">To create the Finance Tables condition</span></span>  
  
1.  <span data-ttu-id="51ffb-109">オブジェクト エクスプローラーで、 **[管理]**、 **[ポリシー管理]** の順に展開し、 **[条件]** を右クリックして **[新しい条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-109">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Conditions**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="51ffb-110">**[新しい条件の作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **Finance のテーブル**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-110">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Tables**.</span></span>  
  
3.  <span data-ttu-id="51ffb-111">**[ファセット]** ボックスの一覧で **[マルチパート名]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-111">In the **Facet** list, select **Multipart Name**.</span></span>  
  
4.  <span data-ttu-id="51ffb-112">[**式**] 領域の [**フィールド**] ボックスで、[ \*\* \@ 名前**] を選択します。 [**演算子**] ボックスで [ **Like**] を選択し、[**値**] ボックスに「 **' finfin% '** 」と入力して、すべてのテーブル名を強制的**に文字で\*\*始まるようにします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-112">In the **Expression** area, in the **Field** box, select **\@Name**; in the **Operator** box, select **Like**; and in the **Value** box, type **'fintbl%'** to force all table names to start with the letters **fintbl**.</span></span>  
  
5.  <span data-ttu-id="51ffb-113">**[説明]** ページで、「 **Finance のテーブル名は必ず fintbl で始める**」と入力し、 **[OK]** をクリックして条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-113">On the **Description** page, type **Finance table names must begin with fintbl**, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-finance-name-policy"></a><span data-ttu-id="51ffb-114">Finance の名前ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="51ffb-114">To create the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="51ffb-115">オブジェクト エクスプローラーで **[ポリシー]** を右クリックし、 **[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-115">In Object Explorer, right-click **Policies**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="51ffb-116">**[新しいポリシーの作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **Finance の名前**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-116">In the **Create New Policy** dialog box, in the **Name** box, type **Finance Name**.</span></span>  
  
3.  <span data-ttu-id="51ffb-117">**[条件の確認]** ボックスの一覧で、 **[Finance のテーブル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-117">In the **Check condition** list, select **Finance Tables**.</span></span> <span data-ttu-id="51ffb-118">このボックスは **[マルチパート名]** 領域にあります。</span><span class="sxs-lookup"><span data-stu-id="51ffb-118">This is in the **Multipart Name** area.</span></span>  
  
4.  <span data-ttu-id="51ffb-119">**[対象]** 領域に、このポリシーを適用できるデータベース オブジェクトの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="51ffb-119">In the **Against** area you will see a list of the database objects that could apply this policy.</span></span> <span data-ttu-id="51ffb-120">**[すべてのテーブル]** のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-120">Select the check box for **Every Table**.</span></span>  
  
5.  <span data-ttu-id="51ffb-121">**[すべてのデータベース]** 領域で、 **[すべて]** を展開し、 **[新しい条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-121">In the **Every Database** area, expand **Every**, and then click **New condition**.</span></span>  
  
6.  <span data-ttu-id="51ffb-122">**[新しい条件の作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **Finance データベース**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-122">In the **Create New Condition** dialog box, in the **Name** box, type **Finance Database**.</span></span>  
  
7.  <span data-ttu-id="51ffb-123">[**式**] ボックスで、 \*\* \@ "名前 = ' Finance '\*\* を含む式を入力し、[ **OK** ] をクリックして条件ページを閉じます。</span><span class="sxs-lookup"><span data-stu-id="51ffb-123">In the **Expression** box, complete the expression to include **\@Name = 'Finance'**, and then click **OK** to close the condition page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51ffb-124">Tab キーを押して **[値]** ボックスから移動しないと、 **[OK]** ボタンが有効にならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="51ffb-124">You might have to tab out of the **Value** box to enable the **OK** button.</span></span>  
  
8.  <span data-ttu-id="51ffb-125">**[評価モード]** の一覧で、 **[変更時: 回避]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-125">In the **Evaluation Mode** list, select **On change: prevent**.</span></span> <span data-ttu-id="51ffb-126">これにより、Finance データベースでデータベース トリガーを作成することでポリシーが適用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="51ffb-126">This will enforce the policy by creating a database trigger on the Finance database.</span></span>  
  
9. <span data-ttu-id="51ffb-127">**[有効]** チェック ボックスをオンにします</span><span class="sxs-lookup"><span data-stu-id="51ffb-127">Select the **Enabled** list.</span></span> <span data-ttu-id="51ffb-128">( **[要求時]** ポリシーには **[有効]** ボックスが適用されません)。</span><span class="sxs-lookup"><span data-stu-id="51ffb-128">(The **Enabled** box does not apply to **On demand** policies.)</span></span>  
  
10. <span data-ttu-id="51ffb-129">**[サーバーの制限]** ボックスの一覧で **[なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="51ffb-129">In the **Server restriction** list, select **None**.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a><span data-ttu-id="51ffb-130">Finance ポリシー カテゴリを作成するには</span><span class="sxs-lookup"><span data-stu-id="51ffb-130">To create the Finance policy category</span></span>  
  
1.  <span data-ttu-id="51ffb-131">オブジェクト エクスプローラーで **[管理]** を展開し、 **[ポリシー管理]** を右クリックして、 **[カテゴリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-131">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="51ffb-132">[**ポリシーカテゴリの管理**] ダイアログボックスの [**名前**] で、 `Finance` 空のボックスに「」と入力し、[**データベースのサブスクリプション**の要求] をオフにします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-132">In the **Manage Policy Categories** dialog box, under **Name**, type `Finance` in the blank box, and then clear **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="51ffb-133">**[データベースのサブスクリプションの要求]** では、インスタンス内のすべてのデータベースは、このポリシー カテゴリに属するポリシーをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="51ffb-133">**Mandate Database Subscriptions** will force every database in the instance to subscribe to the policies that belong to this policy category.</span></span> <span data-ttu-id="51ffb-134">このレッスンでは、Finance の名前ポリシーをサブスクライブするのは Finance データベースだけです。</span><span class="sxs-lookup"><span data-stu-id="51ffb-134">For this lesson, only the Finance database should subscribe to the Finance Name policy.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="51ffb-135">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="51ffb-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="51ffb-136">Finance の名前ポリシーのサブスクライブおよび確認</span><span class="sxs-lookup"><span data-stu-id="51ffb-136">Subscribe to and Check the Finance Name Policy</span></span>](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
