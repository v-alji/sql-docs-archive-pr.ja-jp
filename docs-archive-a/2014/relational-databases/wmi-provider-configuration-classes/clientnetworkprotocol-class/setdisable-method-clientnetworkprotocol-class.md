---
title: SetDisable メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: bce69ab9-ea5b-43fd-8114-08b1b5890755
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2bad312f1f7c7e9540acdaf3dd46df78b953d4ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646062"
---
# <a name="setdisable-method-clientnetworkprotocol-class"></a><span data-ttu-id="ee697-102">SetDisable メソッド (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="ee697-102">SetDisable Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="ee697-103">[クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)によって指定されたクライアントネットワークプロトコルを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ee697-103">Disables the client network protocol that is specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee697-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee697-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="ee697-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="ee697-105">Parts</span></span>  
 <span data-ttu-id="ee697-106">*object*</span><span class="sxs-lookup"><span data-stu-id="ee697-106">*object*</span></span>  
 <span data-ttu-id="ee697-107">クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee697-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ee697-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="ee697-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="ee697-109">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="ee697-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee697-110">解説</span><span class="sxs-lookup"><span data-stu-id="ee697-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee697-111">参照</span><span class="sxs-lookup"><span data-stu-id="ee697-111">See Also</span></span>  
 [<span data-ttu-id="ee697-112">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="ee697-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
