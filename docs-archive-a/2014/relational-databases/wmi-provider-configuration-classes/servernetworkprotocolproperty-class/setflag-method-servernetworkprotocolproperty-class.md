---
title: SetFlag メソッド (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 95288931-8eb1-4477-ad80-619cf7073e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1a90b4fca194f20cc0a2d70c947577594155f051
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713953"
---
# <a name="setflag-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="29272-102">SetFlag メソッド (ServerNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="29272-102">SetFlag Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="29272-103">参照されたプロパティのフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="29272-103">Sets the flag of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29272-104">構文</span><span class="sxs-lookup"><span data-stu-id="29272-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="29272-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="29272-105">Parts</span></span>  
 <span data-ttu-id="29272-106">*object*</span><span class="sxs-lookup"><span data-stu-id="29272-106">*object*</span></span>  
 <span data-ttu-id="29272-107">のインスタンス上のネットワークプロトコルの属性を表す [ServerNetworkProtocolProperty クラス] servernetworkprotocolproperty-class.md) オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="29272-107">A [ServerNetworkProtocolProperty Class]servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="29272-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29272-108">Parameters</span></span>  
  
|<span data-ttu-id="29272-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29272-109">Parameter</span></span>|<span data-ttu-id="29272-110">説明</span><span class="sxs-lookup"><span data-stu-id="29272-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29272-111">*ブール値*</span><span class="sxs-lookup"><span data-stu-id="29272-111">*BoolValue*</span></span>|<span data-ttu-id="29272-112">フラグの新しい値を指定するブール値</span><span class="sxs-lookup"><span data-stu-id="29272-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="29272-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="29272-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="29272-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="29272-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29272-115">解説</span><span class="sxs-lookup"><span data-stu-id="29272-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29272-116">参照</span><span class="sxs-lookup"><span data-stu-id="29272-116">See Also</span></span>  
 <span data-ttu-id="29272-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="29272-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
