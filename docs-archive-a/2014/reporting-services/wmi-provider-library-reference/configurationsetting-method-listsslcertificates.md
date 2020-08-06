---
title: ListSSLCertificates メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a5ced8371817adc44bbbc89400dc83e0dfccef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639861"
---
# <a name="listsslcertificates-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="33f3c-102">ListSSLCertificates メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="33f3c-102">ListSSLCertificates Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="33f3c-103">レポート サーバー コンピューター上にある証明書の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="33f3c-103">Returns a list of certificates on the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="33f3c-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f3c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33f3c-105">Parameters</span></span>  
 <span data-ttu-id="33f3c-106">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="33f3c-106">*CertificateHash[]*</span></span>  
 <span data-ttu-id="33f3c-107">[out] 証明書ハッシュ。</span><span class="sxs-lookup"><span data-stu-id="33f3c-107">[out] The certificate hashes.</span></span>  
  
 <span data-ttu-id="33f3c-108">*CertName[]*</span><span class="sxs-lookup"><span data-stu-id="33f3c-108">*CertName[]*</span></span>  
 <span data-ttu-id="33f3c-109">[out] 証明書の名前。</span><span class="sxs-lookup"><span data-stu-id="33f3c-109">[out] Names of the certificate.</span></span>  
  
 <span data-ttu-id="33f3c-110">*HostName[]*</span><span class="sxs-lookup"><span data-stu-id="33f3c-110">*HostName[]*</span></span>  
 <span data-ttu-id="33f3c-111">[out] 証明書のホスト名。</span><span class="sxs-lookup"><span data-stu-id="33f3c-111">[out] The host names for the certificates.</span></span>  
  
 <span data-ttu-id="33f3c-112">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="33f3c-112">*Length*</span></span>  
 <span data-ttu-id="33f3c-113">[out] *CertificateHash*配列、 *CertName* 配列、および *HostName* 配列の長さを表します。</span><span class="sxs-lookup"><span data-stu-id="33f3c-113">[out] Represents the length of the *CertificateHash*, *CertName* and *HostName* arrays.</span></span>  
  
 <span data-ttu-id="33f3c-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="33f3c-114">*HRESULT*</span></span>  
 <span data-ttu-id="33f3c-115">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="33f3c-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33f3c-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="33f3c-116">Return Value</span></span>  
 <span data-ttu-id="33f3c-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="33f3c-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="33f3c-118">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="33f3c-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33f3c-119">解説</span><span class="sxs-lookup"><span data-stu-id="33f3c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f3c-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="33f3c-120">Requirements</span></span>  
 <span data-ttu-id="33f3c-121">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33f3c-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f3c-122">参照</span><span class="sxs-lookup"><span data-stu-id="33f3c-122">See Also</span></span>  
 [<span data-ttu-id="33f3c-123">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="33f3c-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
