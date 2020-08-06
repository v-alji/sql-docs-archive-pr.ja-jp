---
title: InitializeReportServer メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639879"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7f235-102">InitializeReportServer メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7f235-102">InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7f235-103">指定されたレポート サービス インスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="7f235-103">Initializes the specified report service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f235-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f235-104">Syntax</span></span>  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f235-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f235-105">Parameters</span></span>  
 <span data-ttu-id="7f235-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="7f235-106">*InstallationID*</span></span>  
 <span data-ttu-id="7f235-107">暗号化キーを暗号化するための文字列。暗号化キーを返す前に、この文字列を使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="7f235-107">A string used to encrypt the encryption key before it is returned.</span></span>  
  
 <span data-ttu-id="7f235-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="7f235-108">*HRESULT*</span></span>  
 <span data-ttu-id="7f235-109">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="7f235-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="7f235-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="7f235-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="7f235-111">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="7f235-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f235-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f235-112">Return Value</span></span>  
 <span data-ttu-id="7f235-113">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="7f235-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="7f235-114">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7f235-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="7f235-115">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7f235-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f235-116">解説</span><span class="sxs-lookup"><span data-stu-id="7f235-116">Remarks</span></span>  
 <span data-ttu-id="7f235-117">このメソッドを呼び出すと、レポート サーバー データベースのセキュリティで保護された情報にアクセスする暗号化キーが、 *InstallationID*で特定されるレポート サーバーの公開キーを使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="7f235-117">When this method is called, the encryption key that accesses the report server database secure information is encrypted using the public key of the report server identified by *InstallationID*.</span></span>  
  
 <span data-ttu-id="7f235-118">指定したレポート サーバーの公開キーは、レポート サーバー データベースに書き込んでおく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f235-118">The specified report server's public key must have previously been written into the report server database.</span></span>  
  
 <span data-ttu-id="7f235-119">セキュリティで保護された情報に既にアクセスしたレポート サーバーに対して、 *InitializeReportServer* メソッドを呼び出して、暗号化キーの暗号を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f235-119">The *InitializeReportServer* method must be called against a report server that already has access to the secure information so that it can decrypt the encryption key.</span></span> <span data-ttu-id="7f235-120">次に、暗号化された暗号化キーがレポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7f235-120">The resulting encrypted encryption key is then stored in the report server database.</span></span>  
  
 <span data-ttu-id="7f235-121">初期化された初期化メソッドが呼び出されたときに、レポートサーバーの[isinitialized](configurationsetting-property-isinitialized.md)プロパティがに設定されている場合 `true` 、メソッドは暗号化キーの暗号化を試行せずに成功を返します。</span><span class="sxs-lookup"><span data-stu-id="7f235-121">If the report server's [IsInitialized](configurationsetting-property-isinitialized.md) property is set to `true` when the InitializeReportServer method is called, the method returns success without trying to encrypt the encryption key.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f235-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="7f235-122">Requirements</span></span>  
 <span data-ttu-id="7f235-123">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f235-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f235-124">参照</span><span class="sxs-lookup"><span data-stu-id="7f235-124">See Also</span></span>  
 [<span data-ttu-id="7f235-125">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="7f235-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
