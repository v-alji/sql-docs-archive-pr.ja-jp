---
title: AcceptStop プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptStop Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d555a3763b4e8c769cd52ce72019b66bddd594fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640806"
---
# <a name="acceptstop-property-sqlservice-class"></a><span data-ttu-id="d2d5c-102">AcceptStop プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="d2d5c-102">AcceptStop Property (SqlService Class)</span></span>
  <span data-ttu-id="d2d5c-103">サービスを停止できるかどうかを指定するブール型のプロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d2d5c-103">Gets the Boolean property value that specifies whether the service can be stopped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d5c-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2d5c-104">Syntax</span></span>  
  
```  
  
object  
.AcceptStop [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="d2d5c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d2d5c-105">Parts</span></span>  
 <span data-ttu-id="d2d5c-106">*object*</span><span class="sxs-lookup"><span data-stu-id="d2d5c-106">*object*</span></span>  
 <span data-ttu-id="d2d5c-107">サービスを表す[Sqlservice クラス](sqlservice-class.md)オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d2d5c-107">A [SqlService Class](sqlservice-class.md) object that represents the service</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d2d5c-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="d2d5c-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d2d5c-109">サービスを停止できるかどうかを指定するブール値。サービスを停止できる場合は `true`、サービスを停止できない場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="d2d5c-109">A Boolean value that specifies whether the service can be stopped: `true` if the service can be stopped, or `false` if the service cannot be stopped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2d5c-110">解説</span><span class="sxs-lookup"><span data-stu-id="d2d5c-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d5c-111">参照</span><span class="sxs-lookup"><span data-stu-id="d2d5c-111">See Also</span></span>  
 <span data-ttu-id="d2d5c-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d2d5c-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
