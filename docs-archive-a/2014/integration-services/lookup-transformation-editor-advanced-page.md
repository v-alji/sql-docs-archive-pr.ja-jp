---
title: '[参照変換エディター] ([詳細設定] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23f235ef0506da7ac808d832db6ac36d53cfa604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641068"
---
# <a name="lookup-transformation-editor-advanced-page"></a><span data-ttu-id="e46a8-102">[参照変換エディター] ([詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="e46a8-102">Lookup Transformation Editor (Advanced Page)</span></span>
  <span data-ttu-id="e46a8-103">**[参照変換エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用して、部分キャッシュを構成し、参照変換用 SQL ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="e46a8-103">Use the **Advanced** page of the **Lookup Transformation Editor** dialog box to configure partial caching and to modify the SQL statement for the Lookup transformation.</span></span>  
  
 <span data-ttu-id="e46a8-104">参照変換の詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e46a8-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e46a8-105">Options</span><span class="sxs-lookup"><span data-stu-id="e46a8-105">Options</span></span>  
 <span data-ttu-id="e46a8-106">**[キャッシュ サイズ (32 ビット)]**</span><span class="sxs-lookup"><span data-stu-id="e46a8-106">**Cache size (32-bit)**</span></span>  
 <span data-ttu-id="e46a8-107">32 ビット コンピューター用のキャッシュ サイズを MB 単位で調整します。</span><span class="sxs-lookup"><span data-stu-id="e46a8-107">Adjust the  cache size (in megabytes) for 32-bit computers.</span></span> <span data-ttu-id="e46a8-108">既定値は 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="e46a8-108">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="e46a8-109">**[キャッシュ サイズ (64 ビット)]**</span><span class="sxs-lookup"><span data-stu-id="e46a8-109">**Cache size (64-bit)**</span></span>  
 <span data-ttu-id="e46a8-110">64 ビット コンピューター用のキャッシュ サイズを MB 単位で調整します。</span><span class="sxs-lookup"><span data-stu-id="e46a8-110">Adjust the cache size (in megabytes) for 64-bit computers.</span></span> <span data-ttu-id="e46a8-111">既定値は 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="e46a8-111">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="e46a8-112">**[エントリが一致しない行のキャッシュを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="e46a8-112">**Enable cache for rows with no matching entries**</span></span>  
 <span data-ttu-id="e46a8-113">一致するエントリが参照データセットにない行をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="e46a8-113">Cache rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="e46a8-114">**[キャッシュからの割り当て]**</span><span class="sxs-lookup"><span data-stu-id="e46a8-114">**Allocation from cache**</span></span>  
 <span data-ttu-id="e46a8-115">一致するエントリが参照データセットにない行に対して割り当てるキャッシュの割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="e46a8-115">Specify the percentage of the cache to allocate for rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="e46a8-116">**[SQL ステートメントを変更する]**</span><span class="sxs-lookup"><span data-stu-id="e46a8-116">**Modify the SQL statement**</span></span>  
 <span data-ttu-id="e46a8-117">参照データセットを生成するために使用される SQL ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="e46a8-117">Modify the SQL statement that is used to generate the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e46a8-118">このページで指定するオプションの SQL ステートメントは、**[参照変換エディター]** の **[接続]** ページで指定したテーブル名をオーバーライドおよび置換します。</span><span class="sxs-lookup"><span data-stu-id="e46a8-118">The optional SQL statement that you specify on this page overrides and replaces the table name that you specified on the **Connection** page of the **Lookup Transformation Editor**.</span></span> <span data-ttu-id="e46a8-119">詳細については、「 [[参照変換エディター] &#40;[接続] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e46a8-119">For more information, see [Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).</span></span>  
  
 <span data-ttu-id="e46a8-120">**[パラメーターの設定]**</span><span class="sxs-lookup"><span data-stu-id="e46a8-120">**Set Parameters**</span></span>  
 <span data-ttu-id="e46a8-121">**[クエリ パラメーターの設定]** ダイアログ ボックスを使用して、入力列をパラメーターにマップします。</span><span class="sxs-lookup"><span data-stu-id="e46a8-121">Map input columns to parameters by using the **Set Query Parameters** dialog box.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e46a8-122">外部リソース</span><span class="sxs-lookup"><span data-stu-id="e46a8-122">External Resources</span></span>  
 <span data-ttu-id="e46a8-123">blogs.msdn.com のブログ「 [キャッシュ モードの参照](https://go.microsoft.com/fwlink/?LinkId=219518) 」</span><span class="sxs-lookup"><span data-stu-id="e46a8-123">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46a8-124">参照</span><span class="sxs-lookup"><span data-stu-id="e46a8-124">See Also</span></span>  
 <span data-ttu-id="e46a8-125">[[参照変換エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e46a8-125">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="e46a8-126">[[参照変換エディター] &#40;接続ページ&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="e46a8-126">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="e46a8-127">[[参照変換エディター] &#40;[列] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e46a8-127">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e46a8-128">[[参照変換エディター] &#40;エラー出力ページ&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e46a8-128">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="e46a8-129">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e46a8-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="e46a8-130">あいまい参照変換</span><span class="sxs-lookup"><span data-stu-id="e46a8-130">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
