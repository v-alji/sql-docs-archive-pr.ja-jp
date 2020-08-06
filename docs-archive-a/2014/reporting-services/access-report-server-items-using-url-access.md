---
title: URL アクセスを使用したレポート サーバー アイテムへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6693419490c1b3770ccb41b2645cbdba8996630a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642630"
---
# <a name="access-report-server-items-using-url-access"></a><span data-ttu-id="b592d-102">URL アクセスを使用したレポート サーバー アイテムへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b592d-102">Access Report Server Items Using URL Access</span></span>
  <span data-ttu-id="b592d-103">このトピックでは、*rs:Command*=*Value* を使用してレポート サーバー データベースまたは SharePoint サイトにある異なる種類のカタログ アイテムにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b592d-103">This topic describes how to access catalog items of different types in a report server data base or in a SharePoint site using *rs:Command*=*Value*.</span></span>  
  
 <span data-ttu-id="b592d-104">このパラメーター文字列を追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b592d-104">It is not necessary to add this parameter string.</span></span> <span data-ttu-id="b592d-105">この文字列を省略した場合、レポート サーバーがアイテムの種類を評価し、適切なパラメーター値を自動的に選択します。</span><span class="sxs-lookup"><span data-stu-id="b592d-105">If you omit it, the report server evaluates the item type and selects the appropriate parameter value automatically.</span></span> <span data-ttu-id="b592d-106">ただし、URL に *rs:Command*=*Value* 文字列を使用することで、レポート サーバーのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="b592d-106">However, using the *rs:Command*=*Value* string in the URL improves the performance of the report server.</span></span>  
  
 <span data-ttu-id="b592d-107">以下の例では、 `_vti_bin` プロキシ構文に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b592d-107">Note the `_vti_bin` proxy syntax in the examples below.</span></span> <span data-ttu-id="b592d-108">プロキシ構文の詳細については、「 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b592d-108">For more information about using the proxy syntax, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="access-a-report"></a><span data-ttu-id="b592d-109">レポートへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b592d-109">Access a Report</span></span>  
 <span data-ttu-id="b592d-110">ブラウザーでレポートを表示するには、 *rs: Command* = *Render*パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b592d-110">To view a report in the browser, use the *rs:Command*=*Render* parameter.</span></span> <span data-ttu-id="b592d-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b592d-111">For example:</span></span>  
  
 <span data-ttu-id="b592d-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="b592d-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
 <span data-ttu-id="b592d-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="b592d-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="b592d-114">SharePoint および `_vti_bin` HTTP プロキシ経由で要求をルーティングする [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プロキシ構文を URL に含めることは重要です。</span><span class="sxs-lookup"><span data-stu-id="b592d-114">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="b592d-115">プロキシによって、HTTP 要求にいくつかのコンテキストが追加されます。これは、SharePoint モード レポート サーバーに対してレポートを適切に実行するために必要なコンテキストです。</span><span class="sxs-lookup"><span data-stu-id="b592d-115">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
## <a name="access-a-resource"></a><span data-ttu-id="b592d-116">リソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b592d-116">Access a Resource</span></span>  
 <span data-ttu-id="b592d-117">リソースにアクセスするには、 *rs: Command* = *GetResourceContents*パラメーターを使用します。リソースがブラウザーと互換性がある場合 (イメージなど)、ブラウザーで開かれます。</span><span class="sxs-lookup"><span data-stu-id="b592d-117">To access a resource, use the *rs:Command*=*GetResourceContents* parameter.If the resource is compatible with the browser, such as an image, it is opened in the browser.</span></span> <span data-ttu-id="b592d-118">それ以外の場合は、ファイルまたはリソースを開くか、ディスクに保存するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="b592d-118">Otherwise, you are prompted to open or save the file or resource to disk.</span></span>  
  
 <span data-ttu-id="b592d-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="b592d-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span></span>  
  
 <span data-ttu-id="b592d-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="b592d-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span></span>  
  
## <a name="access-a-data-source"></a><span data-ttu-id="b592d-121">データ ソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b592d-121">Access a Data Source</span></span>  
 <span data-ttu-id="b592d-122">データソースにアクセスするには、 *rs: Command* = *GetDataSourceContents*パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b592d-122">To access a data source, use the *rs:Command*=*GetDataSourceContents* parameter.</span></span> <span data-ttu-id="b592d-123">ブラウザーで XML がサポートされている場合、そのデータ ソース定義が表示されます。ただし、目的のデータ ソースに対して `Read Contents` 権限が与えられている認証ユーザーであることが条件となります。</span><span class="sxs-lookup"><span data-stu-id="b592d-123">If your browser supports XML, the data source definition is displayed if you are an authenticated user with `Read Contents` permission on the data source.</span></span> <span data-ttu-id="b592d-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b592d-124">For example:</span></span>  
  
 <span data-ttu-id="b592d-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="b592d-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="b592d-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="b592d-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="b592d-127">XML 構造は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="b592d-127">The XML structure might look similar to the following example:</span></span>  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 <span data-ttu-id="b592d-128">接続文字列は、レポート サーバーの **SecureConnectionLevel** 設定に基づいて返されます。</span><span class="sxs-lookup"><span data-stu-id="b592d-128">The connection string is returned based on the **SecureConnectionLevel** setting of the report server.</span></span> <span data-ttu-id="b592d-129">**SecureConnectionLevel** 設定の詳細については、「 [セキュリティで保護された Web サービス メソッドの使用](report-server-web-service/net-framework/using-secure-web-service-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b592d-129">For more information about the **SecureConnectionLevel** setting, see [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).</span></span>  
  
## <a name="access-the-contents-of-a-folder"></a><span data-ttu-id="b592d-130">フォルダーのコンテンツへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b592d-130">Access the Contents of a Folder</span></span>  
 <span data-ttu-id="b592d-131">フォルダーの内容にアクセスするには、 *rs: Command* = *getchildren*パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b592d-131">To access the contents of a folder, use the *rs:Command*=*GetChildren* parameter.</span></span> <span data-ttu-id="b592d-132">要求されたフォルダーのサブフォルダー、レポート、データ ソース、およびリソースへのリンクを含む汎用フォルダー ナビゲーション ページが返されます。</span><span class="sxs-lookup"><span data-stu-id="b592d-132">A generic folder-navigation page is returned that contains links to the subfolders, reports, data sources, and resources in the requested folder.</span></span> <span data-ttu-id="b592d-133">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b592d-133">For example:</span></span>  
  
 <span data-ttu-id="b592d-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="b592d-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="b592d-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="b592d-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="b592d-136">表示されるユーザー インターフェイスは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS) で使用されるディレクトリ参照モードと似ています。</span><span class="sxs-lookup"><span data-stu-id="b592d-136">The user interface you see is similar to the directory browsing mode used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS).</span></span> <span data-ttu-id="b592d-137">ビルド番号を含むレポート サーバーのバージョン番号もフォルダー一覧の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b592d-137">The version number, including the build number, of the report server is also displayed below the folder listing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b592d-138">参照</span><span class="sxs-lookup"><span data-stu-id="b592d-138">See Also</span></span>  
 <span data-ttu-id="b592d-139">[SSRS&#41;&#40;URL アクセス](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b592d-139">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="b592d-140">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="b592d-140">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
