---
title: 依存関係ネットワーク内の特定のノードを検索する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nodes [Analysis Services]
- dependency network nodes [Analysis Services]
- Mining Model Viewer [Analysis Services], dependency network nodes
ms.assetid: 37c54602-ab25-48be-ae7a-59819deea8ed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d22d6201c48ac77de5ab1e86ebed276478de683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634729"
---
# <a name="find-a-specific-node-in-a-dependency-network"></a><span data-ttu-id="aed66-102">依存関係ネットワークでの特定のノードの検索</span><span class="sxs-lookup"><span data-stu-id="aed66-102">Find a Specific Node in a Dependency Network</span></span>
  <span data-ttu-id="aed66-103">マイニングモデルの依存関係ネットワークには [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多数のノードを含めることができるため、関心のあるデータを見つけるのが困難になります。</span><span class="sxs-lookup"><span data-stu-id="aed66-103">A dependency network in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mining model can contain many nodes, making it difficult to locate the data you are interested in.</span></span> <span data-ttu-id="aed66-104">データ マイニング デザイナーの **[依存関係ネットワーク]** タブでは、 **[ノードの検索]** ダイアログ ボックスを使用して特定のノードを検索できるので、この問題を解決することができます。</span><span class="sxs-lookup"><span data-stu-id="aed66-104">To solve this problem, you can use the **Find Node** dialog box on the **Dependency Network** tab of Data Mining Designer to search for a specific node.</span></span>  
  
### <a name="to-find-a-specific-node-in-a-dependency-network"></a><span data-ttu-id="aed66-105">依存関係ネットワークで特定のノードを検索するには</span><span class="sxs-lookup"><span data-stu-id="aed66-105">To find a specific node in a dependency network</span></span>  
  
1.  <span data-ttu-id="aed66-106">**の** データ マイニング デザイナー **の** [マイニング モデル ビューアー] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、マイニング モデル ビューアーの **[依存関係ネットワーク]** タブにあるツール バーの **[ノードの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aed66-106">On the **Mining Model Viewer** tab of **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Find Node** on the toolbar of the **Dependency Network** tab of the mining model viewer.</span></span>  
  
     <span data-ttu-id="aed66-107">**[ノードの検索]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="aed66-107">The **Find Node** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="aed66-108">**[以下を含むノード名]** ボックスに、検索するノードの名前の一部を入力します。</span><span class="sxs-lookup"><span data-stu-id="aed66-108">In the **Node name contains** box, enter part of the name of the node for which you want to search.</span></span>  
  
     <span data-ttu-id="aed66-109">ノードの一覧がフィルター選択され、検索パスの一部を含んでいるノードだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aed66-109">The list of nodes is filtered to display only those nodes that contain part of the search path.</span></span>  
  
3.  <span data-ttu-id="aed66-110">一覧から正しいノードを選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aed66-110">Select the correct node from the list, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed66-111">参照</span><span class="sxs-lookup"><span data-stu-id="aed66-111">See Also</span></span>  
 [<span data-ttu-id="aed66-112">マイニング モデル ビューアーのタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="aed66-112">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
