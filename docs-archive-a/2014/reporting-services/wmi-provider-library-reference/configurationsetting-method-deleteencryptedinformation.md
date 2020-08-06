---
title: DeleteEncryptedInformation メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d00dc3e90816cd04c84f124cdc3d25a9ac122bba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639890"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="a9078-102">DeleteEncryptedInformation メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="a9078-102">DeleteEncryptedInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="a9078-103">レポート サーバー データベースから暗号化された情報を削除します。</span><span class="sxs-lookup"><span data-stu-id="a9078-103">Deletes the encrypted information from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9078-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9078-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9078-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9078-105">Parameters</span></span>  
 <span data-ttu-id="a9078-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="a9078-106">*HRESULT*</span></span>  
 <span data-ttu-id="a9078-107">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="a9078-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="a9078-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="a9078-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="a9078-109">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="a9078-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9078-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a9078-110">Return Value</span></span>  
 <span data-ttu-id="a9078-111">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="a9078-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="a9078-112">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a9078-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="a9078-113">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a9078-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9078-114">解説</span><span class="sxs-lookup"><span data-stu-id="a9078-114">Remarks</span></span>  
 <span data-ttu-id="a9078-115">このメソッドを呼び出すと、次のデータが削除されます。</span><span class="sxs-lookup"><span data-stu-id="a9078-115">When this method is invoked, the following data is deleted:</span></span>  
  
-   <span data-ttu-id="a9078-116">ユーザー名とパスワードを含む、暗号化されたデータ ソース情報</span><span class="sxs-lookup"><span data-stu-id="a9078-116">Data source information that is encrypted, including user name and password.</span></span>  
  
-   <span data-ttu-id="a9078-117">配信拡張機能インターフェイスを使用して暗号化されたサブスクリプション データ</span><span class="sxs-lookup"><span data-stu-id="a9078-117">Subscription data that is encrypted using the delivery extension interfaces.</span></span>  
  
-   <span data-ttu-id="a9078-118">レポート サーバー データベースのキー テーブルからのすべての情報</span><span class="sxs-lookup"><span data-stu-id="a9078-118">All the information from the keys table in the report server database.</span></span>  
  
 <span data-ttu-id="a9078-119">このメソッドを呼び出した後は、ユーザーがレポート サーバー データベースを使用する各コンピューターを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9078-119">After this method is invoked, the user must initialize each computer that uses the report server database.</span></span>  
  
 <span data-ttu-id="a9078-120">DeleteEncryptedInformation メソッドを呼び出しても、レポート サーバー構成ファイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="a9078-120">Calling the DeleteEncryptedInformation method does not affect the report server configuration file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9078-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="a9078-121">Requirements</span></span>  
 <span data-ttu-id="a9078-122">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9078-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9078-123">参照</span><span class="sxs-lookup"><span data-stu-id="a9078-123">See Also</span></span>  
 [<span data-ttu-id="a9078-124">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="a9078-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
