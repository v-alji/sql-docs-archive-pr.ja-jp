---
title: '[パーティション処理変換先エディター] ([マッピング] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.mapping.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: e75b766c-85ba-453e-9576-4a1a34f91ecc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3855b15c7ebf1f6fa95c941931869064d552680e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644538"
---
# <a name="partition-processing-destination-editor-mappings-page"></a><span data-ttu-id="84130-102">[パーティション処理変換先エディター] ([マッピング] ページ)</span><span class="sxs-lookup"><span data-stu-id="84130-102">Partition Processing Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="84130-103">**[パーティション処理変換先エディター]** ダイアログ ボックスの **[マッピング]** ページを使用すると、入力列をパーティション列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="84130-103">Use the **Mappings** page of the **Partition Processing Destination Editor** dialog box to map input columns to partition columns.</span></span>  
  
 <span data-ttu-id="84130-104">パーティション処理変換先の詳細については、「 [Partition Processing Destination](data-flow/partition-processing-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84130-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84130-105">ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="84130-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="84130-106">テーブル モデルで入力列をパーティション列にマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="84130-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="84130-107">代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="84130-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="84130-108">Options</span><span class="sxs-lookup"><span data-stu-id="84130-108">Options</span></span>  
 <span data-ttu-id="84130-109">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="84130-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="84130-110">使用できる入力列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="84130-110">View the list of available input columns.</span></span> <span data-ttu-id="84130-111">ドラッグ アンド ドロップ操作により、テーブル内の使用できる入力列を変換先列にマップします。</span><span class="sxs-lookup"><span data-stu-id="84130-111">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="84130-112">**使用できる変換先列**</span><span class="sxs-lookup"><span data-stu-id="84130-112">**Available Destination Columns**</span></span>  
 <span data-ttu-id="84130-113">使用できる変換先列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="84130-113">View the list of available destination columns.</span></span> <span data-ttu-id="84130-114">ドラッグ アンド ドロップ操作により、テーブル内の使用できる変換先列を入力列にマップします。</span><span class="sxs-lookup"><span data-stu-id="84130-114">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="84130-115">**入力列**</span><span class="sxs-lookup"><span data-stu-id="84130-115">**Input Column**</span></span>  
 <span data-ttu-id="84130-116">上の表で選択された入力列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="84130-116">View input columns selected from the table above.</span></span> <span data-ttu-id="84130-117">**[使用できる入力列]** ボックスの一覧を使用して、マッピングを変更できます。</span><span class="sxs-lookup"><span data-stu-id="84130-117">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="84130-118">**変換先列**</span><span class="sxs-lookup"><span data-stu-id="84130-118">**Destination Column**</span></span>  
 <span data-ttu-id="84130-119">マップされているかどうかに関係なく、使用できる変換先列を表示します。</span><span class="sxs-lookup"><span data-stu-id="84130-119">View each available destination column, whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84130-120">参照</span><span class="sxs-lookup"><span data-stu-id="84130-120">See Also</span></span>  
 <span data-ttu-id="84130-121">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="84130-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="84130-122">[[パーティション処理変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="84130-122">[Partition Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="84130-123">[[パーティション処理変換先エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="84130-123">[Partition Processing Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)</span></span>  
  
  
