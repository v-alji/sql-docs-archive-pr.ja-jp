---
title: SetSecureConnectionLevel メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4361f09eb38b3e5650b68ae6f86b7f2266bbf1a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737717"
---
# <a name="setsecureconnectionlevel-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d314f-102">SetSecureConnectionLevel メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d314f-102">SetSecureConnectionLevel Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d314f-103">レポート サーバーのセキュリティで保護された接続レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="d314f-103">Sets the secure connection level of the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d314f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d314f-104">Syntax</span></span>  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d314f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d314f-105">Parameters</span></span>  
 <span data-ttu-id="d314f-106">*Level*</span><span class="sxs-lookup"><span data-stu-id="d314f-106">*Level*</span></span>  
 <span data-ttu-id="d314f-107">セキュリティで保護された接続レベルを表す整数値。</span><span class="sxs-lookup"><span data-stu-id="d314f-107">An integer value representing a secure connection level.</span></span>  
  
 <span data-ttu-id="d314f-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d314f-108">*HRESULT*</span></span>  
 <span data-ttu-id="d314f-109">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="d314f-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d314f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d314f-110">Return Value</span></span>  
 <span data-ttu-id="d314f-111">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="d314f-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d314f-112">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d314f-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="d314f-113">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d314f-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d314f-114">解説</span><span class="sxs-lookup"><span data-stu-id="d314f-114">Remarks</span></span>  
 <span data-ttu-id="d314f-115">このメソッドを呼び出すと、レポート サーバーの SecureConnectionLevel プロパティ値が指定した値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d314f-115">When called, the report server SecureConnectionLevel property is set to the value specified.</span></span> <span data-ttu-id="d314f-116">値 0 は、SSL がオフであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d314f-116">A value of 0 indicates that SSL is turned off.</span></span> <span data-ttu-id="d314f-117">1 以上の値は、SSL がオンであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d314f-117">A value greater than or equal to 1 indicates that SSL is turned on.</span></span>  
  
-   <span data-ttu-id="d314f-118">値を設定すると、レポートサーバー構成ファイルの SecureConnectionLevel 要素が変更され、指定した `URLRoot` *レベル*が1以上の場合は "https://" を、指定した*レベル*が0の場合は "http://" を使用するように構成ファイル内の要素が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d314f-118">When the value is set, the SecureConnectionLevel element in the report server configuration file is changed, and the `URLRoot` element in the configuration file is set to use "https://" if the specified *Level* is greater than or equal to 1, or "http://" if the specified *Level* is 0.</span></span>  
  
 <span data-ttu-id="d314f-119">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]で、SecureConnectionLevel がオン/オフのスイッチとして使用されます。既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="d314f-119">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SecureConnectionLevel is made an on/off switch, default value is 0.</span></span> <span data-ttu-id="d314f-120">SetSecureConnectionLevel メソッド API に渡された値が 1 以上である場合、SSL はオンであると見なされ、それに従って rsreportserver.config ファイルで構成プロパティ SecureConnectionLevel が設定されます。</span><span class="sxs-lookup"><span data-stu-id="d314f-120">For any value greater than or equal to 1 passed through SetSecureConnectionLevel method API, SSL is considered on and the configuration property SecureConnectionLevel is set accordingly in the rsreportserver.config file.</span></span> <span data-ttu-id="d314f-121">値 2 と 3 は、旧バージョンとの互換性のために許可されています。</span><span class="sxs-lookup"><span data-stu-id="d314f-121">Values of 2 and 3 are still allowed for backward compatibility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d314f-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="d314f-122">Requirements</span></span>  
 <span data-ttu-id="d314f-123">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d314f-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d314f-124">参照</span><span class="sxs-lookup"><span data-stu-id="d314f-124">See Also</span></span>  
 [<span data-ttu-id="d314f-125">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="d314f-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
