---
title: DirectQuery デザインモードを有効にする (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ccd2dc88f447e78f6558565a89accc341eac37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641880"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a><span data-ttu-id="29609-102">DirectQuery デザイン モードの有効化 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="29609-102">Enable DirectQuery Design Mode (SSAS Tabular)</span></span>
  <span data-ttu-id="29609-103">DirectQuery モードでモデルを作成するには、最初にデザイン時環境を変更して、DirectQuery モードのユーザーがサポートされるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29609-103">To create a model in DirectQuery mode, you must first change the design-time environment so that it supports the user of DirectQuery mode.</span></span> <span data-ttu-id="29609-104">この場合、デザイナーで以下の操作も行われます。</span><span class="sxs-lookup"><span data-stu-id="29609-104">When you do so, the designer will also do the following:</span></span>  
  
-   <span data-ttu-id="29609-105">DirectQuery の配置プロパティの使用を有効にします。</span><span class="sxs-lookup"><span data-stu-id="29609-105">Enable the use of the DirectQuery deployment properties.</span></span>  
  
-   <span data-ttu-id="29609-106">デザインにキャッシュを使用するハイブリッド モードで稼働するようにワークスペース データベースを変更します。</span><span class="sxs-lookup"><span data-stu-id="29609-106">Change the workspace database to run in a hybrid mode that uses the cache for designing.</span></span> <span data-ttu-id="29609-107">実際にモデルを配置すると、モードはプロジェクトの配置プロパティで指定された値に戻されます。</span><span class="sxs-lookup"><span data-stu-id="29609-107">When you actually deploy the model, the mode will be changed back to whatever value you specified in the project deployment properties.</span></span>  
  
-   <span data-ttu-id="29609-108">DirectQuery モードと互換性のないデザイン機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="29609-108">Disable design features that are incompatible with DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="29609-109">既存のモデルを検証します。</span><span class="sxs-lookup"><span data-stu-id="29609-109">Validate the existing model.</span></span>  
  
 <span data-ttu-id="29609-110">この手順では、デザイナーで DirectQuery モードを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="29609-110">This procedure describes how to enable DirectQuery mode in the designer.</span></span>  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a><span data-ttu-id="29609-111">モデルで DirectQuery の使用を有効にするには</span><span class="sxs-lookup"><span data-stu-id="29609-111">To enable use of DirectQuery in a model</span></span>  
  
1.  <span data-ttu-id="29609-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="29609-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the solution file.</span></span>  
  
2.  <span data-ttu-id="29609-113">オブジェクト エクスプローラーで、Model.bim ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="29609-113">In Object Explorer, double-click the Model.bim file.</span></span>  
  
3.  <span data-ttu-id="29609-114">**[プロパティ]** ペインで、 **DirectQueryMode**プロパティを **On**に変更します。</span><span class="sxs-lookup"><span data-stu-id="29609-114">In the **Properties** pane, change the property, **DirectQueryMode**, to **On**.</span></span>  
  
4.  <span data-ttu-id="29609-115">エラーが発生した場合は、Visual Studio で**エラー一覧**を開き、モデルが DirectQuery モードに切り替わるのを妨げている問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="29609-115">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being switched to DirectQuery mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29609-116">参照</span><span class="sxs-lookup"><span data-stu-id="29609-116">See Also</span></span>  
 [<span data-ttu-id="29609-117">DirectQuery モード &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="29609-117">DirectQuery Mode &#40;SSAS Tabular&#41;</span></span>](directquery-mode-ssas-tabular.md)  
  
  
