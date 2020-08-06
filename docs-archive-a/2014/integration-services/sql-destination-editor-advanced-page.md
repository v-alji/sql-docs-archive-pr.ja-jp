---
title: SQL 変換先エディター ([詳細設定] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ccf25ad888c93f694678a152417affe5c0e16091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633209"
---
# <a name="sql-destination-editor-advanced-page"></a><span data-ttu-id="4f9d6-102">[SQL 変換先エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="4f9d6-102">SQL Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="4f9d6-103">**[SQL 変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、詳細な一括挿入オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-103">Use the **Advanced** page of the **SQL Destination Editor** dialog box to specify advanced bulk insert options.</span></span>  
  
 <span data-ttu-id="4f9d6-104">SQL Server 変換先の詳細については、「 [SQL Server Destination](data-flow/sql-server-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-104">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4f9d6-105">Options</span><span class="sxs-lookup"><span data-stu-id="4f9d6-105">Options</span></span>  
 <span data-ttu-id="4f9d6-106">**[ID を保持する]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-106">**Keep identity**</span></span>  
 <span data-ttu-id="4f9d6-107">タスクが値を ID 列に挿入するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-107">Specify whether the task should insert values into identity columns.</span></span> <span data-ttu-id="4f9d6-108">このプロパティの既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-108">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="4f9d6-109">**[NULL を保持する]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-109">**Keep nulls**</span></span>  
 <span data-ttu-id="4f9d6-110">タスクが NULL 値を保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-110">Specify whether the task should keep null values.</span></span> <span data-ttu-id="4f9d6-111">このプロパティの既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-111">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="4f9d6-112">**[テーブル ロック]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-112">**Table lock**</span></span>  
 <span data-ttu-id="4f9d6-113">データが読み込まれるときにテーブルをロックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-113">Specify whether the table is locked when the data is loaded.</span></span> <span data-ttu-id="4f9d6-114">このプロパティの既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-114">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="4f9d6-115">**CHECK 制約**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-115">**Check constraints**</span></span>  
 <span data-ttu-id="4f9d6-116">タスクが制約をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-116">Specify whether the task should check constraints.</span></span> <span data-ttu-id="4f9d6-117">このプロパティの既定値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-117">The default value of this property is `True`.</span></span>  
  
 <span data-ttu-id="4f9d6-118">**[トリガーを起動する]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-118">**Fire triggers**</span></span>  
 <span data-ttu-id="4f9d6-119">テーブルにおける一括挿入でトリガーを起動するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-119">Specify whether the bulk insert should fire triggers on tables.</span></span> <span data-ttu-id="4f9d6-120">このプロパティの既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-120">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="4f9d6-121">**[先頭行]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-121">**First Row**</span></span>  
 <span data-ttu-id="4f9d6-122">先頭行が挿入されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-122">Specify the first row to insert.</span></span> <span data-ttu-id="4f9d6-123">このプロパティの既定値は、 **-1**です。これは、値が割り当てられていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-123">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f9d6-124">このプロパティに値を割り当てない場合、 **[SQL 変換先エディター]** のテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-124">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="4f9d6-125">**[プロパティ]** ウィンドウ、 **[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-125">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="4f9d6-126">**[最終行]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-126">**Last Row**</span></span>  
 <span data-ttu-id="4f9d6-127">最終行が挿入されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-127">Specify the last row to insert.</span></span> <span data-ttu-id="4f9d6-128">このプロパティの既定値は、 **-1**です。これは、値が割り当てられていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-128">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f9d6-129">このプロパティに値を割り当てない場合、 **[SQL 変換先エディター]** のテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-129">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="4f9d6-130">**[プロパティ]** ウィンドウ、 **[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-130">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="4f9d6-131">**エラーの最大数**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-131">**Maximum number of errors**</span></span>  
 <span data-ttu-id="4f9d6-132">一括挿入を停止する前に許容するエラー数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-132">Specify the number of errors that can occur before the bulk insert stops.</span></span> <span data-ttu-id="4f9d6-133">このプロパティの既定値は、 **-1**です。これは、値が割り当てられていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-133">The default value of this property is **-1**, indicating that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f9d6-134">このプロパティに値を割り当てない場合、 **[SQL 変換先エディター]** のテキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-134">Clear the text box in the **SQL Destination Editor** to indicate that you do not want to assign a value for this property.</span></span> <span data-ttu-id="4f9d6-135">**[プロパティ]** ウィンドウ、 **[詳細エディター]**、およびオブジェクト モデルでは、-1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-135">Use -1 in the **Properties** window, the **Advanced Editor**, and the object model.</span></span>  
  
 <span data-ttu-id="4f9d6-136">**タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-136">**Timeout**</span></span>  
 <span data-ttu-id="4f9d6-137">タイムアウトで一括挿入が停止されるまでの待機時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-137">Specify the number of seconds to wait before the bulk insert stops because of a time-out.</span></span>  
  
 <span data-ttu-id="4f9d6-138">**[列の順序]**</span><span class="sxs-lookup"><span data-stu-id="4f9d6-138">**Order columns**</span></span>  
 <span data-ttu-id="4f9d6-139">キー列の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-139">Type the names of the sort columns.</span></span> <span data-ttu-id="4f9d6-140">各列は、昇順または降順で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-140">Each column can be sorted in ascending or descending order.</span></span> <span data-ttu-id="4f9d6-141">複数のキー列を使用する場合は、リストをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="4f9d6-141">If you use multiple sort columns, delimit the list with commas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9d6-142">参照</span><span class="sxs-lookup"><span data-stu-id="4f9d6-142">See Also</span></span>  
 <span data-ttu-id="4f9d6-143">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4f9d6-143">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="4f9d6-144">[[SQL 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="4f9d6-144">[SQL Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="4f9d6-145">[SQL 変換先エディター &#40;マッピングページ&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="4f9d6-145">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="4f9d6-146">SQL Server 変換先を使用してデータの一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="4f9d6-146">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
