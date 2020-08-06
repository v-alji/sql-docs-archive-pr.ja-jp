---
title: ReencryptSecureInformation メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1a0c657b69d624df8895ae4d5a6d12277b011b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643163"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="a9773-102">ReencryptSecureInformation メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="a9773-102">ReencryptSecureInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="a9773-103">新しい暗号化キーを生成し、この新しいキーを使用してカタログ内のセキュリティで保護されたすべての情報を再度暗号化します。</span><span class="sxs-lookup"><span data-stu-id="a9773-103">Generates a new encryption key and re-encrypts all secure information in the catalog using this new key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9773-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9773-104">Syntax</span></span>  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9773-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9773-105">Parameters</span></span>  
 <span data-ttu-id="a9773-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="a9773-106">*HRESULT*</span></span>  
 <span data-ttu-id="a9773-107">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="a9773-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="a9773-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="a9773-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="a9773-109">[out] 呼び出しによって返されたその他のエラーを含む文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="a9773-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9773-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a9773-110">Return Value</span></span>  
 <span data-ttu-id="a9773-111">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="a9773-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="a9773-112">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a9773-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="a9773-113">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a9773-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9773-114">解説</span><span class="sxs-lookup"><span data-stu-id="a9773-114">Remarks</span></span>  
 <span data-ttu-id="a9773-115">ReencryptSecureInformation メソッドを使用することによって、管理者は既存の暗号化キーを新しいキーと置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="a9773-115">The ReencryptSecureInformation method allows the administrator to replace the existing encryption key with a new key.</span></span>  
  
 <span data-ttu-id="a9773-116">このメソッドを呼び出すと、レポート サーバーが新しい暗号化キーを生成し、新しい暗号化キーを使用してすべての暗号化されたコンテンツを反復処理して再度暗号化します。</span><span class="sxs-lookup"><span data-stu-id="a9773-116">When this method is invoked, the report server generates a new encryption key and iterates through all encrypted content to re-encrypt it with the new encryption key.</span></span>  
  
 <span data-ttu-id="a9773-117">配信拡張機能は、セキュリティで保護された情報を配信設定構造に格納できます。</span><span class="sxs-lookup"><span data-stu-id="a9773-117">Delivery extensions can store secured information in their delivery settings structures.</span></span> <span data-ttu-id="a9773-118">ReencryptSecureInformation を呼び出すと、レポート サーバーが各サブスクリプションと対応する拡張機能を読み込み、関連付けられた設定に格納された情報を再度暗号化します。</span><span class="sxs-lookup"><span data-stu-id="a9773-118">When ReencryptSecureInformation is called, the report server loads each subscription and the corresponding delivery extension to re-encrypt information stored in the associated settings.</span></span>  
  
 <span data-ttu-id="a9773-119">スケールアウト配置のコンピューターでこのメソッドを実行する場合は、スケールアウト配置の各コンピューターを再度初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9773-119">If this method is run on a computer in a scale-out deployment, each computer in the scale-out deployment will need to be initialized again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9773-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="a9773-120">Requirements</span></span>  
 <span data-ttu-id="a9773-121">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9773-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9773-122">参照</span><span class="sxs-lookup"><span data-stu-id="a9773-122">See Also</span></span>  
 [<span data-ttu-id="a9773-123">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="a9773-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
