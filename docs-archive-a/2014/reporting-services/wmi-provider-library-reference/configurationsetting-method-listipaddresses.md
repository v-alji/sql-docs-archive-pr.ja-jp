---
title: ListIPAddresses メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 845f7ba7db02a0b860f966184463580733af0faf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639873"
---
# <a name="listipaddresses-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="8c2af-102">ListIPAddresses メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="8c2af-102">ListIPAddresses Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="8c2af-103">レポート サーバー コンピューターの IP アドレスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8c2af-103">Lists the IP addresses for the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2af-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c2af-104">Syntax</span></span>  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c2af-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c2af-105">Parameters</span></span>  
 <span data-ttu-id="8c2af-106">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="8c2af-106">*IPAddress[]*</span></span>  
 <span data-ttu-id="8c2af-107">[out] コンピューターの IP アドレスの一覧。</span><span class="sxs-lookup"><span data-stu-id="8c2af-107">[out] The list of IP address for the computer.</span></span>  
  
 <span data-ttu-id="8c2af-108">*IPVersion[]*</span><span class="sxs-lookup"><span data-stu-id="8c2af-108">*IPVersion[]*</span></span>  
 <span data-ttu-id="8c2af-109">[out] IP アドレスのバージョン。</span><span class="sxs-lookup"><span data-stu-id="8c2af-109">[out] The version for the IP addresses.</span></span>  
  
 <span data-ttu-id="8c2af-110">*IsDhcpEnabled[]*</span><span class="sxs-lookup"><span data-stu-id="8c2af-110">*IsDhcpEnabled[]*</span></span>  
 <span data-ttu-id="8c2af-111">[out] IP アドレスが DHCP 対応かどうか。</span><span class="sxs-lookup"><span data-stu-id="8c2af-111">[out] Indicates whether the IP addresses are DHCP enabled.</span></span>  
  
 <span data-ttu-id="8c2af-112">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="8c2af-112">*Length*</span></span>  
 <span data-ttu-id="8c2af-113">[out] メソッドによって返される配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="8c2af-113">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="8c2af-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="8c2af-114">*HRESULT*</span></span>  
 <span data-ttu-id="8c2af-115">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="8c2af-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c2af-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c2af-116">Return Value</span></span>  
 <span data-ttu-id="8c2af-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="8c2af-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="8c2af-118">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8c2af-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c2af-119">解説</span><span class="sxs-lookup"><span data-stu-id="8c2af-119">Remarks</span></span>  
 <span data-ttu-id="8c2af-120">*IPVersion* の文字列は、"V4" または "V6" です。</span><span class="sxs-lookup"><span data-stu-id="8c2af-120">*IPVersion* strings are V4, V6.</span></span>  
  
 <span data-ttu-id="8c2af-121">*IsDhcpEnabled*がの場合 `True` 、 *IPAddress*は動的です。</span><span class="sxs-lookup"><span data-stu-id="8c2af-121">If *IsDhcpEnabled* is `True`, the *IPAddress* is dynamic.</span></span> <span data-ttu-id="8c2af-122">これは、SSL バインドには使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8c2af-122">It should not be used for SSL bindings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c2af-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="8c2af-123">Requirements</span></span>  
 <span data-ttu-id="8c2af-124">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c2af-124">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2af-125">参照</span><span class="sxs-lookup"><span data-stu-id="8c2af-125">See Also</span></span>  
 [<span data-ttu-id="8c2af-126">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="8c2af-126">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
