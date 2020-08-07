---
title: RemoveUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RemoveUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveUnattendedExecutionAccount method
ms.assetid: 77e371c1-7c26-44f9-9119-7c8dc838db32
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efe0523c9aa13315399c043367ef05a63da46e91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719413"
---
# <a name="removeunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="90e05-102">RemoveUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="90e05-102">RemoveUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="90e05-103">レポート サーバー構成ファイルから自動実行用アカウント エントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="90e05-103">Deletes the unattended execution account entry from the report server configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e05-104">構文</span><span class="sxs-lookup"><span data-stu-id="90e05-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveUnattendedExecutionAccount(ByRef HRESULT as Int32)  
```  
  
```csharp  
public void RemoveUnattendedExecutionAccount (out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90e05-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="90e05-105">Parameters</span></span>  
 <span data-ttu-id="90e05-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="90e05-106">*HRESULT*</span></span>  
 <span data-ttu-id="90e05-107">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="90e05-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90e05-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="90e05-108">Return Value</span></span>  
 <span data-ttu-id="90e05-109">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="90e05-109">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="90e05-110">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="90e05-110">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="90e05-111">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="90e05-111">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90e05-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="90e05-112">Requirements</span></span>  
 <span data-ttu-id="90e05-113">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90e05-113">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e05-114">参照</span><span class="sxs-lookup"><span data-stu-id="90e05-114">See Also</span></span>  
 [<span data-ttu-id="90e05-115">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="90e05-115">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
