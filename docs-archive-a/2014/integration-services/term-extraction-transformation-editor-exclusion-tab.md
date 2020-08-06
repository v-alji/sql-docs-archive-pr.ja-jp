---
title: '[用語抽出変換エディター] ([除外] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.inclusionexclusion.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bc4b0401a1dd27111d0498e9e0d848c80da1742
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645176"
---
# <a name="term-extraction-transformation-editor-exclusion-tab"></a><span data-ttu-id="7f8b3-102">[用語抽出変換エディター] ([除外] タブ)</span><span class="sxs-lookup"><span data-stu-id="7f8b3-102">Term Extraction Transformation Editor (Exclusion Tab)</span></span>
  <span data-ttu-id="7f8b3-103">**[用語抽出変換エディター]** ダイアログ ボックスの **[除外]** タブを使用すると、除外テーブルへの接続を設定し、除外用語が含まれている列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-103">Use the **Exclusion** tab of the **Term Extraction Transformation Editor** dialog box to set up a connection to an exclusion table and specify the columns that contain exclusion terms.</span></span>  
  
 <span data-ttu-id="7f8b3-104">用語抽出変換の詳細については、「 [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f8b3-105">オプション</span><span class="sxs-lookup"><span data-stu-id="7f8b3-105">Options</span></span>  
 <span data-ttu-id="7f8b3-106">**[除外用語を使用する]**</span><span class="sxs-lookup"><span data-stu-id="7f8b3-106">**Use exclusion terms**</span></span>  
 <span data-ttu-id="7f8b3-107">除外用語が含まれている列を指定することにより、用語抽出のときに特定の用語を除外するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-107">Indicate whether to exclude specific terms during term extraction by specifying a column that contains exclusion terms.</span></span> <span data-ttu-id="7f8b3-108">用語を除外する場合は、次のソース プロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-108">You must specify the following source properties if you choose to exclude terms.</span></span>  
  
 <span data-ttu-id="7f8b3-109">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="7f8b3-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="7f8b3-110">既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-110">Select an existing OLE DB connection manager, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="7f8b3-111">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="7f8b3-111">**New**</span></span>  
 <span data-ttu-id="7f8b3-112">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、データベースへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-112">Create a new connection to a database by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="7f8b3-113">**[テーブルまたはビュー]**</span><span class="sxs-lookup"><span data-stu-id="7f8b3-113">**Table or view**</span></span>  
 <span data-ttu-id="7f8b3-114">除外用語が含まれているテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-114">Select the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="7f8b3-115">**列**</span><span class="sxs-lookup"><span data-stu-id="7f8b3-115">**Column**</span></span>  
 <span data-ttu-id="7f8b3-116">除外用語が含まれているテーブルまたはビューの列を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-116">Select the column in the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="7f8b3-117">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="7f8b3-117">**Configure Error Output**</span></span>  
 <span data-ttu-id="7f8b3-118">[[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスは、エラーが発生した行に対するエラー処理を指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="7f8b3-118">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8b3-119">参照</span><span class="sxs-lookup"><span data-stu-id="7f8b3-119">See Also</span></span>  
 <span data-ttu-id="7f8b3-120">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7f8b3-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="7f8b3-121">[[用語抽出変換エディター] &#40;[用語抽出] タブ&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="7f8b3-121">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="7f8b3-122">[[用語抽出変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="7f8b3-122">[Term Extraction Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="7f8b3-123">用語参照変換</span><span class="sxs-lookup"><span data-stu-id="7f8b3-123">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
