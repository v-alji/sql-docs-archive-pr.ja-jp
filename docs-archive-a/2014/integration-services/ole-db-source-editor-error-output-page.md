---
title: '[OLE DB ソースエディター] ([エラー出力] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.errorhandling.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 7737c6ae-c16b-4856-aa6e-5882640093b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ded87747f041a4d8451048d4ef4671b029125873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644552"
---
# <a name="ole-db-source-editor-error-output-page"></a><span data-ttu-id="1c6a3-102">[OLE DB ソース エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="1c6a3-102">OLE DB Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="1c6a3-103">**[OLE DB ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-103">Use the **Error Output** page of the **OLE DB Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="1c6a3-104">OLE DB ソースの詳細については、「 [OLE DB Source](data-flow/ole-db-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c6a3-105">Options</span><span class="sxs-lookup"><span data-stu-id="1c6a3-105">Options</span></span>  
 <span data-ttu-id="1c6a3-106">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-106">**Input/Output**</span></span>  
 <span data-ttu-id="1c6a3-107">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="1c6a3-108">**列**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-108">**Column**</span></span>  
 <span data-ttu-id="1c6a3-109">**[OLE DB ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択されている外部 (ソース) 列を表示します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-109">View the external (source) columns that you selected on the **Connection Manager** page of the **OLE DB Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="1c6a3-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-110">**Error**</span></span>  
 <span data-ttu-id="1c6a3-111">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1c6a3-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="1c6a3-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="1c6a3-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-113">**Truncation**</span></span>  
 <span data-ttu-id="1c6a3-114">切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1c6a3-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-115">**Description**</span></span>  
 <span data-ttu-id="1c6a3-116">エラーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="1c6a3-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="1c6a3-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="1c6a3-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="1c6a3-119">**Apply**</span></span>  
 <span data-ttu-id="1c6a3-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="1c6a3-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6a3-121">参照</span><span class="sxs-lookup"><span data-stu-id="1c6a3-121">See Also</span></span>  
 <span data-ttu-id="1c6a3-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1c6a3-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="1c6a3-123">[OLE DB ソースエディター &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="1c6a3-123">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="1c6a3-124">[OLE DB ソースエディター &#40;列] ページ&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="1c6a3-124">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="1c6a3-125">[OLE DB ソースを使用してデータを抽出する](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="1c6a3-125">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="1c6a3-126">OLE DB 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="1c6a3-126">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
