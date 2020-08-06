---
title: フィルターの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d82d5f38eb460f392f1eb2ed3387ce3d97757db5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632356"
---
# <a name="filter-settings"></a><span data-ttu-id="5501a-102">[フィルターの設定]</span><span class="sxs-lookup"><span data-stu-id="5501a-102">Filter Settings</span></span>
  <span data-ttu-id="5501a-103">**[フィルターの設定]** ダイアログ ボックスを使用すると、レプリケーション モニターのグリッドのフィルターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5501a-103">The **Filter Settings** dialog box lets you define filters for grids in Replication Monitor.</span></span> <span data-ttu-id="5501a-104">たとえば、アクティブなサブスクリプションのみを **[すべてのサブスクリプション]** タブに表示するには、 **[列名]** 列から **[状態]** を選択し、 **[演算子]** 列から **[等しい]** を選択し、 **[値 1]** 列から **[アクティブ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5501a-104">For example, to show only those subscriptions that are active on the **All Subscriptions** tab, select **Status** from the **Column Name** column, **Equals** from the **Operator** column, and **Active** from the **Value1** column.</span></span> <span data-ttu-id="5501a-105">1 つ以上の列に基づくフィルターを定義したら、フィルター条件に一致する行のサブセットのみがグリッドに表示されるようにフィルターが適用されます。</span><span class="sxs-lookup"><span data-stu-id="5501a-105">After you define a filter that is based one or more columns, the filter is applied so that the grid displays only the subset of rows that match the filter criteria.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5501a-106">オプション</span><span class="sxs-lookup"><span data-stu-id="5501a-106">Options</span></span>  
 <span data-ttu-id="5501a-107">**列名**</span><span class="sxs-lookup"><span data-stu-id="5501a-107">**Column Name**</span></span>  
 <span data-ttu-id="5501a-108">フィルター選択する列の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="5501a-108">Select the name of the column on which you want to filter.</span></span> <span data-ttu-id="5501a-109">1 つ以上の列をフィルター処理の基にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5501a-109">You can base a filter on one or more columns.</span></span>  
  
 <span data-ttu-id="5501a-110">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="5501a-110">**Operator**</span></span>  
 <span data-ttu-id="5501a-111">フィルターで使用する演算子 (たとえば、 **[次の値以下]** ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="5501a-111">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="5501a-112">**[値 1]** および **[値 2]**</span><span class="sxs-lookup"><span data-stu-id="5501a-112">**Value1** and **Value2**</span></span>  
 <span data-ttu-id="5501a-113">フィルターの値を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="5501a-113">Enter or select a value for the filter.</span></span> <span data-ttu-id="5501a-114">ほとんどの演算子は **[値 1]** 列に値を入力するだけで済みますが、 **[次の値の間]** と **[次の値の範囲外]** の操作は、 **[値 2]** 列にも値を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5501a-114">Most operators only require a value in the **Value1** column, but the **Between** and **Not Between** operators also require a value in the **Value2** column.</span></span>  
  
 <span data-ttu-id="5501a-115">**[フィルターのクリア]**</span><span class="sxs-lookup"><span data-stu-id="5501a-115">**Clear Filter**</span></span>  
 <span data-ttu-id="5501a-116">このボタンをクリックすると、定義されているすべてのフィルターがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="5501a-116">Click this button to clear all filters that have been defined.</span></span> <span data-ttu-id="5501a-117">単一のフィルターを削除するには、フィルター行を選択して Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5501a-117">To remove a single filter, select the filter row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5501a-118">参照</span><span class="sxs-lookup"><span data-stu-id="5501a-118">See Also</span></span>  
 [<span data-ttu-id="5501a-119">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="5501a-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
