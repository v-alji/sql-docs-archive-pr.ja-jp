---
title: Setブール値メソッド (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0c7142d6f192e94e9850b3c1a8a9481dc15a222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713969"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="67626-102">SetBoolValue メソッド (SqlServiceAdvancedProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="67626-102">SetBoolValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="67626-103">プロパティのブール値を設定します。</span><span class="sxs-lookup"><span data-stu-id="67626-103">Sets the Boolean value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67626-104">構文</span><span class="sxs-lookup"><span data-stu-id="67626-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="67626-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="67626-105">Parts</span></span>  
 <span data-ttu-id="67626-106">*object*</span><span class="sxs-lookup"><span data-stu-id="67626-106">*object*</span></span>  
 <span data-ttu-id="67626-107">詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="67626-107">A [SqlServiceAdvancedProperty Class](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="67626-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67626-108">Parameters</span></span>  
  
|<span data-ttu-id="67626-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67626-109">Parameter</span></span>|<span data-ttu-id="67626-110">説明</span><span class="sxs-lookup"><span data-stu-id="67626-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67626-111">*ブール値*</span><span class="sxs-lookup"><span data-stu-id="67626-111">*BoolValue*</span></span>|<span data-ttu-id="67626-112">詳細プロパティの値を指定するブール値</span><span class="sxs-lookup"><span data-stu-id="67626-112">A Boolean value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="67626-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="67626-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="67626-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="67626-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67626-115">解説</span><span class="sxs-lookup"><span data-stu-id="67626-115">Remarks</span></span>  
 <span data-ttu-id="67626-116">プロパティをブール値に設定するには、プロパティ値の型がブール型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="67626-116">The property value type must be Boolean to set the property to a Boolean value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67626-117">参照</span><span class="sxs-lookup"><span data-stu-id="67626-117">See Also</span></span>  
 <span data-ttu-id="67626-118">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="67626-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
