---
title: RestoreEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e67478541bab615a6d441ae273ed3385a8654203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737746"
---
# <a name="restoreencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="9a358-102">RestoreEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="9a358-102">RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="9a358-103">指定した暗号化キーをレポート サーバー データベースに再適用します。</span><span class="sxs-lookup"><span data-stu-id="9a358-103">Reapplies the specified encryption key to the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a358-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a358-104">Syntax</span></span>  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a358-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a358-105">Parameters</span></span>  
 <span data-ttu-id="9a358-106">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="9a358-106">*KeyFile[]*</span></span>  
 <span data-ttu-id="9a358-107">[out] 暗号化された暗号化キーを含む配列。</span><span class="sxs-lookup"><span data-stu-id="9a358-107">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="9a358-108">*[データ型]*</span><span class="sxs-lookup"><span data-stu-id="9a358-108">*Length*</span></span>  
 <span data-ttu-id="9a358-109">[out] メソッドによって返される配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="9a358-109">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="9a358-110">*パスワード*</span><span class="sxs-lookup"><span data-stu-id="9a358-110">*Password*</span></span>  
 <span data-ttu-id="9a358-111">暗号化キーの暗号化に使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="9a358-111">A string used to encrypt the encryption key.</span></span>  
  
 <span data-ttu-id="9a358-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="9a358-112">*HRESULT*</span></span>  
 <span data-ttu-id="9a358-113">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="9a358-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="9a358-114">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="9a358-114">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="9a358-115">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="9a358-115">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a358-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a358-116">Return Value</span></span>  
 <span data-ttu-id="9a358-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="9a358-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="9a358-118">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9a358-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="9a358-119">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9a358-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a358-120">解説</span><span class="sxs-lookup"><span data-stu-id="9a358-120">Remarks</span></span>  
 <span data-ttu-id="9a358-121">レポート サーバー データベースのレポート サーバーに既にエントリが存在する場合、そのエントリは削除されます。</span><span class="sxs-lookup"><span data-stu-id="9a358-121">If an entry already exists for the report server in the report server database, it is deleted.</span></span> <span data-ttu-id="9a358-122">その後、指定した暗号化キーとレポート サーバーの公開キーを使用して、新しいエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9a358-122">The new entry is then created using the specified encryption key and the report server's public key.</span></span>  
  
 <span data-ttu-id="9a358-123">このメソッドが最も効果的なのは、暗号化キーの一覧を消去する [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) メソッドの後に呼び出した場合です。</span><span class="sxs-lookup"><span data-stu-id="9a358-123">The method is most effective when called after the [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) method, which clears the list of encryption keys.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a358-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="9a358-124">Requirements</span></span>  
 <span data-ttu-id="9a358-125">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a358-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a358-126">参照</span><span class="sxs-lookup"><span data-stu-id="9a358-126">See Also</span></span>  
 [<span data-ttu-id="9a358-127">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="9a358-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
