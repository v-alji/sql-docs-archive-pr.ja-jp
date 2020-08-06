---
title: '[ウィザードの完了] (ディメンションウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.finish.f1
ms.assetid: 1137740d-3063-4ab1-9cfe-8319194db937
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61f6bf16ea38ab88995ff06ba31a06feb976d900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634125"
---
# <a name="completing-the-wizard-dimension-wizard"></a><span data-ttu-id="135a6-102">[ウィザードの完了] (ディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="135a6-102">Completing the Wizard (Dimension Wizard)</span></span>
  <span data-ttu-id="135a6-103">**[ウィザードの完了]** ページを使用すると、次の手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="135a6-103">Use the **Completing the Wizard** page to do the following procedures:</span></span>  
  
-   <span data-ttu-id="135a6-104">ディメンションに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="135a6-104">Name the dimension.</span></span>  
  
-   <span data-ttu-id="135a6-105">**[完了]** をクリックしたときに行われる変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="135a6-105">Review the changes that will be made when **Finish** is clicked.</span></span>  
  
-   <span data-ttu-id="135a6-106">必要に応じて、ディメンションのサポートに必要なスキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="135a6-106">If necessary, generate the schema needed to support the dimension.</span></span>  
  
 <span data-ttu-id="135a6-107">**ディメンション ウィザードを開くには**</span><span class="sxs-lookup"><span data-stu-id="135a6-107">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="135a6-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラー**で、 **プロジェクトの** [ディメンション] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] フォルダーを右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="135a6-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="135a6-109">Options</span><span class="sxs-lookup"><span data-stu-id="135a6-109">Options</span></span>  
 <span data-ttu-id="135a6-110">**名前**</span><span class="sxs-lookup"><span data-stu-id="135a6-110">**Name**</span></span>  
 <span data-ttu-id="135a6-111">新しいディメンションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="135a6-111">Type the name of the new dimension.</span></span>  
  
 <span data-ttu-id="135a6-112">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="135a6-112">**Preview**</span></span>  
 <span data-ttu-id="135a6-113">新しいディメンション用に作成されるディメンションの属性と階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="135a6-113">Displays the dimension attributes and hierarchies to be created for the new dimension.</span></span>  
  
 <span data-ttu-id="135a6-114">**[今すぐスキーマを生成する]**</span><span class="sxs-lookup"><span data-stu-id="135a6-114">**Generate schema now**</span></span>  
 <span data-ttu-id="135a6-115">選択すると、ディメンションをサポートするために必要なスキーマを生成します。</span><span class="sxs-lookup"><span data-stu-id="135a6-115">Select to generate the schema needed to support the dimension.</span></span> <span data-ttu-id="135a6-116">このオプションを選択すると、スキーマ生成ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="135a6-116">Selecting this option opens the Schema Generation Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="135a6-117">このオプションは、**[作成方法の選択]** ページで **[データ ソースに時間テーブルを生成]** または **[データ ソースに時間テーブル以外のテーブルを生成]** をクリックした場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="135a6-117">This option appears only if you selected **Generate a time table in the data source** or **Generate a non-time table in the data source** on the **Select Creation Method** page.</span></span> <span data-ttu-id="135a6-118">詳細については、「[[作成方法の選択] (ディメンション ウィザード)](select-creation-method-dimension-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="135a6-118">For more information, see [Select Creation Method &#40;Dimension Wizard&#41;](select-creation-method-dimension-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="135a6-119">参照</span><span class="sxs-lookup"><span data-stu-id="135a6-119">See Also</span></span>  
 <span data-ttu-id="135a6-120">[ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="135a6-120">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="135a6-121">[ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="135a6-121">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="135a6-122">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="135a6-122">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
