---
title: SetDatabaseQueryTimeout メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseQueryTimeout method
ms.assetid: bd2809e5-7848-45b3-a502-b04fc698b646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ab6b5bf27eca5e9d6d083d03af48c0ab71b4dd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737723"
---
# <a name="setdatabasequerytimeout-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6a4c4-102">SetDatabaseQueryTimeout メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6a4c4-102">SetDatabaseQueryTimeout Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6a4c4-103">レポート サーバー データベース クエリの既定のタイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6a4c4-103">Specifies the default time-out value for report server database queries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a4c4-104">構文</span><span class="sxs-lookup"><span data-stu-id="6a4c4-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseQueryTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseQueryTimeout (Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a4c4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a4c4-105">Parameters</span></span>  
 <span data-ttu-id="6a4c4-106">*LogonTimeout*</span><span class="sxs-lookup"><span data-stu-id="6a4c4-106">*LogonTimeout*</span></span>  
 <span data-ttu-id="6a4c4-107">レポート サーバー データベース クエリの既定のタイムアウト値 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="6a4c4-107">The default timeout value, in seconds, for report server database queries.</span></span>  
  
 <span data-ttu-id="6a4c4-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="6a4c4-108">*HRESULT*</span></span>  
 <span data-ttu-id="6a4c4-109">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="6a4c4-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a4c4-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6a4c4-110">Return Value</span></span>  
 <span data-ttu-id="6a4c4-111">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="6a4c4-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="6a4c4-112">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6a4c4-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="6a4c4-113">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6a4c4-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a4c4-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="6a4c4-114">Requirements</span></span>  
 <span data-ttu-id="6a4c4-115">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a4c4-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4c4-116">参照</span><span class="sxs-lookup"><span data-stu-id="6a4c4-116">See Also</span></span>  
 [<span data-ttu-id="6a4c4-117">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="6a4c4-117">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
