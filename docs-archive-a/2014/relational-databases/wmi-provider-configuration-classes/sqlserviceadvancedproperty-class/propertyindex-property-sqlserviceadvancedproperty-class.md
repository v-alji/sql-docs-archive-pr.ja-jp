---
title: PropertyIndex プロパティ (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyIndex Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyIndex property
ms.assetid: b18b45a2-e187-44f5-a8c9-26fd9828b6c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e328c2fcf6b5f6ab6fc95383b7020deb9e172b07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712870"
---
# <a name="propertyindex-property-sqlserviceadvancedproperty-class"></a><span data-ttu-id="929bf-102">PropertyIndex プロパティ (SqlServiceAdvancedProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="929bf-102">PropertyIndex Property (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="929bf-103">参照されたサービスに属する詳細プロパティの配列内で、詳細プロパティの位置を指定するプロパティ インデックスを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="929bf-103">Gets or sets the property index that specifies the position of an advanced property in an array of advanced properties that belong to a referenced service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="929bf-104">Syntax</span></span>  
  
```  
  
object  
.PropertyIndex [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="929bf-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="929bf-105">Parts</span></span>  
 <span data-ttu-id="929bf-106">*object*</span><span class="sxs-lookup"><span data-stu-id="929bf-106">*object*</span></span>  
 <span data-ttu-id="929bf-107">詳細プロパティを表す [SqlServiceAdvancedProperty クラス](sqlserviceadvancedproperty-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="929bf-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="929bf-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="929bf-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="929bf-109">参照されたサービスに属する詳細プロパティ配列内で、詳細プロパティの位置を指定する `uint32` 値。</span><span class="sxs-lookup"><span data-stu-id="929bf-109">A `uint32` value that specifies the position of the advanced property in the advanced property array that belongs to the referenced service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="929bf-110">解説</span><span class="sxs-lookup"><span data-stu-id="929bf-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="929bf-111">参照</span><span class="sxs-lookup"><span data-stu-id="929bf-111">See Also</span></span>  
 <span data-ttu-id="929bf-112">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="929bf-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
