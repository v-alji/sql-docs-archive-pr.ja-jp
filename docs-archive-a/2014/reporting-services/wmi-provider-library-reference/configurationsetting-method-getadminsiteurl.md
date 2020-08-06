---
title: GetAdminSiteUrl メソッド (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cae1a6f7e363ddce8c47c00eb5ef25fc832e59c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639877"
---
# <a name="getadminsiteurl-method-wmi"></a><span data-ttu-id="526d3-102">GetAdminSiteUrl メソッド (WMI)</span><span class="sxs-lookup"><span data-stu-id="526d3-102">GetAdminSiteUrl Method (WMI)</span></span>
  <span data-ttu-id="526d3-103">レポート サーバーが統合されている Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ファームのサーバー管理 Web サイトの絶対 URL を取得します。</span><span class="sxs-lookup"><span data-stu-id="526d3-103">Gets the absolute URL for the Central Administration Web site for the Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] farm that the report server is integrated with.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="526d3-104">Syntax</span></span>  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="526d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="526d3-105">Parameters</span></span>  
 <span data-ttu-id="526d3-106">*AdminSiteUrl*</span><span class="sxs-lookup"><span data-stu-id="526d3-106">*AdminSiteUrl*</span></span>  
 <span data-ttu-id="526d3-107">[out] レポート サーバーが統合されている SharePoint ファームのサーバー管理 Web サイトの絶対 URL を表す文字列。</span><span class="sxs-lookup"><span data-stu-id="526d3-107">[out] A string that contains the absolute URL for the Central Administration Web site for the SharePoint farm that the report server is integrated with.</span></span>  
  
 <span data-ttu-id="526d3-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="526d3-108">*HRESULT*</span></span>  
 <span data-ttu-id="526d3-109">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="526d3-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="526d3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="526d3-110">Return Value</span></span>  
 <span data-ttu-id="526d3-111">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="526d3-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="526d3-112">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="526d3-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="526d3-113">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="526d3-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="526d3-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="526d3-114">Requirements</span></span>  
 <span data-ttu-id="526d3-115">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="526d3-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526d3-116">参照</span><span class="sxs-lookup"><span data-stu-id="526d3-116">See Also</span></span>  
 [<span data-ttu-id="526d3-117">MSReportServer_ConfigurationSetting Methods</span><span class="sxs-lookup"><span data-stu-id="526d3-117">MSReportServer_ConfigurationSetting Methods</span></span>](msreportserver-configurationsetting-methods.md)  
  
  
