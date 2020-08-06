---
title: キューブ階層のプロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8903a49754357aad9cf24ee63fffa45fbf120e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712569"
---
# <a name="define-cube-hierarchy-properties"></a><span data-ttu-id="60a40-102">キューブ階層のプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="60a40-102">Define Cube Hierarchy Properties</span></span>
  <span data-ttu-id="60a40-103">キューブ階層のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のユーザー定義階層に一意の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="60a40-103">Cube hierarchy properties enable you to specify unique settings for user-defined hierarchies in cube dimensions based on the same database dimension.</span></span> <span data-ttu-id="60a40-104">次の表では、キューブ階層のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="60a40-104">The following table describes the properties of a cube hierarchy.</span></span>  
  
|<span data-ttu-id="60a40-105">プロパティ</span><span class="sxs-lookup"><span data-stu-id="60a40-105">Property</span></span>|<span data-ttu-id="60a40-106">説明</span><span class="sxs-lookup"><span data-stu-id="60a40-106">Description</span></span>|  
|--------------|-----------------|  
|`Enabled`|<span data-ttu-id="60a40-107">キューブ ディメンションの階層が有効かどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="60a40-107">Determines whether the hierarchy is enabled for the cube dimension.</span></span>|  
|`HierarchyID`|<span data-ttu-id="60a40-108">階層の一意の識別子 (ID) を格納します。</span><span class="sxs-lookup"><span data-stu-id="60a40-108">Contains the unique identifier (ID) of the hierarchy.</span></span>|  
|`OptimizedState`|<span data-ttu-id="60a40-109">階層に適用される最適化のレベルを決定します。</span><span class="sxs-lookup"><span data-stu-id="60a40-109">Determines the level of optimization that is applied to the hierarchy.</span></span> <span data-ttu-id="60a40-110">このプロパティは、以下の値をとります。</span><span class="sxs-lookup"><span data-stu-id="60a40-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="60a40-111">`FullyOptimized`: インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="60a40-111">`FullyOptimized`: The instance builds indexes for the hierarchy to improve query performance.</span></span> <span data-ttu-id="60a40-112">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="60a40-112">This is the default value.</span></span><br /><br /> <span data-ttu-id="60a40-113">`NotOptimized`: インスタンスは追加のインデックスを構築しません。</span><span class="sxs-lookup"><span data-stu-id="60a40-113">`NotOptimized`: The instance does not build additional indexes.</span></span>|  
|`Visible`|<span data-ttu-id="60a40-114">キューブ階層の表示を決定します。</span><span class="sxs-lookup"><span data-stu-id="60a40-114">Determines the visibility of the cube hierarchy.</span></span> <span data-ttu-id="60a40-115">既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="60a40-115">The default value is `True`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60a40-116">参照</span><span class="sxs-lookup"><span data-stu-id="60a40-116">See Also</span></span>  
 [<span data-ttu-id="60a40-117">ユーザー階層</span><span class="sxs-lookup"><span data-stu-id="60a40-117">User Hierarchies</span></span>](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
