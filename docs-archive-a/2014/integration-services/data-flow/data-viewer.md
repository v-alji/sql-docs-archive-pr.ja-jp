---
title: '[データ ビューアー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dc576981e875eade84dd3576f4ed93b66784411f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641784"
---
# <a name="data-viewer"></a><span data-ttu-id="9b7ac-102">[データ ビューアー]</span><span class="sxs-lookup"><span data-stu-id="9b7ac-102">Data Viewer</span></span>
  <span data-ttu-id="9b7ac-103">パスがデータ ビューアーを使用するように構成されている場合、データ ビューアーはデータが 2 つのデータ フロー コンポーネントを移動するときに、バッファーによるデータ バッファーを表示します。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-103">If a path is configured to use a data viewer, the Data Viewer displays the data buffer by buffer as data moves between two data flow components.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9b7ac-104">オプション</span><span class="sxs-lookup"><span data-stu-id="9b7ac-104">Options</span></span>  
 <span data-ttu-id="9b7ac-105">**緑色の矢印**</span><span class="sxs-lookup"><span data-stu-id="9b7ac-105">**Green arrow**</span></span>  
 <span data-ttu-id="9b7ac-106">クリックすると、次のバッファーのデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-106">Click to display the data in the next buffer.</span></span> <span data-ttu-id="9b7ac-107">データが 1 つのバッファーに移動される場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-107">If the data can be moved in a single buffer, this option is not available.</span></span>  
  
 <span data-ttu-id="9b7ac-108">**[デタッチ]**</span><span class="sxs-lookup"><span data-stu-id="9b7ac-108">**Detach**</span></span>  
 <span data-ttu-id="9b7ac-109">データ ビューアーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-109">Detach the data viewer.</span></span>  
  
 <span data-ttu-id="9b7ac-110">**注** &#xA0;&#xA0;&#xA0;データ ビューアーをデタッチしてもデータ ビューアーは削除されません。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-110">**Note** Detaching a data viewer does not delete the data viewer.</span></span> <span data-ttu-id="9b7ac-111">データ ビューアーがデタッチされた場合、データはパスを流れますが、ビューアー内のデータを各バッファーのデータに一致させる更新は行われません。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-111">If the data viewer has been detached, data continues to flow through the path, but the data in the viewer is not updated to match the data in each buffer.</span></span>  
  
 <span data-ttu-id="9b7ac-112">**[アタッチ]**</span><span class="sxs-lookup"><span data-stu-id="9b7ac-112">**Attach**</span></span>  
 <span data-ttu-id="9b7ac-113">データ ビューアーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-113">Attach a data viewer.</span></span>  
  
 <span data-ttu-id="9b7ac-114">**注** &#xA0;&#xA0;&#xA0;アタッチされたデータ ビューアーは、データ フロー内の各バッファーからの情報を表示してから、一時停止します。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-114">**Note** When the data viewer is attached, it displays information from each buffer in the data flow and then pauses.</span></span> <span data-ttu-id="9b7ac-115">緑色の矢印を使用して次のバッファーに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-115">You can advance through the buffers by using the green arrow.</span></span>  
  
 <span data-ttu-id="9b7ac-116">**[データのコピー]**</span><span class="sxs-lookup"><span data-stu-id="9b7ac-116">**Copy Data**</span></span>  
 <span data-ttu-id="9b7ac-117">現在のバッファーのデータをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9b7ac-117">Copy data in the current buffer to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7ac-118">参照</span><span class="sxs-lookup"><span data-stu-id="9b7ac-118">See Also</span></span>  
 [<span data-ttu-id="9b7ac-119">データ フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9b7ac-119">Debugging Data Flow</span></span>](../troubleshooting/debugging-data-flow.md)  
  
  
