---
title: データマイニングクエリタスクエディター ([マイニングモデル] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.miningmodel.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 0ede9b86-be27-471e-b012-22a65adce579
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 794365c8d15ff9725fc385bb43d51e70ffa529b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718626"
---
# <a name="data-mining-query-task-editor-mining-model-tab"></a><span data-ttu-id="dbcf4-102">[データ マイニング クエリ タスク エディター] ([マイニング モデル] タブ)</span><span class="sxs-lookup"><span data-stu-id="dbcf4-102">Data Mining Query Task Editor (Mining Model Tab)</span></span>
  <span data-ttu-id="dbcf4-103">**[データ マイニング クエリ タスク]** ダイアログ ボックスの **[マイニング モデル]** タブを使用すると、使用するマイニング構造とマイニング モデルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-103">Use the **Mining Model** tab of the **Data Mining Query Task** dialog box to specify the mining structure and mining model to use.</span></span>  
  
 <span data-ttu-id="dbcf4-104">パッケージでのデータ マイニングの実装の詳細については、「 [データ マイニング クエリ タスク](control-flow/data-mining-query-task.md) 」および「 [データ マイニング ソリューション](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="dbcf4-105">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="dbcf4-105">General Options</span></span>  
 <span data-ttu-id="dbcf4-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="dbcf4-106">**Name**</span></span>  
 <span data-ttu-id="dbcf4-107">データ マイニング クエリ タスクに固有の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="dbcf4-108">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbcf4-109">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="dbcf4-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="dbcf4-110">**Description**</span></span>  
 <span data-ttu-id="dbcf4-111">データ マイニング クエリ タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="mining-model-tab-options"></a><span data-ttu-id="dbcf4-112">[マイニング モデル] タブのオプション</span><span class="sxs-lookup"><span data-stu-id="dbcf4-112">Mining Model Tab Options</span></span>  
 <span data-ttu-id="dbcf4-113">**接続**</span><span class="sxs-lookup"><span data-stu-id="dbcf4-113">**Connection**</span></span>  
 <span data-ttu-id="dbcf4-114">既存の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-114">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="dbcf4-115">**関連トピック:**  [Analysis Services 接続マネージャーの追加](connection-manager/analysis-services-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="dbcf4-115">**Related Topics:**  [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="dbcf4-116">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="dbcf4-116">**New**</span></span>  
 <span data-ttu-id="dbcf4-117">新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-117">Create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager.</span></span>  
  
 <span data-ttu-id="dbcf4-118">**関連トピック:** [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="dbcf4-118">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)</span></span>  
  
 <span data-ttu-id="dbcf4-119">**マイニング構造**</span><span class="sxs-lookup"><span data-stu-id="dbcf4-119">**Mining structure**</span></span>  
 <span data-ttu-id="dbcf4-120">一覧からマイニング構造を選択します。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-120">Select a mining structure in the list.</span></span>  
  
 <span data-ttu-id="dbcf4-121">**[マイニング モデル]**</span><span class="sxs-lookup"><span data-stu-id="dbcf4-121">**Mining models**</span></span>  
 <span data-ttu-id="dbcf4-122">選択したマイニング構造に基づいて構築されるマイニング モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="dbcf4-122">Select a mining model built on the selected mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbcf4-123">参照</span><span class="sxs-lookup"><span data-stu-id="dbcf4-123">See Also</span></span>  
 <span data-ttu-id="dbcf4-124">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dbcf4-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="dbcf4-125">[データマイニングクエリタスクエディター &#40;[クエリ] タブ&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="dbcf4-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 <span data-ttu-id="dbcf4-126">[[データマイニングクエリタスクエディター] &#40;[出力] タブ&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span><span class="sxs-lookup"><span data-stu-id="dbcf4-126">[Data Mining Query Task Editor &#40;Output Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-output-tab.md) </span></span>  
 [<span data-ttu-id="dbcf4-127">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="dbcf4-127">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
