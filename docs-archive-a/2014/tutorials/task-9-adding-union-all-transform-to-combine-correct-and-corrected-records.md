---
title: 'タスク 9: 全体結合変換を追加して、正しいレコードと修正されたレコードを結合する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 83afb5ea9367660048fe36d00ab59d808da17b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742682"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a><span data-ttu-id="7ea2f-102">タスク 9: 全体結合変換を追加して適切なレコードと修正済みレコードを結合する</span><span class="sxs-lookup"><span data-stu-id="7ea2f-102">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>
  <span data-ttu-id="7ea2f-103">ここでは、全体結合変換をデータ フローに追加します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-103">In this task, you add the Union All Transform to the data flow.</span></span> <span data-ttu-id="7ea2f-104">全体結合変換は、複数の入力を 1 つの出力に結合します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-104">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="7ea2f-105">このシナリオでは、1 つのストリームに適切なレコードと修正済みレコードを結合します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-105">In your scenario, it combine both Correct and Corrected records into one stream.</span></span>  
  
1.  <span data-ttu-id="7ea2f-106">**SSIS ツールボックス**の [**共通**] セクションから [**データフロー** ] タブに [全体**結合**変換] をドラッグアンドドロップし、[**適切なレコードと修正済みレコードを選択**] の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-106">Drag-drop **Union All** Transform from **Common** section of the **SSIS Toolbox** to the **Data Flow** tab and place it under **Pick Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="7ea2f-107">[**データフロー** ] タブで [全体**結合**変換] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-107">Right-click **Union All** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="7ea2f-108">「**正しいレコードと修正**されたレコードの組み合わせ」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-108">Type **Combine Correct and Corrected Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="7ea2f-109">![適切なレコードと修正済みレコードの結合](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "適切なレコードと修正済みレコードの結合")</span><span class="sxs-lookup"><span data-stu-id="7ea2f-109">![Combine Correct and Corrected Reocrds](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "Combine Correct and Corrected Reocrds")</span></span>  
  
3.  <span data-ttu-id="7ea2f-110">Blue コネクタを使用して、[**データフロー** ] タブで正しいレコードと修正された**レコードを結合**するには、 **[適切なレコードを選択**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-110">Connect **Pick Correct and Corrected Records** to **Combine Correct and Corrected Records** in the **Data Flow** tab by using the blue connector.</span></span> <span data-ttu-id="7ea2f-111">[**入力出力の選択**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-111">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="7ea2f-112">[**入力出力**] ダイアログボックスで、[**出力**] の [**適切**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-112">In the **Input Output** dialog box, select **Correct** for **Output** and click **OK**.</span></span>  
  
     <span data-ttu-id="7ea2f-113">![[入出力の選択] ダイアログ ボックス](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "[入出力の選択] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="7ea2f-113">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="7ea2f-114">コネクタの最後にあるドットを左にドラッグアンドドロップして、**コネクタを左に移動**します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-114">Move the connector titled **Correct** to the left by dragging and dropping the dot at the end of the connector to left.</span></span>  
  
     <span data-ttu-id="7ea2f-115">![適切なレコードと修正済みレコードを結合するために適切なレコードを接続](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "適切なレコードと修正済みレコードを結合するために適切なレコードを接続")</span><span class="sxs-lookup"><span data-stu-id="7ea2f-115">![Connect Correct to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connect Correct to Combine Correct and Corrected")</span></span>  
  
6.  <span data-ttu-id="7ea2f-116">[**正しいレコードの選択**] を選択すると、別の青いコネクタが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-116">If you select **Pick Correct and Corrected Records** transform, you should see another blue connector.</span></span> <span data-ttu-id="7ea2f-117">青いコネクタをドラッグして **、正しいレコードと修正**されたレコードを結合します。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-117">Drag that blue connector to **Combine Correct and Corrected Records**.</span></span>  
  
     <span data-ttu-id="7ea2f-118">![正しい結合と修正された接続を修正しました](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "正しい結合と修正された接続を修正しました")</span><span class="sxs-lookup"><span data-stu-id="7ea2f-118">![Connect Corrected to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connect Corrected to Combine Correct and Corrected")</span></span>  
  
7.  <span data-ttu-id="7ea2f-119">この**コネクタ**のタイトルは "**修正**済み" にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-119">This **connector** should be titled **Corrected**.</span></span> <span data-ttu-id="7ea2f-120">**正しい**条件は2つ**だけであり、1**つの条件が既に使用されているため、[**入力出力の選択**] ダイアログボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-120">Since you have only two conditions **Correct** and **Corrected**, and one condition was already used, the **Input Output Selection** dialog box is not displayed this time.</span></span> <span data-ttu-id="7ea2f-121">コネクタが重複する場合は、左側のコネクタを右側のコネクタに、または右側のコネクタを左側のコネクタにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="7ea2f-121">If the connectors overlap, move one to left and the other one to right by dragging the connector to left or right.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7ea2f-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="7ea2f-122">Next Step</span></span>  
 [<span data-ttu-id="7ea2f-123">タスク 10: あいまいグループ化変換を追加して重複を識別する</span><span class="sxs-lookup"><span data-stu-id="7ea2f-123">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
