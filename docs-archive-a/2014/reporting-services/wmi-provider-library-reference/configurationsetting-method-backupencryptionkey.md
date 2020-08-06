---
title: BackupEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- BackupEncryptionKey method
ms.assetid: da1d5dae-2517-448e-96fb-5379c93222ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d625401324e2117ee1e9677d840854fa7b63c6e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737770"
---
# <a name="backupencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="4ab30-102">BackupEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="4ab30-102">BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="4ab30-103">指定されたレポート サーバー インスタンスの暗号化キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="4ab30-103">Backs up the encryption key for the specified report server instance.</span></span> <span data-ttu-id="4ab30-104">暗号化キーは、パスワードを使用して暗号化されて格納されます。</span><span class="sxs-lookup"><span data-stu-id="4ab30-104">The encryption key is stored encrypted with a password.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab30-105">構文</span><span class="sxs-lookup"><span data-stu-id="4ab30-105">Syntax</span></span>  
  
```vb  
Public Sub BackupEncryptionKey(Password as String, _  
    ByRef KeyFile() as Integer, ByRef Length as Int32, _  
    ByRef HRESULT as Int32, ByRef ExtendedErrors() as String)  
  
```  
  
```csharp  
public void BackupEncryptionKey(string Password, out Byte[] KeyFile,   
    out Int32 Length, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ab30-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ab30-106">Parameters</span></span>  
 <span data-ttu-id="4ab30-107">*パスワード*</span><span class="sxs-lookup"><span data-stu-id="4ab30-107">*Password*</span></span>  
 <span data-ttu-id="4ab30-108">暗号化キーを暗号化するための文字列。暗号化キーを返す前に、この文字列を使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="4ab30-108">A string used to encrypt the encryption key before it is returned.</span></span>  
  
 <span data-ttu-id="4ab30-109">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="4ab30-109">*KeyFile[]*</span></span>  
 <span data-ttu-id="4ab30-110">[out] 暗号化された暗号化キーを含む配列。</span><span class="sxs-lookup"><span data-stu-id="4ab30-110">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="4ab30-111">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="4ab30-111">*Length*</span></span>  
 <span data-ttu-id="4ab30-112">[out] メソッドによって返される配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="4ab30-112">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="4ab30-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="4ab30-113">*HRESULT*</span></span>  
 <span data-ttu-id="4ab30-114">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="4ab30-114">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="4ab30-115">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="4ab30-115">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="4ab30-116">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="4ab30-116">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ab30-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="4ab30-117">Return Value</span></span>  
 <span data-ttu-id="4ab30-118">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="4ab30-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="4ab30-119">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="4ab30-119">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="4ab30-120">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="4ab30-120">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab30-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="4ab30-121">Requirements</span></span>  
 <span data-ttu-id="4ab30-122">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab30-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab30-123">参照</span><span class="sxs-lookup"><span data-stu-id="4ab30-123">See Also</span></span>  
 [<span data-ttu-id="4ab30-124">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="4ab30-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
