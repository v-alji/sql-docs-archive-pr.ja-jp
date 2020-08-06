---
title: '[フラットファイル接続マネージャーエディター] ([プレビュー] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.preview.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: de47ea98-135e-4730-900e-dac629848798
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0f71b347bc943216a4b309cc58202ed8ab9183e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632614"
---
# <a name="flat-file-connection-manager-editor-preview-page"></a><span data-ttu-id="cbf1c-102">[フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)</span><span class="sxs-lookup"><span data-stu-id="cbf1c-102">Flat File Connection Manager Editor (Preview Page)</span></span>
  <span data-ttu-id="cbf1c-103">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[プレビュー]** ノードを使用すると、ソース ファイルの内容を表形式で表示できます。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-103">Use the **Preview** node of the **Flat File Connection Manager Editor** dialog box to view the contents of the source file in a tabular format.</span></span>  
  
 <span data-ttu-id="cbf1c-104">フラット ファイル接続マネージャーの詳細については、「 [Flat File Connection Manager](connection-manager/file-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cbf1c-105">Options</span><span class="sxs-lookup"><span data-stu-id="cbf1c-105">Options</span></span>  
 <span data-ttu-id="cbf1c-106">**接続マネージャー名**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-106">**Connection manager name**</span></span>  
 <span data-ttu-id="cbf1c-107">ワークフローにおけるフラット ファイル接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="cbf1c-108">指定された名前は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="cbf1c-109">**説明**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-109">**Description**</span></span>  
 <span data-ttu-id="cbf1c-110">接続の説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-110">Describe the connection.</span></span> <span data-ttu-id="cbf1c-111">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続の目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="cbf1c-112">**[スキップするデータ行数]**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-112">**Data rows to skip**</span></span>  
 <span data-ttu-id="cbf1c-113">フラット ファイルの冒頭でスキップする行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-113">Specify how many rows to skip at the beginning of the flat file.</span></span>  
  
 <span data-ttu-id="cbf1c-114">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-114">**Refresh**</span></span>  
 <span data-ttu-id="cbf1c-115">**[最新の情報に更新]** をクリックすると、スキップする行数を変更した結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-115">View the effect of changing the number of rows to skip by clicking **Refresh**.</span></span> <span data-ttu-id="cbf1c-116">このボタンは、他の接続オプションを変更した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-116">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="cbf1c-117">**[プレビュー]**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-117">**Preview rows**</span></span>  
 <span data-ttu-id="cbf1c-118">フラット ファイル内のサンプル データを、選択したオプションに基づいて列と行に分割して表示します。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-118">View sample data in the flat file, divided into columns and rows according to the options you have selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf1c-119">参照</span><span class="sxs-lookup"><span data-stu-id="cbf1c-119">See Also</span></span>  
 <span data-ttu-id="cbf1c-120">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cbf1c-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cbf1c-121">[[フラットファイル接続マネージャーエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="cbf1c-121">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="cbf1c-122">[[フラットファイル接続マネージャーエディター &#40;列] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="cbf1c-122">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span></span>  
 <span data-ttu-id="cbf1c-123">[[フラット ファイル接続マネージャー エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="cbf1c-123">[Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
  
