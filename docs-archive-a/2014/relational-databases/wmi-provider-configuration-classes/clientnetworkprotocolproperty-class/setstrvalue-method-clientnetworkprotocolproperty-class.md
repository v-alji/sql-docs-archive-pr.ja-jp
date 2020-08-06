---
title: SetStrValue メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStrValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStrValue method
ms.assetid: 4ff80124-6e2e-4d96-a692-57c17b53c55e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f3c23eebdbe948e1b77c47ef56a04691fa391938
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740762"
---
# <a name="setstrvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="7e452-102">SetStrValue メソッド (ClientNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="7e452-102">SetStrValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="7e452-103">[PropertyIdx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md) の値によって参照される現在のプロパティの文字列値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7e452-103">Sets the string value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e452-104">構文</span><span class="sxs-lookup"><span data-stu-id="7e452-104">Syntax</span></span>  
  
```  
  
object  
.SetStrValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="7e452-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="7e452-105">Parts</span></span>  
 <span data-ttu-id="7e452-106">*object*</span><span class="sxs-lookup"><span data-stu-id="7e452-106">*object*</span></span>  
 <span data-ttu-id="7e452-107">[クライアントによって使用されるネットワーク プロトコルの属性を表す](clientnetworkprotocolproperty-class.md) ClientNetworkProtocolProperty クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7e452-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="7e452-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e452-108">Parameters</span></span>  
  
|<span data-ttu-id="7e452-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e452-109">Parameter</span></span>|<span data-ttu-id="7e452-110">説明</span><span class="sxs-lookup"><span data-stu-id="7e452-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e452-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="7e452-111">*StrValue*</span></span>|<span data-ttu-id="7e452-112">現在のプロパティの新しい値を指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="7e452-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7e452-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="7e452-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="7e452-114">uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="7e452-114">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e452-115">解説</span><span class="sxs-lookup"><span data-stu-id="7e452-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e452-116">参照</span><span class="sxs-lookup"><span data-stu-id="7e452-116">See Also</span></span>  
 [<span data-ttu-id="7e452-117">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="7e452-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
