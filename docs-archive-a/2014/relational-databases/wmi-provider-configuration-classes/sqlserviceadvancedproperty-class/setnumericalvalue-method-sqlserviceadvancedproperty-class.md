---
title: SetNumericalValue メソッド (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumericalValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: 950ed1e8-0538-4db4-807c-a2c36f43cf6b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db823938d77f4e2c67284cae0f11faca12aba6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738083"
---
# <a name="setnumericalvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="68418-102">SetNumericalValue メソッド (SqlServiceAdvancedProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="68418-102">SetNumericalValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="68418-103">プロパティの数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="68418-103">Sets the numeric value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68418-104">構文</span><span class="sxs-lookup"><span data-stu-id="68418-104">Syntax</span></span>  
  
```  
  
object  
.SetNumericalValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="68418-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="68418-105">Parts</span></span>  
 <span data-ttu-id="68418-106">*object*</span><span class="sxs-lookup"><span data-stu-id="68418-106">*object*</span></span>  
 <span data-ttu-id="68418-107">詳細プロパティを表す [SqlServiceAdvancedProperty クラス](sqlserviceadvancedproperty-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="68418-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="68418-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68418-108">Parameters</span></span>  
  
|<span data-ttu-id="68418-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68418-109">Parameter</span></span>|<span data-ttu-id="68418-110">説明</span><span class="sxs-lookup"><span data-stu-id="68418-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68418-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="68418-111">*NumValue*</span></span>|<span data-ttu-id="68418-112">詳細プロパティの値を指定する `uint32` 値</span><span class="sxs-lookup"><span data-stu-id="68418-112">A `uint32` value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="68418-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="68418-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="68418-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="68418-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68418-115">解説</span><span class="sxs-lookup"><span data-stu-id="68418-115">Remarks</span></span>  
 <span data-ttu-id="68418-116">プロパティを数値に設定するには、プロパティ値の型が数値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="68418-116">The property value type must be numeric to be able to set the property to a numeric value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68418-117">参照</span><span class="sxs-lookup"><span data-stu-id="68418-117">See Also</span></span>  
 <span data-ttu-id="68418-118">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="68418-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
