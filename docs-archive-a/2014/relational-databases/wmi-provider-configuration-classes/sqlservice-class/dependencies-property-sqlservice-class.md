---
title: Dependencies プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b5b64aee371a41bc0d58ec4a52a1a1526bc13388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738124"
---
# <a name="dependencies-property-sqlservice-class"></a><span data-ttu-id="92fe1-102">Dependencies プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="92fe1-102">Dependencies Property (SqlService Class)</span></span>
  <span data-ttu-id="92fe1-103">参照されたサービスに依存するサービスのリストを取得します。</span><span class="sxs-lookup"><span data-stu-id="92fe1-103">Gets a list of services that are dependent on the referenced service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92fe1-104">構文</span><span class="sxs-lookup"><span data-stu-id="92fe1-104">Syntax</span></span>  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="92fe1-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="92fe1-105">Parts</span></span>  
 <span data-ttu-id="92fe1-106">*object*</span><span class="sxs-lookup"><span data-stu-id="92fe1-106">*object*</span></span>  
 <span data-ttu-id="92fe1-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="92fe1-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="92fe1-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="92fe1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="92fe1-109">参照されたサービスに依存するサービスのリストを格納する string[] 配列。</span><span class="sxs-lookup"><span data-stu-id="92fe1-109">A string[] array that contains a list of services dependent on the referenced service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92fe1-110">解説</span><span class="sxs-lookup"><span data-stu-id="92fe1-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92fe1-111">参照</span><span class="sxs-lookup"><span data-stu-id="92fe1-111">See Also</span></span>  
 <span data-ttu-id="92fe1-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="92fe1-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
