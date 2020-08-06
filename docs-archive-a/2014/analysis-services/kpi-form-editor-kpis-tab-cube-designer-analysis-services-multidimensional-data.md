---
title: KPI フォームエディター (キューブデザイナーの [Kpi] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpidefinitionpane.f1
ms.assetid: 45c6453a-bbe2-4ca5-836e-c7ef11cfcb65
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c88d6fcec60634f37ddad8b6d0f5cb2124fa1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633407"
---
# <a name="kpi-form-editor-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="c2c7b-102">KPI フォーム エディター (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="c2c7b-102">KPI Form Editor (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c2c7b-103">キューブ デザイナーの **[KPI]** タブの **KPI フォーム エディター** ペインを使用すると、選択した主要業績評価指標 (KPI) を変更したり作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-103">Use the **KPI Form Editor** pane on the **KPIs** tab in Cube Designer to create or modify the selected Key Performance Indicator (KPI).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7b-104">このペインはフォーム ビューでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c2c7b-105">Options</span><span class="sxs-lookup"><span data-stu-id="c2c7b-105">Options</span></span>  
 <span data-ttu-id="c2c7b-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-106">**Name**</span></span>  
 <span data-ttu-id="c2c7b-107">KPI の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-107">Type the name of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-108">**[関連付けられたメジャー グループ]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-108">**Associated measure group**</span></span>  
 <span data-ttu-id="c2c7b-109">KPI に関連付けられているメジャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-109">Select the measure group associated with the KPI.</span></span> <span data-ttu-id="c2c7b-110">クライアント アプリケーションでこの情報を使用して、ユーザーがこの KPI を参照するときに使用できるディメンションを判別できます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-110">The client application can use this information to determine which dimensions are available when the user browses this KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-111">**値式**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-111">**Value Expression**</span></span>  
 <span data-ttu-id="c2c7b-112">展開すると、KPI の値を返す多次元式 (MDX) を表示したり、編集したりできます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-112">Expand to view or edit the Multidimensional Expressions (MDX) expression for the value of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-113">KPI の値を返す MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-113">Type the MDX expression that returns the value of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-114">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-114">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="c2c7b-115">**[目標式]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-115">**Goal Expression**</span></span>  
 <span data-ttu-id="c2c7b-116">展開すると、KPI の目標値を返す MDX 式を表示したり、編集したりできます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-116">Expand to view or edit the MDX expression for the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-117">KPI を実行したときの目標値を返す MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-117">Type the MDX expression that returns the goal value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="c2c7b-118">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-118">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="c2c7b-119">**状態**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-119">**Status**</span></span>  
 <span data-ttu-id="c2c7b-120">展開すると、 **[状態マーク]** および **[状態式]** のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-120">Expand to view the **Status graphic** and **Status expression** options.</span></span>  
  
 <span data-ttu-id="c2c7b-121">**[状態マーク]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-121">**Status graphic**</span></span>  
 <span data-ttu-id="c2c7b-122">クライアント アプリケーションで状態値をグラフィカルに表すために使用されるグラフィックを選択します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-122">Select the graphic to be used by the client application to represent the status value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7b-123">選択したグラフィックがクライアント アプリケーションでサポートされない場合、適切なグラフィックに置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-123">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="c2c7b-124">**[状態式]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-124">**Status expression**</span></span>  
 <span data-ttu-id="c2c7b-125">KPI を実行したときの状態値を返す MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-125">Type the MDX expression that returns the status value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="c2c7b-126">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-126">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="c2c7b-127">この式では、-1 ~ 1 の範囲の10進数を返すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-127">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="c2c7b-128">低い数値が悪い状況を表し、高い数値が良い状況を表すようにします。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-128">A lower number represents a negative situation, while a higher number represents a positive situation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7b-129">-1 以上の値は使用できますが、サードパーティのクライアントアプリケーションで正しく解釈されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-129">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="c2c7b-130">**傾向**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-130">**Trend**</span></span>  
 <span data-ttu-id="c2c7b-131">展開すると、 **[傾向マーク]** および **[傾向式]** のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-131">Expand to view the **Trend graphic** and **Trend expression** options.</span></span>  
  
 <span data-ttu-id="c2c7b-132">**[傾向マーク]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-132">**Trend graphic**</span></span>  
 <span data-ttu-id="c2c7b-133">クライアント アプリケーションで傾向値をグラフィカルに表すために使用されるグラフィックを選択します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-133">Select the graphic to be used by the client application to represent the trend value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7b-134">選択したグラフィックがクライアント アプリケーションでサポートされない場合、適切なグラフィックに置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-134">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="c2c7b-135">**[傾向式]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-135">**Trend expression**</span></span>  
 <span data-ttu-id="c2c7b-136">KPI の傾向値を返す MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-136">Type the MDX expression that returns the trend value of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-137">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-137">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="c2c7b-138">指定されたビジネス コンテキストで有効な時間ベースの条件に基づく傾向式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-138">The trend expression can be based on any time-based criteria that makes sense in a given business context.</span></span> <span data-ttu-id="c2c7b-139">この式では、-1 ~ 1 の範囲の10進数を返すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-139">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="c2c7b-140">低い数値が一定期間の悪い傾向を表し、高い数値が一定期間の良い傾向を表すようにします。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-140">A lower number represents a negative trend over time; a higher number represents a positive trend over time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7b-141">-1 以上の値は使用できますが、サードパーティのクライアントアプリケーションで正しく解釈されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-141">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="c2c7b-142">**追加のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-142">**Additional Properties**</span></span>  
 <span data-ttu-id="c2c7b-143">展開すると、 **[フォルダーの表示]**、 **[親 KPI]**、 **[現在の時間メンバー]**、 **[加重]**、 **[説明]** のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-143">Expand to view the **Display folder**, **Parent KPI**, **Current time member**, **Weight**, and **Description** options.</span></span>  
  
 <span data-ttu-id="c2c7b-144">**[フォルダーの表示]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-144">**Display folder**</span></span>  
 <span data-ttu-id="c2c7b-145">表示のためにクライアント アプリケーションで使用される KPI の分類を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-145">Type the categorization of the KPI for use by the client application for display purposes.</span></span>  
  
 <span data-ttu-id="c2c7b-146">表示フォルダー内のフォルダー名は円記号 (\\) を使用して区切り、複数の表示フォルダーはセミコロン (;) を使用して区切ります。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-146">Use a backward slash (\\) to separate folder names in a display folder and a semicolon (;) to separate multiple display folders.</span></span> <span data-ttu-id="c2c7b-147">たとえば、「 `Category\Goal\Scientific;Category\Goal\Metric`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-147">For example, type `Category\Goal\Scientific;Category\Goal\Metric`.</span></span>  
  
 <span data-ttu-id="c2c7b-148">**[親 KPI]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-148">**Parent KPI**</span></span>  
 <span data-ttu-id="c2c7b-149">クライアント アプリケーションで使用する KPI を分類するための、既存の KPI を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-149">Select an existing KPI under which to categorize the KPI for use by the client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7b-150">このオプションを既存の KPI に設定した場合、 **[フォルダーの表示]** は無視されます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-150">If this option is set to an existing KPI, **Display folder** is ignored.</span></span>  
  
 <span data-ttu-id="c2c7b-151">**[現在の時間メンバー]**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-151">**Current time member**</span></span>  
 <span data-ttu-id="c2c7b-152">KPI の一時的なコンテキストを識別するメンバーを返す MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-152">Type the MDX expression that returns the member that identifies the temporal context of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-153">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c2c7b-154">この MDX 式では、 **[関連付けられたメジャー グループ]** で指定されたメジャー グループに関連付けられている時間ディメンション内の、メンバーの一意の名前が返される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-154">The MDX expression must return the unique name of a member within a time dimension associated with the measure group specified in **Associated measure group**.</span></span>  
  
 <span data-ttu-id="c2c7b-155">**Weight**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-155">**Weight**</span></span>  
 <span data-ttu-id="c2c7b-156">展開すると、KPI の重み計数を返す MDX 式を表示したり、編集したりできます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-156">Expand to view or edit the MDX expression for the weighting factor of the KPI.</span></span>  
  
 <span data-ttu-id="c2c7b-157">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-157">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="c2c7b-158">**説明**</span><span class="sxs-lookup"><span data-stu-id="c2c7b-158">**Description**</span></span>  
 <span data-ttu-id="c2c7b-159">KPI の説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="c2c7b-159">Type the optional description of the KPI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c7b-160">参照</span><span class="sxs-lookup"><span data-stu-id="c2c7b-160">See Also</span></span>  
 [<span data-ttu-id="c2c7b-161">Kpi &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c7b-161">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
