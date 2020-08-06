---
title: State プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7456113d9ec4444507d1057892a65adf241992f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717601"
---
# <a name="state-property-sqlservice-class"></a><span data-ttu-id="1b548-102">State プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="1b548-102">State Property (SqlService Class)</span></span>
  <span data-ttu-id="1b548-103">サービスの現在の状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="1b548-103">Gets or sets the current state of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b548-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b548-104">Syntax</span></span>  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="1b548-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1b548-105">Parts</span></span>  
 <span data-ttu-id="1b548-106">*object*</span><span class="sxs-lookup"><span data-stu-id="1b548-106">*object*</span></span>  
 <span data-ttu-id="1b548-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1b548-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1b548-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="1b548-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="1b548-109">サービスの状態を指定する uint32 値。</span><span class="sxs-lookup"><span data-stu-id="1b548-109">A uint32 value that specifies the state of the service.</span></span>  
  
 <span data-ttu-id="1b548-110">値には、次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b548-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="1b548-111">1</span><span class="sxs-lookup"><span data-stu-id="1b548-111">1</span></span>  
 <span data-ttu-id="1b548-112">停止中。</span><span class="sxs-lookup"><span data-stu-id="1b548-112">Stopped.</span></span> <span data-ttu-id="1b548-113">サービスが停止しています。</span><span class="sxs-lookup"><span data-stu-id="1b548-113">The service is stopped.</span></span>  
  
 <span data-ttu-id="1b548-114">2</span><span class="sxs-lookup"><span data-stu-id="1b548-114">2</span></span>  
 <span data-ttu-id="1b548-115">開始保留中。</span><span class="sxs-lookup"><span data-stu-id="1b548-115">Start Pending.</span></span> <span data-ttu-id="1b548-116">サービスは開始を待機しています。</span><span class="sxs-lookup"><span data-stu-id="1b548-116">The service is waiting to start.</span></span>  
  
 <span data-ttu-id="1b548-117">3</span><span class="sxs-lookup"><span data-stu-id="1b548-117">3</span></span>  
 <span data-ttu-id="1b548-118">停止保留中。</span><span class="sxs-lookup"><span data-stu-id="1b548-118">Stop Pending.</span></span> <span data-ttu-id="1b548-119">サービスは停止を待機しています。</span><span class="sxs-lookup"><span data-stu-id="1b548-119">The service is waiting to stop.</span></span>  
  
 <span data-ttu-id="1b548-120">4</span><span class="sxs-lookup"><span data-stu-id="1b548-120">4</span></span>  
 <span data-ttu-id="1b548-121">実行中。</span><span class="sxs-lookup"><span data-stu-id="1b548-121">Running.</span></span> <span data-ttu-id="1b548-122">サービスは実行中です。</span><span class="sxs-lookup"><span data-stu-id="1b548-122">The service is running.</span></span>  
  
 <span data-ttu-id="1b548-123">5</span><span class="sxs-lookup"><span data-stu-id="1b548-123">5</span></span>  
 <span data-ttu-id="1b548-124">継続保留中。</span><span class="sxs-lookup"><span data-stu-id="1b548-124">Continue Pending.</span></span> <span data-ttu-id="1b548-125">サービスは継続を待機しています。</span><span class="sxs-lookup"><span data-stu-id="1b548-125">The service is waiting to continue.</span></span>  
  
 <span data-ttu-id="1b548-126">6</span><span class="sxs-lookup"><span data-stu-id="1b548-126">6</span></span>  
 <span data-ttu-id="1b548-127">一時停止保留中。</span><span class="sxs-lookup"><span data-stu-id="1b548-127">Pause Pending.</span></span> <span data-ttu-id="1b548-128">サービスは一時停止を待機しています。</span><span class="sxs-lookup"><span data-stu-id="1b548-128">The service is waiting to pause.</span></span>  
  
 <span data-ttu-id="1b548-129">7</span><span class="sxs-lookup"><span data-stu-id="1b548-129">7</span></span>  
 <span data-ttu-id="1b548-130">一時停止。</span><span class="sxs-lookup"><span data-stu-id="1b548-130">Paused.</span></span> <span data-ttu-id="1b548-131">サービスは一時中断されています。</span><span class="sxs-lookup"><span data-stu-id="1b548-131">The service is paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b548-132">解説</span><span class="sxs-lookup"><span data-stu-id="1b548-132">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b548-133">参照</span><span class="sxs-lookup"><span data-stu-id="1b548-133">See Also</span></span>  
 <span data-ttu-id="1b548-134">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1b548-134">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
