---
title: '[ODBC ソースエディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a11ab6a86978366d07fbe63362f1702310b5d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718573"
---
# <a name="odbc-source-editor-columns-page"></a><span data-ttu-id="7bd5f-102">[ODBC ソース エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="7bd5f-102">ODBC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="7bd5f-103">**[ODBC ソース エディター]** ダイアログ ボックスの **[列]** ページを使用すると、出力列をそれぞれの外部 (入力元) 列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-103">Use the **Columns** page of the **ODBC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="7bd5f-104">ODBC 入力元の詳細については、「 [ODBC Source](data-flow/odbc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-104">To learn more about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="7bd5f-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="7bd5f-105">Task List</span></span>  
 <span data-ttu-id="7bd5f-106">**[ODBC 入力元エディター] の [列] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="7bd5f-106">**To open the ODBC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="7bd5f-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
2.  <span data-ttu-id="7bd5f-108">**[データ フロー]** タブで、ODBC 入力元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-108">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
3.  <span data-ttu-id="7bd5f-109">**[ODBC 入力元エディター]** で、 **[列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-109">In the **ODBC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7bd5f-110">オプション</span><span class="sxs-lookup"><span data-stu-id="7bd5f-110">Options</span></span>  
  
### <a name="available-external-columns"></a><span data-ttu-id="7bd5f-111">使用できる外部列</span><span class="sxs-lookup"><span data-stu-id="7bd5f-111">Available External Columns</span></span>  
 <span data-ttu-id="7bd5f-112">データ ソース内の使用できる外部列の一覧です。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="7bd5f-113">このテーブルを使用して列を追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="7bd5f-114">入力元から使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-114">Select the columns to use from the source.</span></span> <span data-ttu-id="7bd5f-115">選択した列は、選択した順序で **[外部列]** の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="7bd5f-116">**[すべて選択]** チェック ボックスをオンにすると、すべての列が選択されます。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-116">Select the **Select All** check box to select all of the columns.</span></span>  
  
### <a name="external-column"></a><span data-ttu-id="7bd5f-117">外部列</span><span class="sxs-lookup"><span data-stu-id="7bd5f-117">External Column</span></span>  
 <span data-ttu-id="7bd5f-118">外部 (入力元) 列のビューです。ODBC 入力元のデータを使用するコンポーネントを構成するときの表示順になります。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-118">A view of the external (source) columns in the order that you see them when configuring components that consume data from the ODBC source.</span></span>  
  
### <a name="output-column"></a><span data-ttu-id="7bd5f-119">出力列</span><span class="sxs-lookup"><span data-stu-id="7bd5f-119">Output Column</span></span>  
 <span data-ttu-id="7bd5f-120">各出力列の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-120">Enter a unique name for each output column.</span></span> <span data-ttu-id="7bd5f-121">既定では選択された外部 (変換元) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-121">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="7bd5f-122">入力した名前は、SSIS デザイナーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="7bd5f-122">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd5f-123">参照</span><span class="sxs-lookup"><span data-stu-id="7bd5f-123">See Also</span></span>  
 <span data-ttu-id="7bd5f-124">[ODBC ソースエディター &#40;接続マネージャーのページ&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="7bd5f-124">[ODBC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="7bd5f-125">[[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="7bd5f-125">[ODBC Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)</span></span>  
  
  
