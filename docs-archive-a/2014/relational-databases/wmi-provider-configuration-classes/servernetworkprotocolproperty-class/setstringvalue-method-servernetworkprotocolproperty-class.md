---
title: SetStringValue メソッド (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 0911df30-55f7-4fca-a1fb-01d2c91c1467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8eb4a27d700d801e3ca94362663c6d7feaa7dc86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712942"
---
# <a name="setstringvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="c2166-102">SetStringValue メソッド (ServerNetworkProtocolProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="c2166-102">SetStringValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="c2166-103">参照されたプロパティの文字列値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c2166-103">Sets the string value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2166-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2166-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="c2166-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c2166-105">Parts</span></span>  
 <span data-ttu-id="c2166-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c2166-106">*object*</span></span>  
 <span data-ttu-id="c2166-107">のインスタンス上のネットワークプロトコルの属性を表す[Servernetworkprotocolproperty クラス](servernetworkprotocolproperty-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c2166-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="c2166-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2166-108">Parameters</span></span>  
  
|<span data-ttu-id="c2166-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2166-109">Parameter</span></span>|<span data-ttu-id="c2166-110">説明</span><span class="sxs-lookup"><span data-stu-id="c2166-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2166-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="c2166-111">*StrValue*</span></span>|<span data-ttu-id="c2166-112">現在のプロパティの新しい値を指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="c2166-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c2166-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="c2166-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="c2166-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="c2166-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2166-115">解説</span><span class="sxs-lookup"><span data-stu-id="c2166-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2166-116">参照</span><span class="sxs-lookup"><span data-stu-id="c2166-116">See Also</span></span>  
 <span data-ttu-id="c2166-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c2166-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
