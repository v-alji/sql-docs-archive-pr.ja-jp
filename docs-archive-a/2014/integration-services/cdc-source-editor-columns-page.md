---
title: '[CDC ソースエディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa30defb5e6873ea05e8e41c733477cf50d0dc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644591"
---
# <a name="cdc-source-editor-columns-page"></a><span data-ttu-id="98518-102">[CDC ソース エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="98518-102">CDC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="98518-103">**[CDC ソース エディター]** ダイアログ ボックスの **[列]** ページを使用すると、出力列をそれぞれの外部 (ソース) 列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="98518-103">Use the **Columns** page of the **CDC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="98518-104">CDC ソースの詳細については、「 [CDC Source](data-flow/cdc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98518-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="98518-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="98518-105">Task List</span></span>  
 <span data-ttu-id="98518-106">**[CDC ソース エディター] の [列] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="98518-106">**To open the CDC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="98518-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、CDC ソースを含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="98518-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="98518-108">**[データ フロー]** タブで、CDC ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="98518-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="98518-109">**[CDC ソース エディター]** で、 **[列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98518-109">In the **CDC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98518-110">オプション</span><span class="sxs-lookup"><span data-stu-id="98518-110">Options</span></span>  
 <span data-ttu-id="98518-111">**使用できる外部列**</span><span class="sxs-lookup"><span data-stu-id="98518-111">**Available External Columns**</span></span>  
 <span data-ttu-id="98518-112">データ ソース内の使用できる外部列の一覧です。</span><span class="sxs-lookup"><span data-stu-id="98518-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="98518-113">このテーブルを使用して列を追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="98518-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="98518-114">ソースで使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="98518-114">Select the columns to use in the source.</span></span> <span data-ttu-id="98518-115">選択した列は、選択した順序で **[外部列]** の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="98518-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="98518-116">**[外部列]**</span><span class="sxs-lookup"><span data-stu-id="98518-116">**External Column**</span></span>  
 <span data-ttu-id="98518-117">外部 (ソース) 列のビューです。CDC ソースのデータを使用するコンポーネントを構成するときの表示順になります。</span><span class="sxs-lookup"><span data-stu-id="98518-117">A view of the external (source) columns in the order that you see them when configuring components that consume data from the CDC source.</span></span> <span data-ttu-id="98518-118">この順序を変更するには、まず **[使用できる外部列]** の一覧で選択した列を消去してから、別の順序で一覧から外部列を選択します。</span><span class="sxs-lookup"><span data-stu-id="98518-118">To change this order, first clear the selected columns in the **Available External Columns** list, and then select external columns from the list in a different order.</span></span> <span data-ttu-id="98518-119">選択した列は、選択した順序で **[外部列]** の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="98518-119">The selected columns are added to the **External Column** list in the order you select them.</span></span>  
  
 <span data-ttu-id="98518-120">**出力列**</span><span class="sxs-lookup"><span data-stu-id="98518-120">**Output Column**</span></span>  
 <span data-ttu-id="98518-121">各出力列の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="98518-121">Enter a unique name for each output column.</span></span> <span data-ttu-id="98518-122">既定では選択された外部 (ソース) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="98518-122">The default is the name of the selected external (source) column, however you can choose any unique, descriptive name.</span></span> <span data-ttu-id="98518-123">入力した名前は、SSIS デザイナーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="98518-123">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98518-124">参照</span><span class="sxs-lookup"><span data-stu-id="98518-124">See Also</span></span>  
 <span data-ttu-id="98518-125">[CDC ソース エディター &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="98518-125">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="98518-126">[CDC ソース エディター &#40;[エラー出力] ページ&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="98518-126">[CDC Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)</span></span>  
  
  
