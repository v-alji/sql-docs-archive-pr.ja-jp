---
title: OLE DB 変換先エディター ([エラー出力] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.errorhandling.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: 3c01f480-16c9-49eb-b40c-13cbc90b019d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25bf9e3c293879022cffdcf2731bc2cc9e20d7d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633216"
---
# <a name="ole-db-destination-editor-error-output-page"></a><span data-ttu-id="a0297-102">[OLE DB 変換先エディター] ([エラー出力] ページ)</span><span class="sxs-lookup"><span data-stu-id="a0297-102">OLE DB Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="a0297-103">**[OLE DB 変換先エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a0297-103">Use the **Error Output** page of the **OLE DB Destination Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="a0297-104">OLE DB 変換先の詳細については、「 [OLE DB Destination](data-flow/ole-db-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0297-104">To learn more about the OLE DB destination, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a0297-105">Options</span><span class="sxs-lookup"><span data-stu-id="a0297-105">Options</span></span>  
 <span data-ttu-id="a0297-106">**[入力または出力]**</span><span class="sxs-lookup"><span data-stu-id="a0297-106">**Input/Output**</span></span>  
 <span data-ttu-id="a0297-107">入力の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="a0297-107">View the name of the input.</span></span>  
  
 <span data-ttu-id="a0297-108">**列**</span><span class="sxs-lookup"><span data-stu-id="a0297-108">**Column**</span></span>  
 <span data-ttu-id="a0297-109">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="a0297-109">Not used.</span></span>  
  
 <span data-ttu-id="a0297-110">**Error**</span><span class="sxs-lookup"><span data-stu-id="a0297-110">**Error**</span></span>  
 <span data-ttu-id="a0297-111">エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0297-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a0297-112">**関連トピック:** [データのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="a0297-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="a0297-113">**切り捨て**</span><span class="sxs-lookup"><span data-stu-id="a0297-113">**Truncation**</span></span>  
 <span data-ttu-id="a0297-114">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="a0297-114">Not used.</span></span>  
  
 <span data-ttu-id="a0297-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="a0297-115">**Description**</span></span>  
 <span data-ttu-id="a0297-116">操作の説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="a0297-116">View the description of the operation.</span></span>  
  
 <span data-ttu-id="a0297-117">**[選択したセルに設定する値]**</span><span class="sxs-lookup"><span data-stu-id="a0297-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="a0297-118">エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0297-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="a0297-119">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="a0297-119">**Apply**</span></span>  
 <span data-ttu-id="a0297-120">選択したセルにエラー処理オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="a0297-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0297-121">参照</span><span class="sxs-lookup"><span data-stu-id="a0297-121">See Also</span></span>  
 <span data-ttu-id="a0297-122">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a0297-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a0297-123">[OLE DB 変換先エディター &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/ole-db-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="a0297-123">[OLE DB Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="a0297-124">[OLE DB 変換先エディター &#40;マッピング] ページ&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="a0297-124">[OLE DB Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="a0297-125">OLE DB 変換先を使用してデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="a0297-125">Load Data by Using the OLE DB Destination</span></span>](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
