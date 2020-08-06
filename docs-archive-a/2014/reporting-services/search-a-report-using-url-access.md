---
title: URL アクセスを使用してレポートを検索する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b45f3fabf58a0980d41ee7b4b89a771655477d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739192"
---
# <a name="search-a-report-using-url-access"></a><span data-ttu-id="77017-102">URL アクセスを使用してレポートを検索する</span><span class="sxs-lookup"><span data-stu-id="77017-102">Search a Report Using URL Access</span></span>
  <span data-ttu-id="77017-103">URL アクセスを使用して、レポート内に特定の文字列があるかどうかを検索できます。</span><span class="sxs-lookup"><span data-stu-id="77017-103">You can search a report for a specific set of text using URL access.</span></span> <span data-ttu-id="77017-104">レポート内を検索するには、URL の *rc:FindString* パラメーターの値として検索する文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="77017-104">To search a report, set the value of the *rc:FindString* parameter on the URL equal to the text for which you want to search.</span></span> <span data-ttu-id="77017-105">さらに、 *rc:StartFind* パラメーターと *rc:EndFind* パラメーターを使用すれば、検索対象をレポート内の特定のページに絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="77017-105">Additionally, use the *rc:StartFind* and *rc:EndFind* parameters to narrow your search to specific pages within the report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77017-106">例</span><span class="sxs-lookup"><span data-stu-id="77017-106">Example</span></span>  
 <span data-ttu-id="77017-107">次の URL アクセスの例では、Product Catalog サンプル レポートの 1 ～ 5 ページを検索し、最初に出現する Mountain-400 という文字列を探します。</span><span class="sxs-lookup"><span data-stu-id="77017-107">The following URL access example searches for the first occurrence of the text "Mountain-400" in the Product Catalog sample report starting with page one and ending with page five:</span></span>  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a><span data-ttu-id="77017-108">参照</span><span class="sxs-lookup"><span data-stu-id="77017-108">See Also</span></span>  
 <span data-ttu-id="77017-109">[URL アクセス (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="77017-109">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="77017-110">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="77017-110">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
