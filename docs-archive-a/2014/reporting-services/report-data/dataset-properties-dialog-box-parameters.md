---
title: '[パラメーター] ([データセットのプロパティ] ダイアログ ボックス) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0073971de373321ce347f416657671e1f497dd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742890"
---
# <a name="dataset-properties-dialog-box-parameters"></a><span data-ttu-id="60e17-102">[パラメーター] ([データセットのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="60e17-102">Dataset Properties Dialog Box, Parameters</span></span>
  <span data-ttu-id="60e17-103">**[データセットのプロパティ]** ダイアログ ボックスの **[パラメーター]** を選択すると、クエリ パラメーター (レポート パラメーターにリンクするクエリ パラメーターを含む) の追加、変更、および削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="60e17-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters, including query parameters that link to report parameters.</span></span>  
  
 <span data-ttu-id="60e17-104">[クエリ] タブでクエリが変更されるたびに、クエリ コマンドが解析されます。</span><span class="sxs-lookup"><span data-stu-id="60e17-104">Whenever the query is changed on the query tab, the query command is parsed.</span></span> <span data-ttu-id="60e17-105">識別されたクエリ パラメーターごとに、大文字と小文字の区別も含めて同じ名前のレポート パラメーターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="60e17-105">For each query parameter that is identified, a report parameter with an identical case-sensitive name is created.</span></span> <span data-ttu-id="60e17-106">既定では、クエリ パラメーターは自動的にクエリ パラメーターの一覧に追加され、対応するレポート パラメーターにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="60e17-106">By default, the query parameter is automatically added to the query parameter list and linked to the corresponding report parameter.</span></span>  
  
 <span data-ttu-id="60e17-107">レポート パラメーターの既定値が、クエリ パラメーターにリンクする別のレポート パラメーターに依存している場合は、( **[レポート パラメーターのプロパティ]** ダイアログ ボックスに表示されている) レポート パラメーターの順序が重要になります。</span><span class="sxs-lookup"><span data-stu-id="60e17-107">If there are dependencies for the default values of one report parameter on another report parameter that is linked to a query parameter, the order of report parameters (as they appear in the **Report Parameters Properties** dialog box) is important.</span></span> <span data-ttu-id="60e17-108">一覧で後方にあるレポート パラメーターは、一覧で前方にあるレポート パラメーターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="60e17-108">Report parameters later in the list can refer to report parameters earlier in the list.</span></span> <span data-ttu-id="60e17-109">レポート パラメーターの詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60e17-109">For more information about report parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="60e17-110">オプション</span><span class="sxs-lookup"><span data-stu-id="60e17-110">Options</span></span>  
 <span data-ttu-id="60e17-111">**追加**</span><span class="sxs-lookup"><span data-stu-id="60e17-111">**Add**</span></span>  
 <span data-ttu-id="60e17-112">一覧に新しいパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="60e17-112">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="60e17-113">**削除**</span><span class="sxs-lookup"><span data-stu-id="60e17-113">**Delete**</span></span>  
 <span data-ttu-id="60e17-114">選択したパラメーターを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="60e17-114">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="60e17-115">**パラメーター名**</span><span class="sxs-lookup"><span data-stu-id="60e17-115">**Parameter name**</span></span>  
 <span data-ttu-id="60e17-116">**[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** タブでデータセットに追加したクエリ パラメーターの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="60e17-116">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="60e17-117">**パラメーター値**</span><span class="sxs-lookup"><span data-stu-id="60e17-117">**Parameter value**</span></span>  
 <span data-ttu-id="60e17-118">クエリ パラメーターの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="60e17-118">Enter a value for the query parameter.</span></span> <span data-ttu-id="60e17-119">この値には、静的な値、またはレポート内のオブジェクトを参照するがレポート アイテムやフィールドは参照できない式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="60e17-119">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="60e17-120">既定では、 **[値]** に、レポート パラメーターを参照する式が設定されています。</span><span class="sxs-lookup"><span data-stu-id="60e17-120">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="60e17-121">**上矢印**</span><span class="sxs-lookup"><span data-stu-id="60e17-121">**Up arrow**</span></span>  
 <span data-ttu-id="60e17-122">選択したパラメーターを一覧内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="60e17-122">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="60e17-123">**下矢印**</span><span class="sxs-lookup"><span data-stu-id="60e17-123">**Down arrow**</span></span>  
 <span data-ttu-id="60e17-124">選択したパラメーターを一覧内で下に移動します。</span><span class="sxs-lookup"><span data-stu-id="60e17-124">Move the selected parameter down in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e17-125">参照</span><span class="sxs-lookup"><span data-stu-id="60e17-125">See Also</span></span>  
 <span data-ttu-id="60e17-126">[レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="60e17-126">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="60e17-127">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60e17-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="60e17-128">レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="60e17-128">Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
