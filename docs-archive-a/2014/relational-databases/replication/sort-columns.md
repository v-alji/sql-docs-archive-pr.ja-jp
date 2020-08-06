---
title: '[列の並べ替え] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5fe56688a009fd60a7731b199f32352d78bb5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743214"
---
# <a name="sort-columns"></a><span data-ttu-id="38334-102">[列の並べ替え]</span><span class="sxs-lookup"><span data-stu-id="38334-102">Sort Columns</span></span>
  <span data-ttu-id="38334-103">**[列の並べ替え]** ダイアログ ボックスでは、1 つ以上の列を基準にしてレプリケーション モニターのグリッドを並べ替えることができます</span><span class="sxs-lookup"><span data-stu-id="38334-103">The **Sort Columns** dialog box lets you sort grids in Replication Monitor based on one or more columns.</span></span> <span data-ttu-id="38334-104">(また、レプリケーション モニターのグリッドの列ヘッダーをクリックすることにより、1 つの列を基準にして並べ替えることもできます)。</span><span class="sxs-lookup"><span data-stu-id="38334-104">(You can also sort on a single column by clicking the column header in the Replication Monitor grid).</span></span> <span data-ttu-id="38334-105">たとえば、 **[すべてのサブスクリプション]** タブのサブスクリプションを、まず状態を基準にして並べ替え、次に接続の種類を基準にして並べ替えるには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="38334-105">For example, to sort subscriptions on the **All Subscriptions** tab based on status and then connection type, follow these steps:</span></span>  
  
1.  <span data-ttu-id="38334-106">グリッドの最初の行で、 **[列名]** 列から **[状態]** を選択し、 **[並べ替え順序]** 列から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="38334-106">In the first row of the grid, select **Status** from the **Column Name** column and a value from the **Sort Order** column</span></span>  
  
2.  <span data-ttu-id="38334-107">グリッドの 2 番目の行で、 **[列名]** 列から **[接続の種類]** を選択し、 **[並べ替え順序]** 列から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="38334-107">In the second row of the grid, select **Connection Type** from the **Column Name** column, and a value from the **Sort Order** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="38334-108">オプション</span><span class="sxs-lookup"><span data-stu-id="38334-108">Options</span></span>  
 <span data-ttu-id="38334-109">**列名**</span><span class="sxs-lookup"><span data-stu-id="38334-109">**Column Name**</span></span>  
 <span data-ttu-id="38334-110">並べ替える列の名前です。</span><span class="sxs-lookup"><span data-stu-id="38334-110">The name of the column on which you want to sort.</span></span> <span data-ttu-id="38334-111">1 つ以上の列を基準にして並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="38334-111">You can sort on one or more columns.</span></span> <span data-ttu-id="38334-112">**[パブリケーション]** タブの **[現在の平均パフォーマンス]** 列または **[現在の最低パフォーマンス]** 列を基準にして並べ替えることはできません。その理由は、これらの列の値の計算方法にあります。</span><span class="sxs-lookup"><span data-stu-id="38334-112">You cannot sort on the **Current Average Performance** or **Current Worst Performance** columns on the **Publications** tab, because of the way in which these column values are calculated.</span></span>  
  
 <span data-ttu-id="38334-113">**[並べ替え順序]**</span><span class="sxs-lookup"><span data-stu-id="38334-113">**Sort Order**</span></span>  
 <span data-ttu-id="38334-114">**[昇順]** または **[降順]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="38334-114">Specify a value of **Ascending** or **Descending**.</span></span>  
  
 <span data-ttu-id="38334-115">**[すべてクリア]**</span><span class="sxs-lookup"><span data-stu-id="38334-115">**Clear All**</span></span>  
 <span data-ttu-id="38334-116">並べ替えグリッドからすべての行を削除します。</span><span class="sxs-lookup"><span data-stu-id="38334-116">Remove all rows from the sorting grid.</span></span> <span data-ttu-id="38334-117">1 つの行を削除するには、行を選択して Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="38334-117">To remove a single row, select the row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38334-118">参照</span><span class="sxs-lookup"><span data-stu-id="38334-118">See Also</span></span>  
 [<span data-ttu-id="38334-119">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="38334-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
