---
title: StartMode プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bafffcc3c8f82f69896d0a22e9b0a9060e04cd10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717619"
---
# <a name="startmode-property-sqlservice-class"></a><span data-ttu-id="69b2b-102">StartMode プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="69b2b-102">StartMode Property (SqlService Class)</span></span>
  <span data-ttu-id="69b2b-103">サービスの開始モードを取得します。</span><span class="sxs-lookup"><span data-stu-id="69b2b-103">Gets the start mode of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b2b-104">構文</span><span class="sxs-lookup"><span data-stu-id="69b2b-104">Syntax</span></span>  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="69b2b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="69b2b-105">Parts</span></span>  
 <span data-ttu-id="69b2b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="69b2b-106">*object*</span></span>  
 <span data-ttu-id="69b2b-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="69b2b-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="69b2b-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="69b2b-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="69b2b-109">サービスのモードを指定する uint32 値。</span><span class="sxs-lookup"><span data-stu-id="69b2b-109">A uint32 value that specifies the mode of the service.</span></span>  
  
 <span data-ttu-id="69b2b-110">値には、次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="69b2b-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="69b2b-111">ブート</span><span class="sxs-lookup"><span data-stu-id="69b2b-111">Boot</span></span>  
 <span data-ttu-id="69b2b-112">値 = 0。</span><span class="sxs-lookup"><span data-stu-id="69b2b-112">Value = 0.</span></span> <span data-ttu-id="69b2b-113">オペレーティング システム ローダーによって開始されるサービスです。</span><span class="sxs-lookup"><span data-stu-id="69b2b-113">Service started by the operating system loader.</span></span> <span data-ttu-id="69b2b-114">このオプションは、ドライバー サービスにのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="69b2b-114">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="69b2b-115">システム</span><span class="sxs-lookup"><span data-stu-id="69b2b-115">System</span></span>  
 <span data-ttu-id="69b2b-116">値 = 1。</span><span class="sxs-lookup"><span data-stu-id="69b2b-116">Value = 1.</span></span> <span data-ttu-id="69b2b-117">`IoInitSystem` メソッドによって開始されるサービスです。</span><span class="sxs-lookup"><span data-stu-id="69b2b-117">Service started by the `IoInitSystem` method.</span></span> <span data-ttu-id="69b2b-118">このオプションは、ドライバー サービスにのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="69b2b-118">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="69b2b-119">自動</span><span class="sxs-lookup"><span data-stu-id="69b2b-119">Automatic</span></span>  
 <span data-ttu-id="69b2b-120">値 = 2。</span><span class="sxs-lookup"><span data-stu-id="69b2b-120">Value = 2.</span></span> <span data-ttu-id="69b2b-121">システムの起動時にサービス コントロール マネージャーによって自動的に開始されるサービスです。</span><span class="sxs-lookup"><span data-stu-id="69b2b-121">Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="69b2b-122">マニュアル</span><span class="sxs-lookup"><span data-stu-id="69b2b-122">Manual</span></span>  
 <span data-ttu-id="69b2b-123">値 = 3。</span><span class="sxs-lookup"><span data-stu-id="69b2b-123">Value = 3.</span></span> <span data-ttu-id="69b2b-124">プロセスが `StartService` メソッドを呼び出すとコンピューター マネージャーによって開始されるサービスです。</span><span class="sxs-lookup"><span data-stu-id="69b2b-124">Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="69b2b-125">無効</span><span class="sxs-lookup"><span data-stu-id="69b2b-125">Disabled</span></span>  
 <span data-ttu-id="69b2b-126">値 = 4。</span><span class="sxs-lookup"><span data-stu-id="69b2b-126">Value = 4.</span></span> <span data-ttu-id="69b2b-127">サービスを開始できません。</span><span class="sxs-lookup"><span data-stu-id="69b2b-127">Service cannot be started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69b2b-128">解説</span><span class="sxs-lookup"><span data-stu-id="69b2b-128">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b2b-129">参照</span><span class="sxs-lookup"><span data-stu-id="69b2b-129">See Also</span></span>  
 <span data-ttu-id="69b2b-130">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="69b2b-130">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
