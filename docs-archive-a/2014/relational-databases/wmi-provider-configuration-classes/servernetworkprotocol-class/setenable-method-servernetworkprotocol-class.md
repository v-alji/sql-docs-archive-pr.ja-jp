---
title: SetEnable メソッド (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: a287950b-086f-4b6d-a2d8-4d3973bd1b21
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8f77b7a92fe226e349a03ffba03cfe8d67c280e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634351"
---
# <a name="setenable-method-servernetworkprotocol-class"></a><span data-ttu-id="27675-102">SetEnable メソッド (ServerNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="27675-102">SetEnable Method (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="27675-103">サーバー ネットワーク プロトコルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="27675-103">Enables the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27675-104">構文</span><span class="sxs-lookup"><span data-stu-id="27675-104">Syntax</span></span>  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="27675-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="27675-105">Parts</span></span>  
 <span data-ttu-id="27675-106">*object*</span><span class="sxs-lookup"><span data-stu-id="27675-106">*object*</span></span>  
 <span data-ttu-id="27675-107">のインスタンスによって使用されるネットワークプロトコルを表す[Servernetworkprotocol クラス](servernetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="27675-107">A [ServerNetworkProtocol Class](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="27675-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="27675-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="27675-109">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="27675-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27675-110">解説</span><span class="sxs-lookup"><span data-stu-id="27675-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27675-111">参照</span><span class="sxs-lookup"><span data-stu-id="27675-111">See Also</span></span>  
 <span data-ttu-id="27675-112">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="27675-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
