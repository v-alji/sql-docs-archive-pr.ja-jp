---
title: SetOrderValue メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetOrderValue method
ms.assetid: 15f693fd-37f6-41d9-9dab-d2c93db19895
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6839e85b6131c54e233d980c84a8727eeda2202a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645457"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="bef8b-102">SetOrderValue メソッド (ClientNetworkProtocol クラス)</span><span class="sxs-lookup"><span data-stu-id="bef8b-102">SetOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="bef8b-103">クライアント プロトコル リストから、指定された順序値を持つプロトコルを選択します。</span><span class="sxs-lookup"><span data-stu-id="bef8b-103">Selects the protocol with the specified order value from the client protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="bef8b-104">Syntax</span></span>  
  
```  
  
object  
.SetOrderValue(  
OrderValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="bef8b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="bef8b-105">Parts</span></span>  
 <span data-ttu-id="bef8b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="bef8b-106">*object*</span></span>  
 <span data-ttu-id="bef8b-107">[クライアントによって使用されるネットワーク プロトコルを表す](clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bef8b-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="bef8b-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bef8b-108">Parameters</span></span>  
  
|<span data-ttu-id="bef8b-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bef8b-109">Parameter</span></span>|<span data-ttu-id="bef8b-110">説明</span><span class="sxs-lookup"><span data-stu-id="bef8b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bef8b-111">*OrderValue*</span><span class="sxs-lookup"><span data-stu-id="bef8b-111">*OrderValue*</span></span>|<span data-ttu-id="bef8b-112">順序値を設定する `int32` 値</span><span class="sxs-lookup"><span data-stu-id="bef8b-112">A u`int32` value that sets the order value.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="bef8b-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="bef8b-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="bef8b-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="bef8b-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bef8b-115">解説</span><span class="sxs-lookup"><span data-stu-id="bef8b-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef8b-116">参照</span><span class="sxs-lookup"><span data-stu-id="bef8b-116">See Also</span></span>  
 <span data-ttu-id="bef8b-117">[[クライアント プロトコルのプロパティ] ダイアログ ボックス ([順序] タブ)](https://technet.microsoft.com/library/ms187884.aspx)</span><span class="sxs-lookup"><span data-stu-id="bef8b-117">[Client Protocols Properties (Order Tab)](https://technet.microsoft.com/library/ms187884.aspx)</span></span>  
  
  
