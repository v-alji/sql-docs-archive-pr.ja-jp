---
title: '[列マッピングの指定] ダイアログボックス (マイニング精度チャート) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ede835567f678f4152b3d1944f3c2c7160c6837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643528"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="ff30b-102">[列マッピングの指定] ダイアログ ボックス (マイニング精度チャート)</span><span class="sxs-lookup"><span data-stu-id="ff30b-102">Specify Column Mapping Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="ff30b-103">**[列マッピングの指定]** タブを使用して、外部データ ソースからテーブルを選択し、列をデータ マイニング モデルにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="ff30b-103">Use the **Specify Column Mapping** tab to select tables from an external data source and map the columns to a data mining model.</span></span> <span data-ttu-id="ff30b-104">次に外部データを使用してマイニング モデルの精度をテストして、その結果を精度チャートに表示します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-104">You can then use the external data to test the accuracy of a mining model and displays the results in the accuracy chart.</span></span>  
  
 <span data-ttu-id="ff30b-105">**詳細情報: 「** [テストおよび検証 &#40;データ マイニング&#41;](data-mining/testing-and-validation-data-mining.md)」</span><span class="sxs-lookup"><span data-stu-id="ff30b-105">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="ff30b-106">Options</span><span class="sxs-lookup"><span data-stu-id="ff30b-106">Options</span></span>  
 <span data-ttu-id="ff30b-107">**[マイニング構造]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-107">**Mining Structure**</span></span>  
 <span data-ttu-id="ff30b-108">テストする対象モデルを含む、選択されたマイニング構造を表示します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-108">Displays the selected mining structure that contains the model that you will test.</span></span>  
  
 <span data-ttu-id="ff30b-109">**[構造の選択]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-109">**Select Structure**</span></span>  
 <span data-ttu-id="ff30b-110">クリックして **[マイニング構造の選択]** ダイアログ ボックスを開き、別のマイニング構造を選択します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-110">Click to open the **Select Mining Structure** dialog box and select a different mining structure.</span></span>  
  
 <span data-ttu-id="ff30b-111">**[入力テーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-111">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="ff30b-112">リフト チャートの生成に使用するために選択された入力テーブルを表示します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-112">Displays the selected input tables that are used to generate the lift chart.</span></span> <span data-ttu-id="ff30b-113">モデルの精度のテストに使用するテスト データが含まれたテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-113">Select the table that contains the test data that you will use to test the accuracy of the models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff30b-114">ペインにテーブルが表示されない場合は、 **[ケース テーブルの選択]** をクリックし、データ ソース ビューからテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-114">If the pane does not contain any tables, click **Select Case Table** to add tables from a data source view.</span></span>  
  
 <span data-ttu-id="ff30b-115">**[テーブルの削除]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-115">**Remove Table**</span></span>  
 <span data-ttu-id="ff30b-116">選択されているテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-116">Removes the selected table.</span></span> <span data-ttu-id="ff30b-117">テーブルが選択されていないとき、または **[入力テーブルの選択]** ボックスの一覧にテーブルが表示されていないとき、このボタンは無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff30b-117">This button is disabled if a table has not been selected or if no tables are displayed in the **Select Input Tables** list.</span></span>  
  
 <span data-ttu-id="ff30b-118">**[ケース テーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-118">**Select Case Table**</span></span>  
 <span data-ttu-id="ff30b-119">クリックして **[テーブルの選択]** ダイアログ ボックスを開き、データ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-119">Click to open the **Select Table** dialog box and select a data source view.</span></span>  
  
 <span data-ttu-id="ff30b-120">**注** このボタンは、ケース テーブルが選択されていない場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff30b-120">**Note** This button appears only if a case table has not been selected.</span></span> <span data-ttu-id="ff30b-121">別のケース テーブルを選択できるようにこのボタンを有効にするには、すべての既存のテーブルを選択し、 **[テーブルの削除]** をクリックして、一覧を消去します。</span><span class="sxs-lookup"><span data-stu-id="ff30b-121">To enable the button so that you can select a different case table, clear the list by selecting all existing tables and then clicking **Remove Table**.</span></span>  
  
 <span data-ttu-id="ff30b-122">**[入れ子になったテーブルの選択]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-122">**Select Nested Table**</span></span>  
 <span data-ttu-id="ff30b-123">**[テーブルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ff30b-123">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="ff30b-124">このボタンは、ケース テーブルが選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="ff30b-124">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="ff30b-125">関連付けられているマイニング構造に入れ子になったテーブルが含まれていない場合、このボタンは無効になります。</span><span class="sxs-lookup"><span data-stu-id="ff30b-125">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="ff30b-126">**[結合の変更]**</span><span class="sxs-lookup"><span data-stu-id="ff30b-126">**Modify Join**</span></span>  
 <span data-ttu-id="ff30b-127">**[入れ子になった結合の指定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ff30b-127">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="ff30b-128">このボタンは、入れ子になったテーブルが選択されている場合にのみアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="ff30b-128">This button is active only if the nested table is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff30b-129">参照</span><span class="sxs-lookup"><span data-stu-id="ff30b-129">See Also</span></span>  
 <span data-ttu-id="ff30b-130">[テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ff30b-130">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="ff30b-131">マイニング精度チャートデザイナー &#40;データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="ff30b-131">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
