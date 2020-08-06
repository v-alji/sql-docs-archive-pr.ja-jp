---
title: URL 内でレポート パラメーターを渡す | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], passing parameters
- passing parameters [Reporting Services]
ms.assetid: f93a94cc-27b5-435a-aa85-69e6ec6459ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf41ed82728d5d7c840276e135937b08f83fb131
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739516"
---
# <a name="pass-a-report-parameter-within-a-url"></a><span data-ttu-id="687ff-102">URL 内でレポート パラメーターを渡す</span><span class="sxs-lookup"><span data-stu-id="687ff-102">Pass a Report Parameter Within a URL</span></span>
  <span data-ttu-id="687ff-103">レポート パラメーターはレポート URL に含めることでレポートに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="687ff-103">You can pass report parameters to a report by including them in a report URL.</span></span> <span data-ttu-id="687ff-104">このような URL パラメーターにはプレフィックスを付けません。パラメーターはレポート処理エンジンに直接渡されるためです。</span><span class="sxs-lookup"><span data-stu-id="687ff-104">These URL parameters are not prefixed because they are passed directly to the report processing engine.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="687ff-105">SharePoint および `_vti_bin` HTTP プロキシ経由で要求をルーティングする [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プロキシ構文を URL に含めることは重要です。</span><span class="sxs-lookup"><span data-stu-id="687ff-105">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="687ff-106">プロキシによって、HTTP 要求にいくつかのコンテキストが追加されます。これは、SharePoint モード レポート サーバーに対してレポートを適切に実行するために必要なコンテキストです。</span><span class="sxs-lookup"><span data-stu-id="687ff-106">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
>   
>  <span data-ttu-id="687ff-107">プロキシ構文を含めない場合は、パラメーターの前に*rp:* というプレフィックスを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="687ff-107">If you don't include the proxy syntax, then you need to prefix the parameter with *rp:*.</span></span>  
  
 <span data-ttu-id="687ff-108">すべてのクエリ パラメーターには、対応するレポート パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="687ff-108">All query parameters can have corresponding report parameters.</span></span> <span data-ttu-id="687ff-109">クエリ パラメーターをレポートに渡すには、対応するレポート パラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="687ff-109">You pass a query parameter to a report by passing the corresponding report parameter.</span></span> <span data-ttu-id="687ff-110">詳細については、「[リレーショナル クエリ デザイナーでのクエリの作成 &#40;レポート ビルダーおよび SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="687ff-110">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="687ff-111">レポート パラメーターでは大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="687ff-111">Report parameters are case-sensitive.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="687ff-112">レポート パラメーターでは大文字と小文字が区別され、次の特殊文字が使用されます。</span><span class="sxs-lookup"><span data-stu-id="687ff-112">Report parameters are case-sensitive and utilize the following special characters:</span></span>  
> 
>  -   <span data-ttu-id="687ff-113">URL 文字列では、URL エンコード規格に基づいてすべての空白文字が文字列 "%20" に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="687ff-113">Any space characters in the URL string are replaced with the characters "%20," according to URL encoding standards.</span></span>  
> -   <span data-ttu-id="687ff-114">URL のパラメーター部分にある空白文字はプラス記号 (+) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="687ff-114">A space character in the parameter portion of the URL is replaced with a plus character (+).</span></span>  
> -   <span data-ttu-id="687ff-115">文字列の任意の部分にあるセミコロンは文字列 "%3A" に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="687ff-115">A semicolon in any portion of the string is replaced with the characters "%3A."</span></span>  
> -   <span data-ttu-id="687ff-116">通常、適切な URL エンコードはブラウザーによって自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="687ff-116">Browsers should automatically perform the proper URL encoding.</span></span> <span data-ttu-id="687ff-117">これらの文字を手動でエンコードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="687ff-117">You do not have to encode any of the characters manually.</span></span>  
  
 <span data-ttu-id="687ff-118">URL 内にレポート パラメーターを設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="687ff-118">To set a report parameter within a URL, use the following syntax:</span></span>  
  
```  
  
parameter=value  
```  
  
 <span data-ttu-id="687ff-119">たとえば、レポートで定義されている "ReportMonth" と "ReportYear" の 2 つのパラメーターを指定するには、ネイティブ モードのレポート サーバーで次の URL を使用します。</span><span class="sxs-lookup"><span data-stu-id="687ff-119">For example, to specify two parameters, "ReportMonth" and "ReportYear", defined in a report, use the following URL for a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="687ff-120">たとえば、レポートで定義されている同じ 2 つのパラメーターを指定するには、SharePoint 統合モードのレポート サーバーで次の URL を使用します。</span><span class="sxs-lookup"><span data-stu-id="687ff-120">For example, to specify the same two parameters defined in a report, use the following URL for a SharePoint integrated mode report server.</span></span> <span data-ttu-id="687ff-121">`/_vti_bin`に注意してください。</span><span class="sxs-lookup"><span data-stu-id="687ff-121">Note the `/_vti_bin`:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="687ff-122">パラメーターに NULL 値を渡すには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="687ff-122">To pass a null value for a parameter, use the following syntax:</span></span>  
  
```  
  
parameter  
:isnull=true  
  
```  
  
 <span data-ttu-id="687ff-123">たとえば、</span><span class="sxs-lookup"><span data-stu-id="687ff-123">For example,</span></span>  
  
```  
SalesOrderNumber:isnull=true  
```  
  
 <span data-ttu-id="687ff-124">`Boolean` 値を渡す場合、False には 0 を、True には 1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="687ff-124">To pass a `Boolean` value, use 0 for false and 1 for true.</span></span> <span data-ttu-id="687ff-125">`Float` 値を渡すには、サーバー ロケールに応じた小数点の記号を指定します。</span><span class="sxs-lookup"><span data-stu-id="687ff-125">To pass a `Float` value, include the decimal separator of the server locale</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="687ff-126">既定値を持つレポート パラメーターがレポートに含まれており、`Prompt` プロパティの値が `false` である場合 (つまりレポート マネージャーで Prompt User プロパティが選択されていない場合)、URL 内でそのレポート パラメーターに値を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="687ff-126">If your report contains a report parameter that has a default value and the value of the `Prompt` property is `false` (that is, the Prompt User property is not selected in Report Manager), then you cannot pass a value for that report parameter within a URL.</span></span> <span data-ttu-id="687ff-127">管理者はこの方法を使用して、エンド ユーザーが特定のレポート パラメーターの値を追加したり変更したりすることを禁止できます。</span><span class="sxs-lookup"><span data-stu-id="687ff-127">This provides administrators an option for preventing end users from adding or modifying the values of certain report parameters.</span></span>  
  
##  <a name="additional-examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="687ff-128">その他の例</span><span class="sxs-lookup"><span data-stu-id="687ff-128">Additional Examples</span></span>  
 <span data-ttu-id="687ff-129">次の URL の例には、空白や複数のパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="687ff-129">The following URL example includes spaces and multiple parameters</span></span>  
  
-   <span data-ttu-id="687ff-130">"SQL Server User Education Team" のフォルダー名には空白が含まれているため、各空白が "+" に置き換わります。</span><span class="sxs-lookup"><span data-stu-id="687ff-130">Folder name of "SQL Server User Education Team" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="687ff-131">"team project report" というレポート名には空白が含まれているため、各空白が "+" に置き換わります。</span><span class="sxs-lookup"><span data-stu-id="687ff-131">Report name of "team project report" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="687ff-132">値 "xgroup" を指定した "teamgrouping2" および値 "ygroup" を指定した "teamgrouping1" という 2 つのパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="687ff-132">Passes two parameters of "teamgrouping2" with a value of "xgroup" and "teamgrouping1" with a value of "ygroup".</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup  
```  
  
 <span data-ttu-id="687ff-133">次の URL の例には、複数の値を持つパラメーター "OrderID" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="687ff-133">The following URL example includes a multi-value parameter "OrderID.</span></span> <span data-ttu-id="687ff-134">複数の値を持つパラメーターの形式では、値ごとにパラメーター名を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="687ff-134">The format for a Multi-Value parameter is to repeat the parameter name for each value.</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup&OrderID=747&OrderID=787&OrderID=12  
```  
  
 <span data-ttu-id="687ff-135">次の URL の例では、ネイティブモードのレポートサーバーに対して、値が "7/1/2005" の*Sellstartdate*の1つのパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="687ff-135">The following URL example passes a single parameter of *SellStartDate* with a value of "7/1/2005", for a native mode report server.</span></span>  
  
```  
http://myserver/ReportServer/Pages/ReportViewer.aspx?%2fProduct_and_Sales_Report_AdventureWorks&SellStartDate=7/1/2005  
```  
  
## <a name="see-also"></a><span data-ttu-id="687ff-136">参照</span><span class="sxs-lookup"><span data-stu-id="687ff-136">See Also</span></span>  
 <span data-ttu-id="687ff-137">[SSRS&#41;&#40;URL アクセス](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="687ff-137">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="687ff-138">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="687ff-138">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
