---
title: StopService メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StopService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StopService method
ms.assetid: ef8e1856-4930-417a-8f52-be470fd3f15c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 534db69b9c5474638ef5e893847f7d6b9bbb645d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717600"
---
# <a name="stopservice-method-sqlservice-class"></a><span data-ttu-id="9a3f5-102">StopService メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="9a3f5-102">StopService Method (SqlService Class)</span></span>
  <span data-ttu-id="9a3f5-103">サービスを停止状態にする動作を試行します。</span><span class="sxs-lookup"><span data-stu-id="9a3f5-103">Attempts to place the service in the stopped state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a3f5-104">Syntax</span></span>  
  
```  
  
object  
.StopService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="9a3f5-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9a3f5-105">Parts</span></span>  
 <span data-ttu-id="9a3f5-106">*object*</span><span class="sxs-lookup"><span data-stu-id="9a3f5-106">*object*</span></span>  
 <span data-ttu-id="9a3f5-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9a3f5-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9a3f5-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="9a3f5-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="9a3f5-109">`uint32` 値。`ResumeService` 要求が正常に受け入れられた場合は 0、要求がサポートされない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="9a3f5-109">A `uint32` value, which is 0 if the `ResumeService` request was accepted, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a3f5-110">解説</span><span class="sxs-lookup"><span data-stu-id="9a3f5-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3f5-111">参照</span><span class="sxs-lookup"><span data-stu-id="9a3f5-111">See Also</span></span>  
 <span data-ttu-id="9a3f5-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9a3f5-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
