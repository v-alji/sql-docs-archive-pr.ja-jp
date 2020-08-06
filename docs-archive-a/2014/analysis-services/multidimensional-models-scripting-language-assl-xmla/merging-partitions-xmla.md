---
title: パーティションのマージ (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639725"
---
# <a name="merging-partitions-xmla"></a><span data-ttu-id="002b7-102">パーティションのマージ (XMLA)</span><span class="sxs-lookup"><span data-stu-id="002b7-102">Merging Partitions (XMLA)</span></span>
  <span data-ttu-id="002b7-103">パーティションの集計デザインと構造が同じである場合は、XML for Analysis (XMLA) の[Mergepartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla)コマンドを使用してパーティションをマージできます。</span><span class="sxs-lookup"><span data-stu-id="002b7-103">If partitions have the same aggregation design and structure, you can merge the partition by using the [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) command in XML for Analysis (XMLA).</span></span> <span data-ttu-id="002b7-104">パーティション管理において、パーティションのマージは重要な操作です。日付によってパーティション分割された履歴データを含むパーティションの場合は特に重要です。</span><span class="sxs-lookup"><span data-stu-id="002b7-104">Merging partitions is an important action to perform when you manage partitions, especially those partitions that contain historical data partitioned by date.</span></span>  
  
 <span data-ttu-id="002b7-105">たとえば、次の 2 つのパーティションを使用する財務キューブがあるとします。</span><span class="sxs-lookup"><span data-stu-id="002b7-105">For example, a financial cube may use two partitions:</span></span>  
  
-   <span data-ttu-id="002b7-106">1 つのパーティションは現在の年の財務データを表し、パフォーマンスのためにリアルタイム リレーショナル OLAP (ROLAP) ストレージ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="002b7-106">One partition represents financial data for the current year, using real-time relational OLAP (ROLAP) storage settings for performance.</span></span>  
  
-   <span data-ttu-id="002b7-107">もう 1 つのパーティションは過去の年の財務データを格納し、ストレージのために多次元 OLAP (MOLAP) ストレージ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="002b7-107">Another partition contains financial data for previous years, using multidimensional OLAP (MOLAP) storage settings for storage.</span></span>  
  
 <span data-ttu-id="002b7-108">2 つのパーティションは異なるストレージ設定を使用しますが、集計デザインは同じものを使用します。</span><span class="sxs-lookup"><span data-stu-id="002b7-108">Both partitions use different storage settings, but use the same aggregation design.</span></span> <span data-ttu-id="002b7-109">年の終わりに複数年にわたる履歴データについてキューブを処理する代わりに、`MergePartitions` コマンドを使用して、現在の年のパーティションを過去の年のパーティションにマージできます。</span><span class="sxs-lookup"><span data-stu-id="002b7-109">Instead of processing the cube across years of historical data at the end of the year, you can instead use the `MergePartitions` command to merge the partition for the current year into the partition for previous years.</span></span> <span data-ttu-id="002b7-110">こうすれば、多くの時間をかけてキューブを詳細に処理しなくても、集計データを保持できます。</span><span class="sxs-lookup"><span data-stu-id="002b7-110">This preserves the aggregation data without requiring a potentially time-consuming full processing of the cube.</span></span>  
  
## <a name="specifying-partitions-to-merge"></a><span data-ttu-id="002b7-111">マージするパーティションの指定</span><span class="sxs-lookup"><span data-stu-id="002b7-111">Specifying Partitions to Merge</span></span>  
 <span data-ttu-id="002b7-112">コマンドを `MergePartitions` 実行すると、 [source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)プロパティで指定されたソースパーティションに格納されている集計データが、[ターゲット](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)プロパティで指定された対象パーティションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="002b7-112">When the `MergePartitions` command runs, the aggregation data stored in the source partitions specified in the [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property is added to the target partition specified in the [Target](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="002b7-113">`Source` プロパティには複数のパーティション オブジェクト参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="002b7-113">The `Source` property can contain more than one partition object reference.</span></span> <span data-ttu-id="002b7-114">しかし、`Target` プロパティには複数を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="002b7-114">However, the `Target` property cannot.</span></span>  
  
 <span data-ttu-id="002b7-115">正常にマージするためには、`Source` と `Target` で指定されるパーティションが同じメジャー グループに含まれ、同じ集計デザインを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="002b7-115">To be successfully merged, the partitions specified in both the `Source` and `Target` must be contained by the same measure group and use the same aggregation design.</span></span> <span data-ttu-id="002b7-116">そうでない場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="002b7-116">Otherwise, an error occurs.</span></span>  
  
 <span data-ttu-id="002b7-117">`Source` で指定されたパーティションは、`MergePartitions` コマンドが正常に完了した後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="002b7-117">The partitions specified in the `Source` are deleted after the `MergePartitions` command is successfully completed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="002b7-118">例</span><span class="sxs-lookup"><span data-stu-id="002b7-118">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="002b7-119">説明</span><span class="sxs-lookup"><span data-stu-id="002b7-119">Description</span></span>  
 <span data-ttu-id="002b7-120">次の例では、 **adventure works DW**サンプルデータベースの**adventure works**キューブの**Customer カウント**メジャーグループに含まれるすべてのパーティション [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を、 **Customers_2004**パーティションにマージします。</span><span class="sxs-lookup"><span data-stu-id="002b7-120">The following example merges all the partitions in the **Customer Counts** measure group of the **Adventure Works** cube in the **Adventure Works DW** sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database into the **Customers_2004** partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="002b7-121">コード</span><span class="sxs-lookup"><span data-stu-id="002b7-121">Code</span></span>  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="002b7-122">参照</span><span class="sxs-lookup"><span data-stu-id="002b7-122">See Also</span></span>  
 [<span data-ttu-id="002b7-123">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="002b7-123">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
