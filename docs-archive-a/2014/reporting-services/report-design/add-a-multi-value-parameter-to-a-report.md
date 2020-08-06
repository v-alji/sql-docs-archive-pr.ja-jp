---
title: 複数の値を持つパラメーターのレポートへの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5269293b6a21f3b1d82eb6835efbd275e3be9620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712758"
---
# <a name="add-a-multi-value-parameter-to-a-report"></a><span data-ttu-id="2240c-102">複数の値を持つパラメーターのレポートへの追加</span><span class="sxs-lookup"><span data-stu-id="2240c-102">Add a multi-value parameter to a Report</span></span>
  <span data-ttu-id="2240c-103">ユーザーがパラメーター値として複数の値を選択できるパラメーターをレポートに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2240c-103">You can add a parameter to a report that allows the user to select more than one value for the parameter.</span></span>  
  
 <span data-ttu-id="2240c-104">レポート URL に複数のパラメーター値を含めてレポートに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2240c-104">You can pass multiple parameter values to the report within the report URL.</span></span> <span data-ttu-id="2240c-105">複数の値を持つパラメーターを含む URL の例は、「 [URL 内でレポート パラメーターを渡す](../pass-a-report-parameter-within-a-url.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-105">For a URL example includes a multi-value parameter, see [Pass a Report Parameter Within a URL](../pass-a-report-parameter-within-a-url.md).</span></span>  
  
 <span data-ttu-id="2240c-106">複数のパラメーター値をストアド プロシージャに渡す方法については、mssqltips.com の「 [SSRS レポートでの複数選択パラメーターの操作](https://go.microsoft.com/fwlink/?LinkId=321529) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-106">For information on how to pass multiple parameter values to a stored procedure, see [Working With Multi-Select Parameters for SSRS Reports](https://go.microsoft.com/fwlink/?LinkId=321529) on mssqltips.com.</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="2240c-107">複数の値を持つパラメーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="2240c-107">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="2240c-108">レポート ビルダーで、複数の値を持つパラメーターを追加するレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2240c-108">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="2240c-109">レポート データセットを右クリックし、 **[データセットのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2240c-109">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="2240c-110">**[クエリ]** ボックスでクエリ テキストを編集するか、クエリ デザイナーを使用してフィルターを追加することで、データセット クエリに変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="2240c-110">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="2240c-111">詳細については、「[リレーショナル クエリ デザイナーでのクエリの作成 &#40;レポート ビルダーおよび SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-111">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2240c-112">クエリ テキストには、クエリ変数の DECLARE ステートメントを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="2240c-112">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2240c-113">クエリ変数のテキストには、次の例のように、`IN` 演算子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2240c-113">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2240c-114">上に示したように、変数をかっこで囲まないと、レポートは表示されず、"スカラー変数を宣言する必要があります" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-114">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="2240c-115">埋め込みデータセットまたは共有データセットのデータセット パラメーターは、クエリ変数に対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-115">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="2240c-116">レポート パラメーターは、データセット パラメーターに対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-116">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="2240c-117">**レポート データ** ペインで **[パラメーター]** ノードを展開し、データセット パラメーターに対して自動的に生成されたレポート パラメーターを右クリックして、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2240c-117">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="2240c-118">**[全般]** タブで、 **[複数の値を許可]** を選択して、パラメーターに複数の値を選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2240c-118">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="2240c-119">(省略可能) **[使用できる値]** タブで、ユーザーに対して表示する使用可能な値の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="2240c-119">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="2240c-120">使用可能な値の一覧を使用すると、ユーザーがパラメーターに選択できる値が有効な値のみに制限されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-120">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="2240c-121">値が複数ある場合は、一覧の先頭に **[すべて選択]** という項目が用意されるため、ユーザーは 1 回のクリックですべての値を選択またはクリアできます。</span><span class="sxs-lookup"><span data-stu-id="2240c-121">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="2240c-122">レポート パラメーターで使用できる値をデータセット クエリから取得する場合は、同じレポート パラメーターに関連付けられているクエリ変数を含まないデータセットを選択してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-122">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="2240c-123">詳細については、「[レポート パラメーターの値の追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-123">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="2240c-124">複数の値を持つパラメーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="2240c-124">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="2240c-125">レポート ビルダーで、複数の値を持つパラメーターを追加するレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2240c-125">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="2240c-126">レポート データセットを右クリックし、 **[データセットのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2240c-126">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="2240c-127">**[クエリ]** ボックスでクエリ テキストを編集するか、クエリ デザイナーを使用してフィルターを追加することで、データセット クエリに変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="2240c-127">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="2240c-128">詳細については、「[リレーショナル クエリ デザイナーでのクエリの作成 &#40;レポート ビルダーおよび SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-128">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2240c-129">クエリ テキストには、クエリ変数の DECLARE ステートメントを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="2240c-129">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2240c-130">クエリ変数のテキストには、次の例のように、`IN` 演算子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2240c-130">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2240c-131">上に示したように、変数をかっこで囲まないと、レポートは表示されず、"スカラー変数を宣言する必要があります" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-131">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="2240c-132">埋め込みデータセットまたは共有データセットのデータセット パラメーターは、クエリ変数に対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-132">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="2240c-133">レポート パラメーターは、データセット パラメーターに対して自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-133">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="2240c-134">**レポート データ** ペインで **[パラメーター]** ノードを展開し、データセット パラメーターに対して自動的に生成されたレポート パラメーターを右クリックして、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2240c-134">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="2240c-135">**[全般]** タブで、 **[複数の値を許可]** を選択して、パラメーターに複数の値を選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2240c-135">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="2240c-136">(省略可能) **[使用できる値]** タブで、ユーザーに対して表示する使用可能な値の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="2240c-136">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="2240c-137">使用可能な値の一覧を使用すると、ユーザーがパラメーターに選択できる値が有効な値のみに制限されます。</span><span class="sxs-lookup"><span data-stu-id="2240c-137">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="2240c-138">値が複数ある場合は、一覧の先頭に **[すべて選択]** という項目が用意されるため、ユーザーは 1 回のクリックですべての値を選択またはクリアできます。</span><span class="sxs-lookup"><span data-stu-id="2240c-138">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="2240c-139">レポート パラメーターで使用できる値をデータセット クエリから取得する場合は、同じレポート パラメーターに関連付けられているクエリ変数を含まないデータセットを選択してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-139">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="2240c-140">詳細については、「[レポート パラメーターの値の追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2240c-140">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2240c-141">参照</span><span class="sxs-lookup"><span data-stu-id="2240c-141">See Also</span></span>  
 <span data-ttu-id="2240c-142">[カスケード型パラメーターをレポートに追加する &#40;レポートビルダーと SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2240c-142">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2240c-143">レポート パラメーターの追加、変更、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2240c-143">Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
