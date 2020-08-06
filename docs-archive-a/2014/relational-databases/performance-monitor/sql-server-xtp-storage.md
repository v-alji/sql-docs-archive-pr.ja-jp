---
title: XTP ストレージ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: efd4a9eba36060d3d4bab9b371678ab2b2c409ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641635"
---
# <a name="xtp-storage"></a><span data-ttu-id="3dd4b-102">XTP ストレージ</span><span class="sxs-lookup"><span data-stu-id="3dd4b-102">XTP Storage</span></span>
  <span data-ttu-id="3dd4b-103">XTP ストレージのパフォーマンス オブジェクトには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の XTP ストレージに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-103">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3dd4b-104">次の表では、 **XTP ストレージ**カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-104">This table describes the **XTP Storage** counters.</span></span>  
  
|<span data-ttu-id="3dd4b-105">カウンター</span><span class="sxs-lookup"><span data-stu-id="3dd4b-105">Counter</span></span>|<span data-ttu-id="3dd4b-106">説明</span><span class="sxs-lookup"><span data-stu-id="3dd4b-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3dd4b-107">**終了したチェックポイント**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-107">**Checkpoints Closed**</span></span>|<span data-ttu-id="3dd4b-108">オンライン エージェントによって終了されたチェックポイントの数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-108">Count of checkpoints closed done by online agent.</span></span>|  
|<span data-ttu-id="3dd4b-109">**完了したチェックポイント**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-109">**Checkpoints Completed**</span></span>|<span data-ttu-id="3dd4b-110">オフライン チェックポイント スレッドによって処理されたチェックポイントの数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-110">Count of checkpoints processed by offline checkpoint thread.</span></span>|  
|<span data-ttu-id="3dd4b-111">**完了したコア マージ**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-111">**Core Merges Completed**</span></span>|<span data-ttu-id="3dd4b-112">マージ ワーカー スレッドによって実行されたコア マージの数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-112">The number of core merges completed by the merge worker thread.</span></span> <span data-ttu-id="3dd4b-113">これらのマージは、引き続きインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-113">These merges still need to be installed.</span></span>|  
|<span data-ttu-id="3dd4b-114">**マージ ポリシーの評価**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-114">**Merge Policy Evaluations**</span></span>|<span data-ttu-id="3dd4b-115">サーバーが開始してから行われたマージ ポリシーの評価の数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-115">The number of merge policy evaluations since the server started.</span></span>|  
|<span data-ttu-id="3dd4b-116">**未処理のマージ要求**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-116">**Merge Requests Outstanding**</span></span>|<span data-ttu-id="3dd4b-117">サーバーが開始してから未処理になっているのマージ要求の数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-117">The number of merge requests outstanding since the server started.</span></span>|  
|<span data-ttu-id="3dd4b-118">**放棄されたマージ**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-118">**Merges Abandoned**</span></span>|<span data-ttu-id="3dd4b-119">エラーにより放棄されたマージの数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-119">The number of merges abandoned due to failure.</span></span>|  
|<span data-ttu-id="3dd4b-120">**インストールされているマージ**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-120">**Merges Installed**</span></span>|<span data-ttu-id="3dd4b-121">適切にインストールされたマージの数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-121">The number of merges successfully installed.</span></span>|  
|<span data-ttu-id="3dd4b-122">**マージされているファイルの総数**</span><span class="sxs-lookup"><span data-stu-id="3dd4b-122">**Total Files Merged**</span></span>|<span data-ttu-id="3dd4b-123">マージされているソース ファイルの総数。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-123">The total number of source files merged.</span></span> <span data-ttu-id="3dd4b-124">この数を使用すると、マージ内のソース ファイル数の平均がわかります。</span><span class="sxs-lookup"><span data-stu-id="3dd4b-124">This count can be used to find the average number of source files in the merge.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3dd4b-125">参照</span><span class="sxs-lookup"><span data-stu-id="3dd4b-125">See Also</span></span>  
 [<span data-ttu-id="3dd4b-126">XTP &#40;インメモリ OLTP&#41; パフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="3dd4b-126">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
