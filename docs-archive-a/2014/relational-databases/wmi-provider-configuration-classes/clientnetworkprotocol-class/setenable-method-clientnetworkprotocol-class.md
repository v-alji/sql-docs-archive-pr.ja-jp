---
title: SetEnable メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: a66c756a-1311-4f4a-8088-818f8ed90056
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dfba695506dd04ded82083b85bfbb751913fbcbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644860"
---
# <a name="setenable-method-clientnetworkprotocol-class"></a><span data-ttu-id="2d8df-102">SetEnable メソッド (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="2d8df-102">SetEnable Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="2d8df-103">[クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)によって指定されたクライアントネットワークプロトコルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2d8df-103">Enables the client network protocol that is specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d8df-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d8df-104">Syntax</span></span>  
  
```  
  
object  
.SetEnableMethod()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="2d8df-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="2d8df-105">Parts</span></span>  
 <span data-ttu-id="2d8df-106">*object*</span><span class="sxs-lookup"><span data-stu-id="2d8df-106">*object*</span></span>  
 <span data-ttu-id="2d8df-107">クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2d8df-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2d8df-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="2d8df-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="2d8df-109">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="2d8df-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d8df-110">解説</span><span class="sxs-lookup"><span data-stu-id="2d8df-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8df-111">参照</span><span class="sxs-lookup"><span data-stu-id="2d8df-111">See Also</span></span>  
 [<span data-ttu-id="2d8df-112">クライアントのネットワーク プロトコルと Net-Library の構成</span><span class="sxs-lookup"><span data-stu-id="2d8df-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
