---
title: SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737686"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="e6eba-102">SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="e6eba-102">SetWindowsServiceIdentity Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="e6eba-103">レポート サーバーの Windows サービスを指定された Windows ユーザーとして実行させ、レポート サーバーを運用できるファイル システム権限をこのアカウントに与えます。</span><span class="sxs-lookup"><span data-stu-id="e6eba-103">Makes the Report Server Windows service run as a specified Windows user, and grants this account sufficient file system permissions to allow the report server to operate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6eba-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6eba-104">Syntax</span></span>  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6eba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e6eba-105">Parameters</span></span>  
 <span data-ttu-id="e6eba-106">*UseBuiltInAccount*</span><span class="sxs-lookup"><span data-stu-id="e6eba-106">*UseBuiltInAccount*</span></span>  
 <span data-ttu-id="e6eba-107">指定したアカウントが組み込み Windows アカウントであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e6eba-107">Indicates whether the specified account is a built-in Windows account.</span></span>  
  
 <span data-ttu-id="e6eba-108">*アカウント*</span><span class="sxs-lookup"><span data-stu-id="e6eba-108">*Account*</span></span>  
 <span data-ttu-id="e6eba-109">Windows サービスの実行に使用する "DOMAIN\alias" 形式の Windows アカウント。</span><span class="sxs-lookup"><span data-stu-id="e6eba-109">The Windows account to use to run the Windows service, in the format "DOMAIN\alias".</span></span>  
  
 <span data-ttu-id="e6eba-110">*パスワード*</span><span class="sxs-lookup"><span data-stu-id="e6eba-110">*Password*</span></span>  
 <span data-ttu-id="e6eba-111">アカウントのパスワード。</span><span class="sxs-lookup"><span data-stu-id="e6eba-111">The password for the account.</span></span>  
  
 <span data-ttu-id="e6eba-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="e6eba-112">*HRESULT*</span></span>  
 <span data-ttu-id="e6eba-113">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="e6eba-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6eba-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="e6eba-114">Return Value</span></span>  
 <span data-ttu-id="e6eba-115">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="e6eba-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="e6eba-116">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6eba-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="e6eba-117">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6eba-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6eba-118">解説</span><span class="sxs-lookup"><span data-stu-id="e6eba-118">Remarks</span></span>  
 <span data-ttu-id="e6eba-119">*UseBuiltInAccount*パラメーターがに設定され、 `true` レポートサーバーが Microsoft または Windows XP で実行されている場合 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] 、 *Name*、 *Domain*、および*Password*の各パラメーターの値は無視され、ローカルシステムアカウントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e6eba-119">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] or Windows XP, the value of the *Name*, *Domain*, and *Password* parameters are ignored and the Local system account is used.</span></span>  
  
 <span data-ttu-id="e6eba-120">*UseBuiltInAccount*パラメーターがに設定され、 `true` レポートサーバーが Windows server 2003 で実行されている場合、*ドメイン*と*パスワード*のプロパティは無視され、名前フィールドには "指定" または "builtin\networkservice" または "Builtin\LocalService" のいずれかが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6eba-120">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Windows Server 2003, the *Domain* and *Password* properties are ignored, and the name field must contain either "Builtin\NetworkService" or "Builtin\System" or "Builtin\LocalService".</span></span>  
  
 <span data-ttu-id="e6eba-121">SetWindowsServiceIdentity メソッドはレポート サーバーのインストール ディレクトリのファイルおよびフォルダーに対するファイル権限を設定します。</span><span class="sxs-lookup"><span data-stu-id="e6eba-121">The SetWindowsServiceIdentity method sets file permissions on files and folders in the report server installation directory.</span></span>  
  
 <span data-ttu-id="e6eba-122">*Account*パラメーターで指定されたアカウントには、 `LogonAsService` Windows の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e6eba-122">The account specified in the *Account* parameter requires `LogonAsService` rights in Windows.</span></span> <span data-ttu-id="e6eba-123">このメソッドは、指定されたアカウントにこの権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="e6eba-123">The method grants this right to the specified account.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6eba-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="e6eba-124">Requirements</span></span>  
 <span data-ttu-id="e6eba-125">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6eba-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6eba-126">参照</span><span class="sxs-lookup"><span data-stu-id="e6eba-126">See Also</span></span>  
 [<span data-ttu-id="e6eba-127">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="e6eba-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
