---
title: ProtocolOrder プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8bccb7109972dea4697e9e289081cbf47d2f9492
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645458"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a><span data-ttu-id="2b2d0-102">ProtocolOrder プロパティ (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="2b2d0-102">ProtocolOrder Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="2b2d0-103">[Setordervalue メソッド (ClientNetworkProtocol クラス)](clientnetworkprotocol-class.md)メソッドによって指定された現在参照されているクライアントネットワークプロトコルの順序番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="2b2d0-103">Gets the order number of the currently referenced client network protocol as specified by the [SetOrderValue Method (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b2d0-104">Syntax</span></span>  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="2b2d0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="2b2d0-105">Parts</span></span>  
 <span data-ttu-id="2b2d0-106">*object*</span><span class="sxs-lookup"><span data-stu-id="2b2d0-106">*object*</span></span>  
 <span data-ttu-id="2b2d0-107">クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2b2d0-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2b2d0-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="2b2d0-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="2b2d0-109">現在参照されているクライアント ネットワーク プロトコルに対して、`uint32` メソッドによって設定されている順序番号を指定する `OrderValue` 値。</span><span class="sxs-lookup"><span data-stu-id="2b2d0-109">A `uint32` value that specifies the order number of the currently referenced client network protocol as set by the `OrderValue` method.</span></span> <span data-ttu-id="2b2d0-110">クライアント ネットワーク プロトコルが無効の場合、この値は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="2b2d0-110">If the client network protocol is disabled, this value will be zero.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b2d0-111">解説</span><span class="sxs-lookup"><span data-stu-id="2b2d0-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2d0-112">参照</span><span class="sxs-lookup"><span data-stu-id="2b2d0-112">See Also</span></span>  
 <span data-ttu-id="2b2d0-113">[クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="2b2d0-113">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="2b2d0-114">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="2b2d0-114">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
