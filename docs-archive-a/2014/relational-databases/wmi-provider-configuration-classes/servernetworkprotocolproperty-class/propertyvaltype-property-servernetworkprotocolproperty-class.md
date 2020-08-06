---
title: PropertyValType プロパティ (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be6c42fbaa36080ec8144d95abb045a3b4328057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739607"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a><span data-ttu-id="d7ffc-102">PropertyValType プロパティ (ServerNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="d7ffc-102">PropertyValType Property (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="d7ffc-103">参照されたプロパティに格納される値のデータ型を取得します。</span><span class="sxs-lookup"><span data-stu-id="d7ffc-103">Gets the data type of the value stored in the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ffc-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7ffc-104">Syntax</span></span>  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="d7ffc-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d7ffc-105">Parts</span></span>  
 <span data-ttu-id="d7ffc-106">*object*</span><span class="sxs-lookup"><span data-stu-id="d7ffc-106">*object*</span></span>  
 <span data-ttu-id="d7ffc-107">のインスタンス上のネットワークプロトコルの属性を表す[Servernetworkprotocolproperty クラス](servernetworkprotocolproperty-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d7ffc-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d7ffc-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="d7ffc-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d7ffc-109">プロパティ値のデータ型を指定する `uint32` 値。</span><span class="sxs-lookup"><span data-stu-id="d7ffc-109">A `uint32` value that specifies the data type of the property value.</span></span> <span data-ttu-id="d7ffc-110">文字列型の値の場合は 0、数値型の値の場合は 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="d7ffc-110">It returns 0 for a string value and 1 for a numerical type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7ffc-111">解説</span><span class="sxs-lookup"><span data-stu-id="d7ffc-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ffc-112">参照</span><span class="sxs-lookup"><span data-stu-id="d7ffc-112">See Also</span></span>  
 <span data-ttu-id="d7ffc-113">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d7ffc-113">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
