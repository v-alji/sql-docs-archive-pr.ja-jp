---
title: SetNumericalValue メソッド (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumericalValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: b3b4bce8-9d9e-4ccb-a223-0454281353b0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5a4b8d6819dae11abe4cc097f0e423c23d909e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640817"
---
# <a name="setnumericalvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="46944-102">SetNumericalValue メソッド (ServerNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="46944-102">SetNumericalValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="46944-103">参照されたプロパティの数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="46944-103">Sets the numeric value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46944-104">構文</span><span class="sxs-lookup"><span data-stu-id="46944-104">Syntax</span></span>  
  
```  
  
object  
.SetNumericalValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="46944-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="46944-105">Parts</span></span>  
 <span data-ttu-id="46944-106">*object*</span><span class="sxs-lookup"><span data-stu-id="46944-106">*object*</span></span>  
 <span data-ttu-id="46944-107">のインスタンス上のネットワークプロトコルの属性を表す [ServerNetworkProtocolProperty クラス] servernetworkprotocolproperty-class.md) オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="46944-107">A [ServerNetworkProtocolProperty Class]servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="46944-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46944-108">Parameters</span></span>  
  
|<span data-ttu-id="46944-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46944-109">Parameter</span></span>|<span data-ttu-id="46944-110">説明</span><span class="sxs-lookup"><span data-stu-id="46944-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46944-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="46944-111">*NumValue*</span></span>|<span data-ttu-id="46944-112">現在のプロパティの新しい値を指定する `uint32` 値</span><span class="sxs-lookup"><span data-stu-id="46944-112">A `uint32` value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="46944-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="46944-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="46944-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="46944-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46944-115">解説</span><span class="sxs-lookup"><span data-stu-id="46944-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46944-116">参照</span><span class="sxs-lookup"><span data-stu-id="46944-116">See Also</span></span>  
 <span data-ttu-id="46944-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="46944-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
