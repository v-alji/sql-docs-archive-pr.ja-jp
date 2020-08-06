---
title: SetCurrentCertificate メソッド (SInstance クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 7349fb87-b973-4160-a2be-cab73abf5b31
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 44e65ab30659cacca09e63a94a1f3596a182dda5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712914"
---
# <a name="setcurrentcertificate-method-sinstance-class"></a><span data-ttu-id="eda69-102">SetCurrentCertificate メソッド (SInstance クラス)</span><span class="sxs-lookup"><span data-stu-id="eda69-102">SetCurrentCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="eda69-103">現在のセキュリティ証明書を設定します。</span><span class="sxs-lookup"><span data-stu-id="eda69-103">Sets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda69-104">構文</span><span class="sxs-lookup"><span data-stu-id="eda69-104">Syntax</span></span>  
  
```  
  
object  
.SetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="eda69-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="eda69-105">Parts</span></span>  
 <span data-ttu-id="eda69-106">*object*</span><span class="sxs-lookup"><span data-stu-id="eda69-106">*object*</span></span>  
 <span data-ttu-id="eda69-107">のインスタンス上のサーバー設定を表す[Sinstance クラス](sinstance-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eda69-107">An [SInstance Class](sinstance-class.md) object that represents the server setting on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="eda69-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eda69-108">Parameters</span></span>  
  
|<span data-ttu-id="eda69-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eda69-109">Parameter</span></span>|<span data-ttu-id="eda69-110">説明</span><span class="sxs-lookup"><span data-stu-id="eda69-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eda69-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="eda69-111">*SHA*</span></span>|<span data-ttu-id="eda69-112">現在のセキュリティ証明書を指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="eda69-112">A string value that specifies the current security certificate.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="eda69-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="eda69-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="eda69-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="eda69-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eda69-115">解説</span><span class="sxs-lookup"><span data-stu-id="eda69-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda69-116">参照</span><span class="sxs-lookup"><span data-stu-id="eda69-116">See Also</span></span>  
 <span data-ttu-id="eda69-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="eda69-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
