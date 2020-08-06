---
title: DeleteEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptionKey method
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e302659615bd620b3b0ed802b83aafc4e9506d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639883"
---
# <a name="deleteencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="71a20-102">DeleteEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="71a20-102">DeleteEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="71a20-103">レポート サーバー データベースから暗号化キーを削除します。</span><span class="sxs-lookup"><span data-stu-id="71a20-103">Deletes the encryption keys from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a20-104">構文</span><span class="sxs-lookup"><span data-stu-id="71a20-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71a20-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71a20-105">Parameters</span></span>  
 <span data-ttu-id="71a20-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="71a20-106">*InstallationID*</span></span>  
 <span data-ttu-id="71a20-107">レポート サーバー データベースのキー テーブルにあるレポート サーバーのインストール ID。</span><span class="sxs-lookup"><span data-stu-id="71a20-107">The installation ID of a report server that is in the keys table of the report server database.</span></span>  
  
 <span data-ttu-id="71a20-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="71a20-108">*HRESULT*</span></span>  
 <span data-ttu-id="71a20-109">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="71a20-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="71a20-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="71a20-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="71a20-111">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="71a20-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71a20-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="71a20-112">Return Value</span></span>  
 <span data-ttu-id="71a20-113">メソッド呼び出しの成功または失敗を示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="71a20-113">Returns an HRESULT indicating success or failure of the method call.</span></span> <span data-ttu-id="71a20-114">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="71a20-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="71a20-115">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="71a20-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71a20-116">解説</span><span class="sxs-lookup"><span data-stu-id="71a20-116">Remarks</span></span>  
 <span data-ttu-id="71a20-117">*DeleteEncryptionKey* メソッドは、レポート サーバー データベースのセキュリティで保護された情報にアクセスするレポート サーバーのキー テーブルからエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="71a20-117">The *DeleteEncryptionKey* method deletes entries from the keys table for any report servers that have access to the secure information in the report server database.</span></span> <span data-ttu-id="71a20-118">指定した *InstallationID* パラメーターがデータベースのインストール ID に対応しない場合、メソッドはエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="71a20-118">If the *InstallationID* parameter specified does not correspond to an installation ID in the database, the method returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71a20-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="71a20-119">Requirements</span></span>  
 <span data-ttu-id="71a20-120">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71a20-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a20-121">参照</span><span class="sxs-lookup"><span data-stu-id="71a20-121">See Also</span></span>  
 [<span data-ttu-id="71a20-122">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="71a20-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
