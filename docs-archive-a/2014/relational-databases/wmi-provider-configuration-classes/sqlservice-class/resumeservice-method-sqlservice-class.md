---
title: ResumeService メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ResumeService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 53d07c8697c6303bc371f442745e2d1864682e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639922"
---
# <a name="resumeservice-method-sqlservice-class"></a><span data-ttu-id="c1025-102">ResumeService メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="c1025-102">ResumeService Method (SqlService Class)</span></span>
  <span data-ttu-id="c1025-103">サービスを再開状態にする動作を試行します。</span><span class="sxs-lookup"><span data-stu-id="c1025-103">Attempts to place the service in the resumed state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1025-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1025-104">Syntax</span></span>  
  
```  
  
object  
.ResumeService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="c1025-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c1025-105">Parts</span></span>  
 <span data-ttu-id="c1025-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c1025-106">*object*</span></span>  
 <span data-ttu-id="c1025-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c1025-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c1025-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="c1025-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c1025-109">uint32 値。`ResumeService` 要求が正常に受け入れられた場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="c1025-109">A uint32 value, which is 0 if the `ResumeService` request was accepted, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1025-110">解説</span><span class="sxs-lookup"><span data-stu-id="c1025-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1025-111">参照</span><span class="sxs-lookup"><span data-stu-id="c1025-111">See Also</span></span>  
 <span data-ttu-id="c1025-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c1025-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  