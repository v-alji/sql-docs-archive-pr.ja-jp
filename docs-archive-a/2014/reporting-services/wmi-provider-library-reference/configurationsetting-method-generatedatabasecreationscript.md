---
title: GenerateDatabaseCreationScript メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639881"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7f961-102">GenerateDatabaseCreationScript メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7f961-102">GenerateDatabaseCreationScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7f961-103">レポート サーバー データベースの作成で使用する SQL スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="7f961-103">Generates a SQL Script that can be used to create a report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f961-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f961-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f961-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f961-105">Parameters</span></span>  
 <span data-ttu-id="7f961-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="7f961-106">*Databasename*</span></span>  
 <span data-ttu-id="7f961-107">作成するレポート サーバー データベースの名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="7f961-107">A string containing the name of the report server database to create.</span></span>  
  
 <span data-ttu-id="7f961-108">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="7f961-108">*Lcid*</span></span>  
 <span data-ttu-id="7f961-109">ロール名のローカライズに使用される値。</span><span class="sxs-lookup"><span data-stu-id="7f961-109">Value used for localization of role names.</span></span>  
  
 <span data-ttu-id="7f961-110">*IsSharePointMode*</span><span class="sxs-lookup"><span data-stu-id="7f961-110">*IsSharePointMode*</span></span>  
 <span data-ttu-id="7f961-111">ネイティブ モードと SharePoint 統合モードのどちらでデータベースを作成するかを示します。</span><span class="sxs-lookup"><span data-stu-id="7f961-111">Indicates whether to create database in native mode or SharePoint mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7f961-112">以降では [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 、 *issharepointmode*はサポートされて = `True` いません。 sharepoint モードでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は sharepoint 共有サービスであり、WMI プロバイダーによって制御されないためです。</span><span class="sxs-lookup"><span data-stu-id="7f961-112">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode*=`True` is not supported because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is a SharePoint shared service and is not controlled by the WMI provider.</span></span> <span data-ttu-id="7f961-113">このパラメーターは常に `False` に設定してください。</span><span class="sxs-lookup"><span data-stu-id="7f961-113">You should always set this parameter to `False`.</span></span>  
  
 <span data-ttu-id="7f961-114">*[スクリプト]*</span><span class="sxs-lookup"><span data-stu-id="7f961-114">*Script*</span></span>  
 <span data-ttu-id="7f961-115">[out] 生成された SQL スクリプトを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="7f961-115">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="7f961-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="7f961-116">*HRESULT*</span></span>  
 <span data-ttu-id="7f961-117">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="7f961-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f961-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f961-118">Return Value</span></span>  
 <span data-ttu-id="7f961-119">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="7f961-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="7f961-120">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7f961-120">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="7f961-121">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7f961-121">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f961-122">解説</span><span class="sxs-lookup"><span data-stu-id="7f961-122">Remarks</span></span>  
 <span data-ttu-id="7f961-123">このメソッドを使用すると、現在接続されているレポート サーバーのバージョンに対応するレポート サーバー データベースを作成する SQL スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7f961-123">This method generates an SQL script that creates report server databases for the version of the report server currently connected to.</span></span>  
  
 <span data-ttu-id="7f961-124">*DatabaseName* パラメーターに指定する値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース名前付け規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f961-124">The value supplied in the *DatabaseName* parameter must conform to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database naming conventions.</span></span>  
  
 <span data-ttu-id="7f961-125">スクリプトを生成する際、このメソッドは、データベースが存在するかどうかをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="7f961-125">The method does not check the existence of the database when generating the script.</span></span>  
  
 <span data-ttu-id="7f961-126">スクリプトを生成する際、このメソッドは、レポート サーバー データベースが存在するかどうかをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="7f961-126">This method does not check for the existence of the report server database when generating the script.</span></span>  
  
 <span data-ttu-id="7f961-127">生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7f961-127">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f961-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="7f961-128">Requirements</span></span>  
 <span data-ttu-id="7f961-129">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f961-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f961-130">参照</span><span class="sxs-lookup"><span data-stu-id="7f961-130">See Also</span></span>  
 [<span data-ttu-id="7f961-131">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="7f961-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
