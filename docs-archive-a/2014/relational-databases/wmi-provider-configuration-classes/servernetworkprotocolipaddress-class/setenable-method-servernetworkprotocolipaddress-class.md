---
title: SetEnable メソッド (ServerNetworkProtocolIPAddress クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: baa86deb-95dd-416f-b2c7-cec1dfb91ab4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5be9c30acacaedba320fd68363e531b178918271
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641992"
---
# <a name="setenable-method-servernetworkprotocolipaddress-class"></a><span data-ttu-id="a6f76-102">SetEnable メソッド (ServerNetworkProtocolIPAddress クラス)</span><span class="sxs-lookup"><span data-stu-id="a6f76-102">SetEnable Method (ServerNetworkProtocolIPAddress Class)</span></span>
  <span data-ttu-id="a6f76-103">IP アドレスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a6f76-103">Enables the IP address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f76-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6f76-104">Syntax</span></span>  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a6f76-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a6f76-105">Parts</span></span>  
 <span data-ttu-id="a6f76-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a6f76-106">*object*</span></span>  
 <span data-ttu-id="a6f76-107">のインスタンス上のネットワークプロトコルの IP アドレスを表す[ServerNetworkProtocolIPAdress クラス](servernetworkprotocolipaddress-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6f76-107">A [ServerNetworkProtocolIPAdress Class](servernetworkprotocolipaddress-class.md) object that represents an IP address for the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a6f76-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="a6f76-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="a6f76-109">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="a6f76-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6f76-110">解説</span><span class="sxs-lookup"><span data-stu-id="a6f76-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f76-111">参照</span><span class="sxs-lookup"><span data-stu-id="a6f76-111">See Also</span></span>  
 <span data-ttu-id="a6f76-112">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a6f76-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
