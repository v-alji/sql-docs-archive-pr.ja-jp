---
title: CreateSSLCertificateBinding メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b9a5f9394d655f7b0592ea688a46f3ac2b9c153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639892"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="e6827-102">CreateSSLCertificateBinding メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="e6827-102">CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="e6827-103">SSL 証明書のバインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="e6827-103">Creates an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6827-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6827-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6827-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e6827-105">Parameters</span></span>  
 <span data-ttu-id="e6827-106">*Application*</span><span class="sxs-lookup"><span data-stu-id="e6827-106">*Application*</span></span>  
 <span data-ttu-id="e6827-107">証明書のバインドを作成する必要があるアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="e6827-107">The name of application that the certificate binding should be created for.</span></span>  
  
 <span data-ttu-id="e6827-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="e6827-108">*CertificateHash*</span></span>  
 <span data-ttu-id="e6827-109">証明書のハッシュ。</span><span class="sxs-lookup"><span data-stu-id="e6827-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="e6827-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="e6827-110">*IPAddress*</span></span>  
 <span data-ttu-id="e6827-111">アプリケーションの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="e6827-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="e6827-112">*[ポート]*</span><span class="sxs-lookup"><span data-stu-id="e6827-112">*Port*</span></span>  
 <span data-ttu-id="e6827-113">バインドに関連付けられた SSL ポート。</span><span class="sxs-lookup"><span data-stu-id="e6827-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="e6827-114">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="e6827-114">*Lcid*</span></span>  
 <span data-ttu-id="e6827-115">返されるエラー メッセージに使用するロケール。</span><span class="sxs-lookup"><span data-stu-id="e6827-115">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="e6827-116">*Error*</span><span class="sxs-lookup"><span data-stu-id="e6827-116">*Error*</span></span>  
 <span data-ttu-id="e6827-117">[out] 発生したエラーの説明。</span><span class="sxs-lookup"><span data-stu-id="e6827-117">[out] The description of the errors that occurred.</span></span>  
  
 <span data-ttu-id="e6827-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="e6827-118">*HRESULT*</span></span>  
 <span data-ttu-id="e6827-119">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="e6827-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6827-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="e6827-120">Return Value</span></span>  
 <span data-ttu-id="e6827-121">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="e6827-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="e6827-122">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6827-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6827-123">解説</span><span class="sxs-lookup"><span data-stu-id="e6827-123">Remarks</span></span>  
 <span data-ttu-id="e6827-124">このメソッドは、アプリケーションの rsreportserver.config にバインドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e6827-124">This method adds a binding to rsreportserver.config for the application.</span></span> <span data-ttu-id="e6827-125">バインドが HTTP.SYS に存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6827-125">If a binding does not already exist in HTTP.SYS, it is created there.</span></span>  
  
 <span data-ttu-id="e6827-126">バインドを作成する前に、メソッドの呼び出しによって、指定されたアプリケーションの URL 予約が調査され、SSL 証明書のバインドが有効かどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="e6827-126">Before creating the binding, the method call examines the Url Reservations for the specified application to determine if the SSL Certificate Binding is valid.</span></span>  
  
 <span data-ttu-id="e6827-127">次の条件が検証されて、その結果エラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6827-127">The following conditions are validated and can result in errors:</span></span>  
  
1.  <span data-ttu-id="e6827-128">証明書が存在しない。</span><span class="sxs-lookup"><span data-stu-id="e6827-128">Certificate does not exist.</span></span>  
  
2.  <span data-ttu-id="e6827-129">指定された IP アドレスがこのコンピューターの IP アドレスと一致しない。</span><span class="sxs-lookup"><span data-stu-id="e6827-129">The IPAddress specified does not correspond to an IPAddress of this computer.</span></span>  
  
3.  <span data-ttu-id="e6827-130">指定された IP アドレスが DHCP の IP アドレス (定期的に変更される) であるため、代わりにワイルドカードの IP アドレス (0.0.0.0) が使用されている。</span><span class="sxs-lookup"><span data-stu-id="e6827-130">The IPAddress specified is a DHCP IPAddress (changes periodically) - use the Wildcard IP address instead (0.0.0.0).</span></span>  
  
4.  <span data-ttu-id="e6827-131">指定された IP アドレスが URL 予約の IP アドレスと一致せず、ワイルドカードまたはホスト名の URL 予約も存在しない。</span><span class="sxs-lookup"><span data-stu-id="e6827-131">IPAddress specified does not match the IP address of a URL reservations AND neither a wildcard or host name URL reservation exist.</span></span>  
  
5.  <span data-ttu-id="e6827-132">ホスト名を指定する URL 予約は存在するが、ホスト名が証明書のホスト名と一致しない。</span><span class="sxs-lookup"><span data-stu-id="e6827-132">A URL reservation that specifies a host name exists, but the host name does not match the certificate host name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6827-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="e6827-133">Requirements</span></span>  
 <span data-ttu-id="e6827-134">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6827-134">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6827-135">参照</span><span class="sxs-lookup"><span data-stu-id="e6827-135">See Also</span></span>  
 [<span data-ttu-id="e6827-136">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="e6827-136">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
