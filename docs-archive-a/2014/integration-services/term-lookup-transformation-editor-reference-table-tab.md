---
title: '[用語参照変換エディター] ([参照テーブル] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.referencetable.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 86ccec6d-615b-4f84-9226-ff80d8012f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f76f15d894896e70139ef80cb2ebad7004ef47ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645172"
---
# <a name="term-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="ac208-102">[用語参照変換エディター] ([参照テーブル] タブ)</span><span class="sxs-lookup"><span data-stu-id="ac208-102">Term Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="ac208-103">**[用語参照変換エディター]** ダイアログ ボックスの **[参照テーブル]** タブを使用すると、参照テーブルへの接続を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac208-103">Use the **Reference Table** tab of the **Term Lookup Transformation Editor** dialog box to specify the connection to the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="ac208-104">用語参照変換の詳細については、「 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac208-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ac208-105">オプション</span><span class="sxs-lookup"><span data-stu-id="ac208-105">Options</span></span>  
 <span data-ttu-id="ac208-106">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="ac208-106">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="ac208-107">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="ac208-107">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="ac208-108">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="ac208-108">**New**</span></span>  
 <span data-ttu-id="ac208-109">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="ac208-109">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="ac208-110">**[参照テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="ac208-110">**Reference table name**</span></span>  
 <span data-ttu-id="ac208-111">一覧から項目を選択することにより、データベースからの参照テーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="ac208-111">Select a lookup table or view from the database by selecting an item from the list.</span></span> <span data-ttu-id="ac208-112">テーブルまたはビューは、変換元の列のテキストとの比較に使用できる、既存の一覧が含まれた列を含んでいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac208-112">The table or view should contain a column with an existing list of terms that the text in the source column can be compared to.</span></span>  
  
 <span data-ttu-id="ac208-113">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="ac208-113">**Configure Error Output**</span></span>  
 <span data-ttu-id="ac208-114">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスは、エラーが発生した行に対するエラー処理オプションを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ac208-114">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac208-115">参照</span><span class="sxs-lookup"><span data-stu-id="ac208-115">See Also</span></span>  
 <span data-ttu-id="ac208-116">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ac208-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ac208-117">[[用語参照変換エディター] &#40;[用語参照] タブ&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ac208-117">[Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span></span>  
 <span data-ttu-id="ac208-118">[[用語参照変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ac208-118">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="ac208-119">用語抽出変換</span><span class="sxs-lookup"><span data-stu-id="ac208-119">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
