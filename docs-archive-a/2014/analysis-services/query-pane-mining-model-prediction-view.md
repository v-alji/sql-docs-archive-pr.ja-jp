---
title: クエリペイン (マイニングモデル予測ビュー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.query.f1
ms.assetid: fdeec72e-d0bd-4453-9eaa-46436e4d6edc
author: minewiskan
ms.author: owend
ms.openlocfilehash: e17a27190891ea9e00be21d5013d0767d61ac148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634704"
---
# <a name="query-pane-mining-model-prediction-view"></a><span data-ttu-id="224a9-102">[クエリ] ペイン ([マイニング モデル予測] ビュー)</span><span class="sxs-lookup"><span data-stu-id="224a9-102">Query Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="224a9-103">**[クエリ]** ペインには、予測クエリ ビルダーによって作成されたデータ マイニング式 (DMX) ステートメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="224a9-103">The **Query** pane displays the Data Mining Expressions (DMX) statements created by Prediction Query Builder.</span></span> <span data-ttu-id="224a9-104">ステートメントを変更してから **[クエリ結果ビューに切り替え]** ボタンをクリックすると、結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="224a9-104">You can modify the statements and then click the **Switch to query result view** button to return the results.</span></span> <span data-ttu-id="224a9-105">**[デザイン]** ビューに戻ると、ステートメントに加えた変更がすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="224a9-105">If you switch back to the **Design** view, any changes you made to the statement will be lost.</span></span>  
  
 <span data-ttu-id="224a9-106">**詳細情報: 「** [データ マイニング拡張機能 &#40;DMX&#41; データ操作ステートメント](/sql/dmx/dmx-statements-data-manipulation)」、「[SQL Server Management Studio での DMX クエリの作成](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)」</span><span class="sxs-lookup"><span data-stu-id="224a9-106">**For More Information:** [Data Mining Extensions &#40;DMX&#41; Data Manipulation Statements](/sql/dmx/dmx-statements-data-manipulation), [Create a DMX Query in SQL Server Management Studio](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="224a9-107">Options</span><span class="sxs-lookup"><span data-stu-id="224a9-107">Options</span></span>  
 <span data-ttu-id="224a9-108">**[クエリ結果ビューに切り替え]**</span><span class="sxs-lookup"><span data-stu-id="224a9-108">**Switch to query result view**</span></span>  
 <span data-ttu-id="224a9-109">クリックすると、ビューを順に **[デザイン]**、 **[クエリ]**、 **[結果]** ペインに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="224a9-109">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="224a9-110">**[結果]** ペインに切り替えると、クエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="224a9-110">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="224a9-111">**[クエリ結果の保存]**</span><span class="sxs-lookup"><span data-stu-id="224a9-111">**Save the query result**</span></span>  
 <span data-ttu-id="224a9-112">**[データ マイニングのクエリ結果を保存]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="224a9-112">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="224a9-113">**Singleton query**</span><span class="sxs-lookup"><span data-stu-id="224a9-113">**Singleton query**</span></span>  
 <span data-ttu-id="224a9-114">入力値のテーブルへの参照ではなく、入力データをクエリに直接提供できる、単一クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="224a9-114">Lets you create a singleton query, in which you provide the input data directly in your query instead of providing a reference to a table of input values.</span></span> <span data-ttu-id="224a9-115">**[入力テーブルの選択]** テーブルは **[単一クエリ入力]** テーブルに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="224a9-115">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span> <span data-ttu-id="224a9-116">単一クエリに切り替えると、現在の予測クエリは失われます。</span><span class="sxs-lookup"><span data-stu-id="224a9-116">The current prediction query will be lost if you switch to a singleton query.</span></span>  
  
 <span data-ttu-id="224a9-117">**[クエリ結果を最新状態に更新します]**</span><span class="sxs-lookup"><span data-stu-id="224a9-117">**Refresh query results**</span></span>  
 <span data-ttu-id="224a9-118">予測クエリを再処理します。</span><span class="sxs-lookup"><span data-stu-id="224a9-118">Reprocesses the prediction query.</span></span> <span data-ttu-id="224a9-119">この操作は **[結果]** ペインでのみ行えます。</span><span class="sxs-lookup"><span data-stu-id="224a9-119">This is enabled only in the **Result** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="224a9-120">参照</span><span class="sxs-lookup"><span data-stu-id="224a9-120">See Also</span></span>  
 <span data-ttu-id="224a9-121">[データマイニングクエリインターフェイス](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="224a9-121">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 <span data-ttu-id="224a9-122">[DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="224a9-122">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 [<span data-ttu-id="224a9-123">予測クエリ ビルダー &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="224a9-123">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
