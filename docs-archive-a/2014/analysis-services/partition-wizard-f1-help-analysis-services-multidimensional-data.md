---
title: パーティションウィザードの F1 ヘルプ (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Partition Wizard
ms.assetid: 3b6d7053-aeef-4d9e-af70-f5b40256e859
author: minewiskan
ms.author: owend
ms.openlocfilehash: fa8c0e94c2b18ffbd1228752bd7cb4ad4f684acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634102"
---
# <a name="partition-wizard-f1-help-analysis-services---multidimensional-data"></a><span data-ttu-id="b53ad-102">パーティション ウィザードの F1 ヘルプ (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="b53ad-102">Partition Wizard F1 Help (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b53ad-103">パーティション ウィザードを使用すると、キューブ内のメジャー グループにパーティションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b53ad-103">You can use the Partition Wizard to define partitions for a measure group in a cube.</span></span> <span data-ttu-id="b53ad-104">既定では、キューブ内のメジャー グループ 1 つにつき 1 つのパーティションが定義されます。</span><span class="sxs-lookup"><span data-stu-id="b53ad-104">By default, a single partition is defined for each measure group in a cube.</span></span> <span data-ttu-id="b53ad-105">しかし、パーティションが大きくなるとアクセスと処理のパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b53ad-105">Access and processing performance, however, can degrade for large partitions.</span></span> <span data-ttu-id="b53ad-106">メジャー グループのデータの一部を含むパーティションを複数作成することにより、そのメジャー グループのアクセスおよび処理のパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="b53ad-106">By creating multiple partitions, each containing a portion of the data for a measure group, you can improve the access and processing performance for that measure group.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b53ad-107">**[基になる情報の指定]** ページまたは **[行の制限]** ページに重複する行がある場合、不正確なデータを含むパーティションが作成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b53ad-107">It is possible to create partitions that may contain incorrect data by including duplicate rows in the **Specify Source Information** or **Restrict Rows** pages.</span></span>  
  
 <span data-ttu-id="b53ad-108">パーティション ウィザードでは、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b53ad-108">The Partition Wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="b53ad-109">パーティションに使用するソース データ ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="b53ad-109">Selecting the data source view for the partition.</span></span>  
  
-   <span data-ttu-id="b53ad-110">パーティションに含めるレコードを選択するフィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="b53ad-110">Creating a filter for the records included in the partition.</span></span>  
  
-   <span data-ttu-id="b53ad-111">処理と格納場所の設定を行います。</span><span class="sxs-lookup"><span data-stu-id="b53ad-111">Setting the processing and storage locations.</span></span>  
  
-   <span data-ttu-id="b53ad-112">パーティションに名前を付けて、保存します。</span><span class="sxs-lookup"><span data-stu-id="b53ad-112">Naming and saving the partition.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b53ad-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b53ad-113">In This Section</span></span>  
  
-   [<span data-ttu-id="b53ad-114">ソース情報の指定 &#40;パーティションウィザード&#41;</span><span class="sxs-lookup"><span data-stu-id="b53ad-114">Specify Source Information &#40;Partition Wizard&#41;</span></span>](specify-source-information-partition-wizard.md)  
  
-   [<span data-ttu-id="b53ad-115">パーティションの制限ウィザード&#41;&#40;行の制限</span><span class="sxs-lookup"><span data-stu-id="b53ad-115">Restrict Rows &#40;Partition Wizard&#41;</span></span>](restrict-rows-partition-wizard.md)  
  
-   [<span data-ttu-id="b53ad-116">パーティションの処理と記憶域の場所の &#40;ウィザード&#41;</span><span class="sxs-lookup"><span data-stu-id="b53ad-116">Processing and Storage Locations &#40;Partition Wizard&#41;</span></span>](processing-and-storage-locations-partition-wizard.md)  
  
-   [<span data-ttu-id="b53ad-117">ウィザードの完了 &#40;パーティションウィザード&#41;</span><span class="sxs-lookup"><span data-stu-id="b53ad-117">Completing the Wizard &#40;Partition Wizard&#41;</span></span>](completing-the-wizard-partition-wizard.md)  
  
-   <span data-ttu-id="b53ad-118">[[リモートフォルダーの参照] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="b53ad-118">[Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53ad-119">参照</span><span class="sxs-lookup"><span data-stu-id="b53ad-119">See Also</span></span>  
 [<span data-ttu-id="b53ad-120">パーティション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="b53ad-120">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
