---
title: Detail プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 060fbaba2b8d4f5a5171e8aa7995432622ba2ba0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719533"
---
# <a name="detail-property"></a><span data-ttu-id="8c906-102">Detail プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c906-102">Detail Property</span></span>
  <span data-ttu-id="8c906-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** クラスの **Detail** プロパティの XML 構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8c906-103">The **Detail** property of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** class has the following XML structure:</span></span>  
  
## <a name="elements"></a><span data-ttu-id="8c906-104">要素</span><span class="sxs-lookup"><span data-stu-id="8c906-104">Elements</span></span>  
 <span data-ttu-id="8c906-105">**詳細**</span><span class="sxs-lookup"><span data-stu-id="8c906-105">**Detail**</span></span>  
 <span data-ttu-id="8c906-106">他のすべてのエラー詳細要素を含む最上位要素。</span><span class="sxs-lookup"><span data-stu-id="8c906-106">The top-level element that contains all other error detail elements.</span></span>  
  
 <span data-ttu-id="8c906-107">**ErrorCode**</span><span class="sxs-lookup"><span data-stu-id="8c906-107">**ErrorCode**</span></span>  
 <span data-ttu-id="8c906-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 固有のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8c906-108">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-specific error code.</span></span>  
  
 <span data-ttu-id="8c906-109">**Httpstatus 別**</span><span class="sxs-lookup"><span data-stu-id="8c906-109">**HttpStatus**</span></span>  
 <span data-ttu-id="8c906-110">HTTP ステータス コード。</span><span class="sxs-lookup"><span data-stu-id="8c906-110">The HTTP status code.</span></span>  
  
 <span data-ttu-id="8c906-111">**Message**</span><span class="sxs-lookup"><span data-stu-id="8c906-111">**Message**</span></span>  
 <span data-ttu-id="8c906-112">レポート サーバーが割り当てたエラー メッセージとエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8c906-112">The error message and the error code assigned by the report server.</span></span>  
  
 <span data-ttu-id="8c906-113">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="8c906-113">**HelpLink**</span></span>  
 <span data-ttu-id="8c906-114">エラーの詳細情報を参照できる Web サイトへのヘルプ リンクの URL。</span><span class="sxs-lookup"><span data-stu-id="8c906-114">The Help link URL to a Web site at which further information about the error can be found.</span></span> <span data-ttu-id="8c906-115">詳細については、「[HelpLink 要素](helplink-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c906-115">For more information, see [HelpLink Element](helplink-element.md).</span></span>  
  
 <span data-ttu-id="8c906-116">**LinkID**</span><span class="sxs-lookup"><span data-stu-id="8c906-116">**LinkID**</span></span>  
 <span data-ttu-id="8c906-117">リンクに割り当てられた ID です。</span><span class="sxs-lookup"><span data-stu-id="8c906-117">The ID assigned to the link.</span></span>  
  
 <span data-ttu-id="8c906-118">**同様**</span><span class="sxs-lookup"><span data-stu-id="8c906-118">**ProductName**</span></span>  
 <span data-ttu-id="8c906-119">製品の名前です。</span><span class="sxs-lookup"><span data-stu-id="8c906-119">The name of the product.</span></span> <span data-ttu-id="8c906-120">既定値は **Microsoft SQL Server Reporting Services** です。</span><span class="sxs-lookup"><span data-stu-id="8c906-120">The default value is **Microsoft SQL Server Reporting Services**.</span></span>  
  
 <span data-ttu-id="8c906-121">**ProductVersion**</span><span class="sxs-lookup"><span data-stu-id="8c906-121">**ProductVersion**</span></span>  
 <span data-ttu-id="8c906-122">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のバージョン。</span><span class="sxs-lookup"><span data-stu-id="8c906-122">The version of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8c906-123">最大長は 15 文字です。</span><span class="sxs-lookup"><span data-stu-id="8c906-123">The maximum length is 15 characters.</span></span> <span data-ttu-id="8c906-124">バージョン番号の形式は、8.00.0xxx.00 のようになります。</span><span class="sxs-lookup"><span data-stu-id="8c906-124">The format of the version number should be as follows: 8.00.0xxx.00.</span></span>  
  
 <span data-ttu-id="8c906-125">**ProductLocaleId**</span><span class="sxs-lookup"><span data-stu-id="8c906-125">**ProductLocaleId**</span></span>  
 <span data-ttu-id="8c906-126">アプリケーションの INTL DLL のロケール ID または言語 ID (0x41A など)。</span><span class="sxs-lookup"><span data-stu-id="8c906-126">The locale ID or language ID of the application's INTL DLL (for example, 0x41A).</span></span>  
  
 <span data-ttu-id="8c906-127">**オペレーティングシステム**</span><span class="sxs-lookup"><span data-stu-id="8c906-127">**OperatingSystem**</span></span>  
 <span data-ttu-id="8c906-128">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] インストール先のオペレーティング システム。</span><span class="sxs-lookup"><span data-stu-id="8c906-128">The operating system [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is installed on.</span></span> <span data-ttu-id="8c906-129">有効値は、依存しないオペレーティング システムの場合は **0**、[!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)] の場合は **1**、Windows XP の場合は **16** です。</span><span class="sxs-lookup"><span data-stu-id="8c906-129">Valid values include **0** for operating system independent, **1** for [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)], and **16** for Windows XP.</span></span>  
  
 <span data-ttu-id="8c906-130">**CountryLocaleId**</span><span class="sxs-lookup"><span data-stu-id="8c906-130">**CountryLocaleId**</span></span>  
 <span data-ttu-id="8c906-131">オペレーティング システムのロケール ID または言語 ID。</span><span class="sxs-lookup"><span data-stu-id="8c906-131">The locale ID or language ID of the operating system.</span></span> <span data-ttu-id="8c906-132">たとえば、Windows のフランス語バージョンの値は 0x040c です。</span><span class="sxs-lookup"><span data-stu-id="8c906-132">For example, the value for the French version of Windows is 0x040c.</span></span>  
  
 <span data-ttu-id="8c906-133">**MoreInformation**</span><span class="sxs-lookup"><span data-stu-id="8c906-133">**MoreInformation**</span></span>  
 <span data-ttu-id="8c906-134">メソッド実行中に発生した入れ子にされた例外を含む XML 文字列です。</span><span class="sxs-lookup"><span data-stu-id="8c906-134">An XML string that contains nested exceptions that occurred while the method ran.</span></span>  
  
 <span data-ttu-id="8c906-135">**ソース**</span><span class="sxs-lookup"><span data-stu-id="8c906-135">**Source**</span></span>  
 <span data-ttu-id="8c906-136">**MoreInformation** の子要素。</span><span class="sxs-lookup"><span data-stu-id="8c906-136">A child element of **MoreInformation**.</span></span> <span data-ttu-id="8c906-137">エラーのソースです。</span><span class="sxs-lookup"><span data-stu-id="8c906-137">The source of the error.</span></span>  
  
 <span data-ttu-id="8c906-138">**Message**</span><span class="sxs-lookup"><span data-stu-id="8c906-138">**Message**</span></span>  
 <span data-ttu-id="8c906-139">**MoreInformation** の子要素。</span><span class="sxs-lookup"><span data-stu-id="8c906-139">A child element of **MoreInformation**.</span></span> <span data-ttu-id="8c906-140">入れ子にされた例外のエラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="8c906-140">The error message of a nested exception.</span></span> <span data-ttu-id="8c906-141">この要素には、**ErrorCode** と **HelpLink** の XML 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8c906-141">This element includes XML attributes for **ErrorCode** and **HelpLink**.</span></span>  
  
 <span data-ttu-id="8c906-142">**Warnings**</span><span class="sxs-lookup"><span data-stu-id="8c906-142">**Warnings**</span></span>  
 <span data-ttu-id="8c906-143">レポート処理から返された警告を含む XML 文字列です。</span><span class="sxs-lookup"><span data-stu-id="8c906-143">An XML string that contains the warnings returned from report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c906-144">参照</span><span class="sxs-lookup"><span data-stu-id="8c906-144">See Also</span></span>  
 <span data-ttu-id="8c906-145">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8c906-145">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="8c906-146">[Reporting Services SoapException クラス](reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="8c906-146">[Reporting Services SoapException Class](reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="8c906-147">Detail プロパティを使用したエラー処理</span><span class="sxs-lookup"><span data-stu-id="8c906-147">Using the Detail Property to Handle Specific Errors</span></span>](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
