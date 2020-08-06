---
title: '[参照変換エディター] ([全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713302"
---
# <a name="lookup-transformation-editor-general-page"></a><span data-ttu-id="f3b4a-102">[参照変換エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="f3b4a-102">Lookup Transformation Editor (General Page)</span></span>
  <span data-ttu-id="f3b4a-103">[参照変換エディター] ダイアログ ボックスの **[全般]** ページを使用して、キャッシュ モードや接続の種類を選択し、一致するエントリがない行の処理方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-103">Use the **General** page of the Lookup Transformation Editor dialog box to select the cache mode, select the connection type, and specify how to handle rows with no matching entries.</span></span>  
  
 <span data-ttu-id="f3b4a-104">参照変換の詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3b4a-105">Options</span><span class="sxs-lookup"><span data-stu-id="f3b4a-105">Options</span></span>  
 <span data-ttu-id="f3b4a-106">**[フル キャッシュ]**</span><span class="sxs-lookup"><span data-stu-id="f3b4a-106">**Full cache**</span></span>  
 <span data-ttu-id="f3b4a-107">参照変換を実行する前に、参照データセットを生成してキャッシュに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-107">Generate and load the reference dataset into cache before the Lookup transformation is executed.</span></span>  
  
 <span data-ttu-id="f3b4a-108">**[部分キャッシュ]**</span><span class="sxs-lookup"><span data-stu-id="f3b4a-108">**Partial cache**</span></span>  
 <span data-ttu-id="f3b4a-109">参照変換の実行中に、参照データセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-109">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="f3b4a-110">参照データセットに一致するエントリがある行、およびデータセットに一致するエントリがない行をキャッシュに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-110">Load the rows with matching entries in the reference dataset and the rows with no matching entries in the dataset into cache.</span></span>  
  
 <span data-ttu-id="f3b4a-111">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="f3b4a-111">**No cache**</span></span>  
 <span data-ttu-id="f3b4a-112">参照変換の実行中に、参照データセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-112">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="f3b4a-113">キャッシュにデータは読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-113">No data is loaded into cache.</span></span>  
  
 <span data-ttu-id="f3b4a-114">**キャッシュ接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="f3b4a-114">**Cache connection manager**</span></span>  
 <span data-ttu-id="f3b4a-115">キャッシュ接続マネージャーを使用するように参照変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-115">Configure the Lookup transformation to use a Cache connection manager.</span></span> <span data-ttu-id="f3b4a-116">このオプションを選択できるのは、[フル キャッシュ] オプションを選択した場合だけです。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-116">This option is available only if the Full cache option is selected.</span></span>  
  
 <span data-ttu-id="f3b4a-117">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="f3b4a-117">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="f3b4a-118">OLE DB 接続マネージャーを使用するように参照変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-118">Configure the Lookup transformation to use an OLE DB connection manager.</span></span>  
  
 <span data-ttu-id="f3b4a-119">**[エントリが一致しない行の処理方法を指定する]**</span><span class="sxs-lookup"><span data-stu-id="f3b4a-119">**Specify how to handle rows with no matching entries**</span></span>  
 <span data-ttu-id="f3b4a-120">参照データセット内で少なくとも 1 つのエントリが一致しない行を処理するためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-120">Select an option for handling rows that do not match at least one entry in the reference dataset.</span></span>  
  
 <span data-ttu-id="f3b4a-121">**[一致なしの出力に行をリダイレクトする]** を選択した場合は、行が一致なしの出力にリダイレクトされ、エラーとして処理されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-121">When you select **Redirect rows to no match output**, the rows are redirected to a no match output and are not handled as errors.</span></span> <span data-ttu-id="f3b4a-122">**[参照変換エディター]** ダイアログ ボックスの **[エラー出力]** ページの **[エラー]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-122">The **Error** option on the **Error Output** page of the **Lookup Transformation Editor** dialog box is not available.</span></span>  
  
 <span data-ttu-id="f3b4a-123">**[エントリが一致しない行の処理方法を指定する]** ボックスの一覧で他のオプションを選択した場合は、行がエラーとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-123">When you select any other option in the **Specify how to handle rows with no matching entries** list box, the rows are handled as errors.</span></span> <span data-ttu-id="f3b4a-124">**[エラー出力]** ページの **[エラー]** オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3b4a-124">The **Error** option on the **Error Output** page is available.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="f3b4a-125">外部リソース</span><span class="sxs-lookup"><span data-stu-id="f3b4a-125">External Resources</span></span>  
 <span data-ttu-id="f3b4a-126">blogs.msdn.com のブログ「 [キャッシュ モードの参照](https://go.microsoft.com/fwlink/?LinkId=219518) 」</span><span class="sxs-lookup"><span data-stu-id="f3b4a-126">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b4a-127">参照</span><span class="sxs-lookup"><span data-stu-id="f3b4a-127">See Also</span></span>  
 <span data-ttu-id="f3b4a-128">[キャッシュ接続マネージャー](connection-manager/cache-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f3b4a-128">[Cache Connection Manager](connection-manager/cache-connection-manager.md) </span></span>  
 <span data-ttu-id="f3b4a-129">[[参照変換エディター] &#40;接続ページ&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="f3b4a-129">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="f3b4a-130">[[参照変換エディター] &#40;[列] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="f3b4a-130">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="f3b4a-131">[[参照変換エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="f3b4a-131">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="f3b4a-132">[参照変換エディター ([エラー出力] ページ)](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="f3b4a-132">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)</span></span>  
  
  
