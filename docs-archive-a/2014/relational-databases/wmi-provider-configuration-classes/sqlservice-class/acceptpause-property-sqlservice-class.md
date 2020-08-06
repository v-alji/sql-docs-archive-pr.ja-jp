---
title: AcceptPause プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 930c82f6e4538f7f2e916deaa374e928b756909b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645431"
---
# <a name="acceptpause-property-sqlservice-class"></a><span data-ttu-id="8457c-102">AcceptPause プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="8457c-102">AcceptPause Property (SqlService Class)</span></span>
  <span data-ttu-id="8457c-103">サービスを一時停止できるかどうかを指定するブール型のプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8457c-103">Gets the Boolean property value that specifies whether the service can be paused.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8457c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8457c-104">Syntax</span></span>  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="8457c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="8457c-105">Parts</span></span>  
 <span data-ttu-id="8457c-106">*object*</span><span class="sxs-lookup"><span data-stu-id="8457c-106">*object*</span></span>  
 <span data-ttu-id="8457c-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8457c-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="8457c-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="8457c-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="8457c-109">サービスを一時停止できるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="8457c-109">A Boolean value that specifies whether the service can be paused.</span></span> <span data-ttu-id="8457c-110">サービスを一時停止できる場合は `true`、サービスを一時停止できない場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="8457c-110">`true` if the service can be paused; `false` if the service cannot be paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8457c-111">解説</span><span class="sxs-lookup"><span data-stu-id="8457c-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8457c-112">参照</span><span class="sxs-lookup"><span data-stu-id="8457c-112">See Also</span></span>  
 <span data-ttu-id="8457c-113">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8457c-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
