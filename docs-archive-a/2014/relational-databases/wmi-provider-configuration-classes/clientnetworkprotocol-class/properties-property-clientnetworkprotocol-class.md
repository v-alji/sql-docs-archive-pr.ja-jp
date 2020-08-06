---
title: Properties プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 09836db1f510ac77635924c51e5341686627d54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646065"
---
# <a name="properties-property-clientnetworkprotocol-class"></a><span data-ttu-id="e4162-102">Properties プロパティ (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="e4162-102">Properties Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="e4162-103">[Configure Client Protocols (クライアント プロトコルの構成)](https://technet.microsoft.com/library/ms181035.aspx)によって指定された現在のクライアント ネットワーク プロトコルに関連付けられたプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="e4162-103">Gets the properties associated with the current client network protocol specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4162-104">構文</span><span class="sxs-lookup"><span data-stu-id="e4162-104">Syntax</span></span>  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="e4162-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="e4162-105">Parts</span></span>  
 <span data-ttu-id="e4162-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e4162-106">*object*</span></span>  
 <span data-ttu-id="e4162-107">[クライアントによって使用されるネットワーク プロトコルを表す](clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e4162-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e4162-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="e4162-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="e4162-109">プロパティによって参照されている現在のクライアントネットワークプロトコルでサポートされているプロパティを表す[Clientnetworkprotocolproperty クラス](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)オブジェクトの配列 `OrderValue` 。</span><span class="sxs-lookup"><span data-stu-id="e4162-109">An array of [ClientNetworkProtocolProperty Class](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) objects that represent the properties supported by the current client network protocol that is referenced by the `OrderValue` property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4162-110">解説</span><span class="sxs-lookup"><span data-stu-id="e4162-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4162-111">参照</span><span class="sxs-lookup"><span data-stu-id="e4162-111">See Also</span></span>  
 [<span data-ttu-id="e4162-112">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="e4162-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
