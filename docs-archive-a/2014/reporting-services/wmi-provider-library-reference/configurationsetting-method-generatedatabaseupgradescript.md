---
title: GenerateDatabaseUpgradeScript メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseUpgradeScript method
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a619584b9f1cc095f8f624670386d388426e4a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639878"
---
# <a name="generatedatabaseupgradescript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="99fc2-102">GenerateDatabaseUpgradeScript メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="99fc2-102">GenerateDatabaseUpgradeScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="99fc2-103">レポート サーバー データベースを [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] スキーマにアップグレードする場合に使用できるスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="99fc2-103">Generates a script that can be used to upgrade the report server database to the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fc2-104">構文</span><span class="sxs-lookup"><span data-stu-id="99fc2-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99fc2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99fc2-105">Parameters</span></span>  
 <span data-ttu-id="99fc2-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="99fc2-106">*Databasename*</span></span>  
 <span data-ttu-id="99fc2-107">更新するレポート サーバー データベースの名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="99fc2-107">A string containing the name of the report server database to upgrade.</span></span>  
  
 <span data-ttu-id="99fc2-108">*ServerVersion*</span><span class="sxs-lookup"><span data-stu-id="99fc2-108">*ServerVersion*</span></span>  
 <span data-ttu-id="99fc2-109">レポート サーバーのバージョンを表す文字列。</span><span class="sxs-lookup"><span data-stu-id="99fc2-109">A string containing the version of the report server.</span></span>  
  
 <span data-ttu-id="99fc2-110">*[スクリプト]*</span><span class="sxs-lookup"><span data-stu-id="99fc2-110">*Script*</span></span>  
 <span data-ttu-id="99fc2-111">[out] 生成された SQL スクリプトを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="99fc2-111">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="99fc2-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="99fc2-112">*HRESULT*</span></span>  
 <span data-ttu-id="99fc2-113">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="99fc2-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99fc2-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="99fc2-114">Return Value</span></span>  
 <span data-ttu-id="99fc2-115">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="99fc2-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="99fc2-116">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="99fc2-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="99fc2-117">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="99fc2-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99fc2-118">解説</span><span class="sxs-lookup"><span data-stu-id="99fc2-118">Remarks</span></span>  
 <span data-ttu-id="99fc2-119">生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。</span><span class="sxs-lookup"><span data-stu-id="99fc2-119">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fc2-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="99fc2-120">Requirements</span></span>  
 <span data-ttu-id="99fc2-121">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fc2-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fc2-122">参照</span><span class="sxs-lookup"><span data-stu-id="99fc2-122">See Also</span></span>  
 [<span data-ttu-id="99fc2-123">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="99fc2-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
