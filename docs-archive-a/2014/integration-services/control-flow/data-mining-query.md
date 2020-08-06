---
title: データ マイニング クエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 657e4e173815fa25458e296f7eadb3d4d0696a02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641817"
---
# <a name="data-mining-query"></a><span data-ttu-id="4e6c8-102">データ マイニング クエリ</span><span class="sxs-lookup"><span data-stu-id="4e6c8-102">Data Mining Query</span></span>
  <span data-ttu-id="4e6c8-103">デザイン ペインには、データ マイニング予測クエリ ビルダーがあり、これを利用してデータ マイニング予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-103">The design pane contains the data mining prediction query builder, which you can use to build data mining prediction queries.</span></span> <span data-ttu-id="4e6c8-104">予測クエリは、入力テーブルまたはシングルトン予測クエリに基づいてデザインできます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-104">You can design either prediction queries based on input tables, or singleton prediction queries.</span></span> <span data-ttu-id="4e6c8-105">クエリを実行して結果を表示するには、結果ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-105">Switch to the result view to run the query and view the results.</span></span> <span data-ttu-id="4e6c8-106">クエリ ビューには、予測クエリ ビルダーによって作成されたデータ マイニング拡張機能 (DMX) のクエリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-106">The query view displays the Data Mining Extensions (DMX) query created by the prediction query builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e6c8-107">オプション</span><span class="sxs-lookup"><span data-stu-id="4e6c8-107">Options</span></span>  
 <span data-ttu-id="4e6c8-108">ビュー切り替えボタン</span><span class="sxs-lookup"><span data-stu-id="4e6c8-108">Switch view button</span></span>  
 <span data-ttu-id="4e6c8-109">デザイン ペインとクエリ ペインを切り替える場合は、アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-109">Click an icon to switch between the design and query pane.</span></span> <span data-ttu-id="4e6c8-110">既定では、デザイン ペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-110">By default, the design pane is open.</span></span>  
  
 <span data-ttu-id="4e6c8-111">デザイン ペインに切り替えるには、![デザイン アイコン](../media/ssis-designicon.gif "デザイン アイコン") アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-111">To switch to the design pane, click the ![Design icon](../media/ssis-designicon.gif "Design icon") icon.</span></span>  
  
 <span data-ttu-id="4e6c8-112">クエリ ペインに切り替えるには、![SQL アイコン](../media/ssis-queryicon.gif "SQL アイコン")アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-112">To switch to the query pane, click the ![SQL icon](../media/ssis-queryicon.gif "SQL icon") icon.</span></span>  
  
 <span data-ttu-id="4e6c8-113">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-113">**Mining Model**</span></span>  
 <span data-ttu-id="4e6c8-114">予測の基準として選択されているマイニング モデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-114">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="4e6c8-115">**[モデルの選択]**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-115">**Select Model**</span></span>  
 <span data-ttu-id="4e6c8-116">**[マイニング モデルの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-116">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="4e6c8-117">**[入力列]**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-117">**Input Columns**</span></span>  
 <span data-ttu-id="4e6c8-118">予測を生成するために選択されている入力列を表示します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-118">Displays the selected input columns used to generate the predictions.</span></span>  
  
 <span data-ttu-id="4e6c8-119">**ソース**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-119">**Source**</span></span>  
 <span data-ttu-id="4e6c8-120">列に使用するフィールドを持つソースをドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-120">Select the source containing the field that you will use for the column from the dropdown list.</span></span> <span data-ttu-id="4e6c8-121">**[マイニング モデル]** テーブルで選択したマイニング モデル、 **[入力テーブルの選択]** テーブルで選択した入力テーブル、予測関数、またはカスタム式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-121">You can either use the mining model selected in the **Mining Model** table, the input table(s) selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="4e6c8-122">マイニング モデルを含むテーブルや入力列から列をセルにドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-122">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
 <span data-ttu-id="4e6c8-123">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-123">**Field**</span></span>  
 <span data-ttu-id="4e6c8-124">ソース テーブルから派生した列の一覧から列を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-124">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="4e6c8-125">**[ソース]** で **[予測関数]** を選択した場合、このセルは、選択されたマイニング モデルで利用できる予測関数のドロップダウン リストを含みます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-125">If you selected **Prediction Function** in **Source**, this cell contains a drop-down list of the prediction functions available for the selected mining model.</span></span>  
  
 <span data-ttu-id="4e6c8-126">**エイリアス**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-126">**Alias**</span></span>  
 <span data-ttu-id="4e6c8-127">サーバーから返された列の名前です。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-127">The name of the column returned by the server.</span></span>  
  
 <span data-ttu-id="4e6c8-128">**[表示]**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-128">**Show**</span></span>  
 <span data-ttu-id="4e6c8-129">列を返す場合、または WHERE 句内でのみ列を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-129">Select to return the column or to only use the column in the WHERE clause.</span></span>  
  
 <span data-ttu-id="4e6c8-130">**グループ**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-130">**Group**</span></span>  
 <span data-ttu-id="4e6c8-131">式をグループ化するために **[ルールの適用条件]** 列と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-131">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="4e6c8-132">たとえば、(expr1 OR expr2) AND expr3 のように指定します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-132">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="4e6c8-133">**[ルールの適用条件]**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-133">**And/Or**</span></span>  
 <span data-ttu-id="4e6c8-134">論理クエリを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-134">Use to create a logical query.</span></span> <span data-ttu-id="4e6c8-135">たとえば、(expr1 OR expr2) AND expr3 のように指定します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-135">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="4e6c8-136">**[条件と引数]**</span><span class="sxs-lookup"><span data-stu-id="4e6c8-136">**Criteria/Argument**</span></span>  
 <span data-ttu-id="4e6c8-137">列に適用する条件またはユーザー式を指定します。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-137">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="4e6c8-138">マイニング モデルを含むテーブルや入力列から列をセルにドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="4e6c8-138">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6c8-139">参照</span><span class="sxs-lookup"><span data-stu-id="4e6c8-139">See Also</span></span>  
 <span data-ttu-id="4e6c8-140">[データマイニングクエリインターフェイス](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span><span class="sxs-lookup"><span data-stu-id="4e6c8-140">[Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span></span>  
 [<span data-ttu-id="4e6c8-141">データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス</span><span class="sxs-lookup"><span data-stu-id="4e6c8-141">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
