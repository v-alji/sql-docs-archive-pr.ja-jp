---
title: SetDisable メソッド (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3176227aba4de1e5aca1be35ec1f071a15caa49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634353"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a><span data-ttu-id="44d27-102">SetDisable メソッド (ServerNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="44d27-102">SetDisable Method (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="44d27-103">サーバー ネットワーク プロトコルを無効にします。</span><span class="sxs-lookup"><span data-stu-id="44d27-103">Disables the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d27-104">構文</span><span class="sxs-lookup"><span data-stu-id="44d27-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="44d27-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="44d27-105">Parts</span></span>  
 <span data-ttu-id="44d27-106">*object*</span><span class="sxs-lookup"><span data-stu-id="44d27-106">*object*</span></span>  
 <span data-ttu-id="44d27-107">のインスタンスによって使用されるネットワークプロトコルを表す [ServerNetworkProtocol Class] servernetworkprotocol-class.md) オブジェクト [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44d27-107">A [ServerNetworkProtocol Class]servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="44d27-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="44d27-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="44d27-109">uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="44d27-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44d27-110">解説</span><span class="sxs-lookup"><span data-stu-id="44d27-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d27-111">参照</span><span class="sxs-lookup"><span data-stu-id="44d27-111">See Also</span></span>  
 <span data-ttu-id="44d27-112">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="44d27-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
