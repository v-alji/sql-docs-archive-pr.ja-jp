---
title: IpAddresses プロパティ (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b94c4c11327abc1f02bd1e99c414f806f75bc145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630828"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a><span data-ttu-id="6078a-102">IpAddresses プロパティ (ServerNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="6078a-102">IpAddresses Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="6078a-103">サーバー ネットワーク プロトコルに関連付けられた IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6078a-103">Gets the IP addresses associated with the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6078a-104">構文</span><span class="sxs-lookup"><span data-stu-id="6078a-104">Syntax</span></span>  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="6078a-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="6078a-105">Parts</span></span>  
 <span data-ttu-id="6078a-106">*object*</span><span class="sxs-lookup"><span data-stu-id="6078a-106">*object*</span></span>  
 <span data-ttu-id="6078a-107">`ServerNetworkProtocol`のインスタンスによって使用されるネットワークプロトコルを表すオブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="6078a-107">A `ServerNetworkProtocol` object that represents the network protocol used by the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="6078a-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="6078a-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="6078a-109">サーバーネットワークプロトコルによってサポートされる IP アドレスを表す[ServerNetworkProtocolIPAdress クラス](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)オブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="6078a-109">An array of [ServerNetworkProtocolIPAdress Class](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) objects that represent the IP addresses supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6078a-110">解説</span><span class="sxs-lookup"><span data-stu-id="6078a-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6078a-111">参照</span><span class="sxs-lookup"><span data-stu-id="6078a-111">See Also</span></span>  
 <span data-ttu-id="6078a-112">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6078a-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
