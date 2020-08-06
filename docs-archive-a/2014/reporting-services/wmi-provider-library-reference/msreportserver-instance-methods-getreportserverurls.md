---
title: GetReportServerUrls メソッド (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f36a5ba10c05276cffabc155e5289d675db8dae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717319"
---
# <a name="getreportserverurls-method-wmi-msreportserver_instance"></a><span data-ttu-id="831e3-102">GetReportServerUrls メソッド (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="831e3-102">GetReportServerUrls Method (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="831e3-103">ユーザーがレポート サーバーおよびレポート マネージャーへのアクセスに使用できる URL の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="831e3-103">Returns a list of URLs users can use to access the report server and report manager.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="831e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="831e3-104">Syntax</span></span>  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="831e3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="831e3-105">Parameters</span></span>  
 <span data-ttu-id="831e3-106">*ApplicationName[]*</span><span class="sxs-lookup"><span data-stu-id="831e3-106">*ApplicationName[]*</span></span>  
 <span data-ttu-id="831e3-107">インストールされているアプリケーションを含む配列。</span><span class="sxs-lookup"><span data-stu-id="831e3-107">An array that contains the applications that are installed.</span></span> <span data-ttu-id="831e3-108">値は `ReportServerWebService` または `ReportManager` です。</span><span class="sxs-lookup"><span data-stu-id="831e3-108">Values are either `ReportServerWebService` or `ReportManager`.</span></span>  
  
 <span data-ttu-id="831e3-109">*URLs[]*</span><span class="sxs-lookup"><span data-stu-id="831e3-109">*URLs[]*</span></span>  
 <span data-ttu-id="831e3-110">正常に登録された URL を含む配列。</span><span class="sxs-lookup"><span data-stu-id="831e3-110">An array that contains the successfully registered Urls.</span></span>  
  
 <span data-ttu-id="831e3-111">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="831e3-111">*Length*</span></span>  
 <span data-ttu-id="831e3-112">返された配列の長さを含む整数値。</span><span class="sxs-lookup"><span data-stu-id="831e3-112">An integer value that contains the length of the arrays returned.</span></span>  
  
 <span data-ttu-id="831e3-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="831e3-113">*HRESULT*</span></span>  
 <span data-ttu-id="831e3-114">成功を表す値またはエラー コード。</span><span class="sxs-lookup"><span data-stu-id="831e3-114">A value that indicates success or an error code.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="831e3-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="831e3-115">Return Values</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="831e3-116">解説</span><span class="sxs-lookup"><span data-stu-id="831e3-116">Remarks</span></span>  
 <span data-ttu-id="831e3-117">WMI 管理オブジェクトによって公開されるメソッドは、InvokeMethod 関数によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="831e3-117">Methods exposed by WMI management objects are called through the InvokeMethod function.</span></span> <span data-ttu-id="831e3-118">詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI ドキュメントの「管理オブジェクトのメソッドの実行」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="831e3-118">For more information, please see "Executing Methods on Management Objects" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="831e3-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="831e3-119">Requirements</span></span>  
 <span data-ttu-id="831e3-120">**名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="831e3-120">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831e3-121">参照</span><span class="sxs-lookup"><span data-stu-id="831e3-121">See Also</span></span>  
 [<span data-ttu-id="831e3-122">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="831e3-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
