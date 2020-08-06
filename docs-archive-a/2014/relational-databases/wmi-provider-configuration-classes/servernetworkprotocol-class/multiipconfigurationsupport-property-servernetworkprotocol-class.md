---
title: MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80401a607c9155451a869082162affcca401ebca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630827"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a><span data-ttu-id="b45f1-102">MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="b45f1-102">MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="b45f1-103">複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール型のプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="b45f1-103">Gets the Boolean property that specifies whether multiple IP addresses are supported by a server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45f1-104">構文</span><span class="sxs-lookup"><span data-stu-id="b45f1-104">Syntax</span></span>  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="b45f1-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="b45f1-105">Parts</span></span>  
 <span data-ttu-id="b45f1-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b45f1-106">*object*</span></span>  
 <span data-ttu-id="b45f1-107">のインスタンスによって使用されるネットワークプロトコルを表す[Protocolname プロパティ (ServerNetworkProtocol クラス)](servernetworkprotocol-class.md)オブジェクト [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b45f1-107">A [ProtocolName Property (ServerNetworkProtocol Class)](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b45f1-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="b45f1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="b45f1-109">複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール値。複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされる場合は `true`、複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされない場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="b45f1-109">A Boolean value that specifies whether multiple IP addresses are supported by the server network protocol: `true` if multiple IP addresses are supported by the server network protocol, or `false` if multiple IP addresses are not supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b45f1-110">解説</span><span class="sxs-lookup"><span data-stu-id="b45f1-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45f1-111">参照</span><span class="sxs-lookup"><span data-stu-id="b45f1-111">See Also</span></span>  
 <span data-ttu-id="b45f1-112">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b45f1-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
