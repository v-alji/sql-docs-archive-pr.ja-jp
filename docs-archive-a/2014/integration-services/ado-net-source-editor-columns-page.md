---
title: '[ADO NET 変換元エディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.columns.f1
ms.assetid: fbc205b9-2001-4737-a76b-1ba777344bd9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d89f8c926761b9149f19269bc2519c12bcf130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641197"
---
# <a name="ado-net-source-editor-columns-page"></a><span data-ttu-id="a5e5c-102">[ADO NET 変換元エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="a5e5c-102">ADO NET Source Editor (Columns Page)</span></span>
  <span data-ttu-id="a5e5c-103">**[ADO NET 変換元エディター]** ダイアログ ボックスの **[列]** ページを使用すると、出力列をそれぞれの外部 (変換元) 列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-103">Use the **Columns** page of the **ADO NET Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="a5e5c-104">ADO NET 変換元の詳細については、「 [ADO NET Source](data-flow/ado-net-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="a5e5c-105">**[列] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="a5e5c-105">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="a5e5c-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="a5e5c-107">**[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="a5e5c-108">**[ADO NET 変換元エディター]** で、 **[列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-108">In the **ADO NET Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a5e5c-109">Options</span><span class="sxs-lookup"><span data-stu-id="a5e5c-109">Options</span></span>  
 <span data-ttu-id="a5e5c-110">**使用できる外部列**</span><span class="sxs-lookup"><span data-stu-id="a5e5c-110">**Available External Columns**</span></span>  
 <span data-ttu-id="a5e5c-111">データ ソース内の使用できる外部列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-111">View the list of available external columns in the data source.</span></span> <span data-ttu-id="a5e5c-112">このテーブルを使用して列を追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-112">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="a5e5c-113">**[外部列]**</span><span class="sxs-lookup"><span data-stu-id="a5e5c-113">**External Column**</span></span>  
 <span data-ttu-id="a5e5c-114">ここで表示される外部 (変換元) 列の順序は、この変換元のデータを使用するコンポーネントを構成するときの列の表示順に反映されます。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-114">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span>  
  
 <span data-ttu-id="a5e5c-115">**出力列**</span><span class="sxs-lookup"><span data-stu-id="a5e5c-115">**Output Column**</span></span>  
 <span data-ttu-id="a5e5c-116">各出力列の一意な名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-116">Provide a unique name for each output column.</span></span> <span data-ttu-id="a5e5c-117">既定では選択された外部 (変換元) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-117">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="a5e5c-118">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5e5c-118">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e5c-119">参照</span><span class="sxs-lookup"><span data-stu-id="a5e5c-119">See Also</span></span>  
 <span data-ttu-id="a5e5c-120">[[ADO NET 変換元エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="a5e5c-120">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="a5e5c-121">[ADO NET 変換元エディター &#40;エラー出力ページ&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="a5e5c-121">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="a5e5c-122">ADO.NET 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="a5e5c-122">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
