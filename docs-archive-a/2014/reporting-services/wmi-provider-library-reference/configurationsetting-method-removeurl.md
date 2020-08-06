---
title: RemoveURL メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a32989e8ce8986b785e829d8cc7fcf58fbbf240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641972"
---
# <a name="removeurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="aaa87-102">RemoveURL メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="aaa87-102">RemoveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="aaa87-103">レポート サーバー用に予約されている URL を削除します。</span><span class="sxs-lookup"><span data-stu-id="aaa87-103">Removes a URL reserved for the report server.</span></span> <span data-ttu-id="aaa87-104">削除の対象となる URL が複数ある場合は、この API を 1 つずつ呼び出して URL を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa87-104">If there are multiple URLs that need to be removed, this must be done one by one calling this API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa87-105">構文</span><span class="sxs-lookup"><span data-stu-id="aaa87-105">Syntax</span></span>  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaa87-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aaa87-106">Parameters</span></span>  
 <span data-ttu-id="aaa87-107">*Application*</span><span class="sxs-lookup"><span data-stu-id="aaa87-107">*Application*</span></span>  
 <span data-ttu-id="aaa87-108">予約を削除する対象のアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="aaa87-108">The name of application for which to remove the reservation.</span></span>  
  
 <span data-ttu-id="aaa87-109">*URLString*</span><span class="sxs-lookup"><span data-stu-id="aaa87-109">*URLString*</span></span>  
 <span data-ttu-id="aaa87-110">予約する URL。</span><span class="sxs-lookup"><span data-stu-id="aaa87-110">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="aaa87-111">*lcid*</span><span class="sxs-lookup"><span data-stu-id="aaa87-111">*lcid*</span></span>  
 <span data-ttu-id="aaa87-112">返されるエラー メッセージに使用するロケール。</span><span class="sxs-lookup"><span data-stu-id="aaa87-112">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="aaa87-113">*Error*</span><span class="sxs-lookup"><span data-stu-id="aaa87-113">*Error*</span></span>  
 <span data-ttu-id="aaa87-114">[out] 発生したエラーの説明。</span><span class="sxs-lookup"><span data-stu-id="aaa87-114">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="aaa87-115">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="aaa87-115">*HRESULT*</span></span>  
 <span data-ttu-id="aaa87-116">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="aaa87-116">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaa87-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="aaa87-117">Return Value</span></span>  
 <span data-ttu-id="aaa87-118">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="aaa87-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="aaa87-119">値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aaa87-119">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaa87-120">解説</span><span class="sxs-lookup"><span data-stu-id="aaa87-120">Remarks</span></span>  
 <span data-ttu-id="aaa87-121">*UrlString* には、仮想ディレクトリの名前が含まれていません。その目的では、[SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="aaa87-121">*UrlString* does not include the Virtual Directory name - the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="aaa87-122">[ReserveURL](configurationsetting-method-reserveurl.md) メソッドを呼び出す前に、 *Application* パラメーターの VirtualDirectory 構成プロパティの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa87-122">Before calling the [ReserveURL](configurationsetting-method-reserveurl.md) method, you must supply a value for the VirtualDirectory configuration property for the *Application* parameter.</span></span> <span data-ttu-id="aaa87-123">[SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) メソッドを利用し、VirtualDirectory プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="aaa87-123">Use the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method to set the VirtualDirectory property.</span></span>  
  
 <span data-ttu-id="aaa87-124">SSL 証明書が [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で準備されていて、他の URL でその証明書を使用する必要がない場合、その SSL 証明書は削除されます。</span><span class="sxs-lookup"><span data-stu-id="aaa87-124">If an SSL Certificate was provisioned by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and no other URLs need it, it is removed.</span></span>  
  
 <span data-ttu-id="aaa87-125">このメソッドにより、すべての非構成アプリケーション ドメインで強制力の高いリサイクル処理が実行され、その処理中にそれらのドメインは停止します。アプリケーション ドメインは、この処理の完了後に再起動します。</span><span class="sxs-lookup"><span data-stu-id="aaa87-125">This method causes all non-configuration app domains to hard recycle and stop during this operation; app domains are restarted after this operation complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa87-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="aaa87-126">Requirements</span></span>  
 <span data-ttu-id="aaa87-127">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa87-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa87-128">参照</span><span class="sxs-lookup"><span data-stu-id="aaa87-128">See Also</span></span>  
 [<span data-ttu-id="aaa87-129">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="aaa87-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
