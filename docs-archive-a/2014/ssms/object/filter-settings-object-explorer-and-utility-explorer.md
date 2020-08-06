---
title: '[フィルターの設定] (オブジェクト エクスプローラーおよびユーティリティ エクスプローラー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.filtersettings.f1
- sql12.swb.common.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: c31fbcbef9cbab86a7bd3ab7b2fae21e626aaa59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630759"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a><span data-ttu-id="de42c-102">[フィルターの設定] (オブジェクト エクスプローラーおよびユーティリティ エクスプローラー)</span><span class="sxs-lookup"><span data-stu-id="de42c-102">Filter Settings (Object Explorer and Utility Explorer)</span></span>
  <span data-ttu-id="de42c-103">このダイアログ ボックスを使用すると、フィルターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="de42c-103">Use this dialog box to specify a filter.</span></span> <span data-ttu-id="de42c-104">フィルターを使用すると、特定の条件を満たす項目だけを表示するようにオブジェクト エクスプローラーとユーティリティ エクスプローラーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="de42c-104">A filter allows you to configure Object Explorer and Utility Explorer to display only items that meet specific criteria.</span></span> <span data-ttu-id="de42c-105">たとえば、フィルターを使用して、"Maintenance" という単語を含む名前のジョブだけを表示できます。</span><span class="sxs-lookup"><span data-stu-id="de42c-105">For example, you can use a filter to show only jobs with names that contain the word "Maintenance."</span></span> <span data-ttu-id="de42c-106">**[フィルターの設定]** ダイアログ ボックスのヘッダーにはサーバーの名前が含まれ、場合によってはデータベースの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="de42c-106">The header for the **Filter Settings** dialog box contains the name of the server, and it may contain the name of the database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="de42c-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="de42c-107">UI element list</span></span>  
 <span data-ttu-id="de42c-108">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="de42c-108">**Property**</span></span>  
 <span data-ttu-id="de42c-109">フィルター処理の対象となるプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-109">Displays the property to filter on.</span></span>  
  
 <span data-ttu-id="de42c-110">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="de42c-110">**Operator**</span></span>  
 <span data-ttu-id="de42c-111">フィルターの値をプロパティに適用する方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="de42c-111">Select the way that the filter applies the value to the property.</span></span> <span data-ttu-id="de42c-112">次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="de42c-112">There are the following options:</span></span>  
  
-   <span data-ttu-id="de42c-113">**[等しい]**</span><span class="sxs-lookup"><span data-stu-id="de42c-113">**Equals**</span></span>  
  
     <span data-ttu-id="de42c-114">このフィルターは、プロパティとこの値が厳密に一致する項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-114">The filter shows items where the property and the value are an exact match.</span></span>  
  
-   <span data-ttu-id="de42c-115">**Contains**</span><span class="sxs-lookup"><span data-stu-id="de42c-115">**Contains**</span></span>  
  
     <span data-ttu-id="de42c-116">このフィルターは、プロパティにこの値が含まれている項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-116">The filter shows items where the property contains the value.</span></span> <span data-ttu-id="de42c-117">プロパティには他のテキストが含まれていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="de42c-117">The property may contain other text.</span></span>  
  
-   <span data-ttu-id="de42c-118">**[次を含まない]**</span><span class="sxs-lookup"><span data-stu-id="de42c-118">**Does not contain**</span></span>  
  
     <span data-ttu-id="de42c-119">このフィルターは、プロパティにこの値が含まれていない項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-119">The filter shows items that where the property does not contain the value.</span></span>  
  
-   <span data-ttu-id="de42c-120">**より小さい**</span><span class="sxs-lookup"><span data-stu-id="de42c-120">**Less than**</span></span>  
  
     <span data-ttu-id="de42c-121">日付に使用できるこのフィルターは、指定された値よりも古い日付を持つ項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-121">Available for dates, this filter shows items whose date is before the value provided.</span></span>  
  
-   <span data-ttu-id="de42c-122">**[次の値以下]**</span><span class="sxs-lookup"><span data-stu-id="de42c-122">**Less than or equal**</span></span>  
  
     <span data-ttu-id="de42c-123">日付に使用できるこのフィルターは、指定された値の日付またはそれよりも古い日付を持つ項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-123">Available for dates, this filter shows items whose date contains or is before the value provided.</span></span>  
  
-   <span data-ttu-id="de42c-124">**より大きい**</span><span class="sxs-lookup"><span data-stu-id="de42c-124">**Greater than**</span></span>  
  
     <span data-ttu-id="de42c-125">日付に使用できるこのフィルターは、指定された値よりも新しい日付を持つ項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-125">Available for dates, this filter shows items whose date is after the value provided.</span></span>  
  
-   <span data-ttu-id="de42c-126">**[次の値以上]**</span><span class="sxs-lookup"><span data-stu-id="de42c-126">**Greater than or equal**</span></span>  
  
     <span data-ttu-id="de42c-127">日付に使用できるこのフィルターは、指定された値の日付またはそれよりも新しい日付を持つ項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-127">Available for dates, this filter shows items whose date contains or is after the value provided.</span></span>  
  
-   <span data-ttu-id="de42c-128">**[次の値の間]**</span><span class="sxs-lookup"><span data-stu-id="de42c-128">**Between**</span></span>  
  
     <span data-ttu-id="de42c-129">日付に使用できるこのフィルターは、指定された 2 つの日付で示される範囲内の日付を持つ項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-129">Available for dates, this filter shows items whose date is between two dates provided.</span></span> <span data-ttu-id="de42c-130">**[次の値の間]** を選択し、Tab キーを押すと、2 番目の日付を入力するための行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="de42c-130">Select **Between** and press TAB to add another row allowing entry of the second date.</span></span>  
  
-   <span data-ttu-id="de42c-131">**[次の値の範囲外]**</span><span class="sxs-lookup"><span data-stu-id="de42c-131">**Not between**</span></span>  
  
     <span data-ttu-id="de42c-132">日付に使用できるこのフィルターは、指定された 2 つの日付で示される範囲よりも前または後の日付を持つ項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-132">Available for dates, this filter shows items whose date is before or after two dates provided.</span></span> <span data-ttu-id="de42c-133">**[次の値の範囲外]** を選択し、Tab キーを押して **[オペレーター]** 列の外に移動すると、2 番目の日付を入力するための行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="de42c-133">Select **Not Between** and tab out of the **Operator** column to add another row allowing entry of the second date.</span></span>  
  
 <span data-ttu-id="de42c-134">**Value**</span><span class="sxs-lookup"><span data-stu-id="de42c-134">**Value**</span></span>  
 <span data-ttu-id="de42c-135">プロパティと比較する値を入力します。</span><span class="sxs-lookup"><span data-stu-id="de42c-135">Type the value to compare to the property.</span></span> <span data-ttu-id="de42c-136">日付の場合は、矢印をクリックして日付を選択するためのカレンダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="de42c-136">For dates, click the down arrow to show a calendar for selecting the date.</span></span>  
  
 <span data-ttu-id="de42c-137">**[フィルターのクリア]**</span><span class="sxs-lookup"><span data-stu-id="de42c-137">**Clear Filter**</span></span>  
 <span data-ttu-id="de42c-138">現在のすべてのフィルター設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="de42c-138">Removes all current filter settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de42c-139">参照</span><span class="sxs-lookup"><span data-stu-id="de42c-139">See Also</span></span>  
 <span data-ttu-id="de42c-140">[SQL Server Management Studio を使用する](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="de42c-140">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="de42c-141">SQL Server ユーティリティの機能とタスク</span><span class="sxs-lookup"><span data-stu-id="de42c-141">SQL Server Utility Features and Tasks</span></span>](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
