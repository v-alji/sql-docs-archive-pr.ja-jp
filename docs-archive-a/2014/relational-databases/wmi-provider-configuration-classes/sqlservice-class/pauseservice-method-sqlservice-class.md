---
title: PauseService メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PauseService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PauseService method
ms.assetid: 5c3a8feb-58b8-4385-b4c8-bf33cf4d276d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8286e123bbbc279ba461336c5716eeb208c5b238
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640805"
---
# <a name="pauseservice-method-sqlservice-class"></a><span data-ttu-id="a7ef4-102">PauseService メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="a7ef4-102">PauseService Method (SqlService Class)</span></span>
  <span data-ttu-id="a7ef4-103">サービスを一時停止状態にする動作を試行します。</span><span class="sxs-lookup"><span data-stu-id="a7ef4-103">Attempts to place the service in the paused state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ef4-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7ef4-104">Syntax</span></span>  
  
```  
  
object  
.PauseService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a7ef4-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a7ef4-105">Parts</span></span>  
 <span data-ttu-id="a7ef4-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a7ef4-106">*object*</span></span>  
 <span data-ttu-id="a7ef4-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a7ef4-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a7ef4-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="a7ef4-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="a7ef4-109">uint32 値。サービスが正常に停止された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="a7ef4-109">A uint32 value, which is 0 if the service was successfully stopped, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ef4-110">解説</span><span class="sxs-lookup"><span data-stu-id="a7ef4-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ef4-111">参照</span><span class="sxs-lookup"><span data-stu-id="a7ef4-111">See Also</span></span>  
 <span data-ttu-id="a7ef4-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a7ef4-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
