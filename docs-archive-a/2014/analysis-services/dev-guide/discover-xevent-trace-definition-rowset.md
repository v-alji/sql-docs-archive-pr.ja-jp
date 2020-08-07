---
title: DISCOVER_XEVENT_TRACE_DEFINITION 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
ms.openlocfilehash: bedd6ec66a188738ac9a522b4802b3b431e82f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718885"
---
# <a name="discover_xevent_trace_definition-rowset"></a><span data-ttu-id="0b348-102">DISCOVER_XEVENT_TRACE_DEFINITION 行セット</span><span class="sxs-lookup"><span data-stu-id="0b348-102">DISCOVER_XEVENT_TRACE_DEFINITION Rowset</span></span>
  <span data-ttu-id="0b348-103">サーバー上で現在アクティブになっている XEvent トレースに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0b348-103">Provides information about XEvent traces that are currently active on the server.</span></span>  
  
 <span data-ttu-id="0b348-104">**適用対象:** テーブルモデル、多次元モデル</span><span class="sxs-lookup"><span data-stu-id="0b348-104">**Applies to:** tabular models, multidimensional models</span></span>  
  
## <a name="rowset-columns"></a><span data-ttu-id="0b348-105">行セットの列</span><span class="sxs-lookup"><span data-stu-id="0b348-105">Rowset Columns</span></span>  
 <span data-ttu-id="0b348-106">`DISCOVER_XEVENT_TRACE_DEFINITION`行セットには、次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0b348-106">The `DISCOVER_XEVENT_TRACE_DEFINITION` rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="0b348-107">列名</span><span class="sxs-lookup"><span data-stu-id="0b348-107">Column name</span></span>|<span data-ttu-id="0b348-108">型を表すインジケーター</span><span class="sxs-lookup"><span data-stu-id="0b348-108">Type indicator</span></span>|<span data-ttu-id="0b348-109">長さ</span><span class="sxs-lookup"><span data-stu-id="0b348-109">Length</span></span>|<span data-ttu-id="0b348-110">Description</span><span class="sxs-lookup"><span data-stu-id="0b348-110">Description</span></span>|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||<span data-ttu-id="0b348-111">XEvent トレースの XML 定義。</span><span class="sxs-lookup"><span data-stu-id="0b348-111">The XML definition of the XEvent trace.</span></span>|  
  
 <span data-ttu-id="0b348-112">このスキーマ行セットは並べ替えられません。</span><span class="sxs-lookup"><span data-stu-id="0b348-112">This schema rowset is not sorted.</span></span>  
  
## <a name="using-adomdnet-to-return-the-rowset"></a><span data-ttu-id="0b348-113">ADOMD.NET を使用した行セットのリターン</span><span class="sxs-lookup"><span data-stu-id="0b348-113">Using ADOMD.NET to return the rowset</span></span>  
 <span data-ttu-id="0b348-114">ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。</span><span class="sxs-lookup"><span data-stu-id="0b348-114">When using ADOMD.NET and the schema rowset to retrieve metadata, you can use either the GUID or string to reference a schema rowset object in the GetSchemaDataSet method.</span></span> <span data-ttu-id="0b348-115">詳細については、「 [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b348-115">For more information, see [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets).</span></span>  
  
 <span data-ttu-id="0b348-116">次の表に、この行セットを識別する GUID と文字列の値を示します。</span><span class="sxs-lookup"><span data-stu-id="0b348-116">The following table provides the GUID and string values that identify this rowset.</span></span>  
  
|<span data-ttu-id="0b348-117">引数</span><span class="sxs-lookup"><span data-stu-id="0b348-117">Argument</span></span>|<span data-ttu-id="0b348-118">値</span><span class="sxs-lookup"><span data-stu-id="0b348-118">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="0b348-119">GUID</span><span class="sxs-lookup"><span data-stu-id="0b348-119">GUID</span></span>|<span data-ttu-id="0b348-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span><span class="sxs-lookup"><span data-stu-id="0b348-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span></span>|  
|<span data-ttu-id="0b348-121">String</span><span class="sxs-lookup"><span data-stu-id="0b348-121">String</span></span>|<span data-ttu-id="0b348-122">DISCOVER_XEVENT_TRACE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b348-122">DISCOVER_XEVENT_TRACE_DEFINITION</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b348-123">参照</span><span class="sxs-lookup"><span data-stu-id="0b348-123">See Also</span></span>  
 <span data-ttu-id="0b348-124">[XML for Analysis スキーマ行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span><span class="sxs-lookup"><span data-stu-id="0b348-124">[XML for Analysis Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span></span>  
 <span data-ttu-id="0b348-125">[SQL Server 拡張イベント &#40;Xevent&#41; を使用して監視 Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="0b348-125">[Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span></span>  
 [<span data-ttu-id="0b348-126">動的管理ビュー (DMV) を使用した Analysis Services の監視</span><span class="sxs-lookup"><span data-stu-id="0b348-126">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
