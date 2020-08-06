---
title: SetStringValue メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 88d67b22-0eea-48c9-ab73-e0b4907953df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba2350b798f1d7092a37a28ca35c17d6f4536a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740766"
---
# <a name="setstringvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="7dec0-102">SetStringValue メソッド (ClientNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="7dec0-102">SetStringValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="7dec0-103">[PropertyIdx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md) の値によって参照される現在のプロパティの文字列値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7dec0-103">Sets the string value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dec0-104">構文</span><span class="sxs-lookup"><span data-stu-id="7dec0-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="7dec0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="7dec0-105">Parts</span></span>  
 <span data-ttu-id="7dec0-106">*object*</span><span class="sxs-lookup"><span data-stu-id="7dec0-106">*object*</span></span>  
 <span data-ttu-id="7dec0-107">クライアントによって使用されるネットワークプロトコルの属性を表す[Clientnetworkprotocolproperty クラス](clientnetworkprotocolproperty-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7dec0-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="7dec0-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dec0-108">Parameters</span></span>  
  
|<span data-ttu-id="7dec0-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dec0-109">Parameter</span></span>|<span data-ttu-id="7dec0-110">説明</span><span class="sxs-lookup"><span data-stu-id="7dec0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7dec0-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="7dec0-111">*StrValue*</span></span>|<span data-ttu-id="7dec0-112">現在のプロパティの新しい値を指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="7dec0-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7dec0-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="7dec0-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="7dec0-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="7dec0-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dec0-115">解説</span><span class="sxs-lookup"><span data-stu-id="7dec0-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dec0-116">参照</span><span class="sxs-lookup"><span data-stu-id="7dec0-116">See Also</span></span>  
 [<span data-ttu-id="7dec0-117">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="7dec0-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
