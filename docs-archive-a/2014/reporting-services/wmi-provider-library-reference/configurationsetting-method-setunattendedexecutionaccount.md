---
title: SetUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73cf4c633c51de1e3e6b878c66d73ee710e98df6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737710"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="85622-102">SetUnattendedExecutionAccount メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="85622-102">SetUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="85622-103">レポートの自動実行に使用するアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="85622-103">Specifies the account used to execute reports unattended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85622-104">構文</span><span class="sxs-lookup"><span data-stu-id="85622-104">Syntax</span></span>  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85622-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85622-105">Parameters</span></span>  
 <span data-ttu-id="85622-106">*UserName*</span><span class="sxs-lookup"><span data-stu-id="85622-106">*UserName*</span></span>  
 <span data-ttu-id="85622-107">自動実行で使用する Windows アカウント。</span><span class="sxs-lookup"><span data-stu-id="85622-107">A Windows account to be used for unattended executions.</span></span>  
  
 <span data-ttu-id="85622-108">*パスワード*</span><span class="sxs-lookup"><span data-stu-id="85622-108">*Password*</span></span>  
 <span data-ttu-id="85622-109">指定したアカウントのパスワード。</span><span class="sxs-lookup"><span data-stu-id="85622-109">The password for the specified account.</span></span>  
  
 <span data-ttu-id="85622-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="85622-110">*HRESULT*</span></span>  
 <span data-ttu-id="85622-111">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="85622-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85622-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="85622-112">Return Value</span></span>  
 <span data-ttu-id="85622-113">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="85622-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="85622-114">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="85622-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="85622-115">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="85622-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85622-116">解説</span><span class="sxs-lookup"><span data-stu-id="85622-116">Remarks</span></span>  
 <span data-ttu-id="85622-117">SetUnattendedExecutionAccount メソッドは、レポート サーバーが指定されたユーザーとしてログインできるかどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="85622-117">The SetUnattendedExecutionAccount method does not verify whether the report server can log in as the specified user.</span></span>  
  
 <span data-ttu-id="85622-118">SetUnattendedExecutionAccount メソッドを使用してレポート サーバー Windows サービスのコンテキストで自動実行を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="85622-118">It is not possible to use the SetUnattendedExecutionAccount method to run unattended executions in the context of the report server Windows service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85622-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="85622-119">Requirements</span></span>  
 <span data-ttu-id="85622-120">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85622-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85622-121">参照</span><span class="sxs-lookup"><span data-stu-id="85622-121">See Also</span></span>  
 [<span data-ttu-id="85622-122">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="85622-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
