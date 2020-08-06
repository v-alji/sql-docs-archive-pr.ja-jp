---
title: 'タスク 11: 条件分割変換を追加して重複をフィルター処理する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e8370563c4275df0d0513d5434a8b16efba728d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742686"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a><span data-ttu-id="85ad2-102">タスク 11: 条件分割変換を追加して重複をフィルターする</span><span class="sxs-lookup"><span data-stu-id="85ad2-102">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>
  <span data-ttu-id="85ad2-103">ここでは、データ フローに条件分割変換を追加します。</span><span class="sxs-lookup"><span data-stu-id="85ad2-103">In this task, you add the Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="85ad2-104">この変換は、受信するレコード セットから重複をフィルターする際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-104">This transform helps you filter duplicates from the incoming record set.</span></span> <span data-ttu-id="85ad2-105">あいまいグループ化変換では、一致として検出したレコードがグループ化され、ピボット レコードとしてレコードのいずれかが選択されます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-105">The Fuzzy Group transform groups the records that it finds to be matches and picks one of the records as a pivot record.</span></span> <span data-ttu-id="85ad2-106">グループ内のすべてのレコードは、同じ _key_out 値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-106">All the records in a group have the same _key_out value.</span></span> <span data-ttu-id="85ad2-107">グループ内のピボット レコードは _key_out 値と同じ _key_in 値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-107">The pivot record in the group has _key_in same as the _key_out value.</span></span> <span data-ttu-id="85ad2-108">グループ内のその他のレコードでは、_key_in と _key_out の値が異なります。</span><span class="sxs-lookup"><span data-stu-id="85ad2-108">The other records in the group have different values for _key_in and _key_out.</span></span> <span data-ttu-id="85ad2-109">そのため、条件の _key_in==_key_out を使用してフィルターすると、グループ内のピボット行のみが取得されます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-109">Therefore, when you filter using the condition _key_in==_key_out, you only get the pivot row in the group.</span></span>  
  
1.  <span data-ttu-id="85ad2-110">**SSIS ツールボックス**の [**共通**] セクションから [**データフロー** ] タブに**条件分割**変換をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="85ad2-110">Drag-drop **Conditional Split** Transform from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="85ad2-111">[**データフロー** ] タブの [**条件分割変換**] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85ad2-111">Right-click **Conditional Split Transform** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="85ad2-112">「**フィルターの重複**を入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="85ad2-112">Type **Filter Duplicates** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="85ad2-113">**一致する id を持つグループサプライヤー**を接続して、**重複をフィルター処理**します。</span><span class="sxs-lookup"><span data-stu-id="85ad2-113">Connect **Group Suppliers with Matching IDs** to **Filter Duplicates**.</span></span>  
  
4.  <span data-ttu-id="85ad2-114">[重複の**フィルター** ] をダブルクリックして、[**条件分割変換エディター** ] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-114">Double-click **Filter Duplicates** to launch the **Conditional Split Transform Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="85ad2-115">左上のペインで [**列**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="85ad2-115">Expand **Columns** in the top-left pane.</span></span>  
  
6.  <span data-ttu-id="85ad2-116">**_Key_in**を [**条件**] 列にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="85ad2-116">Drag-drop **_key_in** to the **Condition** column.</span></span>  
  
7.  <span data-ttu-id="85ad2-117">[ **_Key_in** ] の横に「= = (等しい)」と入力し、 **_key_out**をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="85ad2-117">Type == (equals to) next to **_key_in** and drag-drop **_key_out**.</span></span>  
  
8.  <span data-ttu-id="85ad2-118">[**出力名**] 列の [**ケース 1** ] をクリックし、「**一意のレコード**」と入力して、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="85ad2-118">Click **Case 1** in the **Output Name** column, type **Unique Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="85ad2-119">![条件分割変換エディター](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "条件分割変換エディター")</span><span class="sxs-lookup"><span data-stu-id="85ad2-119">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Conditional Split Transformation Editor")</span></span>  
  
9. <span data-ttu-id="85ad2-120">[ **OK** ] をクリックして [**条件分割変換エディター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="85ad2-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="85ad2-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="85ad2-121">Next Step</span></span>  
 [<span data-ttu-id="85ad2-122">タスク 12: 派生列変換を追加して MDS で必要な列を追加する</span><span class="sxs-lookup"><span data-stu-id="85ad2-122">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
