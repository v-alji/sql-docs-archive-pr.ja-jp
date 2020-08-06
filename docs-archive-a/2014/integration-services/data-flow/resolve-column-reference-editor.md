---
title: 列参照解決エディター | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 600b6f4d5ec12290d654f0854cc548a5bbcf4335
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641780"
---
# <a name="resolve-column-reference-editor"></a><span data-ttu-id="22344-102">列参照解決エディター</span><span class="sxs-lookup"><span data-stu-id="22344-102">Resolve Column Reference Editor</span></span>
  <span data-ttu-id="22344-103">入力パスが接続されていない場合、またはパスにマップ解除された列が存在する場合、対応するデータ パスの横にエラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22344-103">When an input path is disconnected or if there are any unmapped columns in the path, an error icon is displayed beside the corresponding data path.</span></span> <span data-ttu-id="22344-104">列参照エラーの解決を簡素化するために、新しい参照の解決エディターを使用して、マップ解除された出力列を、実行ツリーのすべてのパスのマップ解除された入力列とリンクできます。</span><span class="sxs-lookup"><span data-stu-id="22344-104">To simplify the resolution of column reference errors, the new Resolve References editor allows you to link unmapped output columns with unmapped input columns for all paths in the execution tree.</span></span> <span data-ttu-id="22344-105">また、参照の解決エディターでは、解決されているパスを示すためにパスが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="22344-105">The Resolve References editor will also highlight the paths to indicate which paths are being resolved.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22344-106">これで、入力パスが接続されていない場合でもコンポーネントを編集できます。</span><span class="sxs-lookup"><span data-stu-id="22344-106">It is now possible to edit a component even when its input path is disconnected</span></span>  
  
 <span data-ttu-id="22344-107">すべての列参照が解決された後、他のデータ パス エラーが存在しなければ、データ パスの横にエラー アイコンが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="22344-107">After all column references have been resolved, if there are no other data path errors, no error icons will be displayed beside the data paths.</span></span>  
  
## <a name="options"></a><span data-ttu-id="22344-108">オプション</span><span class="sxs-lookup"><span data-stu-id="22344-108">Options</span></span>  
 <span data-ttu-id="22344-109">[マップ解除された出力列 (変換元)]:</span><span class="sxs-lookup"><span data-stu-id="22344-109">Unmapped Output Columns (Source):</span></span>  
 <span data-ttu-id="22344-110">現在マップされていない上流パスの列。</span><span class="sxs-lookup"><span data-stu-id="22344-110">Columns from the upstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="22344-111">[マップされた列 (変換元)]:</span><span class="sxs-lookup"><span data-stu-id="22344-111">Mapped Columns (Source):</span></span>  
 <span data-ttu-id="22344-112">下流パスから列にマップされた上流パスの列。</span><span class="sxs-lookup"><span data-stu-id="22344-112">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="22344-113">[マップされた列 (変換先)]:</span><span class="sxs-lookup"><span data-stu-id="22344-113">Mapped Columns (Destination):</span></span>  
 <span data-ttu-id="22344-114">下流パスから列にマップされた上流パスの列。</span><span class="sxs-lookup"><span data-stu-id="22344-114">Columns from the upstream path that are mapped to columns from the downstream path</span></span>  
  
 <span data-ttu-id="22344-115">[マップ解除された列 (変換先)]:</span><span class="sxs-lookup"><span data-stu-id="22344-115">Unmapped Input Columns (Destination):</span></span>  
 <span data-ttu-id="22344-116">現在マップされていない下流パスの列。</span><span class="sxs-lookup"><span data-stu-id="22344-116">Columns from the downstream path that are not currently mapped</span></span>  
  
 <span data-ttu-id="22344-117">[マップ解除された入力列の削除]</span><span class="sxs-lookup"><span data-stu-id="22344-117">Delete Unmapped Input Columns</span></span>  
 <span data-ttu-id="22344-118">[マップ解除された入力列の削除] をオンにすると、データ パスの変換先でマップ解除された列が無視されます。</span><span class="sxs-lookup"><span data-stu-id="22344-118">Check Delete Unmapped Input Columns to ignore unmapped columns at the destination of the data path.</span></span> <span data-ttu-id="22344-119">\[変更のプレビュー] ボタンには、[OK] ボタンを押したときに行われる変更の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="22344-119">The Preview Changes button displays a list of the changes that will occur when you press the OK button.</span></span>  
  
  
