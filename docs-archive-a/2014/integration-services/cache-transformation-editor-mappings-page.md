---
title: '[キャッシュ変換エディター] ([マッピング] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetransmap.f1
ms.assetid: ffd53f18-9646-458a-a84a-f2467d601ea5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb31e479ea98133da34dcbf257d59e70f4ffe8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644114"
---
# <a name="cache-transformation-editor-mappings-page"></a><span data-ttu-id="03a75-102">[キャッシュ変換エディター] ([マッピング] ページ)</span><span class="sxs-lookup"><span data-stu-id="03a75-102">Cache Transformation Editor (Mappings Page)</span></span>
  <span data-ttu-id="03a75-103">**[キャッシュ変換エディター]** の **[マッピング]** ページを使用して、キャッシュ変換の入力列をキャッシュ変換マネージャーの変換先列にマップします。</span><span class="sxs-lookup"><span data-stu-id="03a75-103">Use the **Mappings** page of the **Cache Transformation Editor** to map the input columns in the Cache Transform transformation to destination columns in the Cache connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03a75-104">各入力列を変換先列にマップする必要があります。このとき、列のデータ型が一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="03a75-104">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="03a75-105">それ以外の場合、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] デザイナーによりエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03a75-105">Otherwise, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
 <span data-ttu-id="03a75-106">キャッシュ変換の詳細については、「 [Cache Transform](data-flow/transformations/cache-transform.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03a75-106">To learn more about the Cache Transform, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
 <span data-ttu-id="03a75-107">キャッシュ接続マネージャーの詳細については、「 [Cache Connection manager](connection-manager/cache-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03a75-107">To learn more about the Cache connection manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="03a75-108">Options</span><span class="sxs-lookup"><span data-stu-id="03a75-108">Options</span></span>  
 <span data-ttu-id="03a75-109">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="03a75-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="03a75-110">使用できる入力列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="03a75-110">View the list of available input columns.</span></span> <span data-ttu-id="03a75-111">ドラッグ アンド ドロップ操作により、使用できる入力列を変換先列にマップします。</span><span class="sxs-lookup"><span data-stu-id="03a75-111">Use a drag-and-drop operation to map available input columns to destination columns.</span></span>  
  
 <span data-ttu-id="03a75-112">キーボードを使用して、 **[使用できる入力列]** テーブルの列を強調表示し、メニュー キーを押して、 **[一致する名前でアイテムをマップする]** を選択することで、入力列を変換先列にマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="03a75-112">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="03a75-113">**使用できる変換先列**</span><span class="sxs-lookup"><span data-stu-id="03a75-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="03a75-114">使用できる変換先列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="03a75-114">View the list of available destination columns.</span></span> <span data-ttu-id="03a75-115">ドラッグ アンド ドロップ操作により、使用できる変換先列を入力列にマップします。</span><span class="sxs-lookup"><span data-stu-id="03a75-115">Use a drag-and-drop operation to map available destination columns to input columns.</span></span>  
  
 <span data-ttu-id="03a75-116">キーボードを使用して、 **[使用できる変換先列]** テーブルの列を強調表示し、メニュー キーを押して、 **[一致する名前でアイテムをマップする]** を選択することで、入力列を変換先列にマップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="03a75-116">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Destination Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="03a75-117">**入力列**</span><span class="sxs-lookup"><span data-stu-id="03a75-117">**Input Column**</span></span>  
 <span data-ttu-id="03a75-118">このトピックの前の手順で選択した入力列を表示します。</span><span class="sxs-lookup"><span data-stu-id="03a75-118">View input columns selected earlier in this topic.</span></span> <span data-ttu-id="03a75-119">**[使用できる入力列]** ボックスの一覧を使用して、マッピングを変更できます。</span><span class="sxs-lookup"><span data-stu-id="03a75-119">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="03a75-120">**変換先列**</span><span class="sxs-lookup"><span data-stu-id="03a75-120">**Destination Column**</span></span>  
 <span data-ttu-id="03a75-121">利用可能な各変換先列を表示します。</span><span class="sxs-lookup"><span data-stu-id="03a75-121">View each available destination column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a75-122">参照</span><span class="sxs-lookup"><span data-stu-id="03a75-122">See Also</span></span>  
 <span data-ttu-id="03a75-123">[[キャッシュ変換エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/cache-transformation-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="03a75-123">[Cache Transformation Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cache-transformation-editor-connection-manager-page.md)</span></span>  
  
  
