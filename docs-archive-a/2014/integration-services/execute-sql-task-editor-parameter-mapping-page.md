---
title: '[SQL 実行タスクエディター] ([パラメーターマッピング] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfbb4468cb69947dfa54fb519b7698286393d578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634581"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a><span data-ttu-id="d799a-102">[SQL 実行タスク エディター] ([パラメーター マッピング] ページ)</span><span class="sxs-lookup"><span data-stu-id="d799a-102">Execute SQL Task Editor (Parameter Mapping Page)</span></span>
  <span data-ttu-id="d799a-103">**[SQL 実行タスク エディター]** ダイアログ ボックスの **[パラメーター マッピング]** ページを使用すると、SQL ステートメント内のパラメーターに変数をマップできます。</span><span class="sxs-lookup"><span data-stu-id="d799a-103">Use the **Parameter Mapping** page of the **Execute SQL Task Editor** dialog box to map variables to parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="d799a-104">この手順の詳細については、「 [SQL 実行タスク](control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d799a-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d799a-105">Options</span><span class="sxs-lookup"><span data-stu-id="d799a-105">Options</span></span>  
 <span data-ttu-id="d799a-106">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="d799a-106">**Variable Name**</span></span>  
 <span data-ttu-id="d799a-107">**[追加]** をクリックしてパラメーター マッピングを追加した後で、システム変数またはユーザー定義変数を一覧から選択するか、[\<**New variable...**>] をクリックして **[変数の追加]** ダイアログ ボックスで新しい変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="d799a-107">After you have added a parameter mapping by clicking **Add**, select a system or user-defined variable from the list or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="d799a-108">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="d799a-108">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
 <span data-ttu-id="d799a-109">**方向**</span><span class="sxs-lookup"><span data-stu-id="d799a-109">**Direction**</span></span>  
 <span data-ttu-id="d799a-110">パラメーターの方向を選択します。</span><span class="sxs-lookup"><span data-stu-id="d799a-110">Select the direction of the parameter.</span></span> <span data-ttu-id="d799a-111">各変数を入力パラメーター、出力パラメーター、またはリターン コードにマップします。</span><span class="sxs-lookup"><span data-stu-id="d799a-111">Map each variable to an input parameter, output parameter, or a return code.</span></span>  
  
 <span data-ttu-id="d799a-112">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="d799a-112">**Data Type**</span></span>  
 <span data-ttu-id="d799a-113">パラメーターのデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="d799a-113">Select the data type of the parameter.</span></span> <span data-ttu-id="d799a-114">使用できるデータ型の一覧は、タスクによって使用される接続マネージャーで選択したプロバイダーに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="d799a-114">The list of available data types is specific to the provider selected in the connection manager used by the task.</span></span>  
  
 <span data-ttu-id="d799a-115">**パラメーター名**</span><span class="sxs-lookup"><span data-stu-id="d799a-115">**Parameter Name**</span></span>  
 <span data-ttu-id="d799a-116">パラメーター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d799a-116">Provide a parameter name.</span></span>  
  
 <span data-ttu-id="d799a-117">タスクで使用される接続マネージャーの種類によって、数字またはパラメーター名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d799a-117">Depending on the connection manager type that the task uses, you must use numbers or parameter names.</span></span> <span data-ttu-id="d799a-118">接続マネージャーの種類によっては、パラメーター名の先頭文字を \@ 記号にすること、\@Param1 などの特定の名前を使用すること、またはパラメーター名として列名を使用することが求められます。</span><span class="sxs-lookup"><span data-stu-id="d799a-118">Some connection manager types require that the first character of the parameter name is the \@ sign , specific names like \@Param1, or column names as parameter names.</span></span>  
  
 <span data-ttu-id="d799a-119">**関連トピック:** [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="d799a-119">**Related Topics:** [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="d799a-120">**[パラメーター サイズ]**</span><span class="sxs-lookup"><span data-stu-id="d799a-120">**Parameter Size**</span></span>  
 <span data-ttu-id="d799a-121">文字列やバイナリ フィールドなどの可変長パラメーターのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="d799a-121">Provide the size of parameters that have variable length, such as strings and binary fields.</span></span>  
  
 <span data-ttu-id="d799a-122">この設定により、プロバイダーは可変長パラメーター値に十分な領域を割り当てることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="d799a-122">This setting ensures that the provider allocates sufficient space for variable-length parameter values.</span></span>  
  
 <span data-ttu-id="d799a-123">**追加**</span><span class="sxs-lookup"><span data-stu-id="d799a-123">**Add**</span></span>  
 <span data-ttu-id="d799a-124">クリックすると、パラメーター マッピングが追加されます。</span><span class="sxs-lookup"><span data-stu-id="d799a-124">Click to add a parameter mapping.</span></span>  
  
 <span data-ttu-id="d799a-125">**Remove**</span><span class="sxs-lookup"><span data-stu-id="d799a-125">**Remove**</span></span>  
 <span data-ttu-id="d799a-126">一覧からパラメーター マッピングを選択してから **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d799a-126">Select a parameter mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d799a-127">参照</span><span class="sxs-lookup"><span data-stu-id="d799a-127">See Also</span></span>  
 <span data-ttu-id="d799a-128">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d799a-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d799a-129">[[SQL 実行タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d799a-129">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d799a-130">[[SQL 実行タスクエディター &#40;結果セット] ページ&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span><span class="sxs-lookup"><span data-stu-id="d799a-130">[Execute SQL Task Editor &#40;Result Set Page&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span></span>  
 [<span data-ttu-id="d799a-131">TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="d799a-131">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
