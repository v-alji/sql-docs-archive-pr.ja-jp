---
title: '[Web サービスタスクエディター] ([出力] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ad034ae78a096ebe5998ac2c3d2573fe7c3bfd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644526"
---
# <a name="web-service-task-editor-output-page"></a><span data-ttu-id="9d3f4-102">[Web サービス タスク エディター] ([出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="9d3f4-102">Web Service Task Editor (Output Page)</span></span>
  <span data-ttu-id="9d3f4-103">**[Web サービス タスク エディター]** ダイアログ ボックスの **[出力]** ページを使用すると、Web メソッドから返された結果を格納する場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-103">Use the **Output** page of the **Web Service Task Editor** dialog box to specify where to store the result returned by the Web method.</span></span>  
  
 <span data-ttu-id="9d3f4-104">このタスクの詳細については、「 [Web Service Task](control-flow/web-service-task.md)」(Web サービス タスク) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-104">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="9d3f4-105">静的オプション</span><span class="sxs-lookup"><span data-stu-id="9d3f4-105">Static Options</span></span>  
 <span data-ttu-id="9d3f4-106">**[OutputType]**</span><span class="sxs-lookup"><span data-stu-id="9d3f4-106">**OutputType**</span></span>  
 <span data-ttu-id="9d3f4-107">結果を格納するときに使用するストレージ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-107">Select the storage type to use when storing the results.</span></span> <span data-ttu-id="9d3f4-108">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="9d3f4-109">値</span><span class="sxs-lookup"><span data-stu-id="9d3f4-109">Value</span></span>|<span data-ttu-id="9d3f4-110">説明</span><span class="sxs-lookup"><span data-stu-id="9d3f4-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d3f4-111">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="9d3f4-111">**File Connection**</span></span>|<span data-ttu-id="9d3f4-112">結果をファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-112">Store the results in a file.</span></span> <span data-ttu-id="9d3f4-113">この値を選択すると、動的オプションの **[ファイル]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-113">Selecting this value displays the dynamic option, **File**.</span></span>|  
|<span data-ttu-id="9d3f4-114">**変数**</span><span class="sxs-lookup"><span data-stu-id="9d3f4-114">**Variable**</span></span>|<span data-ttu-id="9d3f4-115">結果を変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-115">Store the results in a variable.</span></span> <span data-ttu-id="9d3f4-116">この値を選択すると、動的オプションの **[変数]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-116">Selecting this value displays the dynamic option, **Variable**.</span></span>|  
  
## <a name="outputtype-dynamic-options"></a><span data-ttu-id="9d3f4-117">[OutputType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="9d3f4-117">OutputType Dynamic Options</span></span>  
  
### <a name="outputtype--file-connection"></a><span data-ttu-id="9d3f4-118">[OutputType] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="9d3f4-118">OutputType = File Connection</span></span>  
 <span data-ttu-id="9d3f4-119">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="9d3f4-119">**File**</span></span>  
 <span data-ttu-id="9d3f4-120">一覧でファイル接続マネージャーを選択するか、[\<**New Connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-120">Select a File connection manager in the list or click \<**New Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="9d3f4-121">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="9d3f4-121">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="outputtype--variable"></a><span data-ttu-id="9d3f4-122">[OutputType] = [変数]</span><span class="sxs-lookup"><span data-stu-id="9d3f4-122">OutputType = Variable</span></span>  
 <span data-ttu-id="9d3f4-123">**変数**</span><span class="sxs-lookup"><span data-stu-id="9d3f4-123">**Variable**</span></span>  
 <span data-ttu-id="9d3f4-124">一覧で変数を選択するか、[\<**New Variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="9d3f4-124">Select a variable in the list or click \<**New Variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="9d3f4-125">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="9d3f4-125">**Related Topics:**  [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3f4-126">参照</span><span class="sxs-lookup"><span data-stu-id="9d3f4-126">See Also</span></span>  
 <span data-ttu-id="9d3f4-127">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9d3f4-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9d3f4-128">[Web サービスタスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="9d3f4-128">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="9d3f4-129">[[Web サービスタスクエディター] &#40;入力ページ&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="9d3f4-129">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 <span data-ttu-id="9d3f4-130">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="9d3f4-130">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
