---
title: SetStartMode メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a9b7310623f526d7b106485ed9681df3aa100129
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631709"
---
# <a name="setstartmode-method-sqlservice-class"></a><span data-ttu-id="47244-102">SetStartMode メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="47244-102">SetStartMode Method (SqlService Class)</span></span>
  <span data-ttu-id="47244-103">サービス インスタンスの開始モードを変更します。</span><span class="sxs-lookup"><span data-stu-id="47244-103">Modifies the start mode of the service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47244-104">構文</span><span class="sxs-lookup"><span data-stu-id="47244-104">Syntax</span></span>  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="47244-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="47244-105">Parts</span></span>  
 <span data-ttu-id="47244-106">*object*</span><span class="sxs-lookup"><span data-stu-id="47244-106">*object*</span></span>  
 <span data-ttu-id="47244-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="47244-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="47244-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47244-108">Parameters</span></span>  
 <span data-ttu-id="47244-109">*StartMode*</span><span class="sxs-lookup"><span data-stu-id="47244-109">*StartMode*</span></span>  
 <span data-ttu-id="47244-110">サービス インスタンスの開始モードを指定する `uint32` 値。</span><span class="sxs-lookup"><span data-stu-id="47244-110">A `uint32` value that specifies the start mode of the service instance.</span></span>  
  
 <span data-ttu-id="47244-111">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="47244-111">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="47244-112">値 = 0。</span><span class="sxs-lookup"><span data-stu-id="47244-112">Value = 0.</span></span> <span data-ttu-id="47244-113">(Boot)。デバイス ドライバーがオペレーティング システム ローダーによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="47244-113">Boot - Device driver started by the operating system loader.</span></span> <span data-ttu-id="47244-114">この値は、ドライバー サービスに対してのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="47244-114">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="47244-115">値 = 1。</span><span class="sxs-lookup"><span data-stu-id="47244-115">Value = 1.</span></span> <span data-ttu-id="47244-116">(System)。デバイス ドライバーが `IoInitSystem` メソッドによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="47244-116">System - Device driver started by the `IoInitSystem` method.</span></span> <span data-ttu-id="47244-117">この値は、ドライバー サービスに対してのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="47244-117">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="47244-118">値 = 2。</span><span class="sxs-lookup"><span data-stu-id="47244-118">Value = 2.</span></span> <span data-ttu-id="47244-119">(Automatic)。システムの起動時に、サービス コントロール マネージャーによってサービスが自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="47244-119">Automatic - Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="47244-120">値 = 3。</span><span class="sxs-lookup"><span data-stu-id="47244-120">Value = 3.</span></span> <span data-ttu-id="47244-121">(Manual)。プロセスが `StartService` メソッドを呼び出したとき、コンピューター マネージャーによってサービスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="47244-121">Manual - Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="47244-122">値 = 4。</span><span class="sxs-lookup"><span data-stu-id="47244-122">Value = 4.</span></span> <span data-ttu-id="47244-123">(Disabled)。サービスを開始できません。</span><span class="sxs-lookup"><span data-stu-id="47244-123">Disabled - Service can no longer be started.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="47244-124">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="47244-124">Property Value/Return Value</span></span>  
 <span data-ttu-id="47244-125">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。</span><span class="sxs-lookup"><span data-stu-id="47244-125">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="47244-126">それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="47244-126">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47244-127">解説</span><span class="sxs-lookup"><span data-stu-id="47244-127">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47244-128">参照</span><span class="sxs-lookup"><span data-stu-id="47244-128">See Also</span></span>  
 <span data-ttu-id="47244-129">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="47244-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
