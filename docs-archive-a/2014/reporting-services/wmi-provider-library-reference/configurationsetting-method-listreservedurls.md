---
title: ListReservedURLs メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7639741adb0c756961c4c6b63a3bffb627c4a89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639870"
---
# <a name="listreservedurls-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="c48e3-102">ListReservedURLs メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="c48e3-102">ListReservedURLs Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="c48e3-103">レポート サーバー上のすべてのアプリケーション用に予約されている URL を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c48e3-103">Lists URLs reserved for all applications on the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c48e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="c48e3-104">Syntax</span></span>  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c48e3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c48e3-105">Parameters</span></span>  
 <span data-ttu-id="c48e3-106">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="c48e3-106">*Application[]*</span></span>  
 <span data-ttu-id="c48e3-107">[out] URL を予約しているアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c48e3-107">[out] The applications that have URL reservations.</span></span>  
  
 <span data-ttu-id="c48e3-108">*UrlString[]*</span><span class="sxs-lookup"><span data-stu-id="c48e3-108">*UrlString[]*</span></span>  
 <span data-ttu-id="c48e3-109">[out] 予約されている URL。</span><span class="sxs-lookup"><span data-stu-id="c48e3-109">[out] The URLs that are reserved.</span></span>  
  
 <span data-ttu-id="c48e3-110">*Account[]*</span><span class="sxs-lookup"><span data-stu-id="c48e3-110">*Account[]*</span></span>  
 <span data-ttu-id="c48e3-111">[out] URL 予約のアカウントに関連付けられているアカウント名。</span><span class="sxs-lookup"><span data-stu-id="c48e3-111">[out] The account names associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="c48e3-112">*AccountSID[]*</span><span class="sxs-lookup"><span data-stu-id="c48e3-112">*AccountSID[]*</span></span>  
 <span data-ttu-id="c48e3-113">[out] URL 予約のアカウントに関連付けられているアカウントの SID。</span><span class="sxs-lookup"><span data-stu-id="c48e3-113">[out] The account SIDs associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="c48e3-114">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="c48e3-114">*Length*</span></span>  
 <span data-ttu-id="c48e3-115">[out] メソッドによって返される配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="c48e3-115">[out] The length of the arrays returned by the method.</span></span>  
  
 <span data-ttu-id="c48e3-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="c48e3-116">*HRESULT*</span></span>  
 <span data-ttu-id="c48e3-117">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="c48e3-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c48e3-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="c48e3-118">Return Value</span></span>  
 <span data-ttu-id="c48e3-119">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="c48e3-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="c48e3-120">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c48e3-120">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c48e3-121">解説</span><span class="sxs-lookup"><span data-stu-id="c48e3-121">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c48e3-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="c48e3-122">Requirements</span></span>  
 <span data-ttu-id="c48e3-123">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c48e3-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48e3-124">参照</span><span class="sxs-lookup"><span data-stu-id="c48e3-124">See Also</span></span>  
 [<span data-ttu-id="c48e3-125">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="c48e3-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
