---
title: DirectQuery パーティションの変更 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9df1e66-dd23-41b4-95eb-af110d10eda4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 43d14785f72d9bfe6406e2b81d3f1b97e9b7cc2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634165"
---
# <a name="change-the-directquery-partition-ssas-tabular"></a><span data-ttu-id="75621-102">DirectQuery パーティションの変更 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="75621-102">Change the DirectQuery Partition (SSAS Tabular)</span></span>
  <span data-ttu-id="75621-103">テーブル内で DirectQuery パーティションとして指定できるパーティションは 1 つだけであるため、Analysis Services ではテーブルに作成された最初のパーティションが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="75621-103">Because only one partition in a table can be designated as the DirectQuery partition, by default, Analysis Services uses the first partition that was created in the table.</span></span> <span data-ttu-id="75621-104">モデル プロジェクトの作成時に、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の [パーティション マネージャー] ダイアログ ボックスを使用して DirectQuery パーティションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="75621-104">During model project authoring, you can change the DirectQuery partition by using the Partition Manager dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="75621-105">配置済みのモデルでは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用して DirectQuery パーティションを変更できます</span><span class="sxs-lookup"><span data-stu-id="75621-105">For deployed models, you can change the DirectQuery partition by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="change-the-directquery-partition-for-a-tabular-model-project"></a><span data-ttu-id="75621-106">テーブル モデル プロジェクトの DirectQuery パーティションの変更</span><span class="sxs-lookup"><span data-stu-id="75621-106">Change the DirectQuery partition for a tabular model project</span></span>  
  
1.  <span data-ttu-id="75621-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のモデル デザイナーで、パーティション テーブルが含まれているテーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75621-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in the model designer, click on the table (tab) that contains the partitioned table.</span></span>  
  
2.  <span data-ttu-id="75621-108">**[テーブル]** メニューをクリックし、 **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75621-108">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="75621-109">**[パーティション マネージャー]** で、現在の直接クエリ パーティションであるパーティションはパーティション名に **(DirectQuery)** というプレフィックスで示されます。</span><span class="sxs-lookup"><span data-stu-id="75621-109">In **Partition Manager**, the partition that is the current Direct Query partition in indicated by the prefix **(DirectQuery)** on the partition name.</span></span>  
  
     <span data-ttu-id="75621-110">**[パーティション]** ボックスの一覧で別のパーティションを選択し、 **[DirectQuery として設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75621-110">Select a different partition from the **Partitions** list, and then click **Set as DirectQuery**.</span></span> <span data-ttu-id="75621-111">**[DirectQuery として設定]** ボタンは、現在の DirectQuery パーティションが選択されている場合は無効になり、モデルが直接 Direct Query モードに対して有効になっていない場合は表示されません。</span><span class="sxs-lookup"><span data-stu-id="75621-111">The **Set as DirectQuery** button is not enabled when the current DirectQuery partition is selected, and is not visible if the model has not been enabled for Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="75621-112">必要に応じて、処理オプションを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75621-112">If necessary, change the processing options, and then click **OK**.</span></span>  
  
### <a name="change-the-directquery-partition-for-a-deployed-tabular-model"></a><span data-ttu-id="75621-113">配置済みテーブル モデルの DirectQuery パーティションの変更</span><span class="sxs-lookup"><span data-stu-id="75621-113">Change the DirectQuery partition for a deployed tabular model</span></span>  
  
1.  <span data-ttu-id="75621-114">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーにモデル データベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="75621-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the model database in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="75621-115">**[テーブル]** ノードを展開し、パーティション分割されたテーブルを右クリックして **[パーティション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="75621-115">Expand the **Tables** node, then right-click the partitioned table, and then select **Partitions**.</span></span>  
  
     <span data-ttu-id="75621-116">DirectQuery モードで使用するように指定されたパーティションには、パーティション名にプレフィックス (DirectQuery) があります。</span><span class="sxs-lookup"><span data-stu-id="75621-116">The partition that is designated for use with DirectQuery mode has the prefix (DirectQuery) on the partition name.</span></span>  
  
3.  <span data-ttu-id="75621-117">別のパーティションに変更するには、 **[直接クエリ]** ツール バー アイコンをクリックして **[DirectQuery パーティションの設定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="75621-117">To change to a different partition, click the **Direct Query** toolbar icon to open the **Set DirectQuery Partition** dialog box.</span></span> <span data-ttu-id="75621-118">[直接クエリ] ツール バー アイコンは、直接クエリに対して有効になっていないモデルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="75621-118">The DirectQuery toolbar icon is not available on models that have not been enabled for Direct Query.</span></span>  
  
4.  <span data-ttu-id="75621-119">**[パーティション名]** ボックスの一覧から別のパーティションを選択し、必要に応じてパーティションの処理オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="75621-119">Choose a different partition from the **Partition Name** dropdown list, and then change processing options on the partition if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75621-120">参照</span><span class="sxs-lookup"><span data-stu-id="75621-120">See Also</span></span>  
 [<span data-ttu-id="75621-121">パーティション (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="75621-121">Partitions &#40;SSAS Tabular&#41;</span></span>](tabular-models/partitions-ssas-tabular.md)  
  
  
