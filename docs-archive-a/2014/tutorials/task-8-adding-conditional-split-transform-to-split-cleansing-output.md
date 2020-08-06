---
title: 'タスク 8: 条件分割変換を追加してクレンジング出力を分割する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9be7ea6f5330382ad0417df99e18bcba5b59a4e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631388"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a><span data-ttu-id="71016-102">タスク 8: 条件分割変換を追加してクレンジング出力を分割する</span><span class="sxs-lookup"><span data-stu-id="71016-102">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>
  <span data-ttu-id="71016-103">この変換では、データ フローに条件分割変換を追加します。</span><span class="sxs-lookup"><span data-stu-id="71016-103">In this transform, you add a Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="71016-104">条件分割変換では、データの内容に応じて別の出力に行をルートできます。</span><span class="sxs-lookup"><span data-stu-id="71016-104">The Conditional Split transformation can route rows to different outputs based on the content of the data.</span></span> <span data-ttu-id="71016-105">このチュートリアルでは、DQS クレンジング変換の [**レコードの状態**] 出力列を使用します。</span><span class="sxs-lookup"><span data-stu-id="71016-105">For this tutorial, you use the **Record Status** output column from the DQS Cleansing transform.</span></span> <span data-ttu-id="71016-106">このチュートリアルでは、適切なレコードまたは修正されたレコードのみを MDS サーバーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="71016-106">You will upload only correct or corrected records to MDS server in this tutorial.</span></span> <span data-ttu-id="71016-107">そのため、レコードの**状態**が**適切**であるか、**修正**されたかを確認し、レコードを MDS にアップロードする前にレコードを結合します。</span><span class="sxs-lookup"><span data-stu-id="71016-107">Therefore you check if the **Record Status** is **Correct** or **Corrected**, and combine the records before uploading the records to MDS.</span></span>  
  
1.  <span data-ttu-id="71016-108">**SSIS ツールボックス**の [**共通**] セクションから [**仕入先データのクレンジング**] の [**データフロー** ] タブに**条件分割変換**をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="71016-108">Drag-drop **Conditional Split Transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab under **Cleanse Supplier Data**.</span></span>  
  
2.  <span data-ttu-id="71016-109">[**条件分割**] を右クリックし、[**名前の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71016-109">Right-click **Conditional Split**, and click **Rename**.</span></span> <span data-ttu-id="71016-110">「**正しいレコードと修正**されたレコードを選択する **」と入力**し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="71016-110">Type **Pick Correct and Corrected Records** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="71016-111">Blue コネクタを使用して、 **Supplier データをクレンジング**し、**正しいレコードと修正**されたレコードを選択します。</span><span class="sxs-lookup"><span data-stu-id="71016-111">Connect **Cleanse Supplier Data** and **Pick Correct and Corrected Records** using the blue connector.</span></span>  
  
     <span data-ttu-id="71016-112">![仕入先データのクレンジング-適切な & 修正 > 選択](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "仕入先データのクレンジング -> 適切なデータと修正済みのデータの選択")</span><span class="sxs-lookup"><span data-stu-id="71016-112">![Cleanse Supplier Data -> Pick Correct & Corrected](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier Data -> Pick Correct & Corrected")</span></span>  
  
4.  <span data-ttu-id="71016-113">[**データフロー** ] タブで、[**適切なレコードを選択して修正し**ました] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="71016-113">Double-click **Pick Correct and Corrected Records** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="71016-114">画面の下部にある**既定の出力名**を [**修正**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="71016-114">Change the **Default Output Name** at the bottom of the screen to **Correct**.</span></span>  
  
6.  <span data-ttu-id="71016-115">左上のペインで [**列** **]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="71016-115">Expand **Columns** in the **top-left pane**.</span></span>  
  
     <span data-ttu-id="71016-116">![条件分割変換エディター](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "条件分割変換エディター")</span><span class="sxs-lookup"><span data-stu-id="71016-116">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Conditional Split Transformation Editor")</span></span>  
  
7.  <span data-ttu-id="71016-117">[レコードの**状態**] を [**条件**] 列にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="71016-117">Drag-drop **Record Status** to the **Condition** column.</span></span>  
  
8.  <span data-ttu-id="71016-118">[**条件**] 列の **[レコードの状態]** の横に「 **= = "修正済み"」** と入力します。</span><span class="sxs-lookup"><span data-stu-id="71016-118">Type **=="Corrected"** next to **[Record Status]** for the **Condition** column.</span></span>  
  
9. <span data-ttu-id="71016-119">[**出力名] 列**の**ケース 1**をクリックし、名前を "**修正**済み" に変更します。</span><span class="sxs-lookup"><span data-stu-id="71016-119">Click **Case 1** in the **Output Name Column**, and change the name to **Corrected**.</span></span>  
  
10. <span data-ttu-id="71016-120">[ **OK** ] をクリックして [**条件分割変換エディター** ] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="71016-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="71016-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="71016-121">Next Step</span></span>  
 [<span data-ttu-id="71016-122">タスク 9: 全体結合変換を追加して適切なレコードと修正済みレコードを結合する</span><span class="sxs-lookup"><span data-stu-id="71016-122">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
