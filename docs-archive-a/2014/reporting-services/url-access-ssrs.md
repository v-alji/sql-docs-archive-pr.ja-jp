---
title: URL アクセス (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf44ea3c15c12f37eebf6e89faf4ff3affd64433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634813"
---
# <a name="url-access-ssrs"></a><span data-ttu-id="34de9-102">URL アクセス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="34de9-102">URL Access (SSRS)</span></span>
  <span data-ttu-id="34de9-103">SQL Server Reporting Services (SSRS) のレポート サーバーの URL アクセスにより、URL 要求を使用してレポート サーバーにコマンドを送信できます。</span><span class="sxs-lookup"><span data-stu-id="34de9-103">URL access of the report server in SQL Server Reporting Services (SSRS) enables you to send commands to a report server through a URL request.</span></span> <span data-ttu-id="34de9-104">たとえば、ネイティブ モードのレポート サーバーや SharePoint ライブラリのレポートの表示をカスタマイズすることができます。</span><span class="sxs-lookup"><span data-stu-id="34de9-104">For example, you can customize the rendering of a report on a native mode report server or in a SharePoint library.</span></span> <span data-ttu-id="34de9-105">特定のレポート パラメーター値のセットを使用してレポートを表示したり、レポートの関心のある特定ページを表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="34de9-105">You may have viewed the report using a specific set of report parameter values, or you may have been viewing a particular page of interest in the report.</span></span> <span data-ttu-id="34de9-106">この情報を、事前に定義された URL アクセス パラメーターを使用して URL にカプセル化することができます。</span><span class="sxs-lookup"><span data-stu-id="34de9-106">You can encapsulate this information in the URL using predefined URL access parameters.</span></span> <span data-ttu-id="34de9-107">表示形式またはレポート ビューアーのルック アンド フィールのパラメーターを埋め込むことで、レポート サーバーによるレポートの処理方法をさらにカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="34de9-107">You can further customize how the report server processes the report by embedding parameters for rendering formats or for the look and feel of the report viewer.</span></span> <span data-ttu-id="34de9-108">その後、この URL を電子メールまたは Web ページに直接貼り付けて、他のユーザーがブラウザーから同じ方法でレポートにアクセスできるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="34de9-108">You can then paste this URL directly into an email or Web page to let others to access your report in the same manner in the browser.</span></span>  
  
 <span data-ttu-id="34de9-109">URL アクセスを使用して実行できる他のアクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="34de9-109">Other actions you can perform through URL access are:</span></span>  
  
-   <span data-ttu-id="34de9-110">ルック アンド フィールの調節などのコマンドを HTML ビューアーに送信する</span><span class="sxs-lookup"><span data-stu-id="34de9-110">Send commands to the HTML viewer, such as adjusting its look and feel</span></span>  
  
-   <span data-ttu-id="34de9-111">カタログ フォルダーの子の一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="34de9-111">List the children of a catalog folder</span></span>  
  
-   <span data-ttu-id="34de9-112">カタログ アイテムの XML 定義を取得する</span><span class="sxs-lookup"><span data-stu-id="34de9-112">Retrieve the XML definition of a catalog item</span></span>  
  
-   <span data-ttu-id="34de9-113">特例のレポート履歴スナップショットを表示する</span><span class="sxs-lookup"><span data-stu-id="34de9-113">Render a specific report history snapshot</span></span>  
  
-   <span data-ttu-id="34de9-114">レポート セッションを管理する</span><span class="sxs-lookup"><span data-stu-id="34de9-114">Manage report sessions</span></span>  
  
 <span data-ttu-id="34de9-115">URL アクセスにより使用できるコマンドおよび設定の完全な一覧については、「 [URL Access Parameter Reference](url-access-parameter-reference.md)」(URL アクセス パラメーター リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34de9-115">For the complete list of commands and settings available through URL access, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="url-access-concepts"></a><span data-ttu-id="34de9-116">URL アクセスの概念</span><span class="sxs-lookup"><span data-stu-id="34de9-116">URL Access Concepts</span></span>  
 <span data-ttu-id="34de9-117">レポート サーバーに対する URL 要求には、レポート サーバーによって処理されるパラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="34de9-117">URL requests to the report server contain parameters that are processed by the report server.</span></span> <span data-ttu-id="34de9-118">レポート サーバーが URL 要求を処理する方法は、URL に含まれるパラメーター、パラメーター プレフィックス、アイテムの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="34de9-118">The way in which the report server handles URL requests depends on the parameters, parameter prefixes, and types of items that are included in the URL.</span></span> <span data-ttu-id="34de9-119">レポート サーバーの URL は、World Wide Web Consortium W3C/IETF 共同ドラフト仕様として提案されている URL フォーマット ガイドラインに準拠します。</span><span class="sxs-lookup"><span data-stu-id="34de9-119">Report server URLs adhere to the URL formatting guidelines as proposed by the joint World Wide Web Consortium W3C/IETF draft standard.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="34de9-120">の URL 機能は、標準的な URL アドレス指定をサポートするほとんどのインターネット ブラウザーやアプリケーションと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="34de9-120">URL functionality is compatible with most Internet browsers or applications that support standard URL addressing.</span></span>  
  
### <a name="url-access-syntax"></a><span data-ttu-id="34de9-121">URL アクセスの構文</span><span class="sxs-lookup"><span data-stu-id="34de9-121">URL Access Syntax</span></span>  
 <span data-ttu-id="34de9-122">URL 要求には、任意の順序で一覧表示される複数のパラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="34de9-122">URL requests can contain multiple parameters that are listed in any order.</span></span> <span data-ttu-id="34de9-123">パラメーターはアンパサンド (&) によって区切られ、名前と値のペアは等号 (=) によって区切られます。</span><span class="sxs-lookup"><span data-stu-id="34de9-123">Parameters are separated by an ampersand (&) and name/value pairs are separated by an equal sign (=).</span></span>  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="34de9-124">構文の説明</span><span class="sxs-lookup"><span data-stu-id="34de9-124">Syntax Description</span></span>  
 <span data-ttu-id="34de9-125">*rswebserviceurl*</span><span class="sxs-lookup"><span data-stu-id="34de9-125">*rswebserviceurl*</span></span>  
 <span data-ttu-id="34de9-126">レポート サーバーの Web サービスの URL。</span><span class="sxs-lookup"><span data-stu-id="34de9-126">The Web service URL of the report server.</span></span> <span data-ttu-id="34de9-127">ネイティブ モードでは、Reporting Services Configuration Manager に構成されているレポート サーバー インスタンスの Web サービスの URL です (「[レポート サーバー URL の構成 (SSRS 構成マネージャー)](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="34de9-127">For native mode, it is the Web service URL of the report server instance configured in Reporting Services Configuration Manager (see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)).</span></span> <span data-ttu-id="34de9-128">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34de9-128">For example:</span></span>  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 <span data-ttu-id="34de9-129">SharePoint 統合モードでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] に統合された SharePoint サイトの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]プロキシの URL です。</span><span class="sxs-lookup"><span data-stu-id="34de9-129">For SharePoint integrated mode, it is the URL of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy at a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="34de9-130">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34de9-130">For example:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  <span data-ttu-id="34de9-131">SharePoint および `_vti_bin` HTTP プロキシ経由で要求をルーティングする [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プロキシ構文を URL に含めることは重要です。</span><span class="sxs-lookup"><span data-stu-id="34de9-131">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="34de9-132">プロキシによって、HTTP 要求にいくつかのコンテキストが追加されます。これは、SharePoint モード レポート サーバーに対してレポートを適切に実行するために必要なコンテキストです。</span><span class="sxs-lookup"><span data-stu-id="34de9-132">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
 <span data-ttu-id="34de9-133">*pathinfo*</span><span class="sxs-lookup"><span data-stu-id="34de9-133">*pathinfo*</span></span>  
 <span data-ttu-id="34de9-134">ネイティブ モードのレポート サーバー データベース内のアイテムの相対パス名、または SharePoint カタログ内のアイテムの完全修飾 URL。</span><span class="sxs-lookup"><span data-stu-id="34de9-134">The relative path name of the item in the native mode report server database, or the fully qualified URL of the item in a SharePoint catalog.</span></span>  
  
 <span data-ttu-id="34de9-135">カタログ アイテムのパス。</span><span class="sxs-lookup"><span data-stu-id="34de9-135">The path of the catalog item.</span></span> <span data-ttu-id="34de9-136">ネイティブ モードでは、スラッシュ (`/`) から始まるレポート サーバー データベース内のアイテムの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="34de9-136">For native mode, it is the relative path of the item in the report server database, beginning with a slash (`/`).</span></span> <span data-ttu-id="34de9-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34de9-137">For example:</span></span>  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 <span data-ttu-id="34de9-138">SharePoint 統合モードでは、アイテムの拡張子を含む、SharePoint ライブラリ内のアイテムの完全修飾 URL です。</span><span class="sxs-lookup"><span data-stu-id="34de9-138">For SharePoint integrated mode, it is the fully qualified URL of the item in the SharePoint library, including the item extension.</span></span> <span data-ttu-id="34de9-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="34de9-139">For example:</span></span>  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 `&`  
 <span data-ttu-id="34de9-140">URL アクセス パラメーターの名前と値のペアを区切るために使用します。</span><span class="sxs-lookup"><span data-stu-id="34de9-140">Used to separate name and value pairs of URL access parameters.</span></span>  
  
 <span data-ttu-id="34de9-141">**prefix**</span><span class="sxs-lookup"><span data-stu-id="34de9-141">**prefix**</span></span>  
 <span data-ttu-id="34de9-142">省略可能。</span><span class="sxs-lookup"><span data-stu-id="34de9-142">Optional.</span></span> <span data-ttu-id="34de9-143">URL アクセス パラメーターのプレフィックス ( `rs:` や `rc:`など)。レポート サーバー内で実行している特定のプロセスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="34de9-143">A prefix for the URL access parameter (for example, `rs:` or `rc:`) that accesses a specific process running within the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34de9-144">URL アクセス パラメーターにプレフィックスが含まれていない場合は、レポート サーバーによってパラメーターがレポート パラメーターとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="34de9-144">If a prefix for a URL access parameter is not included, the parameter is processed by the report server as a report parameter.</span></span> <span data-ttu-id="34de9-145">レポート パラメーターではパラメーター プレフィックスが使用されず、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="34de9-145">Report parameters do not use a parameter prefix and are case-sensitive.</span></span>  
  
 <span data-ttu-id="34de9-146">**param**</span><span class="sxs-lookup"><span data-stu-id="34de9-146">**param**</span></span>  
 <span data-ttu-id="34de9-147">パラメーター名。</span><span class="sxs-lookup"><span data-stu-id="34de9-147">The parameter name.</span></span>  
  
 <span data-ttu-id="34de9-148">*value*</span><span class="sxs-lookup"><span data-stu-id="34de9-148">*value*</span></span>  
 <span data-ttu-id="34de9-149">使用しているパラメーターの値に対応する URL テキスト。</span><span class="sxs-lookup"><span data-stu-id="34de9-149">URL text corresponding to the value of the parameter being used.</span></span>  
  
 <span data-ttu-id="34de9-150">**注:** 使用可能な URL アクセス パラメーターの一覧については、「 [URL Access Parameter Reference](url-access-parameter-reference.md)」(URL アクセス パラメーター リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34de9-150">**Note:** For a list of the available URL access parameters, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span> <span data-ttu-id="34de9-151">URL でレポート パラメーターを渡す例については、「 [URL 内でレポート パラメーターを渡す](pass-a-report-parameter-within-a-url.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34de9-151">For examples passing report parameters on the URL, see [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="34de9-152">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="34de9-152">Related Tasks</span></span>  
  
|<span data-ttu-id="34de9-153">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="34de9-153">Task Descriptions</span></span>|<span data-ttu-id="34de9-154">リンク</span><span class="sxs-lookup"><span data-stu-id="34de9-154">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="34de9-155">レポート、共有データ ソース、リソースなどのレポート サーバー アイテムにアクセスする</span><span class="sxs-lookup"><span data-stu-id="34de9-155">Access report server items, such as reports, shared data sources, and resources.</span></span>|[<span data-ttu-id="34de9-156">URL アクセスを使用したレポート サーバー アイテムへのアクセス</span><span class="sxs-lookup"><span data-stu-id="34de9-156">Access Report Server Items Using URL Access</span></span>](access-report-server-items-using-url-access.md)|  
|<span data-ttu-id="34de9-157">レポート パラメーターをレポートに受け渡す</span><span class="sxs-lookup"><span data-stu-id="34de9-157">Pass report parameters to a report.</span></span>|[<span data-ttu-id="34de9-158">URL 内でレポート パラメーターを渡す</span><span class="sxs-lookup"><span data-stu-id="34de9-158">Pass a Report Parameter Within a URL</span></span>](pass-a-report-parameter-within-a-url.md)|  
|<span data-ttu-id="34de9-159">日付、通貨など、ロケール固有の解釈を定義する URL アクセス文字列にレポート パラメーターのロケールを設定する</span><span class="sxs-lookup"><span data-stu-id="34de9-159">Set the locale of the report parameters in the URL access string, which defines the locale-specific interpretations of dates, currencies, and so on.</span></span>|[<span data-ttu-id="34de9-160">URL でレポート パラメーターの言語を設定する</span><span class="sxs-lookup"><span data-stu-id="34de9-160">Set the Language for Report Parameters in a URL</span></span>](set-the-language-for-report-parameters-in-a-url.md)|  
|<span data-ttu-id="34de9-161">レポートの表示形式をカスタマイズする表示拡張機能固有の設定を送信する</span><span class="sxs-lookup"><span data-stu-id="34de9-161">Send rendering extension specific settings that customize how the report is rendered.</span></span>|[<span data-ttu-id="34de9-162">URL でデバイス情報設定を指定する</span><span class="sxs-lookup"><span data-stu-id="34de9-162">Specify Device Information Settings in a URL</span></span>](specify-device-information-settings-in-a-url.md)|  
|<span data-ttu-id="34de9-163">ブラウザーに表示せずに、レポートを直接ファイル形式にエクスポートする</span><span class="sxs-lookup"><span data-stu-id="34de9-163">Export a report directly to a file format without viewing it in the browser.</span></span>|[<span data-ttu-id="34de9-164">URL アクセスを使用してレポートをエクスポート</span><span class="sxs-lookup"><span data-stu-id="34de9-164">Export a Report Using URL Access</span></span>](export-a-report-using-url-access.md)|  
|<span data-ttu-id="34de9-165">レポートを開き、文字列の場所に直接移動する</span><span class="sxs-lookup"><span data-stu-id="34de9-165">Open a report and navigate directly to the location of a string.</span></span>|[<span data-ttu-id="34de9-166">URL アクセスを使用してレポートを検索する</span><span class="sxs-lookup"><span data-stu-id="34de9-166">Search a Report Using URL Access</span></span>](search-a-report-using-url-access.md)|  
|<span data-ttu-id="34de9-167">特例のレポート履歴スナップショットを表示する</span><span class="sxs-lookup"><span data-stu-id="34de9-167">Render a specific report history snapshot.</span></span>|[<span data-ttu-id="34de9-168">URL アクセスを使用してレポート履歴スナップショットを表示する</span><span class="sxs-lookup"><span data-stu-id="34de9-168">Render a Report History Snapshot Using URL Access</span></span>](render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a><span data-ttu-id="34de9-169">参照</span><span class="sxs-lookup"><span data-stu-id="34de9-169">See Also</span></span>  
 <span data-ttu-id="34de9-170">[URL 内でレポート パラメーターを渡す](pass-a-report-parameter-within-a-url.md) </span><span class="sxs-lookup"><span data-stu-id="34de9-170">[Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md) </span></span>  
 <span data-ttu-id="34de9-171">[URL アクセス パラメーター リファレンス](url-access-parameter-reference.md) </span><span class="sxs-lookup"><span data-stu-id="34de9-171">[URL Access Parameter Reference](url-access-parameter-reference.md) </span></span>  
 <span data-ttu-id="34de9-172">[URL アクセスを使用した Reporting Services の統合](application-integration/integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="34de9-172">[Integrating Reporting Services Using URL Access](application-integration/integrating-reporting-services-using-url-access.md) </span></span>  
 [<span data-ttu-id="34de9-173">レポートの検索、表示、管理 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="34de9-173">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
