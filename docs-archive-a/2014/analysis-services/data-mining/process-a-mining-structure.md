---
title: マイニング構造を処理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d25a927ae61ee5ffadf4ca21073a1c04cdb542
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718957"
---
# <a name="process-a-mining-structure"></a><span data-ttu-id="1e4b5-102">マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="1e4b5-102">Process a Mining Structure</span></span>
  <span data-ttu-id="1e4b5-103">マイニング構造に関連付けられているマイニング モデルを参照したり使用したりする前に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置してマイニング構造とマイニング モデルを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-103">Before you can browse or work with the mining models that are associated with a mining structure, you have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span> <span data-ttu-id="1e4b5-104">また、マイニング構造またはマイニング モデルに変更を加えると、それらを再配置し、処理するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-104">Also, if you make a change to the mining structure or mining models, you will be prompted to redeploy and process them.</span></span> <span data-ttu-id="1e4b5-105">**のデータ マイニング デザイナーの** [マイニング構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] タブで構造を処理すると、関連するモデルもすべて処理されます。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-105">Processing the structure in the **Mining Structure** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] processes all the associated models.</span></span>  
  
 <span data-ttu-id="1e4b5-106">マイニング構造は、次のツールを使用して処理できます。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-106">You can process a mining structure by using these tools:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   <span data-ttu-id="1e4b5-107">XMLA: Process コマンド</span><span class="sxs-lookup"><span data-stu-id="1e4b5-107">XMLA: Process command</span></span>  
  
 <span data-ttu-id="1e4b5-108">個々のモデルを処理する方法の詳細については、「 [マイニング モデルの処理](process-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-108">For information about how to process individual models, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a><span data-ttu-id="1e4b5-109">SQL Server データ ツールを使用してマイニング構造および関連するすべてのマイニング モデルを処理するには</span><span class="sxs-lookup"><span data-stu-id="1e4b5-109">To process a mining structure and all associated mining models using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="1e4b5-110">**の** [マイニング モデル] **メニュー項目から** [マイニング構造および全モデルの処理] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を選択します。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-110">Select **Process Mining Structure and All Models** from the **Mining Model** menu item in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
     <span data-ttu-id="1e4b5-111">マイニング構造に変更を加えた場合は、マイニング モデルを処理する前にマイニング構造を再配置するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-111">If you made changes to the structure, you will be prompted to redeploy the structure before processing the models.</span></span> <span data-ttu-id="1e4b5-112">**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-112">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="1e4b5-113">[**マイニング構造の処理- \<structure> \*\* ] ダイアログボックスで [**実行\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-113">Click **Run** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
     <span data-ttu-id="1e4b5-114">**[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-114">The **Process Progress** dialog box opens to display the details of model processing.</span></span>  
  
3.  <span data-ttu-id="1e4b5-115">モデルの処理が完了したら、 **[処理の進行状況]** ダイアログ ボックスの **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-115">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="1e4b5-116">[**マイニング構造の処理- \<structure> \*\* ] ダイアログボックスで [**閉じる\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e4b5-116">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4b5-117">参照</span><span class="sxs-lookup"><span data-stu-id="1e4b5-117">See Also</span></span>  
 [<span data-ttu-id="1e4b5-118">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="1e4b5-118">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
