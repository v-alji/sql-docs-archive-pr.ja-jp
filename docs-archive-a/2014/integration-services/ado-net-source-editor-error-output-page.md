---
title: '[ADO NET 変換元エディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ee480caa8764d70b52b25a416f200f353d30c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740255"
---
# <a name="ado-net-source-editor-error-output-page"></a><span data-ttu-id="4d298-102">[ADO NET 変換元エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="4d298-102">ADO NET Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="4d298-103">**[ADO NET 変換元エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="4d298-103">Use the **Error Output** page of the **ADO NET Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="4d298-104">ADO NET 変換元の詳細については、「 [ADO NET Source](data-flow/ado-net-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d298-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="4d298-105">**[エラー出力] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="4d298-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="4d298-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d298-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="4d298-107">**[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d298-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="4d298-108">**[ADO NET 変換元エディター]** で、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d298-108">In the **ADO NET Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4d298-109">Options</span><span class="sxs-lookup"><span data-stu-id="4d298-109">Options</span></span>  
 <span data-ttu-id="4d298-110">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="4d298-110">**Input/Output**</span></span>  
 <span data-ttu-id="4d298-111">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d298-111">View the name of the data source.</span></span>  
  
 <span data-ttu-id="4d298-112">**列**</span><span class="sxs-lookup"><span data-stu-id="4d298-112">**Column**</span></span>  
 <span data-ttu-id="4d298-113">**[ADO NET 変換元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択した外部 (変換元) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d298-113">View the external (source) columns that you selected on the **Connection Manager** page of the **ADO NET Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="4d298-114">**Error**</span><span class="sxs-lookup"><span data-stu-id="4d298-114">**Error**</span></span>  
 <span data-ttu-id="4d298-115">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d298-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="4d298-116">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="4d298-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="4d298-117">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="4d298-117">**Truncation**</span></span>  
 <span data-ttu-id="4d298-118">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d298-118">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="4d298-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="4d298-119">**Description**</span></span>  
 <span data-ttu-id="4d298-120">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d298-120">View the description of the error.</span></span>  
  
 <span data-ttu-id="4d298-121">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="4d298-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="4d298-122">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4d298-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="4d298-123">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="4d298-123">**Apply**</span></span>  
 <span data-ttu-id="4d298-124">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="4d298-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d298-125">参照</span><span class="sxs-lookup"><span data-stu-id="4d298-125">See Also</span></span>  
 <span data-ttu-id="4d298-126">[[ADO NET 変換元エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="4d298-126">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="4d298-127">[[ADO NET 変換元エディター] &#40;[列] ページ&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="4d298-127">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="4d298-128">ADO.NET 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="4d298-128">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
