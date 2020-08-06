---
title: Web サービスタスクエディター ([入力] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ae876572747b9bb1088fe8b0a1c2c2fdde9f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644529"
---
# <a name="web-service-task-editor-input-page"></a><span data-ttu-id="5c7e9-102">[Web サービス タスク エディター] ([入力] ページ)</span><span class="sxs-lookup"><span data-stu-id="5c7e9-102">Web Service Task Editor (Input Page)</span></span>
  <span data-ttu-id="5c7e9-103">**[Web サービス タスク エディター]** ダイアログ ボックスの **[入力]** ページを使用すると、Web サービス、Web メソッド、および Web メソッドの入力値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-103">Use the **Input** page of the **Web Service Task Editor** dialog box to specify the Web Service, the Web method, and the values to provide to the Web method as input.</span></span> <span data-ttu-id="5c7e9-104">値を指定するには、[値] 列に直接文字列を入力するか、[値] 列から変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-104">The values can be provided either by typing strings directly in the Value column, or by selecting variables in the Value column.</span></span>  
  
 <span data-ttu-id="5c7e9-105">このタスクの詳細については、「 [Web Service Task](control-flow/web-service-task.md)」(Web サービス タスク) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-105">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c7e9-106">Options</span><span class="sxs-lookup"><span data-stu-id="5c7e9-106">Options</span></span>  
 <span data-ttu-id="5c7e9-107">**サービス**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-107">**Service**</span></span>  
 <span data-ttu-id="5c7e9-108">Web メソッドを実行するために使用する Web サービスを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-108">Select a Web service from the list to use to execute the Web method.</span></span>  
  
 <span data-ttu-id="5c7e9-109">**方法**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-109">**Method**</span></span>  
 <span data-ttu-id="5c7e9-110">タスクで実行する Web メソッドを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-110">Select a Web method from the list for the task to execute.</span></span>  
  
 <span data-ttu-id="5c7e9-111">**[WebMethodDocumentation]**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-111">**WebMethodDocumentation**</span></span>  
 <span data-ttu-id="5c7e9-112">Web メソッドの説明を入力するか、参照ボタン ( **[...]** ) をクリックして **[Web メソッド ドキュメント]** ダイアログ ボックスに説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-112">Type a description of Web method, or the click the browse button **(...)** and then type the description in the **Web Method Documentation** dialog box.</span></span>  
  
 <span data-ttu-id="5c7e9-113">**名前**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-113">**Name**</span></span>  
 <span data-ttu-id="5c7e9-114">Web メソッドへの入力の名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-114">Lists the names of the inputs to the Web method.</span></span>  
  
 <span data-ttu-id="5c7e9-115">**Type**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-115">**Type**</span></span>  
 <span data-ttu-id="5c7e9-116">入力のデータ型を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-116">Lists the data type of the inputs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c7e9-117">Web サービス タスクがサポートするパラメーターのデータ型は、整数や文字列などのプリミティブ型、プリミティブ型の配列とシーケンス、および列挙型のみです。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-117">The Web Service task supports parameters of the following data types only: primitive types such as integers and strings; arrays and sequences of primitive types; and enumerations.</span></span>  
  
 <span data-ttu-id="5c7e9-118">**変数**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-118">**Variable**</span></span>  
 <span data-ttu-id="5c7e9-119">変数を使って入力値を指定する場合は、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-119">Select the check boxes to use variables to provide inputs.</span></span>  
  
 <span data-ttu-id="5c7e9-120">**Value**</span><span class="sxs-lookup"><span data-stu-id="5c7e9-120">**Value**</span></span>  
 <span data-ttu-id="5c7e9-121">[Variable] のチェック ボックスをオンにした場合、一覧から変数を選択して入力値を指定します。それ以外の場合は、入力値として使用する値をキーボードから入力します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-121">If the Variable check-boxes are selected, select the variables in the list to provide the inputs; otherwise, type the values to use in the inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7e9-122">参照</span><span class="sxs-lookup"><span data-stu-id="5c7e9-122">See Also</span></span>  
 <span data-ttu-id="5c7e9-123">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5c7e9-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5c7e9-124">[Web サービスタスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="5c7e9-124">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="5c7e9-125">[Web サービスタスクエディター &#40;出力ページ&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="5c7e9-125">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 <span data-ttu-id="5c7e9-126">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="5c7e9-126">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
