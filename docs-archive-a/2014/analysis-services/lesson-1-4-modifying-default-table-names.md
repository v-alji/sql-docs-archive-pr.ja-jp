---
title: 既定のテーブル名の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 254f797be95f60211983400b019415431d4cf39c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631308"
---
# <a name="modifying-default-table-names"></a><span data-ttu-id="ec278-102">既定のテーブル名の変更</span><span class="sxs-lookup"><span data-stu-id="ec278-102">Modifying Default Table Names</span></span>
  <span data-ttu-id="ec278-103">データ ソース ビューのオブジェクトの **FriendlyName** プロパティ値を変更することで、オブジェクトをわかりやすく、また使いやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="ec278-103">You can change the value of the **FriendlyName** property for objects in the data source view to make them easier to notice and use.</span></span>  
  
 <span data-ttu-id="ec278-104">この実習では、データ ソース ビューの各テーブルの表示名から "**Dim**" プレフィックスと "**Fact**" プレフィックスを削除して、わかりやすい名前にします。</span><span class="sxs-lookup"><span data-stu-id="ec278-104">In the following task, you will change the friendly name of each table in the data source view by removing the "**Dim**" and "**Fact**" prefixes from these tables.</span></span> <span data-ttu-id="ec278-105">これにより、次のレッスンで定義するキューブ オブジェクトとディメンション オブジェクトがわかりやすく (使いやすく) なります。</span><span class="sxs-lookup"><span data-stu-id="ec278-105">This will make the cube and dimension objects (that you will define in the next lesson) easier to notice and use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec278-106">より簡単に使用できるようにするため、列の表示名を変更して、計算列を定義し、データ ソース ビューのテーブルやビューを結合します。</span><span class="sxs-lookup"><span data-stu-id="ec278-106">You can also change the friendly names of columns, define calculated columns, and join tables or views in the data source view to make them easier to use.</span></span>  
  
### <a name="to-modify-the-default-name-of-a-table"></a><span data-ttu-id="ec278-107">テーブルの既定の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="ec278-107">To modify the default name of a table</span></span>  
  
1.  <span data-ttu-id="ec278-108">**データ ソース ビュー デザイナー** の **[テーブル]** ペインで **FactInternetSales** テーブルを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec278-108">In the **Tables** pane of **Data Source View Designer**, right-click the **FactInternetSales** table, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ec278-109">Microsoft Visual Studio ウィンドウの右側の [プロパティ] ウィンドウが表示されていない場合は、[プロパティ] ウィンドウのタイトル バーにある **[自動的に隠す]** ボタンをクリックして、[プロパティ] ウィンドウが常に開いたままになるようにします。</span><span class="sxs-lookup"><span data-stu-id="ec278-109">If the Properties window on the right side of the Microsoft Visual Studio window is not displayed, click the **Auto Hide** button on the title bar of the Properties window so that this window remains visible.</span></span>  
  
     <span data-ttu-id="ec278-110">データ ソース ビューの各テーブルのプロパティを変更するときは、[プロパティ] ウィンドウを開いたままにしておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="ec278-110">It is easier to change the properties for each table in the data source view when the Properties window remains open.</span></span> <span data-ttu-id="ec278-111">**[自動的に隠す]** ボタンをクリックしてウィンドウを開いたまま固定しておかないと、 **ダイアグラム** ペイン内の別のオブジェクトをクリックしたときに [プロパティ] ウィンドウが閉じてしまいます。</span><span class="sxs-lookup"><span data-stu-id="ec278-111">If you do not pin the window open by using the **Auto Hide** button, the window will close when you click a different object in the **Diagram** pane.</span></span>  
  
3.  <span data-ttu-id="ec278-112">**FactInternetSales**オブジェクトの**FriendlyName**プロパティをに変更 *`InternetSales`* します。</span><span class="sxs-lookup"><span data-stu-id="ec278-112">Change the **FriendlyName** property for the **FactInternetSales** object to *`InternetSales`*.</span></span>  
  
     <span data-ttu-id="ec278-113">**FriendlyName** 以外のセルをクリックすると、変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec278-113">When you click away from the cell for the **FriendlyName** property, the change is applied.</span></span> <span data-ttu-id="ec278-114">次のレッスンでは、このファクト テーブルを基にしてメジャー グループを定義します。</span><span class="sxs-lookup"><span data-stu-id="ec278-114">In the next lesson, you will define a measure group that is based on this fact table.</span></span> <span data-ttu-id="ec278-115">このレッスンで表示名を変更したので、次に作成するファクト テーブルの名前も FactInternetSales ではなく InternetSales になります。</span><span class="sxs-lookup"><span data-stu-id="ec278-115">The name of the fact table will be InternetSales instead of FactInternetSales because of the change you made in this lesson.</span></span>  
  
4.  <span data-ttu-id="ec278-116">**[テーブル]** ペインで **[DimProduct]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec278-116">Click **DimProduct** in the **Tables** pane.</span></span> <span data-ttu-id="ec278-117">プロパティウィンドウで、 **FriendlyName**プロパティをに変更し *`Product`* ます。</span><span class="sxs-lookup"><span data-stu-id="ec278-117">In the Properties window, change the **FriendlyName** property to *`Product`*.</span></span>  
  
5.  <span data-ttu-id="ec278-118">データ ソース ビューの他のテーブルについても、同じ方法で **FriendlyName** プロパティを変更します。つまり、**Dim**プレフィックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="ec278-118">Change the **FriendlyName** property of each remaining table in the data source view in the same way, to remove the "**Dim**" prefix.</span></span>  
  
6.  <span data-ttu-id="ec278-119">操作が完了したら、 **[自動的に隠す]** ボタンをクリックして、[プロパティ] ウィンドウを再び非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ec278-119">When you have finished, click the **Auto Hide** button to hide the Properties window again.</span></span>  
  
7.  <span data-ttu-id="ec278-120">**[ファイル]** メニューまたは [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のツール バーで、 **[すべてを保存]** をクリックして、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトに対するこの時点までの変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="ec278-120">On the **File** menu, or on the toolbar of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Save All** to save the changes you have made to this point in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="ec278-121">ここでチュートリアルを終了しても、後でこの続きから再開できます。</span><span class="sxs-lookup"><span data-stu-id="ec278-121">You can stop the tutorial here if you want and resume it later.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="ec278-122">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="ec278-122">Next Lesson</span></span>  
 [<span data-ttu-id="ec278-123">レッスン 2: キューブの定義と配置</span><span class="sxs-lookup"><span data-stu-id="ec278-123">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec278-124">参照</span><span class="sxs-lookup"><span data-stu-id="ec278-124">See Also</span></span>  
 <span data-ttu-id="ec278-125">[多次元モデルのデータソースビュー](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="ec278-125">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="ec278-126">データ ソース ビューのプロパティの変更 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ec278-126">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
