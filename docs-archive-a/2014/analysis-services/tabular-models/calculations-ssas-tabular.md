---
title: 計算 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2da86ae5c5652c8b2614cae4bbb721802700d973
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639676"
---
# <a name="calculations-ssas-tabular"></a><span data-ttu-id="192d1-102">計算 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="192d1-102">Calculations (SSAS Tabular)</span></span>
  <span data-ttu-id="192d1-103">データをモデルにインポートした後、計算を追加して、データの拡張、結合、要約、およびセキュリティの確保を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="192d1-103">After you have imported data into your model, you can add calculations to aggregate, filter, extend, combine, and secure that data.</span></span> <span data-ttu-id="192d1-104">テーブル モデルでは、カスタムの計算を作成するための Data Analysis Expressions (DAX) という数式言語を使用します。</span><span class="sxs-lookup"><span data-stu-id="192d1-104">Tabular models use Data Analysis Expressions (DAX), a formula language for creating custom calculations.</span></span> <span data-ttu-id="192d1-105">テーブル モデルでは、 *計算列*、 *メジャー*、および *行フィルター*に使用される計算を DAX の数式を使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="192d1-105">In tabular models, the calculations you create by using DAX formulas are used in *Calculated Columns*, *Measures*, and *Row Filters*.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="192d1-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="192d1-106">In This Section</span></span>  
  
|<span data-ttu-id="192d1-107">トピック</span><span class="sxs-lookup"><span data-stu-id="192d1-107">Topic</span></span>|<span data-ttu-id="192d1-108">説明</span><span class="sxs-lookup"><span data-stu-id="192d1-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="192d1-109">テーブル モデルでの DAX について (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="192d1-109">Understanding DAX in Tabular Models &#40;SSAS Tabular&#41;</span></span>](understanding-dax-in-tabular-models-ssas-tabular.md)|<span data-ttu-id="192d1-110">テーブル モデルの計算列、メジャー、および行フィルターに対して計算を作成する際に使用される Data Analysis Expressions (DAX) の数式言語について説明します。</span><span class="sxs-lookup"><span data-stu-id="192d1-110">Describes the Data Analysis Expressions (DAX) formula language used to create calculations for calculated columns, measures, and row filters in tabular models.</span></span>|  
|[<span data-ttu-id="192d1-111">DirectQuery モードでの数式の互換性</span><span class="sxs-lookup"><span data-stu-id="192d1-111">Formula Compatibility in DirectQuery Mode</span></span>](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|<span data-ttu-id="192d1-112">相違点について説明し、DirectQuery モードではサポートされない関数、およびサポートはされるが異なる結果を返す可能性のある一連の関数を示します。</span><span class="sxs-lookup"><span data-stu-id="192d1-112">Describes the differences, lists the functions that are not supported in DirectQuery mode, and lists the functions that are supported but could return different results.</span></span>|  
|[<span data-ttu-id="192d1-113">データ分析式 &#40;DAX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="192d1-113">Data Analysis Expressions &#40;DAX&#41; Reference</span></span>](/dax/data-analysis-expressions-dax-reference)|<span data-ttu-id="192d1-114">このセクションでは、DAX の構文、演算子、および関数について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="192d1-114">This section provides detailed descriptions of DAX syntax, operators, and functions.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="192d1-115">計算の作成に伴うタスクの実行手順は、このセクションには記載されていません。</span><span class="sxs-lookup"><span data-stu-id="192d1-115">Step-by-step tasks for creating calculations are not provided in this section.</span></span> <span data-ttu-id="192d1-116">計算は、計算列、メジャー、および行フィルター (ロール単位) で指定されるため、DAX の数式の作成先についての説明も、これらの各機能に関連したタスクで説明します。</span><span class="sxs-lookup"><span data-stu-id="192d1-116">Because calculations are specified in calculated columns, measures, and row filters (in roles), instructions on where to create DAX formulas are provided in tasks related to those features.</span></span> <span data-ttu-id="192d1-117">詳細については、「[計算列の作成 (SSAS テーブル)](ssas-calculated-columns-create-a-calculated-column.md)」、「[メジャーを作成および管理する (SSAS テーブル)](measures-ssas-tabular.md)」、および「[ロールの作成および管理 (SSAS テーブル)](roles-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="192d1-117">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](ssas-calculated-columns-create-a-calculated-column.md), [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md), and [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="192d1-118">テーブル モデルをクエリする際にも DAX は使用できますが、このセクションの各トピックでは、DAX の数式を使用した計算の作成に的を絞って説明します。</span><span class="sxs-lookup"><span data-stu-id="192d1-118">While DAX can also be used to query a tabular model, topics in this section focus specifically on using DAX formulas to create calculations.</span></span>  
  
  
