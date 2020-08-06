---
title: GenerateDatabaseRightsScript メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 768e73d13d3b06f7913c3c816fded1b28c56199f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737765"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="c6c65-102">GenerateDatabaseRightsScript メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="c6c65-102">GenerateDatabaseRightsScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="c6c65-103">レポート サーバー データベースおよびレポート サーバーの実行に必要なその他のデータベースに対してユーザー権限を付与する際に使用できる、SQL スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-103">Generates a SQL Script that can be used to grant a user rights to the report server database and other databases required for a report server to run.</span></span> <span data-ttu-id="c6c65-104">呼び出し元は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース サーバーに接続して、スクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6c65-104">The caller is expected to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and execute the script.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6c65-105">構文</span><span class="sxs-lookup"><span data-stu-id="c6c65-105">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6c65-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6c65-106">Parameters</span></span>  
 <span data-ttu-id="c6c65-107">*UserName*</span><span class="sxs-lookup"><span data-stu-id="c6c65-107">*UserName*</span></span>  
 <span data-ttu-id="c6c65-108">スクリプトで権限を与えるユーザーのユーザー名または Windows セキュリティ識別子 (SID)。</span><span class="sxs-lookup"><span data-stu-id="c6c65-108">The user name or Windows security identifier (SID) of the user to which the script will grant rights.</span></span>  
  
 <span data-ttu-id="c6c65-109">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="c6c65-109">*DatabaseName*</span></span>  
 <span data-ttu-id="c6c65-110">スクリプトによってユーザーにアクセス権が付与されるデータベース名。</span><span class="sxs-lookup"><span data-stu-id="c6c65-110">The database name to which the script will grant access to the user.</span></span>  
  
 <span data-ttu-id="c6c65-111">*IsRemote*</span><span class="sxs-lookup"><span data-stu-id="c6c65-111">*IsRemote*</span></span>  
 <span data-ttu-id="c6c65-112">データベースがレポート サーバーに対してリモートであるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="c6c65-112">A Boolean value to indicating whether the database is remote from the report server.</span></span>  
  
 <span data-ttu-id="c6c65-113">*IsWindowsUser*</span><span class="sxs-lookup"><span data-stu-id="c6c65-113">*IsWindowsUser*</span></span>  
 <span data-ttu-id="c6c65-114">指定されたユーザー名が Windows ユーザーか [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="c6c65-114">A Boolean value indicating whether the specified user name is a Windows user or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="c6c65-115">*[スクリプト]*</span><span class="sxs-lookup"><span data-stu-id="c6c65-115">*Script*</span></span>  
 <span data-ttu-id="c6c65-116">[out] 生成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプトを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="c6c65-116">[out] A string containing the generated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span>  
  
 <span data-ttu-id="c6c65-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="c6c65-117">*HRESULT*</span></span>  
 <span data-ttu-id="c6c65-118">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="c6c65-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6c65-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="c6c65-119">Return Value</span></span>  
 <span data-ttu-id="c6c65-120">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-120">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="c6c65-121">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-121">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="c6c65-122">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-122">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6c65-123">解説</span><span class="sxs-lookup"><span data-stu-id="c6c65-123">Remarks</span></span>  
 <span data-ttu-id="c6c65-124">*DatabaseName* が空の場合、 *IsRemote* は無視され、レポート サーバーの構成ファイルの値がデータベース名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-124">If *DatabaseName* is empty then *IsRemote* is ignored and the report server configuration file value is used for the database name.</span></span>  
  
 <span data-ttu-id="c6c65-125">*Iswindowsuser*がに設定されている場合 `true` 、*ユーザー名*は<username の形式にする必要があり \<domain> \\ \> ます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-125">If *IsWindowsUser* is set to `true`, *UserName* should be in the format \<domain>\\<username\>.</span></span>  
  
 <span data-ttu-id="c6c65-126">*Iswindowsuser*がに設定されている場合、 `true` 生成されたスクリプトは、のユーザーにログイン権限を与え [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、レポートサーバーデータベースを既定のデータベースとして設定し、レポートサーバーデータベース、レポートサーバー一時データベース、MASTER データベース、および MSDB システムデータベースに対して**RSExec**ロールを付与します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-126">When *IsWindowsUser* is set to `true`, the generated script grants login rights to the user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], setting the report server database as the default database, and grants the **RSExec** role on the report server database, the report server temporary database, the master database and the MSDB system database.</span></span>  
  
 <span data-ttu-id="c6c65-127">*Iswindowsuser*がに設定されている場合 `true` 、メソッドは標準の Windows sid を入力として受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-127">When *IsWindowsUser* is set to `true`, the method accepts standard Windows SIDs as input.</span></span> <span data-ttu-id="c6c65-128">標準 Windows SID またはサービス アカウント名が指定されると、ユーザー名文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-128">When a standard Windows SID or service account name is supplied, it is translated to a user name string.</span></span> <span data-ttu-id="c6c65-129">データベースがローカルである場合、アカウントはアカウントのローカライズされた正しい表現に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-129">If the database is local, the account is translated to the correct localized representation of the account.</span></span> <span data-ttu-id="c6c65-130">データベースがリモートである場合、アカウントはコンピューターのアカウントとして表されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-130">If the database is remote, the account is represented as the computer's account.</span></span>  
  
 <span data-ttu-id="c6c65-131">次の表は、変換されるアカウントとそのリモート表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="c6c65-131">The following table shows accounts that are translated and their remote representation.</span></span>  
  
|<span data-ttu-id="c6c65-132">変換されるアカウントまたは SID</span><span class="sxs-lookup"><span data-stu-id="c6c65-132">Account / SID that is translated</span></span>|<span data-ttu-id="c6c65-133">共通名</span><span class="sxs-lookup"><span data-stu-id="c6c65-133">Common Name</span></span>|<span data-ttu-id="c6c65-134">リモート名</span><span class="sxs-lookup"><span data-stu-id="c6c65-134">Remote Name</span></span>|  
|---------------------------------------|-----------------|-----------------|  
|<span data-ttu-id="c6c65-135">(S-1-5-18)</span><span class="sxs-lookup"><span data-stu-id="c6c65-135">(S-1-5-18)</span></span>|<span data-ttu-id="c6c65-136">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="c6c65-136">Local System</span></span>|<span data-ttu-id="c6c65-137">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="c6c65-137">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="c6c65-138">.\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="c6c65-138">.\LocalSystem</span></span>|<span data-ttu-id="c6c65-139">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="c6c65-139">Local System</span></span>|<span data-ttu-id="c6c65-140">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="c6c65-140">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="c6c65-141">ComputerName\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="c6c65-141">ComputerName\LocalSystem</span></span>|<span data-ttu-id="c6c65-142">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="c6c65-142">Local System</span></span>|<span data-ttu-id="c6c65-143">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="c6c65-143">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="c6c65-144">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="c6c65-144">LocalSystem</span></span>|<span data-ttu-id="c6c65-145">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="c6c65-145">Local System</span></span>|<span data-ttu-id="c6c65-146">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="c6c65-146">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="c6c65-147">(S-1-5-20)</span><span class="sxs-lookup"><span data-stu-id="c6c65-147">(S-1-5-20)</span></span>|<span data-ttu-id="c6c65-148">Network Service</span><span class="sxs-lookup"><span data-stu-id="c6c65-148">Network Service</span></span>|<span data-ttu-id="c6c65-149">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="c6c65-149">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="c6c65-150">NT AUTHORITY\NetworkService</span><span class="sxs-lookup"><span data-stu-id="c6c65-150">NT AUTHORITY\NetworkService</span></span>|<span data-ttu-id="c6c65-151">Network Service</span><span class="sxs-lookup"><span data-stu-id="c6c65-151">Network Service</span></span>|<span data-ttu-id="c6c65-152">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="c6c65-152">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="c6c65-153">(S-1-5-19)</span><span class="sxs-lookup"><span data-stu-id="c6c65-153">(S-1-5-19)</span></span>|<span data-ttu-id="c6c65-154">Local Service</span><span class="sxs-lookup"><span data-stu-id="c6c65-154">Local Service</span></span>|<span data-ttu-id="c6c65-155">エラー - 下記参照。</span><span class="sxs-lookup"><span data-stu-id="c6c65-155">Error - see below.</span></span>|  
|<span data-ttu-id="c6c65-156">NT AUTHORITY\LocalService</span><span class="sxs-lookup"><span data-stu-id="c6c65-156">NT AUTHORITY\LocalService</span></span>|<span data-ttu-id="c6c65-157">Local Service</span><span class="sxs-lookup"><span data-stu-id="c6c65-157">Local Service</span></span>|<span data-ttu-id="c6c65-158">エラー - 下記参照。</span><span class="sxs-lookup"><span data-stu-id="c6c65-158">Error - see below.</span></span>|  
  
 <span data-ttu-id="c6c65-159">[!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]では、組み込みアカウントを使用し、レポート サーバー データベースがリモートである場合、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-159">On [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)], if you are using a built-in account and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="c6c65-160">`LocalService` 組み込みアカウントを指定し、レポート サーバー データベースがリモートである場合、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-160">If the `LocalService` built-in account is specified and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="c6c65-161">*IsWindowsUser* が true であり、 *UserName* に指定した値を変換する必要がある場合、WMI プロバイダーはレポート サーバー データベースが同じコンピューターにあるかリモート コンピューターにあるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-161">When *IsWindowsUser* is true and the value supplied in *UserName* needs to be translated, the WMI provider determines whether the report server database is located on the same computer or on a remote computer.</span></span> <span data-ttu-id="c6c65-162">インストールがローカルであるかどうかを確認するため、WMI プロバイダーは以下の値一覧に対して DatabaseServerName プロパティを評価します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-162">To determine if the installation is local, the WMI provider evaluates the DatabaseServerName property against the following list of values.</span></span> <span data-ttu-id="c6c65-163">一致が見つかった場合、データベースはローカルです。</span><span class="sxs-lookup"><span data-stu-id="c6c65-163">If a match is found, the database is local.</span></span> <span data-ttu-id="c6c65-164">見つからなかった場合、リモートです。</span><span class="sxs-lookup"><span data-stu-id="c6c65-164">Otherwise, it is remote.</span></span> <span data-ttu-id="c6c65-165">比較では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="c6c65-165">The comparison is case-insensitive.</span></span>  
  
|<span data-ttu-id="c6c65-166">DatabaseServerName の値</span><span class="sxs-lookup"><span data-stu-id="c6c65-166">Value of DatabaseServerName</span></span>|<span data-ttu-id="c6c65-167">例</span><span class="sxs-lookup"><span data-stu-id="c6c65-167">Example</span></span>|  
|---------------------------------|-------------|  
|<span data-ttu-id="c6c65-168">"."</span><span class="sxs-lookup"><span data-stu-id="c6c65-168">"."</span></span>||  
|<span data-ttu-id="c6c65-169">"(local)"</span><span class="sxs-lookup"><span data-stu-id="c6c65-169">"(local)"</span></span>||  
|<span data-ttu-id="c6c65-170">"LOCAL"</span><span class="sxs-lookup"><span data-stu-id="c6c65-170">"LOCAL"</span></span>||  
|<span data-ttu-id="c6c65-171">localhost</span><span class="sxs-lookup"><span data-stu-id="c6c65-171">localhost</span></span>||  
|\<Machinename>|<span data-ttu-id="c6c65-172">testlab14</span><span class="sxs-lookup"><span data-stu-id="c6c65-172">testlab14</span></span>|  
|\<MachineFQDN>|<span data-ttu-id="c6c65-173">example.redmond.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="c6c65-173">example.redmond.microsoft.com</span></span>|  
|\<IPAddress>|<span data-ttu-id="c6c65-174">180.012.345,678</span><span class="sxs-lookup"><span data-stu-id="c6c65-174">180.012.345,678</span></span>|  
  
 <span data-ttu-id="c6c65-175">*Iswindowsuser*がに設定されている場合 `true` 、WMI プロバイダーは LookupAccountName を呼び出してアカウントの SID を取得し、lookupaccountsid 関数を呼び出してスクリプトに含める名前を取得し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-175">When *IsWindowsUser* is set to `true`, the WMI provider calls LookupAccountName to get the SID for the account and then calls LookupAccountSID to get the name to put in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span> <span data-ttu-id="c6c65-176">このようにすると、使用するアカウント名は必ず [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 検証に合格します。</span><span class="sxs-lookup"><span data-stu-id="c6c65-176">This ensures that the account name used will pass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validation.</span></span>  
  
 <span data-ttu-id="c6c65-177">*Iswindowsuser*がに設定されている場合、生成されたスクリプトによって、 `false` レポートサーバーデータベース、レポートサーバー一時データベース、および MSDB データベースの**RSExec**ロールが付与されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-177">When *IsWindowsUser* is set to `false`, the generated script grants the **RSExec** role on the report server database, the report server temporary database, and the MSDB database.</span></span>  
  
 <span data-ttu-id="c6c65-178">*Iswindowsuser*がに設定されている場合 `false` 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプトを正常に実行するには、SQL Server ユーザーがに既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6c65-178">When *IsWindowsUser* is set to `false`, the SQL Server user must already exist on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the script to run successfully.</span></span>  
  
 <span data-ttu-id="c6c65-179">レポート サーバーにレポート サーバー データベースが指定されていない場合、GrantRightsToDatabaseUser を呼び出すとエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="c6c65-179">If the report server does not have a report server database specified, calling GrantRightsToDatabaseUser returns an error.</span></span>  
  
 <span data-ttu-id="c6c65-180">生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。</span><span class="sxs-lookup"><span data-stu-id="c6c65-180">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6c65-181">必要条件</span><span class="sxs-lookup"><span data-stu-id="c6c65-181">Requirements</span></span>  
 <span data-ttu-id="c6c65-182">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6c65-182">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c65-183">参照</span><span class="sxs-lookup"><span data-stu-id="c6c65-183">See Also</span></span>  
 [<span data-ttu-id="c6c65-184">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="c6c65-184">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
