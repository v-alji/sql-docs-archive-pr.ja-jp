---
title: '[データマイニングクエリタスクエディター] ([出力] タブ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.output.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 62f9e015-6fe0-4396-ad90-3ad51bf00025
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1508972b0487daa90f52af723d58185944a19a58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738526"
---
# <a name="data-mining-query-task-editor-output-tab"></a><span data-ttu-id="07360-102">[データ マイニング クエリ タスク エディター] ([出力] タブ)</span><span class="sxs-lookup"><span data-stu-id="07360-102">Data Mining Query Task Editor (Output Tab)</span></span>
  <span data-ttu-id="07360-103">**[データ マイニング クエリ タスク エディター]** ダイアログ ボックスの **[出力]** タブを使用すると、予測クエリの出力先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="07360-103">Use the **Output** tab of the **Data Mining Query Task Editor** dialog box to specify the destination of the prediction query.</span></span>  
  
 <span data-ttu-id="07360-104">パッケージでのデータ マイニングの実装の詳細については、「 [データ マイニング クエリ タスク](control-flow/data-mining-query-task.md) 」および「 [データ マイニング ソリューション](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07360-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="07360-105">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="07360-105">General Options</span></span>  
 <span data-ttu-id="07360-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="07360-106">**Name**</span></span>  
 <span data-ttu-id="07360-107">データ マイニング クエリ タスクに固有の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="07360-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="07360-108">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="07360-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07360-109">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="07360-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="07360-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="07360-110">**Description**</span></span>  
 <span data-ttu-id="07360-111">データ マイニング クエリ タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="07360-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="output-tab-options"></a><span data-ttu-id="07360-112">[出力] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="07360-112">Output Tab Options</span></span>  
 <span data-ttu-id="07360-113">**接続**</span><span class="sxs-lookup"><span data-stu-id="07360-113">**Connection**</span></span>  
 <span data-ttu-id="07360-114">接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="07360-114">Select a connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="07360-115">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="07360-115">**New**</span></span>  
 <span data-ttu-id="07360-116">新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="07360-116">Create a new connection manager.</span></span> <span data-ttu-id="07360-117">使用できる接続マネージャーの種類は、ADO.NET および OLE DB のみです。</span><span class="sxs-lookup"><span data-stu-id="07360-117">Only the ADO.NET and OLE DB connection manager types can be used.</span></span>  
  
 <span data-ttu-id="07360-118">**[出力テーブル]**</span><span class="sxs-lookup"><span data-stu-id="07360-118">**Output table**</span></span>  
 <span data-ttu-id="07360-119">予測クエリの結果が書き込まれるテーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="07360-119">Specify the table to which the prediction query writes its results.</span></span>  
  
 <span data-ttu-id="07360-120">**[出力テーブルを削除して、再作成する]**</span><span class="sxs-lookup"><span data-stu-id="07360-120">**Drop and re-create the output table**</span></span>  
 <span data-ttu-id="07360-121">予測クエリで、出力先のテーブルを削除して再作成することにより、テーブルの内容を上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="07360-121">Indicate whether the prediction query should overwrite content in the destination table by dropping and then re-creating the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07360-122">参照</span><span class="sxs-lookup"><span data-stu-id="07360-122">See Also</span></span>  
 <span data-ttu-id="07360-123">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="07360-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="07360-124">[データマイニングクエリタスクエディター &#40;[マイニングモデル] タブ&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="07360-124">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="07360-125">[データマイニングクエリタスクエディター &#40;[クエリ] タブ&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="07360-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 [<span data-ttu-id="07360-126">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="07360-126">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
