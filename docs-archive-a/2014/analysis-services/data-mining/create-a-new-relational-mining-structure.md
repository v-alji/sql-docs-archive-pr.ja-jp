---
title: 新しいリレーショナルマイニング構造を作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b41dd3ac2e6144011c1b3acde27c4b5829a1661
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632794"
---
# <a name="create-a-new-relational-mining-structure"></a><span data-ttu-id="65b73-102">新しいリレーショナル マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="65b73-102">Create a New Relational Mining Structure</span></span>
  <span data-ttu-id="65b73-103">データマイニングウィザードを使用して、リレーショナルデータベースまたは他のソースのデータを使用して新しいマイニング構造を作成し、その構造と関連モデルをデータベースに保存し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="65b73-103">Use the Data Mining Wizard to create a new mining structure, using data from a relational database or other source, and then save the structure and any related models to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="to-create-a-relational-mining-structure"></a><span data-ttu-id="65b73-104">リレーショナル マイニング構造を作成するには</span><span class="sxs-lookup"><span data-stu-id="65b73-104">To create a relational mining structure</span></span>  
  
1.  <span data-ttu-id="65b73-105">ソリューション エクスプローラーで、 **プロジェクトの** [マイニング構造] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいマイニング構造]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-105">In Solution Explorer, right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure**.</span></span>  
  
     <span data-ttu-id="65b73-106">データ マイニング ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="65b73-106">The Data Mining Wizard opens.</span></span>  
  
2.  <span data-ttu-id="65b73-107">**[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="65b73-108">**[定義方法の選択]** ページで、 **[既存のリレーショナル データベースまたはデータ ウェアハウスを使用する]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-108">On the **Select the Definition Method** page, select **From existing relational database or data warehouse**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="65b73-109">**[データ マイニング技法の選択]** ページで、使用するデータ マイニング アルゴリズムを選択して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-109">On the **Select the Data Mining Technique** page, select the data mining algorithm that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="65b73-110">データ マイニング アルゴリズムの詳細については、「[データ マイニング アルゴリズム (Analysis Services - データ マイニング)](data-mining-algorithms-analysis-services-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65b73-110">For more information about data mining algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="65b73-111">**[データ ソース ビューの選択]** ページの **[使用できるデータ ソース ビュー]** で、使用するデータ ソース ビューをクリックしてから **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-111">On the **Select Data Source View** page, under **Available data source views**, click the data source view that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="65b73-112">データ ソース ビューの作成方法の詳細については、「 [多次元モデルのデータ ソース ビュー](../multidimensional-models/data-source-views-in-multidimensional-models.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65b73-112">For more information about creating a data source view, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
6.  <span data-ttu-id="65b73-113">**[テーブルの種類の指定]** ページの **[入力テーブル]** で、ケース テーブルと入れ子になったテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="65b73-113">On the **Specify Table Types** page, under **Input tables**, select a case table and a nested table.</span></span>  
  
7.  <span data-ttu-id="65b73-114">**[トレーニング データの指定]** ページの **[マイニング モデル構造]** で、キー列、入力列、予測可能列を選択します。</span><span class="sxs-lookup"><span data-stu-id="65b73-114">On the **Specify the Training Data** page, under **Mining model structure**, select the key, input, and predictable columns.</span></span>  
  
     <span data-ttu-id="65b73-115">予測可能列を選択した後、 **[候補検索]** ボタンをクリックすると **[関連列の提示]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="65b73-115">After you select the predictable column, you can click the **Suggest** button to open the **Suggest Related Columns** dialog box.</span></span> <span data-ttu-id="65b73-116">このダイアログ ボックスで **[OK]** をクリックして、提示された列を受け入れると、選択された列をマイニング構造に含めることができます。また、 **[入力]** 列で選択内容を変更してから、 **[OK]** をクリックしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="65b73-116">You can accept the suggested columns by clicking **OK** in this dialog box to include the selected columns in the mining structure, or you can change the selections in the **Input** column first, and then click **OK**.</span></span> <span data-ttu-id="65b73-117">提示された内容を無視するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-117">To ignore the suggestions, click **Cancel**.</span></span>  
  
8.  <span data-ttu-id="65b73-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="65b73-119">**[列のコンテンツおよびデータ型の指定]** ページの **[マイニング モデル構造]** では、各列のコンテンツの種類とデータ型を調整できます。</span><span class="sxs-lookup"><span data-stu-id="65b73-119">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, you can adjust the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65b73-120">**[検出]** をクリックすると、連続データまたは不連続なデータを含む列を自動的に検出できます。</span><span class="sxs-lookup"><span data-stu-id="65b73-120">You can click **Detect** to automatically detect whether a column contains continuous or discrete data.</span></span> <span data-ttu-id="65b73-121">このボタンをクリックすると、 **[コンテンツの種類]** と **[データ型]** 列で、列の内容とデータ型が更新されます。</span><span class="sxs-lookup"><span data-stu-id="65b73-121">After you click this button, the column content and data types will be updated in the **Content Type** and **Data Type** columns.</span></span> <span data-ttu-id="65b73-122">コンテンツの種類とデータ型の詳細については、「[コンテンツの種類 (データ マイニング)](content-types-data-mining.md)」および「[データ型 (データ マイニング)](data-types-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65b73-122">For more information about content types and data types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md) and [Data Types &#40;Data Mining&#41;](data-types-data-mining.md).</span></span>  
  
10. <span data-ttu-id="65b73-123">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-123">Click **Next**.</span></span>  
  
11. <span data-ttu-id="65b73-124">**[ウィザードの完了]** ページで、作成するマイニング構造とそれに関連した初期マイニング モデルの名前を指定し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65b73-124">On the **Completing the Wizard** page, provide a name for the mining structure and the related initial mining model that will be created, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b73-125">参照</span><span class="sxs-lookup"><span data-stu-id="65b73-125">See Also</span></span>  
 [<span data-ttu-id="65b73-126">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="65b73-126">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
