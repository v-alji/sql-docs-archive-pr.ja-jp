---
title: SetStrValue メソッド (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStrValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStrValue method
ms.assetid: 1fededc3-81ba-4b08-83f9-189b96140799
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d977eb9845c820c4128d1d60337151eeb3893eb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717570"
---
# <a name="setstrvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="20e16-102">SetStrValue メソッド (SqlServiceAdvancedProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="20e16-102">SetStrValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="20e16-103">プロパティの文字列値を設定します。</span><span class="sxs-lookup"><span data-stu-id="20e16-103">Sets the string value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e16-104">構文</span><span class="sxs-lookup"><span data-stu-id="20e16-104">Syntax</span></span>  
  
```  
  
object  
.SetStrValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="20e16-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="20e16-105">Parts</span></span>  
 <span data-ttu-id="20e16-106">*object*</span><span class="sxs-lookup"><span data-stu-id="20e16-106">*object*</span></span>  
 <span data-ttu-id="20e16-107">詳細プロパティを表す [SqlServiceAdvancedProperty クラス](sqlserviceadvancedproperty-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20e16-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="20e16-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20e16-108">Parameters</span></span>  
  
|<span data-ttu-id="20e16-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20e16-109">Parameter</span></span>|<span data-ttu-id="20e16-110">説明</span><span class="sxs-lookup"><span data-stu-id="20e16-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20e16-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="20e16-111">*StrValue*</span></span>|<span data-ttu-id="20e16-112">詳細プロパティの値を指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="20e16-112">A string value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="20e16-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="20e16-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="20e16-114">uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="20e16-114">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20e16-115">解説</span><span class="sxs-lookup"><span data-stu-id="20e16-115">Remarks</span></span>  
 <span data-ttu-id="20e16-116">プロパティを文字列値に設定するには、プロパティ値の型が *string* である必要があります。</span><span class="sxs-lookup"><span data-stu-id="20e16-116">The property value type must be *string* to set the property to a string value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e16-117">参照</span><span class="sxs-lookup"><span data-stu-id="20e16-117">See Also</span></span>  
 <span data-ttu-id="20e16-118">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="20e16-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
