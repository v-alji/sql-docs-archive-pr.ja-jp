---
title: ListInstalledSharePointVersions メソッド (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ceee23876461cf31cbd265ea39ae015ddcbc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639875"
---
# <a name="listinstalledsharepointversions-method-wmi"></a><span data-ttu-id="9d27c-102">ListInstalledSharePointVersions メソッド (WMI)</span><span class="sxs-lookup"><span data-stu-id="9d27c-102">ListInstalledSharePointVersions Method (WMI)</span></span>
  <span data-ttu-id="9d27c-103">レポート サーバーと同じコンピューターにインストールされた Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] のバージョンを表すトークンのセットを返します。</span><span class="sxs-lookup"><span data-stu-id="9d27c-103">Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] that are installed on the same computer as the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d27c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d27c-104">Syntax</span></span>  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d27c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d27c-105">Parameters</span></span>  
 <span data-ttu-id="9d27c-106">*VersionTokens[]*</span><span class="sxs-lookup"><span data-stu-id="9d27c-106">*VersionTokens[]*</span></span>  
 <span data-ttu-id="9d27c-107">[out] インストールされたレポート サーバーと互換性がある SharePoint 製品またはテクノロジのバージョンを表すトークンを含む配列。</span><span class="sxs-lookup"><span data-stu-id="9d27c-107">[out] An array that contains the tokens that represent the version of a SharePoint product or technology that is compatible with the installed report server.</span></span>  
  
 <span data-ttu-id="9d27c-108">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="9d27c-108">*Length*</span></span>  
 <span data-ttu-id="9d27c-109">[out] バージョン トークンの配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="9d27c-109">[out] The length of the version tokens array.</span></span>  
  
 <span data-ttu-id="9d27c-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="9d27c-110">*HRESULT*</span></span>  
 <span data-ttu-id="9d27c-111">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="9d27c-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d27c-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="9d27c-112">Return Value</span></span>  
 <span data-ttu-id="9d27c-113">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="9d27c-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="9d27c-114">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9d27c-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="9d27c-115">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9d27c-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d27c-116">解説</span><span class="sxs-lookup"><span data-stu-id="9d27c-116">Remarks</span></span>  
 <span data-ttu-id="9d27c-117">返される各トークンは、現在インストールされているレポート サーバーと互換性がある [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] または [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d27c-117">Each token that is returned represents a version of [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] or [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] that is compatible with the currently installed report server.</span></span> <span data-ttu-id="9d27c-118">SharePoint の特定のバージョンに、それよりも前の SharePoint バージョンとの互換性がある場合は、互換性がある各 SharePoint バージョンのトークンが返されます。</span><span class="sxs-lookup"><span data-stu-id="9d27c-118">If a particular version of SharePoint is compatible with previous SharePoint versions, tokens for each compatible SharePoint version are returned.</span></span>  
  
 <span data-ttu-id="9d27c-119">次の表は、返される SharePoint のトークンを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d27c-119">The following is a table of the SharePoint tokens that are returned.</span></span>  
  
|<span data-ttu-id="9d27c-120">**バージョン トークン**</span><span class="sxs-lookup"><span data-stu-id="9d27c-120">**Version Tokens**</span></span>|<span data-ttu-id="9d27c-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="9d27c-121">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="9d27c-122">WSS_V2_Compatible</span><span class="sxs-lookup"><span data-stu-id="9d27c-122">WSS_V2_Compatible</span></span>|<span data-ttu-id="9d27c-123">[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]2.0 と互換性がある [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 、または [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="9d27c-123">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0.</span></span>|  
|<span data-ttu-id="9d27c-124">WSS_V3_Compatible</span><span class="sxs-lookup"><span data-stu-id="9d27c-124">WSS_V3_Compatible</span></span>|<span data-ttu-id="9d27c-125">[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]3.0 と互換性がある [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 、または [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="9d27c-125">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0.</span></span>|  
|<span data-ttu-id="9d27c-126">WSS_V4_Compatible</span><span class="sxs-lookup"><span data-stu-id="9d27c-126">WSS_V4_Compatible</span></span>|<span data-ttu-id="9d27c-127">Office 14 と互換性がある [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="9d27c-127">A [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with Office 14.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d27c-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="9d27c-128">Requirements</span></span>  
 <span data-ttu-id="9d27c-129">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d27c-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d27c-130">参照</span><span class="sxs-lookup"><span data-stu-id="9d27c-130">See Also</span></span>  
 [<span data-ttu-id="9d27c-131">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="9d27c-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
