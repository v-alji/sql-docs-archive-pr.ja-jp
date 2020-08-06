---
title: マイニング構造からのマイニングモデルの削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72c79dcdccf6225b8e75144f8b090dcab7506c10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644231"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a><span data-ttu-id="28ae1-102">マイニング構造からのマイニング モデルの削除</span><span class="sxs-lookup"><span data-stu-id="28ae1-102">Delete a Mining Model from a Mining Structure</span></span>
  <span data-ttu-id="28ae1-103">データ マイニング デザイナー、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または DMX ステートメントを使用すると、マイニング モデルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="28ae1-103">You can delete mining models by using Data Mining Designer, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or by using DMX statements.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a><span data-ttu-id="28ae1-104">SQL Server データ ツールを使用したマイニング モデルの削除</span><span class="sxs-lookup"><span data-stu-id="28ae1-104">Delete a mining model using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="28ae1-105">**の** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="28ae1-105">Select the **Mining Models** tab in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="28ae1-106">削除するモデルを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28ae1-106">Right-click the model that you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="28ae1-107">**[オブジェクトの削除]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="28ae1-107">The **Delete Objects** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="28ae1-108">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28ae1-108">Click **OK**.</span></span>  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a><span data-ttu-id="28ae1-109">SQL Server Management Studio を使用したマイニング モデルの削除</span><span class="sxs-lookup"><span data-stu-id="28ae1-109">Delete a mining model using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="28ae1-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、モデルが含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="28ae1-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the model.</span></span>  
  
2.  <span data-ttu-id="28ae1-111">**[マイニング構造]** を展開し、 **[マイニング モデル]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="28ae1-111">Expand **Mining Structures**, and then expand **Mining Models**.</span></span>  
  
3.  <span data-ttu-id="28ae1-112">削除するモデルを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28ae1-112">Right-click the model you want to delete, and select **Delete**.</span></span>  
  
     <span data-ttu-id="28ae1-113">モデルを削除してもトレーニング データは削除されず、モデルのトレーニング時に作成したメタデータとパターンのみ削除されます。</span><span class="sxs-lookup"><span data-stu-id="28ae1-113">Deleting the model does not delete the training data, only the metadata and any patterns created when you trained the model.</span></span>  
  
### <a name="delete-a-mining-model-using-dmx"></a><span data-ttu-id="28ae1-114">DMX を使用したマイニング モデルの削除</span><span class="sxs-lookup"><span data-stu-id="28ae1-114">Delete a mining model using DMX</span></span>  
  
-   [<span data-ttu-id="28ae1-115">DROP MINING MODEL &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="28ae1-115">DROP MINING MODEL &#40;DMX&#41;</span></span>](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a><span data-ttu-id="28ae1-116">参照</span><span class="sxs-lookup"><span data-stu-id="28ae1-116">See Also</span></span>  
 [<span data-ttu-id="28ae1-117">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="28ae1-117">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
