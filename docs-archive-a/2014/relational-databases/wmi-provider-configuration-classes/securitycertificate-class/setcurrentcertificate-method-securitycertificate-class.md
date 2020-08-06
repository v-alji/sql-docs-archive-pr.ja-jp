---
title: SetCurrentCertificate メソッド (SecurityCertificate クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4c7065946c858b775e319578eb67c2b7186338f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634359"
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a><span data-ttu-id="f1089-102">SetCurrentCertificate メソッド (SecurityCertificate クラス)</span><span class="sxs-lookup"><span data-stu-id="f1089-102">SetCurrentCertificate Method (SecurityCertificate Class)</span></span>
  <span data-ttu-id="f1089-103">現在のセキュリティ証明書を設定します。</span><span class="sxs-lookup"><span data-stu-id="f1089-103">Sets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1089-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1089-104">Syntax</span></span>  
  
```  
  
object  
.SetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="f1089-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="f1089-105">Parts</span></span>  
 <span data-ttu-id="f1089-106">*object*</span><span class="sxs-lookup"><span data-stu-id="f1089-106">*object*</span></span>  
 <span data-ttu-id="f1089-107">セキュリティ証明書を表す [SecurityCertificate Class] securitycertificate-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f1089-107">A [SecurityCertificate Class]securitycertificate-class.md) object that represents a security certificate.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="f1089-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1089-108">Parameters</span></span>  
  
|<span data-ttu-id="f1089-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1089-109">Parameter</span></span>|<span data-ttu-id="f1089-110">説明</span><span class="sxs-lookup"><span data-stu-id="f1089-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1089-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="f1089-111">*SHA*</span></span>|<span data-ttu-id="f1089-112">必要なセキュリティ証明書に対応する SHA (secure hash algorithm) サムプリントを指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="f1089-112">A string value that specifies the secure hash algorithm (SHA) thumbprint for the required security certificate.</span></span>|  
|<span data-ttu-id="f1089-113">*SQLInstance*</span><span class="sxs-lookup"><span data-stu-id="f1089-113">*SQLInstance*</span></span>|<span data-ttu-id="f1089-114">証明書を必要とするインスタンスを指定する文字列値</span><span class="sxs-lookup"><span data-stu-id="f1089-114">A string value that specifies the instance for which the certificate is required.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f1089-115">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="f1089-115">Property Value/Return Value</span></span>  
 <span data-ttu-id="f1089-116">uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="f1089-116">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1089-117">解説</span><span class="sxs-lookup"><span data-stu-id="f1089-117">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1089-118">参照</span><span class="sxs-lookup"><span data-stu-id="f1089-118">See Also</span></span>  
 <span data-ttu-id="f1089-119">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f1089-119">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
