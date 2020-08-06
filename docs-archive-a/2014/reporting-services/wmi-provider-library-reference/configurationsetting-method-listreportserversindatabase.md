---
title: ListReportServersInDatabase メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9eaea72c0737124d89c86b55281326073597fb38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639872"
---
# <a name="listreportserversindatabase-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ee5c2-102">ListReportServersInDatabase メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ee5c2-102">ListReportServersInDatabase Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ee5c2-103">セキュリティで保護された情報にアクセスできるかどうかに関係なく、レポート サーバー データベースにあるレポート サーバー インストールの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-103">Returns the list of report server installations that are present in the report server database, regardless of whether they have access to secure information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee5c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee5c2-104">Syntax</span></span>  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee5c2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee5c2-105">Parameters</span></span>  
 <span data-ttu-id="ee5c2-106">*MachineNames[]*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-106">*MachineNames[]*</span></span>  
 <span data-ttu-id="ee5c2-107">[out] データベースのレポート サーバーのコンピューター名を含む配列。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-107">[out] An array containing the machine names for the report server installations in the database.</span></span>  
  
 <span data-ttu-id="ee5c2-108">*InstanceNames[]*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-108">*InstanceNames[]*</span></span>  
 <span data-ttu-id="ee5c2-109">[out] データベースの各レポート サーバーのインスタンス名を含む配列。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-109">[out] An array containing the instance names of each of the report server installations in the database.</span></span>  
  
 <span data-ttu-id="ee5c2-110">*InstallationIDs[]*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-110">*InstallationIDs[]*</span></span>  
 <span data-ttu-id="ee5c2-111">[out] データベースの各レポート サーバーのインストール ID を含む配列。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-111">[out] An array containing the installation IDs of each report server installation in the database.</span></span>  
  
 <span data-ttu-id="ee5c2-112">*IsInitialized[]*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-112">*IsInitialized[]*</span></span>  
 <span data-ttu-id="ee5c2-113">[out] データベースの各レポート サーバーの初期化状態を含む配列。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-113">[out] An array containing initialization status for each report server installation in the database.</span></span>  
  
 <span data-ttu-id="ee5c2-114">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-114">*Length*</span></span>  
 <span data-ttu-id="ee5c2-115">[out] メソッドによって返される配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-115">[out] The length of the arrays returned by the method.</span></span> <span data-ttu-id="ee5c2-116">返されるすべての配列が同じ長さになります。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-116">All returned arrays have the same length.</span></span>  
  
 <span data-ttu-id="ee5c2-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-117">*HRESULT*</span></span>  
 <span data-ttu-id="ee5c2-118">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="ee5c2-119">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="ee5c2-119">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="ee5c2-120">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-120">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee5c2-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="ee5c2-121">Return Value</span></span>  
 <span data-ttu-id="ee5c2-122">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-122">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ee5c2-123">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-123">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="ee5c2-124">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-124">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee5c2-125">解説</span><span class="sxs-lookup"><span data-stu-id="ee5c2-125">Remarks</span></span>  
 <span data-ttu-id="ee5c2-126">ListReportServersInDatabase は、セキュリティで保護された情報にアクセスできるかどうかに関係なく、レポート サーバー データベースにあるレポート サーバーの一覧を作成し、各レポート サーバーに関する情報を含む配列セットを返します。</span><span class="sxs-lookup"><span data-stu-id="ee5c2-126">ListReportServersInDatabase lists the report server installations that are present in the report server database, regardless of whether they have access to secure information, and returns a matched set of arrays containing information about each installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee5c2-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="ee5c2-127">Requirements</span></span>  
 <span data-ttu-id="ee5c2-128">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee5c2-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5c2-129">参照</span><span class="sxs-lookup"><span data-stu-id="ee5c2-129">See Also</span></span>  
 [<span data-ttu-id="ee5c2-130">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="ee5c2-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
