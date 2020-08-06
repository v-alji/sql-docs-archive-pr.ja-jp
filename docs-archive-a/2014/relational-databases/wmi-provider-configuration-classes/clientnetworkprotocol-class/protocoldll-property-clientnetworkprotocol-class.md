---
title: ProtocolDLL プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolDLL Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: fe8650d5-7b9d-46f8-bf74-baf1d9d2a06a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cb008003b05b00e342795d51afee2b4491a71260
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640820"
---
# <a name="protocoldll-property-clientnetworkprotocol-class"></a><span data-ttu-id="c4183-102">ProtocolDLL プロパティ (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="c4183-102">ProtocolDLL Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="c4183-103">[クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)によって指定されたネットワークプロトコルに必要な .dll ファイルの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="c4183-103">Gets the name of the .dll file required by the network protocol specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4183-104">構文</span><span class="sxs-lookup"><span data-stu-id="c4183-104">Syntax</span></span>  
  
```  
  
object  
.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="c4183-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c4183-105">Parts</span></span>  
 <span data-ttu-id="c4183-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c4183-106">*object*</span></span>  
 <span data-ttu-id="c4183-107">クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c4183-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c4183-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="c4183-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c4183-109">クライアント ネットワーク プロトコルに必要なプロトコル .dll ファイルを指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="c4183-109">A string value that specifies the protocol .dll file required by the client network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4183-110">解説</span><span class="sxs-lookup"><span data-stu-id="c4183-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4183-111">参照</span><span class="sxs-lookup"><span data-stu-id="c4183-111">See Also</span></span>  
 [<span data-ttu-id="c4183-112">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="c4183-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
