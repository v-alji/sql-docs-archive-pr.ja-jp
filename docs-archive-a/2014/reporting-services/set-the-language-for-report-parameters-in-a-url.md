---
title: URL でレポート パラメーターの言語を設定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8087a181906517bb60d4cd6839eed0681f52a5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716061"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a><span data-ttu-id="b4a94-102">URL でレポート パラメーターの言語を設定する</span><span class="sxs-lookup"><span data-stu-id="b4a94-102">Set the Language for Report Parameters in a URL</span></span>
  <span data-ttu-id="b4a94-103">*rs:ParameterLanguage* URL アクセス パラメーターは、カルチャが特定されたレポート パラメーター (日付、時刻、通貨、数値など) がブラウザーの言語を使用して解釈されるという問題を軽減します。</span><span class="sxs-lookup"><span data-stu-id="b4a94-103">The *rs:ParameterLanguage* URL access parameter alleviates a problem in which culture-sensitive report parameters, such as dates, times, currency, and numbers, are interpreted using the browser language.</span></span> <span data-ttu-id="b4a94-104">*rs:ParameterLanguage*を使用すると、URL はブラウザーとは無関係に解釈されるようになります。</span><span class="sxs-lookup"><span data-stu-id="b4a94-104">With *rs:ParameterLanguage*, the URL is now interpreted independently of the browser.</span></span> <span data-ttu-id="b4a94-105">たとえば、レポート サーバーの地域がドイツ語に設定されている場合、ユーザーが [英語 (U.S.)] に設定されているブラウザーを使用してレポートの URL にアクセスすると、レポート サーバーに渡されるパラメーター値は間違って解釈されます。</span><span class="sxs-lookup"><span data-stu-id="b4a94-105">For example, if the report server is set to a regional setting of German, but a user is accessing a report via a URL using a browser that is set to English-United States, parameter values that are passed to a report server will be misinterpreted.</span></span>  
  
 <span data-ttu-id="b4a94-106">レポートには次の URL を検討してください。</span><span class="sxs-lookup"><span data-stu-id="b4a94-106">Consider the following URL to a report:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 <span data-ttu-id="b4a94-107">上記の場合、カルチャ "de-de" で実行されているサーバーでは、電子メール サブスクリプションまたはハイパーリンクを使用して URL が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b4a94-107">In the above case, the server, running under a culture of "de-de", generates a URL either through an e-mail subscription or a hyperlink.</span></span> <span data-ttu-id="b4a94-108">上記のハイパーリンクは、レポートのパラメーターが、ドイツ語の日付と時刻の標準に基づいた開始日 2008 年 10 月 4 日と終了日 2008 年 10 月 11 日に設定される必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="b4a94-108">The hyperlink indicates that the report should be parameterized by a start date of October 4, 2008 and an end date of October 11, 2008 according to German date/time standards.</span></span> <span data-ttu-id="b4a94-109">この場合に、ユーザーが "en-us" に設定されたブラウザーを使用して URL にアクセスすると、サーバーで解釈される値が、英語 (U.S.) の日付と時刻の標準により、2008 年 4 月 10 日と 2008 年 11 月 10 日になります。</span><span class="sxs-lookup"><span data-stu-id="b4a94-109">However, a user that is accessing the URL through a browser set to "en-us" forces the server to interpret the values as April 10, 2008 and November 10, 2008 under United States English date/time standards.</span></span> <span data-ttu-id="b4a94-110">この問題を解決するには、*rs:ParameterLanguage* を使用してパラメーターの解釈をブラウザーの言語より優先させます。</span><span class="sxs-lookup"><span data-stu-id="b4a94-110">To fix the problem, *rs:ParameterLanguage* can be used to override the browser language for parameter interpretation:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 <span data-ttu-id="b4a94-111">URL アクセス パラメーター **rc:Parameters** には、値 **True** と *False*以外に、値 **Collapsed**を渡すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b4a94-111">In addition to a value of **true** and **false** for the URL access parameter *rc:Parameters*, you can now pass a value of **Collapsed**.</span></span> <span data-ttu-id="b4a94-112">URL に *rc:Parameters*=**Collapsed** を使用すると、HTML ビューアーのパラメーター プロンプト領域が見えないように折りたたまれます。ただし、ユーザーが切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="b4a94-112">When using *rc:Parameters*=**Collapsed** on a URL, the parameter prompt area of the HTML viewer is collapsed out of sight, but can still be toggled by the user.</span></span> <span data-ttu-id="b4a94-113">値を **False** に設定すると、HTML ビューアーのツール バーからパラメーター プロンプト領域が削除され、エンド ユーザーがその領域を使用できません。</span><span class="sxs-lookup"><span data-stu-id="b4a94-113">A value of **false** removes the parameter prompt area from the HTML viewer toolbar and makes it unavailable to the end-user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a94-114">参照</span><span class="sxs-lookup"><span data-stu-id="b4a94-114">See Also</span></span>  
 <span data-ttu-id="b4a94-115">[URL アクセス (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b4a94-115">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="b4a94-116">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="b4a94-116">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
