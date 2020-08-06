---
title: RemoveSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d42d17d9c92f2e100a7800e607536ff6c7eab891
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720937"
---
# <a name="removesslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="f97ba-102">RemoveSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="f97ba-102">RemoveSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="f97ba-103">SSL 証明書のバインドを削除します。</span><span class="sxs-lookup"><span data-stu-id="f97ba-103">Removes an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="f97ba-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f97ba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f97ba-105">Parameters</span></span>  
 <span data-ttu-id="f97ba-106">*Application*</span><span class="sxs-lookup"><span data-stu-id="f97ba-106">*Application*</span></span>  
 <span data-ttu-id="f97ba-107">証明書のバインドを削除する必要のあるアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="f97ba-107">The name of application for which the certificate binding should be removed.</span></span>  
  
 <span data-ttu-id="f97ba-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="f97ba-108">*CertificateHash*</span></span>  
 <span data-ttu-id="f97ba-109">証明書のハッシュ。</span><span class="sxs-lookup"><span data-stu-id="f97ba-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="f97ba-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="f97ba-110">*IPAddress*</span></span>  
 <span data-ttu-id="f97ba-111">アプリケーションの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="f97ba-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="f97ba-112">*[ポート]*</span><span class="sxs-lookup"><span data-stu-id="f97ba-112">*Port*</span></span>  
 <span data-ttu-id="f97ba-113">バインドに関連付けられた SSL ポート。</span><span class="sxs-lookup"><span data-stu-id="f97ba-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="f97ba-114">*lcid*</span><span class="sxs-lookup"><span data-stu-id="f97ba-114">*lcid*</span></span>  
 <span data-ttu-id="f97ba-115">返されるエラー メッセージに使用するロケール。</span><span class="sxs-lookup"><span data-stu-id="f97ba-115">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="f97ba-116">*Error*</span><span class="sxs-lookup"><span data-stu-id="f97ba-116">*Error*</span></span>  
 <span data-ttu-id="f97ba-117">[out] 発生したエラーの説明。</span><span class="sxs-lookup"><span data-stu-id="f97ba-117">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="f97ba-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="f97ba-118">*HRESULT*</span></span>  
 <span data-ttu-id="f97ba-119">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="f97ba-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f97ba-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="f97ba-120">Return Value</span></span>  
 <span data-ttu-id="f97ba-121">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="f97ba-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="f97ba-122">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f97ba-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f97ba-123">解説</span><span class="sxs-lookup"><span data-stu-id="f97ba-123">Remarks</span></span>  
 <span data-ttu-id="f97ba-124">このメソッドは、rsreportserver.config ファイルおよび HTTP.SYS (オプション) から特定のバインドを削除します。</span><span class="sxs-lookup"><span data-stu-id="f97ba-124">This method removes the specific binding from the rsreportserver.config file and optionally HTTP.SYS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f97ba-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="f97ba-125">Requirements</span></span>  
 <span data-ttu-id="f97ba-126">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f97ba-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97ba-127">参照</span><span class="sxs-lookup"><span data-stu-id="f97ba-127">See Also</span></span>  
 [<span data-ttu-id="f97ba-128">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="f97ba-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
