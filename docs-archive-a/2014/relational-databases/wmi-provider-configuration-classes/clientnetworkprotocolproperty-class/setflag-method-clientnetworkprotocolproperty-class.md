---
title: SetFlag メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1c83a1d647b62f0e5c5acf0659d54bf787bf0c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738137"
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="edba9-102">SetFlag メソッド (ClientNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="edba9-102">SetFlag Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="edba9-103">[Propertyidx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md)の値によって参照される現在のプロパティのフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="edba9-103">Sets the flag of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edba9-104">構文</span><span class="sxs-lookup"><span data-stu-id="edba9-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
) [=]  
```  
  
## <a name="parts"></a><span data-ttu-id="edba9-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="edba9-105">Parts</span></span>  
 <span data-ttu-id="edba9-106">*object*</span><span class="sxs-lookup"><span data-stu-id="edba9-106">*object*</span></span>  
 <span data-ttu-id="edba9-107">クライアントによって使用されるネットワークプロトコルの属性を表す[Clientnetworkprotocolproperty クラス](clientnetworkprotocolproperty-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="edba9-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="edba9-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="edba9-108">Parameters</span></span>  
  
|<span data-ttu-id="edba9-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="edba9-109">Parameter</span></span>|<span data-ttu-id="edba9-110">説明</span><span class="sxs-lookup"><span data-stu-id="edba9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edba9-111">*ブール値*</span><span class="sxs-lookup"><span data-stu-id="edba9-111">*BoolValue*</span></span>|<span data-ttu-id="edba9-112">フラグの新しい値を指定するブール値</span><span class="sxs-lookup"><span data-stu-id="edba9-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="edba9-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="edba9-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="edba9-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="edba9-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edba9-115">解説</span><span class="sxs-lookup"><span data-stu-id="edba9-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edba9-116">参照</span><span class="sxs-lookup"><span data-stu-id="edba9-116">See Also</span></span>  
 [<span data-ttu-id="edba9-117">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="edba9-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
