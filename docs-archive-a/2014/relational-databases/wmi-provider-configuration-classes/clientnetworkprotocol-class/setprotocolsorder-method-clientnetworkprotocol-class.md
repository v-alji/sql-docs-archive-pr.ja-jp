---
title: SetProtocolsOrder メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aaa1d43c8a2f7f210f61761b28313a93ac6c7a90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645453"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a><span data-ttu-id="166eb-102">SetProtocolsOrder メソッド (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="166eb-102">SetProtocolsOrder Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="166eb-103">プロトコル リストの順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="166eb-103">Changes the order of the protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166eb-104">構文</span><span class="sxs-lookup"><span data-stu-id="166eb-104">Syntax</span></span>  
  
```  
  
object  
.SetProtocolsOrder(  
ProtocolOrderList  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="166eb-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="166eb-105">Parts</span></span>  
 <span data-ttu-id="166eb-106">*object*</span><span class="sxs-lookup"><span data-stu-id="166eb-106">*object*</span></span>  
 <span data-ttu-id="166eb-107">クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="166eb-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="166eb-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="166eb-108">Parameters</span></span>  
  
|<span data-ttu-id="166eb-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="166eb-109">Parameter</span></span>|<span data-ttu-id="166eb-110">説明</span><span class="sxs-lookup"><span data-stu-id="166eb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="166eb-111">*ProtocolOrderList*</span><span class="sxs-lookup"><span data-stu-id="166eb-111">*ProtocolOrderList*</span></span>|<span data-ttu-id="166eb-112">クライアント ネットワーク プロトコルを新しい順序でリストした string[] 配列</span><span class="sxs-lookup"><span data-stu-id="166eb-112">A string[] array that lists the client network protocols in the new order.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="166eb-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="166eb-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="166eb-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="166eb-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="166eb-115">解説</span><span class="sxs-lookup"><span data-stu-id="166eb-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166eb-116">参照</span><span class="sxs-lookup"><span data-stu-id="166eb-116">See Also</span></span>  
 <span data-ttu-id="166eb-117">[クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="166eb-117">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="166eb-118">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="166eb-118">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
