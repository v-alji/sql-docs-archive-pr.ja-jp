---
title: 入れ子になったテーブルデータを精度チャートの入力として使用する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97d5bbd75d09b1a9e4276c4723ad6986dbabf9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631334"
---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a><span data-ttu-id="402df-102">入れ子になったテーブルのデータを精度チャートの入力として使用する方法</span><span class="sxs-lookup"><span data-stu-id="402df-102">Using Nested Table Data as an Input for an Accuracy Chart</span></span>
  <span data-ttu-id="402df-103">外部データを使用してマイニング モデルの精度をテストする際、マイニング モデルに入れ子になったテーブルが含まれている場合は、外部データにもケース テーブルと関連する入れ子になったテーブルが格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="402df-103">When you test the accuracy of a mining model by using external data, if the mining model contains nested tables, the external data must also contain a case table and an associated nested table.</span></span>  
  
 <span data-ttu-id="402df-104">このトピックでは、モデルのテストに使用する入れ子になったテーブルを操作する方法、モデルおよび外部データの入れ子になったテーブルとケース テーブルをマップする方法、および入れ子になったテーブルにフィルターを適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="402df-104">This topic describes how to work with nested tables used for model testing, how to map nested and case tables in the mode and in the external data, and how to apply a filter to a nested table.</span></span>  
  
 <span data-ttu-id="402df-105">入れ子になったテーブルを操作するときは、次のヒントに留意してください。</span><span class="sxs-lookup"><span data-stu-id="402df-105">When working with nested tables, keep in mind these tips:</span></span>  
  
-   <span data-ttu-id="402df-106">**[マイニング モデルのテスト ケースを使用する]** または **[マイニング構造のテスト ケースを使用する]** というオプションを選択すると、ケース テーブルまたは入れ子になったテーブルを指定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="402df-106">If you select the option **Use mining model test cases** or **Use mining structure test cases**, you do not need to specify a case table or nested table.</span></span> <span data-ttu-id="402df-107">これらのオプションを使用すると、テスト データの定義がマイニング構造に格納され、精度チャートの作成時にそのテスト データが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="402df-107">With those options, the definition of the test data is stored in the mining structure and the test data is automatically selected when you create the accuracy chart.</span></span>  
  
-   <span data-ttu-id="402df-108">データ ソースのケース テーブルと入れ子になったテーブルとの間に既にリレーションシップが存在する場合、マイニング構造の列は入力テーブル内の同じ名前の列に自動的にマップされます。</span><span class="sxs-lookup"><span data-stu-id="402df-108">If a relationship already exists between the case and nested table in the data source, the columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
-   <span data-ttu-id="402df-109">入れ子になったテーブルはケース テーブルを指定しないと選択できません。</span><span class="sxs-lookup"><span data-stu-id="402df-109">You cannot select a nested table until you have specified the case table.</span></span> <span data-ttu-id="402df-110">さらに、マイニング モデルでケース テーブルと入れ子になったテーブル構造を使用しない限り、入れ子になったテーブルを入力として指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="402df-110">Also, you cannot specify a nested table as an input unless the mining model also uses a case table and nested table structure.</span></span>  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a><span data-ttu-id="402df-111">入れ子になったテーブルを精度チャートの入力として使用する</span><span class="sxs-lookup"><span data-stu-id="402df-111">Use a nested table as input to an accuracy chart</span></span>  
  
1.  <span data-ttu-id="402df-112">マイニング構造をダブルクリックしてデータ マイニング デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="402df-112">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="402df-113">**[マイニング精度チャート]** タブを選択し、次に **[入力の選択]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="402df-113">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="402df-114">**[精度チャートに使用するデータセットの選択]** で、 **[別のデータセットを指定する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="402df-114">In **Select data set to be used for accuracy chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="402df-115">参照ボタン ([. **..])** をクリックして、現在のサーバー上のデータソースビューの一覧から外部データセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="402df-115">Click the browse button **(...)** to choose the external data set from a list of data source views on the current server.</span></span>  
  
5.  <span data-ttu-id="402df-116">**[ケース テーブルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="402df-116">Click **Select Case Table**.</span></span> <span data-ttu-id="402df-117">**[テーブルの選択]** ダイアログ ボックスで、ケース データが含まれているテーブルをデータ ソース ビューから選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="402df-117">In the **Select Table** dialog box, choose the table from the data source view that contains the case data, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="402df-118">**[入れ子になったテーブルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="402df-118">Click **Select Nested Table**.</span></span> <span data-ttu-id="402df-119">**[テーブルの選択]** ダイアログ ボックスで、入れ子になったデータが含まれているテーブルを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="402df-119">In the **Select Table** dialog box, select the table that contains the nested data, and then click **OK**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="402df-120">入れ子になったテーブルとケース テーブル間のリレーションシップを変更する必要がある場合は、 **[結合の変更]** をクリックして **[リレーションシップの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="402df-120">If you need to modify the relationship between the nested table and the case table, click **Modify Join** to open the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402df-121">参照</span><span class="sxs-lookup"><span data-stu-id="402df-121">See Also</span></span>  
 <span data-ttu-id="402df-122">[モデルテストデータを選択してマップする](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="402df-122">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="402df-123">モデルのテスト データへのフィルターの適用</span><span class="sxs-lookup"><span data-stu-id="402df-123">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
  
