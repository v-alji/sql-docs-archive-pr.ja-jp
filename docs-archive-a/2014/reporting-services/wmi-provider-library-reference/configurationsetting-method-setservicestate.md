---
title: SetServiceState メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b4a29b3379fc1d312af42a1f5b1296ee35dcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737704"
---
# <a name="setservicestate-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d56aa-102">SetServiceState メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d56aa-102">SetServiceState Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d56aa-103">レポート サーバーの Windows サービスおよび Web サービスを開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="d56aa-103">Turns the Report Server Windows and Web services on and off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56aa-104">構文</span><span class="sxs-lookup"><span data-stu-id="d56aa-104">Syntax</span></span>  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d56aa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d56aa-105">Parameters</span></span>  
 <span data-ttu-id="d56aa-106">*EnableWindowsService*</span><span class="sxs-lookup"><span data-stu-id="d56aa-106">*EnableWindowsService*</span></span>  
 <span data-ttu-id="d56aa-107">Windows サービスの状態を示す `Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="d56aa-107">A `Boolean` value indicating the state of the Windows service.</span></span> <span data-ttu-id="d56aa-108">値が `true` の場合はレポート サーバー Windows サービスを開始し、`false` の場合はレポート サーバー Windows サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="d56aa-108">A value of `true` starts the Report Server Windows service; a value of `false` stops the Windows service.</span></span>  
  
 <span data-ttu-id="d56aa-109">*EnableWebService*</span><span class="sxs-lookup"><span data-stu-id="d56aa-109">*EnableWebService*</span></span>  
 <span data-ttu-id="d56aa-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web サービスの状態を示す `Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="d56aa-110">A `Boolean` value indicating the state of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web service.</span></span> <span data-ttu-id="d56aa-111">値が `true` の場合はレポート サーバー Web サービスを開始し、`false` の場合はレポート サーバー Web サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="d56aa-111">A value of `true` starts the Report Server Web service; a value of `false` stops the Web service</span></span>  
  
 <span data-ttu-id="d56aa-112">*EnableReportManager*</span><span class="sxs-lookup"><span data-stu-id="d56aa-112">*EnableReportManager*</span></span>  
 <span data-ttu-id="d56aa-113">レポート マネージャーの目的の状態を示す `Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="d56aa-113">A `Boolean` value indicating the desired state of the Report manager.</span></span>  
  
 <span data-ttu-id="d56aa-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d56aa-114">*HRESULT*</span></span>  
 <span data-ttu-id="d56aa-115">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="d56aa-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d56aa-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="d56aa-116">Return Value</span></span>  
 <span data-ttu-id="d56aa-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="d56aa-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d56aa-118">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d56aa-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="d56aa-119">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d56aa-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d56aa-120">解説</span><span class="sxs-lookup"><span data-stu-id="d56aa-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d56aa-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="d56aa-121">Requirements</span></span>  
 <span data-ttu-id="d56aa-122">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d56aa-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56aa-123">参照</span><span class="sxs-lookup"><span data-stu-id="d56aa-123">See Also</span></span>  
 [<span data-ttu-id="d56aa-124">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="d56aa-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
