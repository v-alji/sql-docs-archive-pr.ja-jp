---
title: SetDatabaseConnection メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseConnection method
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5c62777edd1fab2b0cb3babc13ab09f7bcf32a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737740"
---
# <a name="setdatabaseconnection-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ab743-102">SetDatabaseConnection メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ab743-102">SetDatabaseConnection Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ab743-103">特定のレポート サーバー データベースへのレポート サーバー データベース接続を設定します。</span><span class="sxs-lookup"><span data-stu-id="ab743-103">Sets the report server database connection to a particular report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab743-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab743-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab743-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab743-105">Parameters</span></span>  
 <span data-ttu-id="ab743-106">*[サーバー]*</span><span class="sxs-lookup"><span data-stu-id="ab743-106">*Server*</span></span>  
 <span data-ttu-id="ab743-107">レポート サーバー データベースをホストするために使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="ab743-107">The name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is used to host the report server database.</span></span>  
  
 <span data-ttu-id="ab743-108">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="ab743-108">*DatabaseName*</span></span>  
 <span data-ttu-id="ab743-109">レポート サーバー データベースの名前。</span><span class="sxs-lookup"><span data-stu-id="ab743-109">The name of the report server database.</span></span>  
  
 <span data-ttu-id="ab743-110">*CredentialsType*</span><span class="sxs-lookup"><span data-stu-id="ab743-110">*CredentialsType*</span></span>  
 <span data-ttu-id="ab743-111">接続に使用する資格情報の種類。</span><span class="sxs-lookup"><span data-stu-id="ab743-111">The type of credentials to use for the connection.</span></span> <span data-ttu-id="ab743-112">可能な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ab743-112">Values can be:</span></span>  
  
-   <span data-ttu-id="ab743-113">0 : Windows</span><span class="sxs-lookup"><span data-stu-id="ab743-113">0 - Windows</span></span>  
  
-   <span data-ttu-id="ab743-114">1 : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab743-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="ab743-115">2 : Windows サービス</span><span class="sxs-lookup"><span data-stu-id="ab743-115">2 - Windows Service</span></span>  
  
 <span data-ttu-id="ab743-116">*UserName*</span><span class="sxs-lookup"><span data-stu-id="ab743-116">*UserName*</span></span>  
 <span data-ttu-id="ab743-117">レポート サーバー データベースへの接続に使用するアカウント名。</span><span class="sxs-lookup"><span data-stu-id="ab743-117">The account name used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="ab743-118">*パスワード*</span><span class="sxs-lookup"><span data-stu-id="ab743-118">*Password*</span></span>  
 <span data-ttu-id="ab743-119">レポート サーバー データベースへの接続に使用するパスワード。</span><span class="sxs-lookup"><span data-stu-id="ab743-119">The password used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="ab743-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ab743-120">*HRESULT*</span></span>  
 <span data-ttu-id="ab743-121">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="ab743-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab743-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="ab743-122">Return Value</span></span>  
 <span data-ttu-id="ab743-123">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="ab743-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ab743-124">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ab743-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="ab743-125">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ab743-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab743-126">解説</span><span class="sxs-lookup"><span data-stu-id="ab743-126">Remarks</span></span>  
 <span data-ttu-id="ab743-127">*CredentialsType* パラメーターを 0 (Windows) に設定する場合は、 *UserName* パラメーターと *Password* パラメーターを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab743-127">When the *CredentialsType* parameter is set to 0 (Windows), the *UserName* and *Password* parameters must be set.</span></span> <span data-ttu-id="ab743-128">*UserName* パラメーターは "domain\username" 形式で設定し、値は有効な Windows ログオンを表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab743-128">The *UserName* parameter must be in the form "domain\username", and the value must represent a valid Windows logon.</span></span>  
  
 <span data-ttu-id="ab743-129">*CredentialsType* パラメーターを 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) に設定する場合は、 *UserName* パラメーターに渡される値が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン名の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab743-129">When the *CredentialsType* parameter is set to 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), the value passed in the *UserName* parameter must conform to the requirements of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login name.</span></span>  
  
 <span data-ttu-id="ab743-130">*CredentialsType* パラメーターを 2 (Windows サービス) に設定する場合は、レポート サーバーがレポート サーバー データベースとの接続に統合セキュリティを使用し、 *UserName* パラメーターと *Password* パラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ab743-130">When the *CredentialsType* parameter is set to 2 (Windows Service), the report server uses integrated security to connect to the report server database and the *UserName* and *Password* parameters are ignored.</span></span> <span data-ttu-id="ab743-131">Reporting Server Web サービスは、レポート サーバー データベースへのアクセスに、[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アカウントまたはアプリケーション プール アカウントのいずれかと、Windows サービス アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab743-131">The Reporting Server Web service will use either the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account or an application pool's account and the Windows service account to access the report server database.</span></span>  
  
 <span data-ttu-id="ab743-132">SetDatabaseConnection メソッドを呼び出すと、資格情報とデータベース情報が暗号化され、指定されたレポート サーバーの構成ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ab743-132">When called, the SetDatabaseConnection method encrypts and stores the credentials and database information in the configuration file for the specified report server.</span></span>  
  
 <span data-ttu-id="ab743-133">SetDatabaseConnection メソッドは、レポート サーバーが指定されたデータを使用してレポート サーバー データベースと接続できるかチェックしません。</span><span class="sxs-lookup"><span data-stu-id="ab743-133">The SetDatabaseConnection method does not check that the report server can connect to the report server database using the data specified.</span></span>  
  
 <span data-ttu-id="ab743-134">ConnectionPoolSize プロパティを初めて設定する場合、その値は、ConnectionPoolSize = #Processors \* 75 で算出されたプロセッサ数に基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="ab743-134">When set for the first time, the ConnectionPoolSize property is set based on the following processors: ConnectionPoolSize = #Processors \* 75.</span></span>  
  
 <span data-ttu-id="ab743-135">SetDatabaseConnection メソッドは、指定されたアカウントに権限を付与しません。</span><span class="sxs-lookup"><span data-stu-id="ab743-135">The SetDatabaseConnection method does not grant permissions to the specified account(s).</span></span> <span data-ttu-id="ab743-136">レポート サーバー データベースへのアクセスを必要とするアカウントごとに [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) メソッドを呼び出し、結果のスクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab743-136">You must call the [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) method for each account that requires access to the report server database and run the resulting script.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab743-137">必要条件</span><span class="sxs-lookup"><span data-stu-id="ab743-137">Requirements</span></span>  
 <span data-ttu-id="ab743-138">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab743-138">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab743-139">参照</span><span class="sxs-lookup"><span data-stu-id="ab743-139">See Also</span></span>  
 [<span data-ttu-id="ab743-140">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="ab743-140">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
