---
title: SetServiceAccountPassword メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccountPassword Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccountPassword method
ms.assetid: e577a1ac-985c-4799-bb38-9393efc3def2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7a83a6d3686b2ec2df98ae79b4c9d3347f621ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712874"
---
# <a name="setserviceaccountpassword-method-sqlservice-class"></a><span data-ttu-id="fc84a-102">SetServiceAccountPassword メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="fc84a-102">SetServiceAccountPassword Method (SqlService Class)</span></span>
  <span data-ttu-id="fc84a-103">参照されたサービスの実行環境に対応するアカウントのパスワードを変更します。</span><span class="sxs-lookup"><span data-stu-id="fc84a-103">Modifies the password for the account that the referenced service runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc84a-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc84a-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccountPassword(  
AccountOldPassword , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="fc84a-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="fc84a-105">Parts</span></span>  
 <span data-ttu-id="fc84a-106">*object*</span><span class="sxs-lookup"><span data-stu-id="fc84a-106">*object*</span></span>  
 <span data-ttu-id="fc84a-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fc84a-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="fc84a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc84a-108">Parameters</span></span>  
 <span data-ttu-id="fc84a-109">*AccountOldPassword*</span><span class="sxs-lookup"><span data-stu-id="fc84a-109">*AccountOldPassword*</span></span>  
 <span data-ttu-id="fc84a-110">アカウントの既存のパスワードを指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="fc84a-110">A string value that specifies the existing password for the account.</span></span>  
  
 <span data-ttu-id="fc84a-111">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="fc84a-111">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="fc84a-112">アカウントの新しいパスワードを指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="fc84a-112">A string value that specifies the new password for the account.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fc84a-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="fc84a-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="fc84a-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="fc84a-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc84a-115">解説</span><span class="sxs-lookup"><span data-stu-id="fc84a-115">Remarks</span></span>  
  
