---
title: '[パーティション処理変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a0f79dfcc9c0d98d871a49618f4dabfb8a3bbac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640124"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="3dd87-102">[パーティション処理変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="3dd87-102">Partition Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="3dd87-103">**[パーティション処理変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3dd87-103">Use the **Connection Manager** page of the **Partition Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3dd87-104">パーティション処理変換先の詳細については、「 [Partition Processing Destination](data-flow/partition-processing-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dd87-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dd87-105">ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="3dd87-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="3dd87-106">テーブル モデルで入力列をパーティション列にマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3dd87-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="3dd87-107">代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="3dd87-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3dd87-108">Options</span><span class="sxs-lookup"><span data-stu-id="3dd87-108">Options</span></span>  
 <span data-ttu-id="3dd87-109">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="3dd87-109">**Connection manager**</span></span>  
 <span data-ttu-id="3dd87-110">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-110">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="3dd87-111">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="3dd87-111">**New**</span></span>  
 <span data-ttu-id="3dd87-112">**[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-112">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="3dd87-113">**利用可能なパーティションの一覧**</span><span class="sxs-lookup"><span data-stu-id="3dd87-113">**List of available partitions**</span></span>  
 <span data-ttu-id="3dd87-114">処理するパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-114">Select the partition to process.</span></span>  
  
 <span data-ttu-id="3dd87-115">**[処理方法]**</span><span class="sxs-lookup"><span data-stu-id="3dd87-115">**Processing method**</span></span>  
 <span data-ttu-id="3dd87-116">処理方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-116">Select the processing method.</span></span> <span data-ttu-id="3dd87-117">このオプションの既定値は **[完全]** です。</span><span class="sxs-lookup"><span data-stu-id="3dd87-117">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="3dd87-118">値</span><span class="sxs-lookup"><span data-stu-id="3dd87-118">Value</span></span>|<span data-ttu-id="3dd87-119">説明</span><span class="sxs-lookup"><span data-stu-id="3dd87-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3dd87-120">[追加 (増分)]</span><span class="sxs-lookup"><span data-stu-id="3dd87-120">Add (incremental)</span></span>|<span data-ttu-id="3dd87-121">パーティションの増分処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-121">Perform an incremental processing of the partition.</span></span>|  
|<span data-ttu-id="3dd87-122">[完全]</span><span class="sxs-lookup"><span data-stu-id="3dd87-122">Full</span></span>|<span data-ttu-id="3dd87-123">パーティションの完全処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-123">Perform full processing of the partition.</span></span>|  
|<span data-ttu-id="3dd87-124">[データのみ]</span><span class="sxs-lookup"><span data-stu-id="3dd87-124">Data only</span></span>|<span data-ttu-id="3dd87-125">パーティションの更新処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="3dd87-125">Perform an update processing of the partition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3dd87-126">参照</span><span class="sxs-lookup"><span data-stu-id="3dd87-126">See Also</span></span>  
 <span data-ttu-id="3dd87-127">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3dd87-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3dd87-128">[[パーティション処理変換先エディター &#40;マッピング] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="3dd87-128">[Partition Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="3dd87-129">[[パーティション処理変換先エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="3dd87-129">[Partition Processing Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)</span></span>  
  
  
