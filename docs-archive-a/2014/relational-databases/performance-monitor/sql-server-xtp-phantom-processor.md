---
title: XTP ファントムプロセッサ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14158b7097427b6704cf5e747fa998a11217ecd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714249"
---
# <a name="xtp-phantom-processor"></a><span data-ttu-id="0de26-102">XTP Phantom Processor</span><span class="sxs-lookup"><span data-stu-id="0de26-102">XTP Phantom Processor</span></span>
  <span data-ttu-id="0de26-103">XTP Phantom Processor パフォーマンス オブジェクトには、XTP エンジンのファントム処理サブシステムに関連するカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0de26-103">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="0de26-104">このコンポーネントには、SERIALIZABLE 分離レベルで実行されているトランザクション内のファントム行を検出する役割があります。</span><span class="sxs-lookup"><span data-stu-id="0de26-104">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>  
  
 <span data-ttu-id="0de26-105">次の表では、 **XTP ファントムプロセッサ**カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0de26-105">This table describes the **XTP Phantom Processor** counters.</span></span>  
  
|<span data-ttu-id="0de26-106">カウンター</span><span class="sxs-lookup"><span data-stu-id="0de26-106">Counter</span></span>|<span data-ttu-id="0de26-107">説明</span><span class="sxs-lookup"><span data-stu-id="0de26-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0de26-108">**Dusty corner scan retries/sec (Phantom-issued)**</span><span class="sxs-lookup"><span data-stu-id="0de26-108">**Dusty corner scan retries/sec (Phantom-issued)**</span></span>|<span data-ttu-id="0de26-109">ファントム プロセッサによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="0de26-109">The number of scan retries due to write conflicts during dusty corner sweeps issued by the phantom processor (on average), per second.</span></span> <span data-ttu-id="0de26-110">これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。</span><span class="sxs-lookup"><span data-stu-id="0de26-110">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="0de26-111">**Phantom expired rows removed/sec**</span><span class="sxs-lookup"><span data-stu-id="0de26-111">**Phantom expired rows removed/sec**</span></span>|<span data-ttu-id="0de26-112">ファントム スキャンによって削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="0de26-112">The number of expired rows removed by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="0de26-113">**Phantom expired rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="0de26-113">**Phantom expired rows touched/sec**</span></span>|<span data-ttu-id="0de26-114">ファントム スキャンによって操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="0de26-114">The number of expired rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="0de26-115">**Phantom expiring rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="0de26-115">**Phantom expiring rows touched/sec**</span></span>|<span data-ttu-id="0de26-116">ファントム スキャンによって操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="0de26-116">The number of expiring rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="0de26-117">**Phantom rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="0de26-117">**Phantom rows touched/sec**</span></span>|<span data-ttu-id="0de26-118">ファントム スキャンによって操作された行の数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="0de26-118">The number of rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="0de26-119">**Phantom scans started/sec**</span><span class="sxs-lookup"><span data-stu-id="0de26-119">**Phantom scans started/sec**</span></span>|<span data-ttu-id="0de26-120">ファントム スキャンが開始された回数に関する 1 秒あたりの平均です。</span><span class="sxs-lookup"><span data-stu-id="0de26-120">The number of phantom scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0de26-121">参照</span><span class="sxs-lookup"><span data-stu-id="0de26-121">See Also</span></span>  
 [<span data-ttu-id="0de26-122">XTP &#40;インメモリ OLTP&#41; パフォーマンスカウンター</span><span class="sxs-lookup"><span data-stu-id="0de26-122">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
