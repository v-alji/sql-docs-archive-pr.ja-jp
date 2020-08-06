---
title: 配置されたキューブの参照 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 849c6109-1453-4fe4-a892-c49a982cfadb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b876c8b2876aaf4ad28b0f4ea3fb8bab32cd787b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642393"
---
# <a name="browsing-the-deployed-cube"></a><span data-ttu-id="a8398-102">配置したキューブの表示</span><span class="sxs-lookup"><span data-stu-id="a8398-102">Browsing the Deployed Cube</span></span>
  <span data-ttu-id="a8398-103">この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを表示します。</span><span class="sxs-lookup"><span data-stu-id="a8398-103">In the following task, you browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="a8398-104">分析で複数のディメンションにわたってメジャーを比較するため、データの参照には Excel のピボットテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8398-104">Because our analysis compares measure across multiple dimensions, you will use an Excel PivotTable to browse your data.</span></span> <span data-ttu-id="a8398-105">ピボットテーブルを使用すると、顧客、日付、および製品情報を異なる軸に配置して、特定の期間、顧客の人口統計、および製品ラインにわたって見たときに、Internet Sales がどのように変化するかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a8398-105">Using a PivotTable lets you place customer, date, and product information on different axes so that you can see how Internet Sales change when viewed across specific time periods, customer demographics, and product lines.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="a8398-106">配置したキューブを表示するには</span><span class="sxs-lookup"><span data-stu-id="a8398-106">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="a8398-107">のキューブデザイナーに切り替えるには、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ソリューションエクスプローラーの [**キューブ**] フォルダーにある [ \*\* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] チュートリアル\*\*] キューブをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8398-107">To switch to Cube Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], double-click the **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial** cube in the **Cubes** folder of the Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="a8398-108">**[ブラウザー]** タブを開き、キューブ デザイナーのツール バーにある **[再接続]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8398-108">Open the **Browser** tab, and then click the **Reconnect** button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="a8398-109">Excel アイコンをクリックして Excel を起動し、データ ソースとしてワークスペース データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8398-109">Click the Excel icon to launch Excel using the workspace database as the data source.</span></span> <span data-ttu-id="a8398-110">接続を有効にするように求めるメッセージが表示されたら、 **[有効]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8398-110">When prompted to enable connections, click **Enable**.</span></span>  
  
4.  <span data-ttu-id="a8398-111">ピボットテーブル フィールド リストで **[Internet Sales]** を展開し、 **Sales Amount** メジャーを **[値]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a8398-111">In the PivotTable Field List, expand **Internet Sales**, and then drag the **Sales Amount** measure to the **Values** area.</span></span>  
  
5.  <span data-ttu-id="a8398-112">ピボットテーブル フィールド リストで **Product**を展開します。</span><span class="sxs-lookup"><span data-stu-id="a8398-112">In the PivotTable Field List, expand **Product**.</span></span>  
  
6.  <span data-ttu-id="a8398-113">**Product Model Lines** ユーザー階層を **[列]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a8398-113">Drag the **Product Model Lines** user hierarchy to the **Columns** area.</span></span>  
  
7.  <span data-ttu-id="a8398-114">ピボットテーブル フィールド リストで **[Customer]** を展開し、 **[Location]** を展開します。次に、Customer ディメンション内の [Location] 表示フォルダーにある **[Customer Geography]** 階層を **[行]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a8398-114">In the PivotTable Field List, expand **Customer**, expand **Location**, and then drag the **Customer Geography** hierarchy from the Location display folder in the Customer dimension to the **Rows** area.</span></span>  
  
8.  <span data-ttu-id="a8398-115">ピボットテーブル フィールド リストで **[Order Date]** を展開し、 **[Order Date.Calendar Date]** 階層を **[レポート フィルター]** 領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a8398-115">In the PivotTable Field List, expand **Order Date**, and then drag the **Order Date.Calendar Date** hierarchy to the **Report Filter** area.</span></span>  
  
9. <span data-ttu-id="a8398-116">データ ペインで、 **Order Date.Calendar Date** フィルターの右側にある矢印をクリックし、 **[(すべて)]** レベルのチェック ボックスをオフにします。次に、 **[2006]**、 **[H1 CY 2006]**、 **[Q1 CY 2006]** の順に展開し、 **[February 2006]** チェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8398-116">Click the arrow to the right of the **Order Date.Calendar Date** filter in the data pane, clear the check box for the **(All)** level, expand **2006**, expand **H1 CY 2006**, expand **Q1 CY 2006**, select the check box for **February 2006**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a8398-117">次の図のように、2006 年 2 月におけるインターネットでの売上が、地域別および製品ライン別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8398-117">Internet sales by region and product line for the month of February, 2006 appear as shown in the following image.</span></span>  
  
     <span data-ttu-id="a8398-118">![地域および製品ラインごとのインターネット販売](../../2014/tutorials/media/l3-cube-browser-finish.gif "地域および製品ラインごとのインターネット販売")</span><span class="sxs-lookup"><span data-stu-id="a8398-118">![Internet sales by region and product line](../../2014/tutorials/media/l3-cube-browser-finish.gif "Internet sales by region and product line")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="a8398-119">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="a8398-119">Next Lesson</span></span>  
 [<span data-ttu-id="a8398-120">レッスン 4:高度な属性およびディメンションのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="a8398-120">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  
