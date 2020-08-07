---
title: URL でデバイス情報設定を指定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00cd1fdc3b5fbe129ae4d51b220a11bc48b4744c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719443"
---
# <a name="specify-device-information-settings-in-a-url"></a><span data-ttu-id="110da-102">URL でデバイス情報設定を指定する</span><span class="sxs-lookup"><span data-stu-id="110da-102">Specify Device Information Settings in a URL</span></span>
  <span data-ttu-id="110da-103">デバイス情報設定は、表示拡張機能に渡すパラメーターのことです。</span><span class="sxs-lookup"><span data-stu-id="110da-103">Device information settings are parameters that are passed to a rendering extension.</span></span> <span data-ttu-id="110da-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート サーバー Web サービスのメソッドを使用してレポートを表示する場合は、`DeviceInfo` XML 要素を入力パラメーターとして渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="110da-104">If you use the methods of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service to render a report, a `DeviceInfo` XML element is passed as an input parameter.</span></span> <span data-ttu-id="110da-105">`DeviceInfo` 要素の子要素は、各種表示拡張機能のデバイス情報設定に固有です。</span><span class="sxs-lookup"><span data-stu-id="110da-105">Child elements of the `DeviceInfo` element are specific to the device information settings of different rendering extensions.</span></span> <span data-ttu-id="110da-106">*rc:tag=value* パラメーターの文字列を使用することによって、デバイス情報設定を URL に含めることができます。ここでは、 *tag* はアクセス先デバイス情報設定要素の名前です。</span><span class="sxs-lookup"><span data-stu-id="110da-106">You can include device information settings in a URL by using the *rc:tag=value* parameter string, where *tag* is the name of the device information settings element being accessed.</span></span> <span data-ttu-id="110da-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のデバイス情報設定の詳細については、「[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="110da-107">For more information about device information settings in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="110da-108">例</span><span class="sxs-lookup"><span data-stu-id="110da-108">Example</span></span>  
 <span data-ttu-id="110da-109">次の例では、画像表示拡張機能の *OutputFormat* デバイス情報設定を使用して、指定されたレポートの形式を JPEG に設定します。読みやすいように改行しています。</span><span class="sxs-lookup"><span data-stu-id="110da-109">The following example sets the format of the specified report to JPEG by using the *OutputFormat* device information setting of the image rendering extension (the line breaks have been added for legibility):</span></span>  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a><span data-ttu-id="110da-110">参照</span><span class="sxs-lookup"><span data-stu-id="110da-110">See Also</span></span>  
 <span data-ttu-id="110da-111">[URL アクセス (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="110da-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="110da-112">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="110da-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
