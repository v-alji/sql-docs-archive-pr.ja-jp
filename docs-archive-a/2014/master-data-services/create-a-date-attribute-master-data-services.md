---
title: 日付属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 93797b90ff03c6a2b60ce8e015897a46a7448aad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631138"
---
# <a name="create-a-date-attribute-master-data-services"></a><span data-ttu-id="8056a-102">日付属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8056a-102">Create a Date Attribute (Master Data Services)</span></span>
  <span data-ttu-id="8056a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ユーザーに属性値として日付を入力させる場合、日付属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="8056a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a date attribute when you want users to enter a date as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8056a-104">属性は DateTime という名前ですが、時間の値はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8056a-104">The attribute is called DateTime, but time values are not supported.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8056a-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="8056a-105">Prerequisites</span></span>  
 <span data-ttu-id="8056a-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="8056a-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8056a-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="8056a-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="8056a-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8056a-108">You must be a model administrator.</span></span> <span data-ttu-id="8056a-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056a-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8056a-110">属性を作成するエンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8056a-110">You must have an entity to create the attribute for.</span></span> <span data-ttu-id="8056a-111">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056a-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-date-attribute"></a><span data-ttu-id="8056a-112">日付属性を作成するには</span><span class="sxs-lookup"><span data-stu-id="8056a-112">To create a date attribute</span></span>  
  
1.  <span data-ttu-id="8056a-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="8056a-114">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="8056a-115">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8056a-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="8056a-116">属性を作成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="8056a-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="8056a-117">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="8056a-118">**[エンティティの編集]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8056a-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="8056a-119">リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="8056a-120">統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="8056a-121">コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="8056a-122">**[属性の追加]** ページで **[自由形式]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8056a-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="8056a-123">**[名前]** ボックスに属性の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8056a-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="8056a-124">属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056a-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="8056a-125">**[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。</span><span class="sxs-lookup"><span data-stu-id="8056a-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="8056a-126">**[データ型]** ボックスの一覧の **[DateTime]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-126">From the **Data type** list, select **DateTime**.</span></span>  
  
11. <span data-ttu-id="8056a-127">**[定型入力]** ボックスの一覧から日付の形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="8056a-127">From the **Input mask** list, select a format for dates.</span></span>  
  
12. <span data-ttu-id="8056a-128">必要に応じて、 **[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="8056a-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="8056a-129">詳細については、「[変更の追跡グループに属性を追加する方法 (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056a-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="8056a-130">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="8056a-131">**[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8056a-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a><span data-ttu-id="8056a-132">datetime 値の時刻部分を表示するには</span><span class="sxs-lookup"><span data-stu-id="8056a-132">To display the time portion of a datetime value</span></span>  
 <span data-ttu-id="8056a-133">ユーザー インターフェイスに datetime 値の時刻部分を表示するには、属性に対する適切な入力マスクを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8056a-133">To have the user interface display the time portion of a datetime value, you must select an appropriate input mask for the attribute.</span></span> <span data-ttu-id="8056a-134">Datetime 属性にそのための組み込みのマスクは存在しませんが、時刻を表示するための新しいマスクを独自に追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="8056a-134">None of the built-in masks for Datetime attributes do this, but you can add a new mask that will allow you to display time.</span></span> <span data-ttu-id="8056a-135">そのためには、組み込みのマスクが格納されている MDS データベースの mdm.tblList テーブルに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="8056a-135">To do so, add a row in the mdm.tblList table of the MDS database, where the built-in masks are stored.</span></span> <span data-ttu-id="8056a-136">この行には、次の値が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8056a-136">The row should have the following values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8056a-137">ListCode</span><span class="sxs-lookup"><span data-stu-id="8056a-137">ListCode</span></span>|<span data-ttu-id="8056a-138">lstInputMask</span><span class="sxs-lookup"><span data-stu-id="8056a-138">lstInputMask</span></span>|  
|<span data-ttu-id="8056a-139">ListName</span><span class="sxs-lookup"><span data-stu-id="8056a-139">ListName</span></span>|<span data-ttu-id="8056a-140">[定型入力]</span><span class="sxs-lookup"><span data-stu-id="8056a-140">Input Mask</span></span>|  
|<span data-ttu-id="8056a-141">Seq</span><span class="sxs-lookup"><span data-stu-id="8056a-141">Seq</span></span>|<span data-ttu-id="8056a-142">19</span><span class="sxs-lookup"><span data-stu-id="8056a-142">19</span></span>|  
|<span data-ttu-id="8056a-143">List Option</span><span class="sxs-lookup"><span data-stu-id="8056a-143">List Option</span></span>|<span data-ttu-id="8056a-144">dd/MM/yyyy hh:mm:ss tt</span><span class="sxs-lookup"><span data-stu-id="8056a-144">dd/MM/yyyy hh:mm:ss tt</span></span>|  
|<span data-ttu-id="8056a-145">Option ID</span><span class="sxs-lookup"><span data-stu-id="8056a-145">Option ID</span></span>|<span data-ttu-id="8056a-146">19</span><span class="sxs-lookup"><span data-stu-id="8056a-146">19</span></span>|  
|<span data-ttu-id="8056a-147">可視</span><span class="sxs-lookup"><span data-stu-id="8056a-147">IsVisible</span></span>|<span data-ttu-id="8056a-148">1</span><span class="sxs-lookup"><span data-stu-id="8056a-148">1</span></span>|  
|<span data-ttu-id="8056a-149">Group_ID</span><span class="sxs-lookup"><span data-stu-id="8056a-149">Group_ID</span></span>|<span data-ttu-id="8056a-150">3</span><span class="sxs-lookup"><span data-stu-id="8056a-150">3</span></span>|  
  
 <span data-ttu-id="8056a-151">上記の値を mdm.tblList テーブルの行に入力すると、[定型入力] リスト ボックスで "dd/MM/yyyy hh:mm:ss tt" マスクを選べるようになります。</span><span class="sxs-lookup"><span data-stu-id="8056a-151">After you enter a row with the above values in the mdm.tblList table, the "dd/MM/yyyy hh:mm:ss tt" mask will be available in the Input mask list box.</span></span> <span data-ttu-id="8056a-152">これで、エンティティの datetime 属性列に日付と時刻を表示するためのマスクを MDS エクスプローラーで選択できます。</span><span class="sxs-lookup"><span data-stu-id="8056a-152">You can then select that mask to display the date and time in a datetime attribute column of an entity in the MDS Explorer.</span></span>  
  
 <span data-ttu-id="8056a-153">[定型入力] は、カスタムの .NET DateTime 書式設定文字列です。</span><span class="sxs-lookup"><span data-stu-id="8056a-153">The Input Mask is a custom .NET DateTime format string.</span></span> <span data-ttu-id="8056a-154">詳しくは、「 [カスタム日時書式指定文字列](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8056a-154">For more information, see [Custom Date and Time Format Strings](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8056a-155">参照</span><span class="sxs-lookup"><span data-stu-id="8056a-155">See Also</span></span>  
 <span data-ttu-id="8056a-156">[属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8056a-156">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="8056a-157">[属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8056a-157">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="8056a-158">[ドメインベースの属性 &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8056a-158">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="8056a-159">ファイル属性を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8056a-159">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
