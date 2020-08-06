---
title: SQLXML 4.0 SP1 の新&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- SQLNCLI, SQLXML
- what's new [SQLXML]
- SQLXML, what's new
- migrating SQLXML applications
- redistributing SQLXML
- SQL Server Native Client, SQLXML
- side-by-side installations [SQLXML]
ms.assetid: 48f7720b-1705-402d-93ce-097ff1737877
author: rothja
ms.author: jroth
ms.openlocfilehash: 880937520385fbe6ce64be3fdfcbbf7d11c73741
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713029"
---
# <a name="what39s-new-in-sqlxml-40-sp1"></a><span data-ttu-id="7d379-102">SQLXML 4.0 SP1 の新機能&#39;</span><span class="sxs-lookup"><span data-stu-id="7d379-102">What&#39;s New in SQLXML 4.0 SP1</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="7d379-103">SQLXML 4.0 SP1 では、多くの更新と拡張が行われています。</span><span class="sxs-lookup"><span data-stu-id="7d379-103">SQLXML 4.0 SP1 includes various updates and enhancements.</span></span> <span data-ttu-id="7d379-104">ここでは、更新内容についてまとめ、詳細情報がある場合はそのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="7d379-104">This topic summarizes the updates and provides links to more detailed information, where available.</span></span> <span data-ttu-id="7d379-105">SQLXML 4.0 SP1 では、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] で導入された新しいデータ型をサポートするための追加の拡張が行われています。</span><span class="sxs-lookup"><span data-stu-id="7d379-105">SQLXML 4.0 SP1 provides additional enhancements to support the new data types introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="7d379-106">このトピックの項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7d379-106">This topic includes the following subjects:</span></span>  
  
-   <span data-ttu-id="7d379-107">SQLXML 4.0 SP1 のインストール</span><span class="sxs-lookup"><span data-stu-id="7d379-107">Installing SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="7d379-108">サイド バイ サイド インストールに関する問題</span><span class="sxs-lookup"><span data-stu-id="7d379-108">Side-by-Side Installation Issues</span></span>  
  
-   <span data-ttu-id="7d379-109">SQLXML 4.0 と MSXML</span><span class="sxs-lookup"><span data-stu-id="7d379-109">SQLXML 4.0 and MSXML</span></span>  
  
-   <span data-ttu-id="7d379-110">SQLXML 4.0 の再配布</span><span class="sxs-lookup"><span data-stu-id="7d379-110">Redistributing SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="7d379-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client のサポート</span><span class="sxs-lookup"><span data-stu-id="7d379-111">Support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="7d379-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入されたデータ型のサポート</span><span class="sxs-lookup"><span data-stu-id="7d379-112">Support for Data Types Introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span></span>  
  
-   <span data-ttu-id="7d379-113">SQLXML 4.0 での XML 一括読み込みの変更点</span><span class="sxs-lookup"><span data-stu-id="7d379-113">XML Bulk Load Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="7d379-114">SQLXML 4.0 でのレジストリ キーの変更点</span><span class="sxs-lookup"><span data-stu-id="7d379-114">Registry Key Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="7d379-115">移行の問題</span><span class="sxs-lookup"><span data-stu-id="7d379-115">Migration Issues</span></span>  
  
## <a name="installing-sqlxml-40-sp1"></a><span data-ttu-id="7d379-116">SQLXML 4.0 SP1 のインストール</span><span class="sxs-lookup"><span data-stu-id="7d379-116">Installing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="7d379-117">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンでは、SQLXML 4.0 は SQL Server に付属してリリースされ、SQL Server のすべてのバージョン (SQL Server Express を除く) の既定のインストールに含まれていました。</span><span class="sxs-lookup"><span data-stu-id="7d379-117">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with SQL Server and was part of the default installation of all SQL Server versions except for SQL Server Express.</span></span> <span data-ttu-id="7d379-118">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の SQL Server には、SQLXML の最新バージョン (SQLXML 4.0 SP1) が含まれないようになりました。</span><span class="sxs-lookup"><span data-stu-id="7d379-118">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in SQL Server.</span></span> <span data-ttu-id="7d379-119">SQLXML 4.0 SP1 をインストールするには、 [sqlxml 4.0 sp1 のインストール場所](https://www.microsoft.com/download/details.aspx?id=30403)からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7d379-119">To install SQLXML 4.0 SP1, download it from [Install Location for SQLXML 4.0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).</span></span>  
  
 <span data-ttu-id="7d379-120">SQLXML 4.0 SP1 のファイルは次の場所にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7d379-120">The SQLXML 4.0 SP1 files are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\SQLXML 4.0\`  
  
> [!NOTE]  
>  <span data-ttu-id="7d379-121">SQLXML 4.0 に必要なレジストリ設定はすべて、インストール処理の一部として行われます。</span><span class="sxs-lookup"><span data-stu-id="7d379-121">All appropriate registry settings for SQLXML 4.0 are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="7d379-122">32 ビットの SQLXML アプリケーションを 64 ビット Windows オペレーティング システム上の Windows on Windows (WOW64) で実行できるようにするには、64 ビットの SQLXML 4.0 SP1 パッケージ (sqlxml4.msi) を実行してください。このパッケージは、ダウンロード センターで入手できます。</span><span class="sxs-lookup"><span data-stu-id="7d379-122">To allow 32-bit SQLXML applications to run under Windows on Windows (WOW64) on 64-bit Windows operating systems, run the 64-bit SQLXML 4.0 SP1 package, named sqlxml4.msi, which can be found on the Download Center.</span></span>  
  
#### <a name="uninstalling-sqlxml-40-sp1"></a><span data-ttu-id="7d379-123">SQLXML 4.0 SP1 のアンインストール</span><span class="sxs-lookup"><span data-stu-id="7d379-123">Uninstalling SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="7d379-124">SQLXML 3.0 SP3、SQLXML 4.0、および SQLXML 4.0 SP1 には、共有のレジストリ キーがあります。</span><span class="sxs-lookup"><span data-stu-id="7d379-124">Shared registry keys exist between SQLXML 3.0 SP3, SQLXML 4.0 and SQLXML 4.0 SP1.</span></span> <span data-ttu-id="7d379-125">SQLXML 3.0 SP3 があるコンピューター上で SQLXML のより新しいバージョンをアンインストールすると、SQLXML 3.0 SP3 を再インストールする必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7d379-125">If the later versions of SQLXML are uninstalled on the same computer which contains SQLXML 3.0 SP3, you might need to reinstall SQLXML 3.0 SP3.</span></span>  
  
## <a name="side-by-side-installation-issues"></a><span data-ttu-id="7d379-126">サイド バイ サイド インストールに関する問題</span><span class="sxs-lookup"><span data-stu-id="7d379-126">Side-by-Side Installation Issues</span></span>  
 <span data-ttu-id="7d379-127">SQLXML 4.0 のインストール処理では、以前のバージョンの SQLXML でインストールされたファイルは削除されません。</span><span class="sxs-lookup"><span data-stu-id="7d379-127">The installation process for SQLXML 4.0 does not remove the files that were installed by earlier versions of SQLXML.</span></span> <span data-ttu-id="7d379-128">したがって、コンピューターに、バージョンの異なる SQLXML の DLL を複数インストールして、</span><span class="sxs-lookup"><span data-stu-id="7d379-128">Therefore, you can have DLLs for several different version-distinctive installations of SQLXML on your computer.</span></span> <span data-ttu-id="7d379-129">同時に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="7d379-129">You can run the installations side-by-side.</span></span> <span data-ttu-id="7d379-130">SQLXML 4.0 には、バージョン固有ではない PROGID とバージョン固有の PROGID の両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d379-130">SQLXML 4.0 includes both version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="7d379-131">すべての製品アプリケーションでは、バージョン固有の PROGID を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d379-131">All production applications should use version-dependent PROGIDs.</span></span>  
  
## <a name="sqlxml-40-sp1-and-msxml"></a><span data-ttu-id="7d379-132">SQLXML 4.0 SP1 と MSXML</span><span class="sxs-lookup"><span data-stu-id="7d379-132">SQLXML 4.0 SP1 and MSXML</span></span>  
 <span data-ttu-id="7d379-133">SQLXML 4.0 では、MSXML はインストールされません。</span><span class="sxs-lookup"><span data-stu-id="7d379-133">SQLXML 4.0 does not install MSXML.</span></span> <span data-ttu-id="7d379-134">SQLXML 4.0 では MSXML 6.0 が使用されますが、これは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のインストール時にその一部としてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7d379-134">SQLXML 4.0 uses MSXML 6.0, which is installed as part of the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later installation.</span></span>  
  
## <a name="redistributing-sqlxml-40-sp1"></a><span data-ttu-id="7d379-135">SQLXML 4.0 SP1 の再配布</span><span class="sxs-lookup"><span data-stu-id="7d379-135">Redistributing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="7d379-136">SQLXML 4.0 SP1 は、再配布可能インストーラー パッケージを使って再配布できます。</span><span class="sxs-lookup"><span data-stu-id="7d379-136">You can distribute SQLXML 4.0 SP1 using the redistributable installer package.</span></span> <span data-ttu-id="7d379-137">チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。</span><span class="sxs-lookup"><span data-stu-id="7d379-137">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="7d379-138">詳細については、「Visual Studio 2005 用のカスタム ブートストラップ パッケージの作成」および「カスタムの必須コンポーネントの追加」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d379-138">For more information, see Authoring a Custom Bootstrapper Package for Visual Studio 2005 and Adding Custom Prerequisites.</span></span>  
  
 <span data-ttu-id="7d379-139">アプリケーションが、開発時に使用したものとは異なるプラットフォームを対象としている場合、Microsoft ダウンロード センターから x64、Itanium、および x86 用のバージョンの sqlncli.msi をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="7d379-139">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="7d379-140">MSXML 6.0 には、個別の再配布インストール プログラム (msxml6.msi) もあります。</span><span class="sxs-lookup"><span data-stu-id="7d379-140">There are also separate redistribution installation programs for MSXML 6.0 (msxml6.msi).</span></span> <span data-ttu-id="7d379-141">これらのプログラムは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール CD の次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="7d379-141">These can be found on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation CD in the following location:</span></span>  
  
 `%CD%\Setup\`  
  
 <span data-ttu-id="7d379-142">これらのインストール ファイルを使用すると、MSXML 6.0 を CD から直接インストールできます。</span><span class="sxs-lookup"><span data-stu-id="7d379-142">These installation files can be used to install MSXML 6.0 directly from the CD.</span></span> <span data-ttu-id="7d379-143">インストール ファイルは、独自に作成したアプリケーションと共に MSXML 6.0 と SQLXML 4.0 SP1 を再配布するときにも自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d379-143">They can also be used to freely redistribute MSXML 6.0 along with SQLXML 4.0 SP1 with your own custom applications.</span></span>  
  
 <span data-ttu-id="7d379-144">独自のアプリケーションでデータ プロバイダーとして使用する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client も再配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d379-144">You will also need to redistribute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client if you are using it as the data provider with your application.</span></span> <span data-ttu-id="7d379-145">詳細については、「 [SQL Server Native Client のインストール](../native-client/applications/installing-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d379-145">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="support-for-sql-server-native-client"></a><span data-ttu-id="7d379-146">SQL Server Native Client のサポート</span><span class="sxs-lookup"><span data-stu-id="7d379-146">Support for SQL Server Native Client</span></span>  
 <span data-ttu-id="7d379-147">SQLXML 4.0 では、SQLOLEDB と Native Client プロバイダーの両方がサポートさ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れています。</span><span class="sxs-lookup"><span data-stu-id="7d379-147">SQLXML 4.0 supports both the SQLOLEDB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers.</span></span> <span data-ttu-id="7d379-148">Native client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は `Date, Time` 、の、 `DateTime2` 、およびの各 `dateTimeOffset` データ型 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] や、native client でサポートされているのデータ型など、サーバーに出荷される新しいデータ型をサポートするように開発されているため、同じバージョンの native client プロバイダーとを使用することをお勧めし [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7d379-148">It is recommended that you use the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is developed to support any new data types that ship in the server, such as the `Date, Time`, `DateTime2`, and `dateTimeOffset` data types in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d379-149">Native Client は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入されたデータ アクセス テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="7d379-149">Native Client is a data access technology that was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="7d379-150">これは SQLOLEDB プロバイダーと SQLODBC ドライバーを組み合わせて 1 つのネイティブ ダイナミック リンク ライブラリ (DLL) にしたものです。Microsoft Data Access Components (MDAC) とは独立した新しい機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-150">It combines the SQLOLEDB Provider and the SQLODBC Driver into one native dynamic link library (DLL), while also providing new functionality that is separate and distinct from the Microsoft Data Access Components (MDAC).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d379-151">で導入された機能のうち、MDAC および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows において SQLOLEDB と SQLODBC でサポートされていない機能を利用する必要がある場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Native Client を使用して、新しいアプリケーションを作成したり既存のアプリケーションを拡張したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7d379-151">Native Client can be used to create new applications or enhance existing applications that need to take advantage of features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not supported by SQLOLEDB and SQLODBC in MDAC and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="7d379-152">たとえば、FOR XML などのクライアント側の SQLXML 機能で `xml` データ型を使用するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client が必要です。</span><span class="sxs-lookup"><span data-stu-id="7d379-152">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is required for client-side SQLXML features, such as FOR XML, to use the `xml` data type.</span></span> <span data-ttu-id="7d379-153">詳細については、「[クライアント側の XML 書式設定 &#40;sqlxml 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md)」、「 [ADO を使用して sqlxml 4.0 クエリを実行する](using-ado-to-execute-sqlxml-4-0-queries.md)」、および「[プログラミング SQL Server Native Client](../native-client/sql-server-native-client-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d379-153">For more information, see [Client-side XML Formatting &#40;SQLXML 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md), [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md), and [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d379-154">SQLXML 4.0 には、下位の SQLXML 3.0 との完全な互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="7d379-154">SQLXML 4.0 is not completely backward compatible with SQLXML 3.0.</span></span> <span data-ttu-id="7d379-155">SQLXML 4.0 では不具合の修正とその他の機能変更が行われており、特に SQLXML ISAPI のサポートが削除されているため、IIS 仮想ディレクトリは使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7d379-155">Because of some bug fixes and other functional changes, particularly the removal of SQLXML ISAPI support, you cannot use IIS virtual directories with SQLXML 4.0.</span></span> <span data-ttu-id="7d379-156">大半のアプリケーションは少し変更すれば使用できますが、SQLXML 4.0 で運用する前には必ずテストを行ってください。</span><span class="sxs-lookup"><span data-stu-id="7d379-156">Although most applications will run with minor modifications, you must test them before putting them into production with SQLXML 4.0.</span></span>  
  
## <a name="support-for-data-types-introduced-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="7d379-157">SQL Server 2005 および SQL Server 2008 で導入されたデータ型のサポート</span><span class="sxs-lookup"><span data-stu-id="7d379-157">Support for Data Types Introduced in SQL Server 2005 and SQL Server 2008</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="7d379-158">では `xml` データ型が導入され、SQLXML 4.0 では `xml` データ型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d379-158">introduced the `xml` data type, and SQLXML 4.0 supports the `xml` data type.</span></span> <span data-ttu-id="7d379-159">詳細については、「 [SQLXML 4.0 での Xml データ型のサポート](xml-data-type-support-in-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d379-159">For more information, see [xml Data Type Support in SQLXML 4.0](xml-data-type-support-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="7d379-160">SQLXML で XML ビューをマッピングするとき、XML の一括読み込みを行うとき、または XML アップデートグラムを実行するときの `xml` データ型の使用方法については、次で提供される例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d379-160">For examples of how to use the `xml` data type in SQLXML when mapping XML views, bulk loading XML or executing XML updategrams, refer to examples provided in the following topics.</span></span>  
  
-   [<span data-ttu-id="7d379-161">XSD の要素と属性からテーブルと列への既定のマッピング</span><span class="sxs-lookup"><span data-stu-id="7d379-161">Default Mapping of XSD Elements and Attributes to Tables and Columns</span></span>](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="7d379-162">XML アップデートグラムを使用したデータの挿入</span><span class="sxs-lookup"><span data-stu-id="7d379-162">Inserting Data by Using XML Updategrams</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="7d379-163">XML ドキュメントの一括読み込みの例</span><span class="sxs-lookup"><span data-stu-id="7d379-163">Examples of Bulk Loading XML Documents</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="7d379-164">では `Date, Time` 、、 `DateTime2` 、および**DateTimeOffset**データ型が導入されました。</span><span class="sxs-lookup"><span data-stu-id="7d379-164">introduced the `Date, Time`, `DateTime2`, and **DateTimeOffset** data types.</span></span> <span data-ttu-id="7d379-165">SQLXML 4.0 SP1 を、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 付属の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB プロバイダー (SQLNCLI11) と共に使用した場合、これらの 4 つの新しいデータ型は組み込みスカラー型として有効になります。</span><span class="sxs-lookup"><span data-stu-id="7d379-165">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB Provider (SQLNCLI11), which ships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="xml-bulk-load-changes-for-sqlxml-40-sp1"></a><span data-ttu-id="7d379-166">SQLXML 4.0 SP1 での XML 一括読み込みの変更点</span><span class="sxs-lookup"><span data-stu-id="7d379-166">XML Bulk Load Changes for SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="7d379-167">SQLXML 4.0 では、データ型を使用して SchemaGen overflow フィールドが作成され `xml` ます。</span><span class="sxs-lookup"><span data-stu-id="7d379-167">For SQLXML 4.0, the SchemaGen overflow field is created using the `xml` data type.</span></span> <span data-ttu-id="7d379-168">詳細については、「 [SQL SERVER XML 一括読み込みオブジェクトモデル](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d379-168">For more information, see [SQL Server XML Bulk Load Object Model](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="7d379-169">以前に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic アプリケーションを作成済みで、SQLXML 4.0 を使用する場合は、Xblkld4.dll を参照するようアプリケーションを再コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d379-169">If you have previously created [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic applications and you want to use SQLXML 4.0, you must recompile the application with reference to Xblkld4.dll.</span></span>  
  
-   <span data-ttu-id="7d379-170">Visual Basic Scripting Edition のアプリケーションについては、使用する DLL を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d379-170">For Visual Basic Scripting Edition applications, you must register the DLL you want to use.</span></span> <span data-ttu-id="7d379-171">次の例で、バージョン固有でない PROGID を指定した場合、アプリケーションは最後に登録された DLL に従って動作します。</span><span class="sxs-lookup"><span data-stu-id="7d379-171">In the following example, if you specify version-independent PROGIDs, the application depends on the last registered DLL:</span></span>  
  
    ```  
    set objBulkLoad = CreateObject("SQLXMLBulkLoad.SQLXMLBulkLoad")   
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d379-172">バージョン固有の PROGID は、SQLXMLBulkLoad.SQLXMLBulkLoad.4.0 です。</span><span class="sxs-lookup"><span data-stu-id="7d379-172">The version-dependent PROGID is SQLXMLBulkLoad.SQLXMLBulkLoad.4.0.</span></span>  
  
## <a name="registry-key-changes-for-sqlxml-40"></a><span data-ttu-id="7d379-173">SQLXML 4.0 でのレジストリ キーの変更点</span><span class="sxs-lookup"><span data-stu-id="7d379-173">Registry Key Changes for SQLXML 4.0</span></span>  
 <span data-ttu-id="7d379-174">SQLXML 4.0 では、以前のリリースと比べてレジストリ キーが次のように変更されています。</span><span class="sxs-lookup"><span data-stu-id="7d379-174">In SQLXML 4.0, the registry keys have changed from the earlier releases to the following:</span></span>  
  
 <span data-ttu-id="7d379-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span><span class="sxs-lookup"><span data-stu-id="7d379-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span></span>  
  
 <span data-ttu-id="7d379-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span><span class="sxs-lookup"><span data-stu-id="7d379-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span></span>  
  
 <span data-ttu-id="7d379-177">SQLXML 4.0 でこれらのキーを有効にするには、設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d379-177">You must change the settings if you want these keys to be in effect for SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="7d379-178">また、SQLXML 4.0 では次のレジストリ キーが導入されています。</span><span class="sxs-lookup"><span data-stu-id="7d379-178">In addition, SQLXML 4.0 introduces the following registry keys:</span></span>  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\ReportErrorsWithSQLInfo`  
  
     <span data-ttu-id="7d379-179">SQLXML 4.0 の既定では、以前のバージョンの SQLXML と違って高いレベルの SQLXML エラーは返されず、代わりに OLE DB と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ エラー情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-179">By default, SQLXML 4.0 returns native error information provided by OLE DB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of a high-level SQLXML error (as was the case in earlier versions of SQLXML).</span></span> <span data-ttu-id="7d379-180">この動作を変更する場合は、DWORD 型のこのレジストリ キーの値を 0 に設定する必要があります (既定値は 1)。</span><span class="sxs-lookup"><span data-stu-id="7d379-180">If you do not want this behavior, the value of this registry key of type DWORD must be set to 0 (default is 1).</span></span>  
  
-   <span data-ttu-id="7d379-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span><span class="sxs-lookup"><span data-stu-id="7d379-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span></span>  
  
     <span data-ttu-id="7d379-182">既定で SQLXML では、SQL Server GUID がかっこで囲まずに返されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-182">By default, SQLXML return SQL Server GUID values without the enclosing braces.</span></span> <span data-ttu-id="7d379-183">GUID 値が中かっこで返されるようにする場合は ({*SOME GUID*} など)、このレジストリキーの値を1に設定する必要があります (既定値は 0)。</span><span class="sxs-lookup"><span data-stu-id="7d379-183">If you want the GUID value returned with the braces (for example, {*some GUID*}), value of this registry key must be set to 1 (default is 0).</span></span>  
  
-   <span data-ttu-id="7d379-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span><span class="sxs-lookup"><span data-stu-id="7d379-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span></span>  
  
     <span data-ttu-id="7d379-185">既定では、XML パーサーでデータが読み込まれるとき、空白文字は XML 1.0 規則に従って正規化されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-185">By default, when the XML parser loads the data, white spaces are normalized according to the XML 1.0 rules.</span></span> <span data-ttu-id="7d379-186">この結果、データの空白文字の一部が失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="7d379-186">This results in loss of some of the white space characters in your data.</span></span> <span data-ttu-id="7d379-187">これによってデータの意味が変わることはありませんが、データのテキストは解析後に同じでなくなります。</span><span class="sxs-lookup"><span data-stu-id="7d379-187">Thus, the textual representation of your data may not be the same after parsing, although semantically the data is the same.</span></span>  
  
     <span data-ttu-id="7d379-188">新しく導入されたこのキーを使用すると、データの空白文字を保持するよう指定できます。</span><span class="sxs-lookup"><span data-stu-id="7d379-188">This key is introduced so that you can choose to keep the white space characters in the data.</span></span> <span data-ttu-id="7d379-189">このレジストリ キーを追加し、値を 0 に設定すると、XML の空白文字 (LF、CR、タブ) は、属性値の場合はエンコードされて返され、</span><span class="sxs-lookup"><span data-stu-id="7d379-189">If you add this registry key and set its value to 0, white space characters (LF, CR, and tab) in the XML are returned encoded in case of attribute values.</span></span> <span data-ttu-id="7d379-190">要素値の場合は CR だけがエンコードされて返されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-190">In case of element values, only CR is returned encoded.</span></span>  
  
     <span data-ttu-id="7d379-191">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7d379-191">For example:</span></span>  
  
    ```  
    CREATE TABLE T( Col1 int, Col2 nvarchar(100));  
    GO  
    -- Insert data with tab, line feed and carriage return).  
    INSERT INTO T VALUES (1, 'This is a tab    . This is a line feed and CR   
     more text');  
    GO  
    -- Test this query (without the registry key).  
    SELECT * FROM T   
    FOR XML AUTO;  
    -- This is the result (no encoding of special characters).  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
    -- Now add registry key with value 0 and execute the query again.  
    -- Note the encoding for carriage return, line-feed and tab in the attribute value.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
  
    -- Update the query and specify ELEMENTS directive  
    SELECT * FROM T  
    FOR XML AUTO, ELEMENTS  
    -- Only the carriage return is returned encoded.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
       <T>  
          <Col1>1</Col1>  
          <Col2>This is a tab    . This is a line feed and CR   
     more text</Col2>  
       </T>  
    </r>  
    ```  
  
## <a name="migration-issues"></a><span data-ttu-id="7d379-192">移行の問題</span><span class="sxs-lookup"><span data-stu-id="7d379-192">Migration Issues</span></span>  
 <span data-ttu-id="7d379-193">SQLXML のレガシ アプリケーションから SQLXML 4.0 への移行に影響を与える可能性のある問題を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7d379-193">The following are issues that could impact migration of your legacy SQLXML applications to SQLXML 4.0.</span></span>  
  
### <a name="ado-and-sqlxml-40-queries"></a><span data-ttu-id="7d379-194">ADO と SQLXML 4.0 のクエリ</span><span class="sxs-lookup"><span data-stu-id="7d379-194">ADO and SQLXML 4.0 Queries</span></span>  
 <span data-ttu-id="7d379-195">以前のバージョンの SQLXML では、IIS 仮想ディレクトリを使用した URL ベースのクエリ実行と、SQLXML ISAPI フィルターがサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="7d379-195">In earlier versions of SQLXML, support for URL-based query execution using IIS virtual directories and the SQLXML ISAPI filter was provided.</span></span> <span data-ttu-id="7d379-196">SQLXML 4.0 を使用するアプリケーションで、このサポートは使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7d379-196">For applications that use SQLXML 4.0, this support is no longer available.</span></span>  
  
 <span data-ttu-id="7d379-197">代わりに、Microsoft Data Access Components (MDAC) 2.6 以降で最初に導入された ADO (ActiveX Data Objects) の SQLXML 拡張を使用して、SQLXML クエリ、テンプレート、アップデートグラムを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7d379-197">Instead, SQLXML queries, templates, and updategrams can be executed by using the SQLXML extensions to ActiveX Data Objects (ADO) first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="7d379-198">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d379-198">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="supportability-for-sqlxml-30-isapi-and-data-types-introduced-in-sql-server-2005"></a><span data-ttu-id="7d379-199">SQLXML 3.0 ISAPI のサポートと SQL Server 2005 で導入されたデータ型</span><span class="sxs-lookup"><span data-stu-id="7d379-199">Supportability for SQLXML 3.0 ISAPI and Data Types Introduced in SQL Server 2005</span></span>  
 <span data-ttu-id="7d379-200">ISAPI サポートが SQLXML 4.0 から削除されているため、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [xml データ型](/sql/t-sql/xml/xml-transact-sql)、[ユーザー定義データ型 (udt)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) 、Web ベースのアクセスなど、で導入された拡張データ型機能が必要な場合は、 [sqlxml マネージクラス](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)などの別の種類の HTTP ハンドラー (SQL Server 2005 用のネイティブ xml Web サービスなど) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d379-200">Because ISAPI support has been removed from SQLXML 4.0, if your solution requires the enhanced data typing features introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] such as the [xml data type](/sql/t-sql/xml/xml-transact-sql) or [user-defined data types (UDTs)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) and Web-based access, you will need to use another solution such as [SQLXML managed classes](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) or another type of HTTP handler, such as Native XML Web Services for SQL Server 2005.</span></span>  
  
 <span data-ttu-id="7d379-201">または、これらの型の拡張機能が必要ない場合は、SQLXML 3.0 を使用してに接続し、をインストールすることもでき [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7d379-201">Alternately, if you do not require these type extensions, you can continue to use SQLXML 3.0 to connect to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] installations.</span></span> <span data-ttu-id="7d379-202">SQLXML 3.0 ISAPI のサポートは、こうした新しいバージョンに対しても有効ですが、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で導入された `xml` データ型や UDT 型はサポートされず、認識されません。</span><span class="sxs-lookup"><span data-stu-id="7d379-202">The SQLXML 3.0 ISAPI support will work against these later versions but does not support or recognize the `xml` data type or UDT type support introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
### <a name="xml-bulk-load-security-changes-for-temporary-files"></a><span data-ttu-id="7d379-203">一時ファイルに関する XML 一括読み込みのセキュリティの変更点</span><span class="sxs-lookup"><span data-stu-id="7d379-203">XML Bulk Load Security Changes for Temporary Files</span></span>  
 <span data-ttu-id="7d379-204">SQLXML 4.0 および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XML 一括読み込みの権限は、一括読み込み操作を実行するユーザーに許可されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-204">For SQLXML 4.0 and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XML Bulk Load file permissions are granted to the user executing the bulk load operation.</span></span> <span data-ttu-id="7d379-205">読み取りと書き込みの権限は、ファイル システムから継承されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-205">Read and Write permissions are inherited from the file system.</span></span> <span data-ttu-id="7d379-206">以前のリリースの SQLXML および SQL Server では、SQLXML での XML 一括読み込みで作成される一時ファイルは保護されず、だれにでも読み取りが可能でした。</span><span class="sxs-lookup"><span data-stu-id="7d379-206">In previous releases of SQLXML and SQL Server, XML Bulk Load under SQLXML would create temporary files that were not secured and could be readable by anyone.</span></span>  
  
### <a name="migration-issues-for-client-side-for-xml"></a><span data-ttu-id="7d379-207">クライアント側の FOR XML の移行に関する問題</span><span class="sxs-lookup"><span data-stu-id="7d379-207">Migration Issues for Client-Side FOR XML</span></span>  
 <span data-ttu-id="7d379-208">実行エンジンが変更されたため、は、で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FOR XML クエリを実行した場合とは異なり、ベーステーブルのメタデータに異なる値を返すことがあり [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7d379-208">Due to changes in the execution engine, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might return different values in the metadata for a base table than would be returned if the FOR XML query was executed under [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="7d379-209">この場合、クライアント側の FOR XML クエリ結果の形式は、クエリの実行対象となるバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="7d379-209">In cases where this occurs, client-side formatting of the FOR XML query results will have differing output depending on which version the query is run against.</span></span>  
  
 <span data-ttu-id="7d379-210">クライアント側で、`xml` データ型の列に対し SQLXML 3.0 を使用して FOR XML クエリを実行する場合、結果のデータは完全にエンティティ化された文字列として返されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-210">If a FOR XML query is executed client-side using SQLXML 3.0 over an `xml` data type column, the data in the results will come back as a fully entitized string.</span></span> <span data-ttu-id="7d379-211">SQLXML 4.0 で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) がプロバイダーとして指定されている場合、データは XML として返されます。</span><span class="sxs-lookup"><span data-stu-id="7d379-211">In SQLXML 4.0, if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) is specified as the provider, the data will be returned as XML.</span></span>  
  
  
