---
title: GetDatabaseVersionDisplayName メソッド (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b39ce39a4f26964c148631c903869b0234e2b9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639876"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a><span data-ttu-id="841c1-102">GetDatabaseVersionDisplayName メソッド (WMI)</span><span class="sxs-lookup"><span data-stu-id="841c1-102">GetDatabaseVersionDisplayName Method (WMI)</span></span>
  <span data-ttu-id="841c1-103">指定したレポート サーバー データベースのバージョン文字列の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="841c1-103">Gets the display name for a given report server database version string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841c1-104">構文</span><span class="sxs-lookup"><span data-stu-id="841c1-104">Syntax</span></span>  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="841c1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="841c1-105">Parameters</span></span>  
 <span data-ttu-id="841c1-106">*バージョン*</span><span class="sxs-lookup"><span data-stu-id="841c1-106">*Version*</span></span>  
 <span data-ttu-id="841c1-107">レポート サーバー データベースのバージョン文字列を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="841c1-107">A string that contains the version string for a report server database.</span></span>  
  
 <span data-ttu-id="841c1-108">*DisplayName*</span><span class="sxs-lookup"><span data-stu-id="841c1-108">*DisplayName*</span></span>  
 <span data-ttu-id="841c1-109">[out] 指定したバージョンに対応する表示名を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="841c1-109">[out] A string that contains the display name that corresponds to the version supplied.</span></span>  
  
 <span data-ttu-id="841c1-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="841c1-110">*HRESULT*</span></span>  
 <span data-ttu-id="841c1-111">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="841c1-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="841c1-112">解説</span><span class="sxs-lookup"><span data-stu-id="841c1-112">Remarks</span></span>  
 <span data-ttu-id="841c1-113">次の表に、データベース バージョンと表示文字列のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="841c1-113">The following table shows the mapping from database version to display string.</span></span>  
  
|<span data-ttu-id="841c1-114">**リリース**</span><span class="sxs-lookup"><span data-stu-id="841c1-114">**Release**</span></span>|`Version`|<span data-ttu-id="841c1-115">**表示名**</span><span class="sxs-lookup"><span data-stu-id="841c1-115">**Display Name**</span></span>|  
|-----------------|-----------------|----------------------|  
|<span data-ttu-id="841c1-116">RS 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="841c1-116">RS 2005 SP2</span></span>|<span data-ttu-id="841c1-117">@DBVersion = 'C.0.8.54'</span><span class="sxs-lookup"><span data-stu-id="841c1-117">@DBVersion = 'C.0.8.54'</span></span>|<span data-ttu-id="841c1-118">SQL Server 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="841c1-118">SQL Server 2005 SP2</span></span>|  
|<span data-ttu-id="841c1-119">RS 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="841c1-119">RS 2005 SP1</span></span>|<span data-ttu-id="841c1-120">@DBVersion = 'C.0.8.43'</span><span class="sxs-lookup"><span data-stu-id="841c1-120">@DBVersion = 'C.0.8.43'</span></span>|<span data-ttu-id="841c1-121">SQL Server 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="841c1-121">SQL Server 2005 SP1</span></span>|  
|<span data-ttu-id="841c1-122">RS 2005 RTM</span><span class="sxs-lookup"><span data-stu-id="841c1-122">RS 2005 RTM</span></span>|<span data-ttu-id="841c1-123">@DBVersion = 'C.0.8.40'</span><span class="sxs-lookup"><span data-stu-id="841c1-123">@DBVersion = 'C.0.8.40'</span></span>|<span data-ttu-id="841c1-124">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="841c1-124">SQL Server 2005</span></span>|  
|<span data-ttu-id="841c1-125">RS 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="841c1-125">RS 2000 SP2</span></span>|<span data-ttu-id="841c1-126">@DBVersion = 'C.0.6.54'</span><span class="sxs-lookup"><span data-stu-id="841c1-126">@DBVersion = 'C.0.6.54'</span></span>|<span data-ttu-id="841c1-127">SQL Server 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="841c1-127">SQL Server 2000 SP2</span></span>|  
|<span data-ttu-id="841c1-128">RS 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="841c1-128">RS 2000 SP1</span></span>|<span data-ttu-id="841c1-129">@DBVersion = 'C.0.6.51'</span><span class="sxs-lookup"><span data-stu-id="841c1-129">@DBVersion = 'C.0.6.51'</span></span>|<span data-ttu-id="841c1-130">SQL Server 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="841c1-130">SQL Server 2000 SP1</span></span>|  
|<span data-ttu-id="841c1-131">RS 2000 RTM</span><span class="sxs-lookup"><span data-stu-id="841c1-131">RS 2000 RTM</span></span>|<span data-ttu-id="841c1-132">@DBVersion = 'C.0.6.43'</span><span class="sxs-lookup"><span data-stu-id="841c1-132">@DBVersion = 'C.0.6.43'</span></span>|<span data-ttu-id="841c1-133">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="841c1-133">SQL Server 2000</span></span>|  
|<span data-ttu-id="841c1-134">修正プログラム</span><span class="sxs-lookup"><span data-stu-id="841c1-134">Hotfix</span></span>||<span data-ttu-id="841c1-135">最も近い適用可能なバージョン</span><span class="sxs-lookup"><span data-stu-id="841c1-135">Closest applicable version</span></span>|  
  
 <span data-ttu-id="841c1-136">*2000 より前の* Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、HRESULT として ACT_E_BAD_VERSION が返されます。</span><span class="sxs-lookup"><span data-stu-id="841c1-136">For a *Version* prior to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 an HRESULT of ACT_E_BAD_VERSION is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="841c1-137">戻り値</span><span class="sxs-lookup"><span data-stu-id="841c1-137">Return Value</span></span>  
 <span data-ttu-id="841c1-138">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="841c1-138">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="841c1-139">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="841c1-139">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="841c1-140">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="841c1-140">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="841c1-141">必要条件</span><span class="sxs-lookup"><span data-stu-id="841c1-141">Requirements</span></span>  
 <span data-ttu-id="841c1-142">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="841c1-142">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841c1-143">参照</span><span class="sxs-lookup"><span data-stu-id="841c1-143">See Also</span></span>  
 [<span data-ttu-id="841c1-144">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="841c1-144">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
