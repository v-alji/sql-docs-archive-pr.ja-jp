---
title: URL アクセスを使用してレポートをエクスポートする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69f340855e37ffde49aec0af096c094a142659d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711754"
---
# <a name="export-a-report-using-url-access"></a><span data-ttu-id="bc0d7-102">URL アクセスを使用してレポートをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="bc0d7-102">Export a Report Using URL Access</span></span>
  <span data-ttu-id="bc0d7-103">必要に応じて、 *rs: format*パラメーターを使用して、レポートを表示する形式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-103">You can optionally specify the format in which to render a report by using the *rs:Format* parameter.</span></span> <span data-ttu-id="bc0d7-104">たとえば、ネイティブ モードのレポート サーバーから直接レポートの PDF コピーを取得するには、次の URL を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-104">For example, to get a PDF copy of a report directly from a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 <span data-ttu-id="bc0d7-105">また、SharePoint 統合モードのレポート サーバーから取得するには、次の URL を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-105">And, from a SharePoint integrated mode report server:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 <span data-ttu-id="bc0d7-106">このパラメーターの有効値は、アクセス先レポート サーバーにインストールされているレポート表示拡張機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-106">Valid values for this parameter are based on the report rendering extensions that are installed on the report server being accessed.</span></span> <span data-ttu-id="bc0d7-107">一般的な拡張機能は HTML4.0、MHTML、IMAGE、EXCEL、WORD、CSV、PDF、XML、および NULL です。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-107">Common extensions are HTML4.0, MHTML, IMAGE, EXCEL, WORD, CSV, PDF, XML, and NULL.</span></span> <span data-ttu-id="bc0d7-108">指定した表示拡張機能がレポート サーバーにインストールされていない場合は、レポートが表示されず、エラーが生成されてブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-108">If a specified rendering extension is not installed on the report server, the report is not rendered and an error is generated and displayed in the browser.</span></span>  
  
 <span data-ttu-id="bc0d7-109">*Format* パラメーターを URL の一部として含めない場合は、レポート サーバーがブラウザーを検出し、適切な HTML 形式でレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="bc0d7-109">If you do not include the *Format* parameter as part of the URL, the report server detects the browser and renders the report in the appropriate HTML format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0d7-110">参照</span><span class="sxs-lookup"><span data-stu-id="bc0d7-110">See Also</span></span>  
 <span data-ttu-id="bc0d7-111">[SSRS&#41;&#40;URL アクセス](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bc0d7-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="bc0d7-112">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="bc0d7-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
