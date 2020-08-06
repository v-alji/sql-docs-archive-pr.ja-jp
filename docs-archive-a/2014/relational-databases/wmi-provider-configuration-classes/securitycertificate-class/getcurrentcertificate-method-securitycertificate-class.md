---
title: GetCurrentCertificate メソッド (SecurityCertificate クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ab96b2e2a8fabf9e9ccce647e54be1983fe40ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712957"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a><span data-ttu-id="a35a9-102">GetCurrentCertificate メソッド (SecurityCertificate クラス)</span><span class="sxs-lookup"><span data-stu-id="a35a9-102">GetCurrentCertificate Method (SecurityCertificate Class)</span></span>
  <span data-ttu-id="a35a9-103">現在のセキュリティ証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="a35a9-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="a35a9-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a35a9-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a35a9-105">Parts</span></span>  
 <span data-ttu-id="a35a9-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a35a9-106">*object*</span></span>  
 <span data-ttu-id="a35a9-107">セキュリティ証明書を表す [SecurityCertificate クラス](securitycertificate-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a35a9-107">A [SecurityCertificate Class](securitycertificate-class.md) object that represents a security certificate.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a35a9-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a35a9-108">Parameters</span></span>  
  
|<span data-ttu-id="a35a9-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a35a9-109">Parameter</span></span>|<span data-ttu-id="a35a9-110">説明</span><span class="sxs-lookup"><span data-stu-id="a35a9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a35a9-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="a35a9-111">*SHA*</span></span>|<span data-ttu-id="a35a9-112">メソッドの完了後に現在のセキュリティ証明書 SHA サムプリントを指定する文字列値 (出力パラメーター)</span><span class="sxs-lookup"><span data-stu-id="a35a9-112">A string value (output parameter) that specifies the current security certificate SHA thumbprint after the method completes.</span></span>|  
|<span data-ttu-id="a35a9-113">*SQLInstance*</span><span class="sxs-lookup"><span data-stu-id="a35a9-113">*SQLInstance*</span></span>|<span data-ttu-id="a35a9-114">証明書を必要とするインスタンスを指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="a35a9-114">A string value that specifies the instance for which the certificate is required.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a35a9-115">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="a35a9-115">Property Value/Return Value</span></span>  
 <span data-ttu-id="a35a9-116">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="a35a9-116">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a35a9-117">解説</span><span class="sxs-lookup"><span data-stu-id="a35a9-117">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35a9-118">参照</span><span class="sxs-lookup"><span data-stu-id="a35a9-118">See Also</span></span>  
 <span data-ttu-id="a35a9-119">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a35a9-119">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
