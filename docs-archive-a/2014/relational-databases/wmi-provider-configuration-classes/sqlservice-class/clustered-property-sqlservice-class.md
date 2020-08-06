---
title: Clustered プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Clustered Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fdc87bb7b691580f7efd5ccd7b333d88a3aa78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712877"
---
# <a name="clustered-property-sqlservice-class"></a><span data-ttu-id="9963b-102">Clustered プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="9963b-102">Clustered Property (SqlService Class)</span></span>
  <span data-ttu-id="9963b-103">サービスがクラスター化インスタンスの一部であるかどうかを指定するブール型のプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9963b-103">Gets the Boolean property value that specifies whether the service is part of a clustered instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9963b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9963b-104">Syntax</span></span>  
  
```  
  
object  
.Clustered [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="9963b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9963b-105">Parts</span></span>  
 <span data-ttu-id="9963b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="9963b-106">*object*</span></span>  
 <span data-ttu-id="9963b-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9963b-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9963b-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="9963b-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="9963b-109">サービスがクラスター化インスタンスに参加しているかどうかを指定するブール値です。サービスがクラスター化インスタンスに参加している場合は `true`、サービスがクラスター化インスタンスに参加していない場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="9963b-109">A Boolean value that specifies whether the service is participating in a clustered instance: `true` if the service is participating in a clustered instance, or `false` if the service is not participating in a clustered instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9963b-110">解説</span><span class="sxs-lookup"><span data-stu-id="9963b-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9963b-111">参照</span><span class="sxs-lookup"><span data-stu-id="9963b-111">See Also</span></span>  
 <span data-ttu-id="9963b-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9963b-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
