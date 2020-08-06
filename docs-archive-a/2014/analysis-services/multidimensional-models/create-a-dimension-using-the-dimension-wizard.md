---
title: ディメンションウィザードを使用してディメンションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], creating
ms.assetid: d84f66ae-7551-49bf-99d0-88368ca2dd0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ec38dc7170b915dce0cedea60c93385560e11f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737056"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a><span data-ttu-id="6f580-102">ディメンション ウィザードを使用したディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="6f580-102">Create a Dimension Using the Dimension Wizard</span></span>
  <span data-ttu-id="6f580-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション ウィザードを使用して新しいディメンションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f580-103">You can create a new dimension by using the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-dimension"></a><span data-ttu-id="6f580-104">新しいディメンションを作成するには</span><span class="sxs-lookup"><span data-stu-id="6f580-104">To create a new dimension</span></span>  
  
1.  <span data-ttu-id="6f580-105">**ソリューション エクスプローラー**で **[ディメンション]** を右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-105">In **Solution Explorer**, right-click **Dimensions**, and then click **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="6f580-106">ディメンション ウィザードの **[作成方法の選択]** ページで、 **[既存のテーブルの使用]** をクリックして、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-106">On the **Select Creation Method** page of the Dimension Wizard, select **Use an existing table**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f580-107">既存のテーブルを使用せずにディメンションを作成することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6f580-107">You might occasionally have to create a dimension without using an existing table.</span></span> <span data-ttu-id="6f580-108">詳細については、「 [データ ソースに時間テーブル以外のテーブルを生成することによるディメンションの作成](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) 」および「 [時間テーブルの生成による時間ディメンションの作成](create-a-time-dimension-by-generating-a-time-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6f580-108">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) and [Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
3.  <span data-ttu-id="6f580-109">**[基になる情報の指定]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6f580-109">On the **Specify Source Information** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="6f580-110">**[データ ソース ビュー]** ボックスの一覧で、データ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f580-110">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="6f580-111">**[メイン テーブル]** ボックスの一覧で、メイン ディメンション テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f580-111">In the **Main table** list, select the main dimension table.</span></span>  
  
    3.  <span data-ttu-id="6f580-112">**[キー列]** ボックスの一覧で、メイン ディメンション テーブルで定義されている主キーに基づいて自動的に選択されたキー列を確認します。</span><span class="sxs-lookup"><span data-stu-id="6f580-112">In the **Key columns** list, review the key columns that the wizard has automatically selected based on the primary key that is defined in the main dimension table.</span></span> <span data-ttu-id="6f580-113">この既定の設定を変更するには、ディメンション テーブルをファクト テーブルにリンクするキー列を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f580-113">To change this default setting, specify the key columns that link the dimension table to the fact table.</span></span>  
  
    4.  <span data-ttu-id="6f580-114">**[名前列]** ボックスの一覧で、ウィザードで自動的に選択された名前列を確認します。</span><span class="sxs-lookup"><span data-stu-id="6f580-114">In the **Name column** drop-down list, review the name column that the wizard has automatically selected.</span></span>  
  
         <span data-ttu-id="6f580-115">この既定の名前は、列に説明情報が含まれている場合に適切です。</span><span class="sxs-lookup"><span data-stu-id="6f580-115">This default name is appropriate when the column contains descriptive information.</span></span> <span data-ttu-id="6f580-116">ただし、エンド ユーザーにとってわかりやすい値を含む名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6f580-116">However, you might want to specify a name that contains values that are more meaningful for the end user.</span></span> <span data-ttu-id="6f580-117">たとえば、製品ディメンションの製品カテゴリ属性でキー列として **ProductCategoryKey** 列が使用される場合は、名前列として **ProductCategoryName** 列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6f580-117">For example, if a product category attribute in a Products dimension uses the **ProductCategoryKey** column as its key column, you can specify the **ProductCategoryName** column as its name column.</span></span>  
  
         <span data-ttu-id="6f580-118">**[キー列]** ボックスの一覧に複数のキー列が含まれている場合、キー属性のメンバー値を提供する名前列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f580-118">If the **Key columns** list contains multiple key columns, you must specify a name column that provides the member values for the key attribute.</span></span> <span data-ttu-id="6f580-119">この操作を行うには、データ ソース ビューで名前付き計算を作成し、それを名前列として使用します。</span><span class="sxs-lookup"><span data-stu-id="6f580-119">To do this, you can create a named calculation in the data source view and use that as the name column.</span></span>  
  
    5.  <span data-ttu-id="6f580-120">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="6f580-121">**[関連テーブルの選択]** ページで、ディメンションに含める関連テーブルを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-121">On the **Select Related Tables** page, select the related tables that you want to include in your dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f580-122">**[関連テーブルの選択]** ページは、指定したメイン ディメンション テーブルに他のディメンション テーブルへのリレーションシップがある場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f580-122">The **Select Related Tables** page appears if the main dimension table that you specified has relationships to other dimension tables.</span></span>  
  
5.  <span data-ttu-id="6f580-123">**[ディメンション属性の選択]** ページで、ディメンションに含める属性を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-123">On the **Select Dimension Attributes** page, select the attributes that you want to include in the dimension, and then click **Next**.</span></span>  
  
     <span data-ttu-id="6f580-124">必要に応じて、属性名の変更、参照の有効化または無効化、および属性の型の指定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6f580-124">Optionally, you can change the attribute names, enable or disable browsing, and specify the attribute type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f580-125">属性の **[参照を有効にする]** フィールドおよび **[属性の型]** フィールドをアクティブにするには、ディメンションに含めるように属性を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f580-125">To make the **Enable Browsing** and **Attribute Type** fields of an attribute active, the attribute must be selected for inclusion in the dimension.</span></span>  
  
6.  <span data-ttu-id="6f580-126">**[勘定科目インテリジェンスの定義]** ページの **[ビルトイン勘定科目の種類]** 列で、勘定科目の種類を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-126">On the **Define Account Intelligence** page, in the **Built-In Account Types** column, select the account type, and then click **Next**.</span></span>  
  
     <span data-ttu-id="6f580-127">勘定科目の種類は、 **[基になるテーブルの勘定科目の種類]** 列に表示されている、基になるテーブルの勘定科目の種類に対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f580-127">The account type must correspond to the account type of the source table that is listed in the **Source Table Account Types** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f580-128">**[勘定科目インテリジェンスの定義]** ページは、ウィザードの **[ディメンション属性の選択]** ページで、ディメンション属性 **[勘定科目の種類]** を定義した場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f580-128">The **Define Account Intelligence** page appears if you defined an **Account Type** dimension attribute on the **Select Dimension Attributes** page of the wizard.</span></span>  
  
7.  <span data-ttu-id="6f580-129">**[ウィザードの完了]** ページで、新しいディメンションの名前を入力し、ディメンション構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="6f580-129">On the **Completing the Wizard** page, enter a name for the new dimension and review the dimension structure.</span></span> <span data-ttu-id="6f580-130">変更が必要な場合は **[戻る]** をクリックします。変更が必要ない場合は **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f580-130">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f580-131">ディメンション ウィザードを完了した後、ディメンション デザイナーを使用して、ディメンションの属性と階層を追加、削除、および設定できます。</span><span class="sxs-lookup"><span data-stu-id="6f580-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f580-132">参照</span><span class="sxs-lookup"><span data-stu-id="6f580-132">See Also</span></span>  
 [<span data-ttu-id="6f580-133">既存のテーブルを使用したディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="6f580-133">Create a Dimension by Using an Existing Table</span></span>](create-a-dimension-by-using-an-existing-table.md)  
  
  
