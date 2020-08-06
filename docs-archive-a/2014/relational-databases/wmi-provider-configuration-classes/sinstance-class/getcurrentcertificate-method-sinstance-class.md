---
title: GetCurrentCertificate メソッド (SInstance クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 47838190e3791e01f8482e3fb064a9dca3a764af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646058"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a><span data-ttu-id="0d736-102">GetCurrentCertificate メソッド (SInstance クラス)</span><span class="sxs-lookup"><span data-stu-id="0d736-102">GetCurrentCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="0d736-103">現在のセキュリティ証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d736-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d736-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d736-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0d736-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0d736-105">Parts</span></span>  
 <span data-ttu-id="0d736-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0d736-106">*object*</span></span>  
 <span data-ttu-id="0d736-107">[のインスタンス上のサーバー設定を表す](sinstance-class.md) SInstance クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0d736-107">An [SInstance Class](sinstance-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0d736-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d736-108">Parameters</span></span>  
  
|<span data-ttu-id="0d736-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d736-109">Parameter</span></span>|<span data-ttu-id="0d736-110">説明</span><span class="sxs-lookup"><span data-stu-id="0d736-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d736-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="0d736-111">*SHA*</span></span>|<span data-ttu-id="0d736-112">メソッドの完了後に現在のセキュリティ証明書を指定する文字列オブジェクトの値 (出力パラメーター)</span><span class="sxs-lookup"><span data-stu-id="0d736-112">A string object value (output parameter) that specifies the current security certificate after the method completes.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0d736-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="0d736-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="0d736-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="0d736-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d736-115">解説</span><span class="sxs-lookup"><span data-stu-id="0d736-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d736-116">参照</span><span class="sxs-lookup"><span data-stu-id="0d736-116">See Also</span></span>  
 <span data-ttu-id="0d736-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0d736-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
