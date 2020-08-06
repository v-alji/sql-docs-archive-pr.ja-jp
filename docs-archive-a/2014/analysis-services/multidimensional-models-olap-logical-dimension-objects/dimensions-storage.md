---
title: ディメンションストレージ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa68ebcfa8f4136bcd4a131842c852665ee9851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712593"
---
# <a name="dimension-storage"></a><span data-ttu-id="4517c-102">ディメンションのストレージ</span><span class="sxs-lookup"><span data-stu-id="4517c-102">Dimension Storage</span></span>
  <span data-ttu-id="4517c-103">のディメンション [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、次の2つのストレージモードをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4517c-103">Dimensions in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support two storage modes:</span></span>  
  
-   <span data-ttu-id="4517c-104">リレーショナル OLAP (ROLAP)</span><span class="sxs-lookup"><span data-stu-id="4517c-104">Relational OLAP (ROLAP)</span></span>  
  
-   <span data-ttu-id="4517c-105">多次元 OLAP (MOLAP)</span><span class="sxs-lookup"><span data-stu-id="4517c-105">Multidimensional OLAP (MOLAP)</span></span>  
  
 <span data-ttu-id="4517c-106">ストレージ モードにより、ディメンションのデータの位置と形式が決定されます。</span><span class="sxs-lookup"><span data-stu-id="4517c-106">The storage mode determines the location and form of a dimension's data.</span></span> <span data-ttu-id="4517c-107">MOLAP はディメンションの既定のストレージ モードです。</span><span class="sxs-lookup"><span data-stu-id="4517c-107">MOLAP is the default storage mode for dimensions.</span></span> <span data-ttu-id="4517c-108">**関連トピック:**[パーティションストレージモードと処理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span><span class="sxs-lookup"><span data-stu-id="4517c-108">**Related topics:**[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)</span></span>  
  
## <a name="molap"></a><span data-ttu-id="4517c-109">[MOLAP]</span><span class="sxs-lookup"><span data-stu-id="4517c-109">MOLAP</span></span>  
 <span data-ttu-id="4517c-110">MOLAP を使用するディメンションのデータは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの多次元構造に格納されます。</span><span class="sxs-lookup"><span data-stu-id="4517c-110">Data for a dimension that uses MOLAP is stored in a multidimensional structure in the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4517c-111">この多次元構造はディメンションが処理されるときに作成および設定されます。</span><span class="sxs-lookup"><span data-stu-id="4517c-111">This multidimensional structure is created and populated when the dimension is processed.</span></span> <span data-ttu-id="4517c-112">MOLAP ディメンションの方が、ROLAP ディメンションよりクエリ パフォーマンスは優れています。</span><span class="sxs-lookup"><span data-stu-id="4517c-112">MOLAP dimensions provide better query performance than ROLAP dimensions.</span></span>  
  
## <a name="rolap"></a><span data-ttu-id="4517c-113">[ROLAP]</span><span class="sxs-lookup"><span data-stu-id="4517c-113">ROLAP</span></span>  
 <span data-ttu-id="4517c-114">ROLAP を使用するディメンションのデータは、実際には、ディメンションを定義するために使用されるテーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4517c-114">Data for a dimension that uses ROLAP is actually stored in the tables used to define the dimension.</span></span> <span data-ttu-id="4517c-115">ROLAP ストレージ モードを使用すると、クエリ パフォーマンスの点で譲歩すれば、大量のデータを複製しなくても大きなディメンションをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="4517c-115">The ROLAP storage mode can be used to support large dimensions without duplicating large amounts of data, but at the expense of query performance.</span></span> <span data-ttu-id="4517c-116">ディメンションはそのディメンションを定義するために使用されるデータ ソース ビューのテーブルに直接依存しているので、ROLAP ストレージ モードは、リアルタイム OLAP もサポートします。</span><span class="sxs-lookup"><span data-stu-id="4517c-116">Because the dimension relies directly on the tables in the data source view used to define the dimension, the ROLAP storage mode also supports real-time OLAP.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4517c-117">ディメンションで ROLAP ストレージ モードが使用され、ディメンションが MOLAP ストレージを使用するキューブに含まれている場合は、元のテーブルのスキーマを変更したら、直ちにキューブを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4517c-117">If a dimension uses the ROLAP storage mode and the dimension is included in a cube that uses MOLAP storage, any schema changes to its source table must be followed by immediate processing of the cube.</span></span> <span data-ttu-id="4517c-118">直ちに処理しないと、キューブをクエリしたときに返される結果に一貫性がなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="4517c-118">Failure to do this may result in inconsistent results when querying the cube.</span></span> <span data-ttu-id="4517c-119">**関連トピック:**[SSIS を使用した Analysis Services 管理タスクの自動化」を](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="4517c-119">**Related topic:**[Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4517c-120">参照</span><span class="sxs-lookup"><span data-stu-id="4517c-120">See Also</span></span>  
 [<span data-ttu-id="4517c-121">パーティションのストレージ モードおよび処理</span><span class="sxs-lookup"><span data-stu-id="4517c-121">Partition Storage Modes and Processing</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
