---
title: ReserveURL メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95a58938ada19b4e49f094e3d8d01b241f1a4286
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737747"
---
# <a name="reserveurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="22e79-102">ReserveURL メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="22e79-102">ReserveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="22e79-103">指定したアプリケーションの URL 予約を追加します。</span><span class="sxs-lookup"><span data-stu-id="22e79-103">Adds a URL reservation for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22e79-104">構文</span><span class="sxs-lookup"><span data-stu-id="22e79-104">Syntax</span></span>  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22e79-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22e79-105">Parameters</span></span>  
 <span data-ttu-id="22e79-106">*Application*</span><span class="sxs-lookup"><span data-stu-id="22e79-106">*Application*</span></span>  
 <span data-ttu-id="22e79-107">URL の予約対象となるアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="22e79-107">The name of application to reserve the URL for.</span></span>  
  
 <span data-ttu-id="22e79-108">*URLString*</span><span class="sxs-lookup"><span data-stu-id="22e79-108">*URLString*</span></span>  
 <span data-ttu-id="22e79-109">予約する URL。</span><span class="sxs-lookup"><span data-stu-id="22e79-109">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="22e79-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="22e79-110">*lcid*</span></span>  
 <span data-ttu-id="22e79-111">返されるエラー メッセージに使用するロケール。</span><span class="sxs-lookup"><span data-stu-id="22e79-111">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="22e79-112">*Error*</span><span class="sxs-lookup"><span data-stu-id="22e79-112">*Error*</span></span>  
 <span data-ttu-id="22e79-113">[out] 発生したエラーの説明。</span><span class="sxs-lookup"><span data-stu-id="22e79-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="22e79-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="22e79-114">*HRESULT*</span></span>  
 <span data-ttu-id="22e79-115">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="22e79-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22e79-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="22e79-116">Return Value</span></span>  
 <span data-ttu-id="22e79-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="22e79-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="22e79-118">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="22e79-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22e79-119">解説</span><span class="sxs-lookup"><span data-stu-id="22e79-119">Remarks</span></span>  
 <span data-ttu-id="22e79-120">*UrlString* には仮想ディレクトリ名は含まれません。</span><span class="sxs-lookup"><span data-stu-id="22e79-120">*UrlString* does not include the virtual directory name.</span></span> <span data-ttu-id="22e79-121">仮想ディレクトリ名の設定用に、 [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="22e79-121">The [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="22e79-122">現在の Windows サービス アカウントに対して URL 予約が作成されます。</span><span class="sxs-lookup"><span data-stu-id="22e79-122">URL reservations are created for the current windows service account.</span></span> <span data-ttu-id="22e79-123">Windows サービス アカウントを変更するには、すべての URL 予約を手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22e79-123">Changing the windows service account requires updating all the URL reservations manually.</span></span>  
  
 <span data-ttu-id="22e79-124">このメソッドを実行すると、すべてのアプリケーション ドメインで強制力の高いリサイクル処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="22e79-124">This method causes all application domains to hard recycle.</span></span> <span data-ttu-id="22e79-125">この処理が完了した後に、アプリケーション ドメインが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="22e79-125">Application domains are restarted after this operation is complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22e79-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="22e79-126">Requirements</span></span>  
 <span data-ttu-id="22e79-127">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22e79-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e79-128">参照</span><span class="sxs-lookup"><span data-stu-id="22e79-128">See Also</span></span>  
 [<span data-ttu-id="22e79-129">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="22e79-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
