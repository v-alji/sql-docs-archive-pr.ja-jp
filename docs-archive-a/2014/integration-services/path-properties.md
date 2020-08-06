---
title: パスのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca263b866fb6d5d7ceb6352f708f387d79cad4f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632552"
---
# <a name="path-properties"></a><span data-ttu-id="9a683-102">パスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="9a683-102">Path Properties</span></span>
  <span data-ttu-id="9a683-103">オブジェクトモデルのデータフローオブジェクトには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンポーネント、入力、出力、入力列、および出力列のレベルで共通のプロパティとカスタムプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9a683-103">The data flow objects in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model have common properties and custom properties at the level of the component, inputs and outputs, and input columns and output columns.</span></span> <span data-ttu-id="9a683-104">多くのプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9a683-104">Many properties have read-only values that are assigned at run time by the data flow engine.</span></span>  
  
 <span data-ttu-id="9a683-105">このトピックでは、データ フロー オブジェクトを連結するパスのカスタム プロパティの一覧を示し、それらのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9a683-105">This topic lists and describes the custom properties of the paths that connect data flow objects.</span></span>  
  
## <a name="path-properties"></a><span data-ttu-id="9a683-106">パスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="9a683-106">Path Properties</span></span>  
 <span data-ttu-id="9a683-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクト モデルでは、データ フロー内のコンポーネントを連結するパスは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="9a683-107">In the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model, a path that connects components in the data flow implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> interface.</span></span>  
  
 <span data-ttu-id="9a683-108">次の表は、データ フロー内のパスの、値が設定できるプロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="9a683-108">The following table describes the configurable properties of the paths in a data flow.</span></span> <span data-ttu-id="9a683-109">データ フロー エンジンは、この一覧にない追加の読み取り専用プロパティにも値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9a683-109">The data flow engine also assigns values to additional read-only properties that are not listed here.</span></span>  
  
|<span data-ttu-id="9a683-110">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="9a683-110">Property name</span></span>|<span data-ttu-id="9a683-111">データ型</span><span class="sxs-lookup"><span data-stu-id="9a683-111">Data Type</span></span>|<span data-ttu-id="9a683-112">説明</span><span class="sxs-lookup"><span data-stu-id="9a683-112">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="9a683-113">[PathAnnotation]</span><span class="sxs-lookup"><span data-stu-id="9a683-113">PathAnnotation</span></span>|<span data-ttu-id="9a683-114">Integer (列挙)</span><span class="sxs-lookup"><span data-stu-id="9a683-114">Integer (enumeration)</span></span>|<span data-ttu-id="9a683-115">注釈をパスと共にデザイナー画面に表示するかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="9a683-115">A value that indicates whether an annotation should be displayed with the path on the designer surface.</span></span> <span data-ttu-id="9a683-116">値には、`AsNeeded`、`SourceName`、`PathName`、および `Never` があります。</span><span class="sxs-lookup"><span data-stu-id="9a683-116">The possible values are `AsNeeded`, `SourceName`, `PathName`, and `Never`.</span></span> <span data-ttu-id="9a683-117">既定値は `AsNeeded` です。</span><span class="sxs-lookup"><span data-stu-id="9a683-117">The default value is `AsNeeded`.</span></span>|  
|<span data-ttu-id="9a683-118">[DestinationName]</span><span class="sxs-lookup"><span data-stu-id="9a683-118">DestinationName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|<span data-ttu-id="9a683-119">パスに関連付けられた入力</span><span class="sxs-lookup"><span data-stu-id="9a683-119">The input associated with the path.</span></span>|  
|<span data-ttu-id="9a683-120">SourceName</span><span class="sxs-lookup"><span data-stu-id="9a683-120">SourceName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|<span data-ttu-id="9a683-121">パスに関連付けられた出力</span><span class="sxs-lookup"><span data-stu-id="9a683-121">The output associated with the path.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a683-122">参照</span><span class="sxs-lookup"><span data-stu-id="9a683-122">See Also</span></span>  
 <span data-ttu-id="9a683-123">[Integration Services のパス](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="9a683-123">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="9a683-124">[共通プロパティ](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9a683-124">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="9a683-125">[変換のカスタムプロパティ](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9a683-125">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="9a683-126">式を使って設定できるデータ フロー プロパティ</span><span class="sxs-lookup"><span data-stu-id="9a683-126">Data Flow Properties that Can Be Set by Using Expressions</span></span>](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
