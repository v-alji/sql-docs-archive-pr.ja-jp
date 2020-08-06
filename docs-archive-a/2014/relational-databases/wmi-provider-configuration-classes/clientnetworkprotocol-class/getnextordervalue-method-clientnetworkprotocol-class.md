---
title: GetNextOrderValue メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bdc3eecd9e151d7da32a5fd65a90552c0743b3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646067"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="910fb-102">GetNextOrderValue メソッド (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="910fb-102">GetNextOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="910fb-103">プロトコル リスト内で次の位置にあるプロトコルを選択します。</span><span class="sxs-lookup"><span data-stu-id="910fb-103">Selects the protocol that is in the next position in the list of protocols.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="910fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="910fb-104">Syntax</span></span>  
  
```  
  
object  
.GetNextOrderValue()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="910fb-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="910fb-105">Parts</span></span>  
 <span data-ttu-id="910fb-106">*object*</span><span class="sxs-lookup"><span data-stu-id="910fb-106">*object*</span></span>  
 <span data-ttu-id="910fb-107">クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="910fb-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="910fb-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="910fb-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="910fb-109">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="910fb-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="910fb-110">解説</span><span class="sxs-lookup"><span data-stu-id="910fb-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="910fb-111">参照</span><span class="sxs-lookup"><span data-stu-id="910fb-111">See Also</span></span>  
 <span data-ttu-id="910fb-112">[クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="910fb-112">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="910fb-113">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="910fb-113">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
