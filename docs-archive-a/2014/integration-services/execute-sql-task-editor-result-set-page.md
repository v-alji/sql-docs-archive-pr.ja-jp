---
title: '[SQL 実行タスクエディター] ([結果セット] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 027f3c77e84b47958e9fb6567acdb308c14eb1e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634580"
---
# <a name="execute-sql-task-editor-result-set-page"></a><span data-ttu-id="379f9-102">[SQL 実行タスク エディター] ([結果セット] ページ)</span><span class="sxs-lookup"><span data-stu-id="379f9-102">Execute SQL Task Editor (Result Set Page)</span></span>
  <span data-ttu-id="379f9-103">**[SQL 実行タスク エディター]** ダイアログ ボックスの **[結果セット]** ページを使用すると、SQL ステートメントの結果を新しい変数または既存の変数にマップできます。</span><span class="sxs-lookup"><span data-stu-id="379f9-103">Use the **Result Set** page of the **Execute SQL Task Editor** dialog to map the result of the SQL statement to new or existing variables.</span></span> <span data-ttu-id="379f9-104">このダイアログ ボックスのオプションは、[全般] ページの **[ResultSet]** が **[なし]** に設定されている場合は無効です。</span><span class="sxs-lookup"><span data-stu-id="379f9-104">The options in this dialog box are disabled if **ResultSet** on the General page is set to **None**.</span></span>  
  
 <span data-ttu-id="379f9-105">このタスクの詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクにおける結果セット](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="379f9-105">For more information about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="379f9-106">Options</span><span class="sxs-lookup"><span data-stu-id="379f9-106">Options</span></span>  
 <span data-ttu-id="379f9-107">**[結果名]**</span><span class="sxs-lookup"><span data-stu-id="379f9-107">**Result Name**</span></span>  
 <span data-ttu-id="379f9-108">**[追加]** をクリックして結果セットのマッピング設定を追加した後、結果に名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="379f9-108">After you have added a result set mapping set by clicking **Add**, provide a name for the result.</span></span> <span data-ttu-id="379f9-109">結果セットの種類によっては、特定の結果名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="379f9-109">Depending on the result set type, you must use specific result names.</span></span>  
  
 <span data-ttu-id="379f9-110">結果セットの種類が " **単一行**" の場合、クエリによって返される列の名前か、クエリによって返される列の列リスト内で列の位置を示す数値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="379f9-110">If the result set type is **Single row**, you can use either the name of a column returned by the query or the number that represents the position of a column in the column list of a column returned by the query.</span></span>  
  
 <span data-ttu-id="379f9-111">結果セットの種類が " **完全な結果セット** " または " **XML**" の場合、結果セット名には 0 を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="379f9-111">If the result set type is **Full result set** or **XML**, you must use 0 as the result set name.</span></span>  
  
 <span data-ttu-id="379f9-112">**関連項目**: [SQL 実行タスクにおける結果セット](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="379f9-112">**Related Topics**: [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="379f9-113">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="379f9-113">**Variable Name**</span></span>  
 <span data-ttu-id="379f9-114">変数を選択して変数に結果セットをマップするか、[\<**New variable...**>] をクリックして **[変数の追加]** ダイアログ ボックスで新しい変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="379f9-114">Map the result set to a variable by selecting a variable or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="379f9-115">**追加**</span><span class="sxs-lookup"><span data-stu-id="379f9-115">**Add**</span></span>  
 <span data-ttu-id="379f9-116">結果セットのマッピングを追加します。</span><span class="sxs-lookup"><span data-stu-id="379f9-116">Click to add a result set mapping.</span></span>  
  
 <span data-ttu-id="379f9-117">**Remove**</span><span class="sxs-lookup"><span data-stu-id="379f9-117">**Remove**</span></span>  
 <span data-ttu-id="379f9-118">一覧で結果セットのマッピングを選択して、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="379f9-118">Select a result set mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="379f9-119">参照</span><span class="sxs-lookup"><span data-stu-id="379f9-119">See Also</span></span>  
 <span data-ttu-id="379f9-120">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="379f9-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="379f9-121">[[SQL 実行タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="379f9-121">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="379f9-122">[[SQL 実行タスクエディター] &#40;[パラメーターマッピング] ページ&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="379f9-122">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 [<span data-ttu-id="379f9-123">TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="379f9-123">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
