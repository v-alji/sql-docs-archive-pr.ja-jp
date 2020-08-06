---
title: SQL Server 2014 | での SQL Server Reporting Services の動作の変更Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 966447192c492a907f0b506ae21befd513b2fcfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633797"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a><span data-ttu-id="9dc6d-102">SQL Server 2014 における SQL Server Reporting Services の動作変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-102">Behavior Changes to SQL Server Reporting Services  in SQL Server 2014</span></span>
  <span data-ttu-id="9dc6d-103">このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における動作変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-103">This topic describes behavior changes in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9dc6d-104">動作変更によって、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の以前のバージョンに比べて、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の機能の動作や操作方法が変わります。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-104">Behavior changes affect how features work or interact in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] as compared to previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9dc6d-105">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="9dc6d-105">In this topic:</span></span>  
  
-   [<span data-ttu-id="9dc6d-106">SQL Server 2014 Reporting Services 動作の変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-106">SQL Server 2014 Reporting Services Behavior Changes</span></span>](#bkmk_sql14)  
  
-   [<span data-ttu-id="9dc6d-107">SQL Server 2012 Reporting Services における動作変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-107">SQL Server 2012 Reporting Services Behavior Changes</span></span>](#bkmk_rc0)  
  
-   [<span data-ttu-id="9dc6d-108">SQL Server 2008 R2 Reporting Services における動作変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-108">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-behavior-changes"></a><a name="bkmk_sql14"></a><span data-ttu-id="9dc6d-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Reporting Services 動作の変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-109">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="9dc6d-110">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]の動作に変更はありません。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-110">There are no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] behavior changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
##  <a name="sssql11-reporting-services-behavior-changes"></a><a name="bkmk_rc0"></a><span data-ttu-id="9dc6d-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Reporting Services 動作の変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-111">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="9dc6d-112">ここでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードでの動作変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-112">This section describes behavior changes to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a><span data-ttu-id="9dc6d-113">"アイテムの表示" 権限によって共有データセットがダウンロードされない (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="9dc6d-113">View Items permission will not download Shared Datasets (SharePoint Mode)</span></span>  
 <span data-ttu-id="9dc6d-114">**新しい動作:**"アイテムの表示" 権限を持つユーザーは、Reporting Services 共有データセットのコンテンツをダウンロードできなくなります。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-114">**New Behavior:** Users with the SharePoint permission of "View Items" can no longer download the contents of Reporting Services shared datasets.</span></span> <span data-ttu-id="9dc6d-115">この動作変更は、レポート、データソース、およびモデルに対する "アイテムの表示" 権限と一致するようになりました。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-115">This behavior change is now consistent with the "View Items" permissions for reports, data sources, and models.</span></span> <span data-ttu-id="9dc6d-116">"アイテムの表示" 権限を持つユーザーは、レポート、データソース、およびモデルを表示および実行できますが、コンテンツをダウンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-116">Users with "View Items" permission can view and execute reports, data sources, and models but they cannot download their content.</span></span>  
  
 <span data-ttu-id="9dc6d-117">**以前の動作:** SharePoint の "アイテムの表示" 権限を持つユーザーは Reporting Services 共有データセットの内容をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-117">**Previous Behavior:** Users with the "View Items" SharePoint permission could download the contents of Reporting Services shared datasets.</span></span>  
  
 <span data-ttu-id="9dc6d-118">SharePoint 権限レベルの詳細については、「 [ユーザー権限とアクセス許可レベル](https://technet.microsoft.com/library/cc721640.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-118">For more information on SharePoint permission levels, see [User permissions and permission levels](https://technet.microsoft.com/library/cc721640.aspx)</span></span>  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a><span data-ttu-id="9dc6d-119">SharePoint モードでは Report Server のトレース ログが新しい場所に置かれる (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="9dc6d-119">Report Server trace logs are in a new location for SharePoint mode (SharePoint Mode)</span></span>  
 <span data-ttu-id="9dc6d-120">**新しい動作:** SharePoint モードでインストールされたレポートサーバーの場合、レポートサーバーのトレースログは%Programfiles%\Common の Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles. にあります。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-120">**New behavior:** For a report server installed in SharePoint mode, the report server trace logs will be under %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.</span></span>  
  
 <span data-ttu-id="9dc6d-121">**以前の動作:** レポートサーバーのトレースログは、次のようなパスで見つかりました:%Programfilesdir%\Microsoft SQL Server \\<RS_instance> \ Reporting Services\LogFiles</span><span class="sxs-lookup"><span data-stu-id="9dc6d-121">**Previous Behavior:** Report Server trace logs were found under a path similar to the following:  %Programfilesdir%\Microsoft SQL Server\\<RS_instance>\Reporting Services\LogFiles</span></span>  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a><span data-ttu-id="9dc6d-122">GetServerConfigInfo SOAP API がサポートされなくなった (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="9dc6d-122">GetServerConfigInfo SOAP API is no longer supported (SharePoint Mode)</span></span>  
 <span data-ttu-id="9dc6d-123">**新しい動作**: PowerShell コマンドレット "SPRSServiceApplicationServers" を使用します。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-123">**New behavior**: Use PowerShell cmdlet "Get-SPRSServiceApplicationServers"</span></span>  
  
 <span data-ttu-id="9dc6d-124">**以前の動作:** エンドポイントと直接通信する SOAP クライアントコードを開発 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] し、GetReportServerConfigInfo () を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-124">**Previous Behavior:** Customers could develop SOAP client code to communicate directly with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] end point, and call GetReportServerConfigInfo().</span></span>  
  
### <a name="report-server-configuration-and-management-tools"></a><span data-ttu-id="9dc6d-125">レポート サーバーの構成と管理のツール</span><span class="sxs-lookup"><span data-stu-id="9dc6d-125">Report Server Configuration and Management Tools</span></span>  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a><span data-ttu-id="9dc6d-126">SharePoint モードで構成マネージャーが使用されない</span><span class="sxs-lookup"><span data-stu-id="9dc6d-126">Configuration Manager is not used for SharePoint Mode</span></span>  
 <span data-ttu-id="9dc6d-127">**新しい動作:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーでは、SharePoint モードのレポート サーバーはサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-127">**New behavior:** The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint Mode report servers.</span></span> <span data-ttu-id="9dc6d-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードの構成は、SharePoint サーバーの全体管理を使用して完了できるようになったため、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーでは SharePoint モードはサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-128">Configuration of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode can now be completed by using SharePoint Central administration and therefore [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager no longer supports SharePoint mode.</span></span> <span data-ttu-id="9dc6d-129">構成マネージャーは今後、ネイティブ モードのレポート サーバーに対してのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-129">Configuration Manager is now only used for Native mode report servers.</span></span>  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a><span data-ttu-id="9dc6d-130">サーバーを別のモードに変更できない</span><span class="sxs-lookup"><span data-stu-id="9dc6d-130">You cannot change the server from one mode to another</span></span>  
 <span data-ttu-id="9dc6d-131">**新しい動作:** サーバー モードを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-131">**New behavior:** You cannot change server modes.</span></span> <span data-ttu-id="9dc6d-132">レポート サーバーをネイティブ モードとしてインストールした場合、それを変更または再構成して SharePoint モードにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-132">If you install a report server as Native mode you cannot change or re-configure it to be SharePoint mode.</span></span> <span data-ttu-id="9dc6d-133">SharePoint モードでインストールした場合は、レポート サーバーをネイティブ モードに変更できます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-133">If you install in SharePoint mode, you can change the report server to native mode.</span></span>  
  
 <span data-ttu-id="9dc6d-134">**以前の動作:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーを SharePoint モードでインストールします。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-134">**Previous Behavior:** Customer installs a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server in SharePoint mode.</span></span> <span data-ttu-id="9dc6d-135">レポート サーバーをネイティブ モードに切り替えたい場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーを開き、新しいネイティブ モード データベースを作成するか、または既存のネイティブ モード データベースに接続することで、ネイティブ モードに切り替えることができました。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-135">If the customer wants to switch the report server to Native mode, they could open the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] configuration manager to switch to Native mode by either creating a new or connecting to an existing Native mode database.</span></span> <span data-ttu-id="9dc6d-136">また、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、SharePoint モードからネイティブ モードに切り替えることもできました。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-136">The customer could also use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager to switch from SharePoint mode to Native mode.</span></span>  
  
##  <a name="sql-server-2008-r2-reporting-services-behavior-changes"></a><a name="bkmk_kj"></a><span data-ttu-id="9dc6d-137">SQL Server 2008 R2 Reporting Services 動作の変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-137">SQL Server 2008 R2 Reporting Services Behavior Changes</span></span>  
 <span data-ttu-id="9dc6d-138">ここでは、での動作の変更について説明し [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-138">This section describes behavior changes in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dc6d-139">SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-139">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a><span data-ttu-id="9dc6d-140">Reporting Services WMI プロバイダー ライブラリの SecureConnectionLevel プロパティ</span><span class="sxs-lookup"><span data-stu-id="9dc6d-140">SecureConnectionLevel Property in the Reporting Services WMI Provider Library</span></span>  
 <span data-ttu-id="9dc6d-141">の WMI プロバイダーライブラリでは、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **secureconnectionlevel**プロパティによって、、、、 `0` 、の `1` `2` `3` `0` いずれかの web サービスメソッドで ssl (Secure Socket Layer) が不要であることが示されています。これは、すべての web サービスメソッドに ssl が必要であることを示し、ssl を `3` `1` `2` 必要とする web サービスメソッドのサブセットを示します。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-141">In the WMI provider library for [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the **SecureConnectionLevel** property allows values of `0`,`1`,`2`,`3`, with `0` indicating that Secure Socket Layer (SSL) is not required for any of the Web service methods, `3` indicating that SSL is required for all the Web service methods, and `1` and `2` indicate subsets of Web service methods that require SSL.</span></span> <span data-ttu-id="9dc6d-142">では [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 、これらの値は次の2つの意味を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-142">In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], these values will have only two possible meanings:</span></span>  
  
-   <span data-ttu-id="9dc6d-143">`0` は、いずれの Web サービス メソッドでも SSL が不要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-143">`0` indicates SSL is not required for any of the Web service methods.</span></span>  
  
-   <span data-ttu-id="9dc6d-144">正の整数は、すべての Web サービス メソッドで SSL が必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-144">A positive integer indicates SSL is required for all the Web service methods.</span></span>  
  
 <span data-ttu-id="9dc6d-145">この変更によって、レポート サーバーが Web サービス呼び出しに応答する方法に影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-145">This change affects how the report server responds to Web service calls.</span></span> <span data-ttu-id="9dc6d-146">たとえば、 <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> **secureconnectionlevel**が0に設定されていて、 <xref:ReportService2005.ReportingService2005> **secureconnectionlevel**が `1` 、、またはに設定されている場合、は何も返さないようになりました `2` `3` 。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-146">For example, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> now returns nothing if **SecureConnectionLevel** is set to 0 and all the methods in <xref:ReportService2005.ReportingService2005> if **SecureConnectionLevel** is set to `1`, `2`, or `3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc6d-147">参照</span><span class="sxs-lookup"><span data-stu-id="9dc6d-147">See Also</span></span>  
 <span data-ttu-id="9dc6d-148">[新機能 &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-148">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="9dc6d-149">[SQL Server 2014 の SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-149">[Deprecated Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md) </span></span>  
 <span data-ttu-id="9dc6d-150">[SQL Server 2014 で SQL Server Reporting Services が廃止された機能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-150">[Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md) </span></span>  
 [<span data-ttu-id="9dc6d-151">SQL Server 2014 における SQL Server Reporting Services における重大な変更</span><span class="sxs-lookup"><span data-stu-id="9dc6d-151">Breaking Changes in SQL Server Reporting Services in SQL Server 2014</span></span>](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
