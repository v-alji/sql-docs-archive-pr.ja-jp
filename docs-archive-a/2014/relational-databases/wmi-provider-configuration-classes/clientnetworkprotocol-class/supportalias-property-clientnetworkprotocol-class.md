---
title: SupportAlias プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SupportAlias Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6fd06ad0921dbb113a89af77e46733a28c2226c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645451"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a><span data-ttu-id="0ac71-102">SupportAlias プロパティ (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="0ac71-102">SupportAlias Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="0ac71-103">[Setordervalue メソッド (ClientNetworkProtocol クラス)](clientnetworkprotocol-class.md)によって指定された現在のネットワークプロトコルがエイリアスをサポートするかどうかを指定するブール型プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="0ac71-103">Gets the Boolean property that specifies whether the current network protocol specified by the [SetOrderValue Method (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) support aliases.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ac71-104">構文</span><span class="sxs-lookup"><span data-stu-id="0ac71-104">Syntax</span></span>  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="0ac71-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0ac71-105">Parts</span></span>  
 <span data-ttu-id="0ac71-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0ac71-106">*object*</span></span>  
 <span data-ttu-id="0ac71-107">[クライアントによって使用されるネットワーク プロトコルを表す](clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0ac71-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0ac71-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="0ac71-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="0ac71-109">クライアント ネットワーク プロトコルが別名をサポートするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="0ac71-109">A Boolean value that specifies whether the client network protocol supports aliases.</span></span>  
  
 <span data-ttu-id="0ac71-110">True の場合、クライアント ネットワーク プロトコルは別名をサポートします。</span><span class="sxs-lookup"><span data-stu-id="0ac71-110">If True, the client network protocol supports aliases.</span></span>  
  
 <span data-ttu-id="0ac71-111">False の場合、クライアント ネットワーク プロトコルは別名をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="0ac71-111">If False, the client network protocol does not support aliases.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ac71-112">解説</span><span class="sxs-lookup"><span data-stu-id="0ac71-112">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac71-113">参照</span><span class="sxs-lookup"><span data-stu-id="0ac71-113">See Also</span></span>  
 [<span data-ttu-id="0ac71-114">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="0ac71-114">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
