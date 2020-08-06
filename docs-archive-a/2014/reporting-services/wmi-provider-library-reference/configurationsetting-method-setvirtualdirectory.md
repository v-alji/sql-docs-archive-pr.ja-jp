---
title: SetVirtualDirectory メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7f45181f3f6a791f5cb64a7519285b6d2a87dd36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737698"
---
# <a name="setvirtualdirectory-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="bbf74-102">SetVirtualDirectory メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="bbf74-102">SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="bbf74-103">指定したアプリケーションの仮想ディレクトリの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="bbf74-103">Sets the name of the virtual directory for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf74-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbf74-104">Syntax</span></span>  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbf74-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbf74-105">Parameters</span></span>  
 <span data-ttu-id="bbf74-106">*Application*</span><span class="sxs-lookup"><span data-stu-id="bbf74-106">*Application*</span></span>  
 <span data-ttu-id="bbf74-107">仮想ディレクトリを設定するアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="bbf74-107">The name of application for which to set the virtual directory.</span></span>  
  
 <span data-ttu-id="bbf74-108">*VirtualDirectory*</span><span class="sxs-lookup"><span data-stu-id="bbf74-108">*VirtualDirectory*</span></span>  
 <span data-ttu-id="bbf74-109">仮想ディレクトリの名前。</span><span class="sxs-lookup"><span data-stu-id="bbf74-109">The name of the virtual directory.</span></span>  
  
 <span data-ttu-id="bbf74-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="bbf74-110">*lcid*</span></span>  
 <span data-ttu-id="bbf74-111">仮想ディレクトリのロケール ID。</span><span class="sxs-lookup"><span data-stu-id="bbf74-111">The locale id for the virtual directory.</span></span>  
  
 <span data-ttu-id="bbf74-112">*Error*</span><span class="sxs-lookup"><span data-stu-id="bbf74-112">*Error*</span></span>  
 <span data-ttu-id="bbf74-113">[out] 発生したエラーの説明。</span><span class="sxs-lookup"><span data-stu-id="bbf74-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="bbf74-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="bbf74-114">*HRESULT*</span></span>  
 <span data-ttu-id="bbf74-115">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="bbf74-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbf74-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="bbf74-116">Return Value</span></span>  
 <span data-ttu-id="bbf74-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="bbf74-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="bbf74-118">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="bbf74-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbf74-119">解説</span><span class="sxs-lookup"><span data-stu-id="bbf74-119">Remarks</span></span>  
 <span data-ttu-id="bbf74-120">アプリケーションは、すべての URL 予約に対して仮想ディレクトリの名前を 1 つだけ持つことができます。</span><span class="sxs-lookup"><span data-stu-id="bbf74-120">An application can have only one virtual directory name for all URL reservations.</span></span>  
  
 <span data-ttu-id="bbf74-121">VirtualDirectory に指定する値は、仮想ディレクトリの名前付け規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbf74-121">VirtualDirectory must conform to naming conventions for virtual directories.</span></span> <span data-ttu-id="bbf74-122">VirtualDirectory には空の文字列または空白を指定できません。</span><span class="sxs-lookup"><span data-stu-id="bbf74-122">VirtualDirectory must not be empty string or blank.</span></span>  
  
 <span data-ttu-id="bbf74-123">Configuration\URLReservations\Application\VirtualDirectory 要素の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="bbf74-123">Updates the value of the \Configuration\URLReservations\Application\VirtualDirectory element.</span></span> <span data-ttu-id="bbf74-124">URL 予約が作成されていない場合でも成功します。</span><span class="sxs-lookup"><span data-stu-id="bbf74-124">Succeeds even if no URL reservations have been created yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf74-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="bbf74-125">Requirements</span></span>  
 <span data-ttu-id="bbf74-126">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf74-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf74-127">参照</span><span class="sxs-lookup"><span data-stu-id="bbf74-127">See Also</span></span>  
 [<span data-ttu-id="bbf74-128">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="bbf74-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
