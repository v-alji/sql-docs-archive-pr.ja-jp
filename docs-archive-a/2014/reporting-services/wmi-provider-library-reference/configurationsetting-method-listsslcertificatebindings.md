---
title: ListSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56b19a138dc95b94a20183909dd444c90b158b26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639864"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ed268-102">ListSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ed268-102">ListSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ed268-103">コンピューターにインストールされている SSL 証明書の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="ed268-103">Returns a list of installed SSL certificates on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed268-104">構文</span><span class="sxs-lookup"><span data-stu-id="ed268-104">Syntax</span></span>  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed268-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed268-105">Parameters</span></span>  
 <span data-ttu-id="ed268-106">*LCID*</span><span class="sxs-lookup"><span data-stu-id="ed268-106">*LCID*</span></span>  
 <span data-ttu-id="ed268-107">返されるエラー メッセージに使用するロケール。</span><span class="sxs-lookup"><span data-stu-id="ed268-107">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="ed268-108">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="ed268-108">*Application[]*</span></span>  
 <span data-ttu-id="ed268-109">[out] 証明書のバインドを含むアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="ed268-109">[out] The applications that have certificate bindings.</span></span>  
  
 <span data-ttu-id="ed268-110">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="ed268-110">*CertificateHash[]*</span></span>  
 <span data-ttu-id="ed268-111">[out] 証明書のハッシュ。</span><span class="sxs-lookup"><span data-stu-id="ed268-111">[out] The hashes for the certificates.</span></span>  
  
 <span data-ttu-id="ed268-112">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="ed268-112">*IPAddress[]*</span></span>  
 <span data-ttu-id="ed268-113">[out] アプリケーションの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="ed268-113">[out] The IP address for the applications.</span></span>  
  
 <span data-ttu-id="ed268-114">*Port[]*</span><span class="sxs-lookup"><span data-stu-id="ed268-114">*Port[]*</span></span>  
 <span data-ttu-id="ed268-115">[out] rsreportserver.config のバインドに格納されているポート番号。</span><span class="sxs-lookup"><span data-stu-id="ed268-115">[out] The port number stored in the binding in rsreportserver.config.</span></span>  
  
 <span data-ttu-id="ed268-116">*Errors[]*</span><span class="sxs-lookup"><span data-stu-id="ed268-116">*Errors[]*</span></span>  
 <span data-ttu-id="ed268-117">[out] 発生したエラーの説明。</span><span class="sxs-lookup"><span data-stu-id="ed268-117">[out] The descriptions for errors that occurred.</span></span>  
  
 <span data-ttu-id="ed268-118">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="ed268-118">*Length*</span></span>  
 <span data-ttu-id="ed268-119">[out] メソッドによって返される配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="ed268-119">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="ed268-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ed268-120">*HRESULT*</span></span>  
 <span data-ttu-id="ed268-121">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="ed268-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed268-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="ed268-122">Return Value</span></span>  
 <span data-ttu-id="ed268-123">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="ed268-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ed268-124">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ed268-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="ed268-125">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ed268-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed268-126">解説</span><span class="sxs-lookup"><span data-stu-id="ed268-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed268-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="ed268-127">Requirements</span></span>  
 <span data-ttu-id="ed268-128">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed268-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed268-129">参照</span><span class="sxs-lookup"><span data-stu-id="ed268-129">See Also</span></span>  
 [<span data-ttu-id="ed268-130">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="ed268-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
