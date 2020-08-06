---
title: SetNumValue メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: c292e2ae-6d0a-44ad-ba54-5b0bd705ef37
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 82a5474c2330d0d5bc0ed8766614773ceb899bf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640823"
---
# <a name="setnumvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="374c3-102">SetNumValue メソッド (ClientNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="374c3-102">SetNumValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="374c3-103">[Propertyidx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md)の値によって参照される、現在のプロパティの数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="374c3-103">Sets the numeric value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374c3-104">構文</span><span class="sxs-lookup"><span data-stu-id="374c3-104">Syntax</span></span>  
  
```  
  
object  
.SetNumValue [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="374c3-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="374c3-105">Parts</span></span>  
 <span data-ttu-id="374c3-106">*object*</span><span class="sxs-lookup"><span data-stu-id="374c3-106">*object*</span></span>  
 <span data-ttu-id="374c3-107">クライアントによって使用されるネットワークプロトコルの属性を表す[Clientnetworkprotocolproperty クラス](clientnetworkprotocolproperty-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="374c3-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="374c3-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="374c3-108">Parameters</span></span>  
  
|<span data-ttu-id="374c3-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="374c3-109">Parameter</span></span>|<span data-ttu-id="374c3-110">説明</span><span class="sxs-lookup"><span data-stu-id="374c3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="374c3-111">*value*</span><span class="sxs-lookup"><span data-stu-id="374c3-111">*value*</span></span>|<span data-ttu-id="374c3-112">参照されたプロパティの数値を指定する `uint32` 値</span><span class="sxs-lookup"><span data-stu-id="374c3-112">A `uint32` value that specifies the numeric value of the referenced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="374c3-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="374c3-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="374c3-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="374c3-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="374c3-115">解説</span><span class="sxs-lookup"><span data-stu-id="374c3-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374c3-116">参照</span><span class="sxs-lookup"><span data-stu-id="374c3-116">See Also</span></span>  
 [<span data-ttu-id="374c3-117">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="374c3-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
