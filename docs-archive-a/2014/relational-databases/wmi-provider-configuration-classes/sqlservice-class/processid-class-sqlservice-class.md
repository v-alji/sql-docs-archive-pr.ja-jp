---
title: ProcessId クラス (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c4c40eea826b5009e52d26b1d930eaf5febbcdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640804"
---
# <a name="processid-class-sqlservice-class"></a><span data-ttu-id="55471-102">ProcessId クラス (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="55471-102">ProcessId Class (SqlService Class)</span></span>
  <span data-ttu-id="55471-103">サービスを一意に識別するシステム プロセス ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="55471-103">Gets the system process ID that uniquely identifies a service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55471-104">構文</span><span class="sxs-lookup"><span data-stu-id="55471-104">Syntax</span></span>  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="55471-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="55471-105">Parts</span></span>  
 <span data-ttu-id="55471-106">*object*</span><span class="sxs-lookup"><span data-stu-id="55471-106">*object*</span></span>  
 <span data-ttu-id="55471-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="55471-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="55471-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="55471-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="55471-109">プロセスを一意に識別する ID を指定する `uint32` 値。</span><span class="sxs-lookup"><span data-stu-id="55471-109">A `uint32` value that specifies the ID that uniquely identifies the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55471-110">解説</span><span class="sxs-lookup"><span data-stu-id="55471-110">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="55471-111">例</span><span class="sxs-lookup"><span data-stu-id="55471-111">Example</span></span>  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a><span data-ttu-id="55471-112">参照</span><span class="sxs-lookup"><span data-stu-id="55471-112">See Also</span></span>  
 <span data-ttu-id="55471-113">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="55471-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
