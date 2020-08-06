---
title: SQL Server オブジェクトとバージョンの DAC サポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], supported objects
- objects [SQL Server], data-tier applications
ms.assetid: b1b78ded-16c0-4d69-8657-ec57925e68fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa1ea498f603992ce2a62b51d95e74e0f9a9c584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643951"
---
# <a name="dac-support-for-sql-server-objects-and-versions"></a><span data-ttu-id="ebe7a-102">SQL Server オブジェクトとバージョンの DAC サポート</span><span class="sxs-lookup"><span data-stu-id="ebe7a-102">DAC Support For SQL Server Objects and Versions</span></span>
  <span data-ttu-id="ebe7a-103">データ層アプリケーション (DAC) では、よく使用される [!INCLUDE[ssDE](../../includes/ssde-md.md)] オブジェクトがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-103">A data-tier application (DAC) supports the most commonly used [!INCLUDE[ssDE](../../includes/ssde-md.md)] objects.</span></span>  
  
 <span data-ttu-id="ebe7a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ebe7a-104">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="ebe7a-105">サポート対象の SQL Server オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ebe7a-105">Supported SQL Server Objects</span></span>](#SupportedObjects)  
  
-   [<span data-ttu-id="ebe7a-106">SQL Server の各バージョンでのデータ層アプリケーション サポート</span><span class="sxs-lookup"><span data-stu-id="ebe7a-106">Data-tier Application Support by the Versions of SQL Server</span></span>](#SupportByVersion)  
  
-   [<span data-ttu-id="ebe7a-107">データ配置の制限</span><span class="sxs-lookup"><span data-stu-id="ebe7a-107">Data Deployment Limitations</span></span>](#DeploymentLimitations)  
  
-   [<span data-ttu-id="ebe7a-108">配置操作に関するその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="ebe7a-108">Additional Considerations for Deployment Actions</span></span>](#Considerations)  
  
##  <a name="supported-sql-server-objects"></a><a name="SupportedObjects"></a><span data-ttu-id="ebe7a-109">サポートされている SQL Server オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ebe7a-109">Supported SQL Server Objects</span></span>  
 <span data-ttu-id="ebe7a-110">作成時または編集時にデータ層アプリケーションで指定できるのは、サポート対象オブジェクトのみです。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-110">Only supported objects can be specified in a data-tier application as it is being authored or edited.</span></span> <span data-ttu-id="ebe7a-111">DAC でサポートされていないオブジェクトを含む既存のデータベースから DAC の抽出、登録、およびインポートを行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-111">You cannot extract, register, or import a DAC from an existing database that contains objects that are not supported in a DAC.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="ebe7a-112">では、DAC の以下のオブジェクトがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-112">supports the following objects in a DAC.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ebe7a-113">DATABASE ROLE</span><span class="sxs-lookup"><span data-stu-id="ebe7a-113">DATABASE ROLE</span></span>|<span data-ttu-id="ebe7a-114">FUNCTION: インライン テーブル値</span><span class="sxs-lookup"><span data-stu-id="ebe7a-114">FUNCTION: Inline Table-valued</span></span>|  
|<span data-ttu-id="ebe7a-115">FUNCTION: 複数ステートメント テーブル値</span><span class="sxs-lookup"><span data-stu-id="ebe7a-115">FUNCTION: Multistatement Table-valued</span></span>|<span data-ttu-id="ebe7a-116">FUNCTION: スカラー</span><span class="sxs-lookup"><span data-stu-id="ebe7a-116">FUNCTION: Scalar</span></span>|  
|<span data-ttu-id="ebe7a-117">INDEX: クラスター化</span><span class="sxs-lookup"><span data-stu-id="ebe7a-117">INDEX: Clustered</span></span>|<span data-ttu-id="ebe7a-118">インデックス: 非クラスター化</span><span class="sxs-lookup"><span data-stu-id="ebe7a-118">INDEX: Nonclustered</span></span>|  
|<span data-ttu-id="ebe7a-119">INDEX: 空間</span><span class="sxs-lookup"><span data-stu-id="ebe7a-119">INDEX: Spacial</span></span>|<span data-ttu-id="ebe7a-120">INDEX: 一意</span><span class="sxs-lookup"><span data-stu-id="ebe7a-120">INDEX: Unique</span></span>|  
|<span data-ttu-id="ebe7a-121">Login</span><span class="sxs-lookup"><span data-stu-id="ebe7a-121">LOGIN</span></span>|<span data-ttu-id="ebe7a-122">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="ebe7a-122">Permissions</span></span>|  
|<span data-ttu-id="ebe7a-123">ロールのメンバーシップ</span><span class="sxs-lookup"><span data-stu-id="ebe7a-123">Role Memberships</span></span>|<span data-ttu-id="ebe7a-124">SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ebe7a-124">SCHEMA</span></span>|  
|<span data-ttu-id="ebe7a-125">統計</span><span class="sxs-lookup"><span data-stu-id="ebe7a-125">Statistics</span></span>|<span data-ttu-id="ebe7a-126">STORED PROCEDURE: Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ebe7a-126">STORED PROCEDURE: Transact-SQL</span></span>|  
|<span data-ttu-id="ebe7a-127">シノニム</span><span class="sxs-lookup"><span data-stu-id="ebe7a-127">Synonyms</span></span>|<span data-ttu-id="ebe7a-128">TABLE: CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="ebe7a-128">TABLE: Check Constraint</span></span>|  
|<span data-ttu-id="ebe7a-129">TABLE: 照合順序</span><span class="sxs-lookup"><span data-stu-id="ebe7a-129">TABLE: Collation</span></span>|<span data-ttu-id="ebe7a-130">TABLE: 列 (計算列も含む)</span><span class="sxs-lookup"><span data-stu-id="ebe7a-130">TABLE: Column, including computed columns</span></span>|  
|<span data-ttu-id="ebe7a-131">TABLE: 制約、DEFAULT</span><span class="sxs-lookup"><span data-stu-id="ebe7a-131">TABLE: Constraint, Default</span></span>|<span data-ttu-id="ebe7a-132">TABLE: 制約、FOREIGN KEY</span><span class="sxs-lookup"><span data-stu-id="ebe7a-132">TABLE: Constraint, Foreign Key</span></span>|  
|<span data-ttu-id="ebe7a-133">TABLE: 制約、INDEX</span><span class="sxs-lookup"><span data-stu-id="ebe7a-133">TABLE: Constraint, Index</span></span>|<span data-ttu-id="ebe7a-134">TABLE: 制約、PRIMARY KEY</span><span class="sxs-lookup"><span data-stu-id="ebe7a-134">TABLE: Constraint, Primary Key</span></span>|  
|<span data-ttu-id="ebe7a-135">TABLE: 制約、UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ebe7a-135">TABLE: Constraint, Unique</span></span>|<span data-ttu-id="ebe7a-136">TRIGGER: DML</span><span class="sxs-lookup"><span data-stu-id="ebe7a-136">TRIGGER: DML</span></span>|  
|<span data-ttu-id="ebe7a-137">TYPE: HIERARCHYID、GEOMETRY、GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="ebe7a-137">TYPE: HIERARCHYID, GEOMETRY, GEOGRAPHY</span></span>|<span data-ttu-id="ebe7a-138">TYPE: ユーザー定義データ型</span><span class="sxs-lookup"><span data-stu-id="ebe7a-138">TYPE: User-defined Data Type</span></span>|  
|<span data-ttu-id="ebe7a-139">TYPE: ユーザー定義テーブル型</span><span class="sxs-lookup"><span data-stu-id="ebe7a-139">TYPE: User-defined Table Type</span></span>|<span data-ttu-id="ebe7a-140">User</span><span class="sxs-lookup"><span data-stu-id="ebe7a-140">USER</span></span>|  
|<span data-ttu-id="ebe7a-141">VIEW</span><span class="sxs-lookup"><span data-stu-id="ebe7a-141">VIEW</span></span>||  
  
##  <a name="data-tier-application-support-by-the-versions-of-sql-server"></a><a name="SupportByVersion"></a><span data-ttu-id="ebe7a-142">SQL Server のバージョンでのデータ層アプリケーションのサポート</span><span class="sxs-lookup"><span data-stu-id="ebe7a-142">Data-tier Application Support by the Versions of SQL Server</span></span>  
 <span data-ttu-id="ebe7a-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンによって、DAC 操作に対するサポート レベルが異なります。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-143">The versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have different levels of support for DAC operations.</span></span> <span data-ttu-id="ebe7a-144">特定のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされるすべての DAC 操作は、そのバージョンのすべてのエディションでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-144">All of the DAC operations supported by a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported by all editions of that version.</span></span>  
  
 <span data-ttu-id="ebe7a-145">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスでは、次の DAC 操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-145">Instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] support the following DAC operations:</span></span>  
  
-   <span data-ttu-id="ebe7a-146">サポートされているすべてのバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で、エクスポートと抽出がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-146">Export and extract are supported on all supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ebe7a-147">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] と、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、および [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]のすべてのバージョンで、すべての操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-147">All operations are supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] and all versions of [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span>  
  
-   <span data-ttu-id="ebe7a-148">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) 以降と [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 以降で、すべての操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-148">All operations are supported on [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) or later, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 or later.</span></span>  
  
 <span data-ttu-id="ebe7a-149">DAC Framework は、DAC パッケージとエクスポート ファイルのビルドおよび処理用のクライアント側ツールで構成されています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-149">The DAC Framework comprises the client-side tools for building and processing DAC packages and export files.</span></span> <span data-ttu-id="ebe7a-150">以下の製品には、DAC Framework が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-150">The following products include the DAC Framework</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="ebe7a-151">および [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] には DAC Framework 3.0 が含まれており、これによってすべての DAC 操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-151">and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] includes DAC Framework 3.0, which supports all DAC operations.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="ebe7a-152">SP1 と Visual Studio 2010 SP1 には DAC Framework 1.1 が含まれており、これによって、エクスポートとインポートを除くすべての DAC 操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-152">SP1 and Visual Studio 2010 SP1 included DAC Framework 1.1, which supports all DAC operations except export and import.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="ebe7a-153">と Visual Studio 2010 には DAC Framework 1.0 が含まれており、これによって、エクスポート、インポート、およびインプレース アップグレードを除くすべての DAC 操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-153">and Visual Studio 2010 included DAC Framework 1.0, which supports all DAC operations except export, import, and in-place upgrade.</span></span>  
  
-   <span data-ttu-id="ebe7a-154">SQL Server または Visual Studio の以前のバージョンのクライアント ツールでは、DAC 操作はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-154">The client tools from earlier versions of SQL Server or Visual Studio do not support DAC operations.</span></span>  
  
 <span data-ttu-id="ebe7a-155">あるバージョンの DAC Framework でビルドされた DAC パッケージまたはエクスポート ファイルは、それ以前のバージョンの DAC Framework では処理できません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-155">A DAC package or export file built with one version of the DAC Framework cannot be processed by an earlier version of the DAC Framework.</span></span> <span data-ttu-id="ebe7a-156">たとえば、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] クライアント ツールを使用して抽出された DAC パッケージは、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] クライアント ツールでは配置できません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-156">For example, a DAC package extracted using the [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] client tools cannot be deployed using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools.</span></span>  
  
 <span data-ttu-id="ebe7a-157">あるバージョンの DAC Framework でビルドされた DAC パッケージまたはエクスポート ファイルは、それ以降の任意のバージョンの DAC Framework で処理できます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-157">A DAC package or export file built with one version of the DAC Framework can be processed by any later version of the DAC Framework.</span></span> <span data-ttu-id="ebe7a-158">たとえば、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] クライアント ツールを使用して抽出された DAC パッケージは、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 以降のクライアント ツールを使用して配置できます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-158">For example, a DAC package extracted using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools can be deployed using either the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 or higher client tools.</span></span>  
  
##  <a name="data-deployment-limitations"></a><a name="DeploymentLimitations"></a><span data-ttu-id="ebe7a-159">データ配置の制限事項</span><span class="sxs-lookup"><span data-stu-id="ebe7a-159">Data Deployment Limitations</span></span>  
 <span data-ttu-id="ebe7a-160">SQL Server 2012 SP1 の DAC Framework データ配置エンジンには、忠実性に関してここで述べるような制限があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-160">Note these fidelity limitations in the DAC Framework data deployment engine in SQL Server 2012 SP1.</span></span> <span data-ttu-id="ebe7a-161">制限が適用される DAC Framework 操作は、.dacpac ファイルの展開またはパブリッシュ、および .bacpac ファイルのインポートです。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-161">The limitations apply to the following DAC Framework actions: deploy or publish a .dacpac file, and import a .bacpac file.</span></span>  
  
1.  <span data-ttu-id="ebe7a-162">sql_variant 列内の特定の条件と基本データ型によるメタデータの消失。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-162">Loss of metadata for certain conditions and base types within sql_variant columns.</span></span> <span data-ttu-id="ebe7a-163">影響を受ける場合は、  **"DAC Framework によって配置される場合、sql_variant 列内で使用される特定のデータ型の特定のプロパティは保持されません。"** という警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-163">In the affected cases, you will see a warning with the following message:  **Certain properties on certain data types used within a sql_variant column are not preserved when deployed by the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="ebe7a-164">MONEY、SMALLMONEY、NUMERIC、DECIMAL の各基本データ型: 有効桁数は保持されません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-164">MONEY, SMALLMONEY, NUMERIC, DECIMAL base types:  Precision is not preserved.</span></span>  
  
        -   <span data-ttu-id="ebe7a-165">有効桁数 38 桁の DECIMAL/NUMERIC 基本データ型: "TotalBytes" という sql_variant のメタデータは常に 21 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-165">DECIMAL/NUMERIC base types with precision 38:  the "TotalBytes" sql_variant metadata is always set to 21.</span></span>  
  
    -   <span data-ttu-id="ebe7a-166">すべてのテキスト基本データ型: データベースの既定の照合順序がすべてのテキストに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-166">All text base types:  The database default collation is applied for all text.</span></span>  
  
    -   <span data-ttu-id="ebe7a-167">BINARY 基本データ型: 最大長プロパティは保持されません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-167">BINARY base types:  Max length property is not preserved.</span></span>  
  
    -   <span data-ttu-id="ebe7a-168">TIME、DATETIMEOFFSET の各基本データ型: 有効桁数は常に 7 桁に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-168">TIME, DATETIMEOFFSET base types:  Precision is always set to 7.</span></span>  
  
2.  <span data-ttu-id="ebe7a-169">sql_variant 列内のデータの消失。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-169">Loss of data within sql_variant columns.</span></span> <span data-ttu-id="ebe7a-170">影響を受ける場合は、  **"3 より大きなスケールを持つ sql_variant DATETIME2 列の値が DAC Framework によって配置されると、データが失われます。配置中、DATETIME2 値は 3 と等しいスケールに制限されます。"** という警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-170">In the affected case, you will see a warning with the following message:  **There will be data loss when a value in a sql_variant DATETIME2 column with scale greater than 3 is deployed by the DAC Framework. The DATETIME2 value is limited to a scale equal to 3 during deployment.**</span></span>  
  
    -   <span data-ttu-id="ebe7a-171">スケールが 3 を超える DATETIME2 基本データ型: スケールが 3 に制限されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-171">DATETIME2 base type with scale greater than 3:  scale is limited to equal 3.</span></span>  
  
3.  <span data-ttu-id="ebe7a-172">sql_variant 列内で以下に述べる条件が成立すると、配置操作が失敗します。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-172">Deployment operation fails for the following conditions within sql_variant columns.</span></span> <span data-ttu-id="ebe7a-173">影響を受ける場合は、  **"DAC Framework のデータ制限のため操作に失敗しました。"** というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-173">In the affected cases, you will see a dialog with the following message:  **Operation failed due to data limitations in the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="ebe7a-174">DATETIME2、SMALLDATETIME、DATE の各基本データ型: 値が DATETIME の範囲外である場合 (年が 1753 未満であるなど)。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-174">DATETIME2, SMALLDATETIME and DATE base types:  If the value is outside of DATETIME range - for example, the year is less than 1753.</span></span>  
  
    -   <span data-ttu-id="ebe7a-175">DECIMAL、NUMERIC の各基本データ型: 値の有効桁数が 28 を超える場合。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-175">DECIMAL, NUMERIC base type:  when precision of the value is greater than 28.</span></span>  
  
##  <a name="additional-considerations-for-deployment-actions"></a><a name="Considerations"></a> <span data-ttu-id="ebe7a-176">配置操作に関するその他の注意点</span><span class="sxs-lookup"><span data-stu-id="ebe7a-176">Additional Considerations for Deployment Actions</span></span>  
 <span data-ttu-id="ebe7a-177">DAC Framework のデータ配置操作に関して次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-177">Note the following considerations for DAC Framework data deployment actions:</span></span>  
  
-   <span data-ttu-id="ebe7a-178">データベースからパッケージを作成するために DAC Framework を使用する**抽出/エクスポート**アクション。たとえば、.dacpac ファイルを抽出し、bacpac ファイルをエクスポートします。これらの制限は適用されません。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-178">**Extract/Export** - On actions that use the DAC Framework to create a package from a database - for example, extract a .dacpac file, export a .bacpac file - these limitations do not apply.</span></span> <span data-ttu-id="ebe7a-179">パッケージのデータは、ソース データベースのデータを完全に忠実に再現しています。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-179">The data in the package is a full-fidelity representation of the data in the source database.</span></span> <span data-ttu-id="ebe7a-180">ここで述べた条件のいずれかがパッケージに存在する場合、抽出およびエクスポート ログに、上で述べたメッセージによって問題の概要が記録されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-180">If any of these conditions are present in the package, the extract/export log will contain a summary of the issues via the messages noted above.</span></span> <span data-ttu-id="ebe7a-181">これは、作成したパッケージが潜在的なデータ配置の問題を抱えていることをユーザーに警告するためです。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-181">This is to warn the user of potential data deployment issues with the package they created.</span></span> <span data-ttu-id="ebe7a-182">ログには、  **"これらの制限は、DAC Framework によって作成された DAC パッケージに格納されたデータ型および値の忠実性には影響しません。DAC パッケージをデータベースに配置した結果のデータ型および値に対してのみ適用されます。" という概要メッセージも記録されます。影響を受けるデータおよび、この制限の対処方法の詳細については、** [こちらのトピック](https://go.microsoft.com/fwlink/?LinkId=267086)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-182">The user will also see the following summary message in the log:  **These limitations do not affect the fidelity of the data types and values stored in the DAC package created by the DAC Framework; they only apply to the data types and values resulting from deploying a DAC package to a database. For more information about the data that is affected and how to work around this limitation, see** [this topic](https://go.microsoft.com/fwlink/?LinkId=267086).</span></span>  
  
-   <span data-ttu-id="ebe7a-183">**配置、パブリッシュ、インポート** - DAC Framework を使用してパッケージをデータベースに配置する操作 (たとえば、.dacpac ファイルの配置またはパブリッシュ、.bacpac ファイルのインポート) では、ここで述べた制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-183">**Deploy/Publish/Import** - On actions that use the DAC Framework to deploy a package to a database, like to deploy or publish a .dacpac file, and import a .bacpac file, these limitations do apply.</span></span> <span data-ttu-id="ebe7a-184">対象データベースに作成されるデータが、パッケージのデータを完全に忠実に再現していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-184">The data that results in the target database may not contain a full-fidelity representation of the data in the package.</span></span> <span data-ttu-id="ebe7a-185">配置およびインポートのログには、問題が発生したすべてのインスタンスに関して、上記のメッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-185">The Deploy/Import log will contain a message, noted above, for every instance the issue is encountered.</span></span> <span data-ttu-id="ebe7a-186">操作はエラーによってブロックされます (上記の分類 3 を参照)。しかし、他の警告では続行されます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-186">The operation will be blocked by errors - see category 3 above - but will proceed with the other warnings.</span></span>  
  
     <span data-ttu-id="ebe7a-187">この場合に影響を受けるデータおよび、配置、パブリッシュ、インポートの各操作時におけるこの制限の対処方法の詳細については、 [こちらのトピック](https://go.microsoft.com/fwlink/?LinkId=267087)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-187">For more information about the data that is affected in this scenario and how to work around this limitation for deploy/publish/import actions, see [this topic](https://go.microsoft.com/fwlink/?LinkId=267087).</span></span>  
  
-   <span data-ttu-id="ebe7a-188">**回避策**-抽出およびエクスポート操作では、完全に忠実な BCP データファイルが .dacpac または bacpac ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-188">**Workarounds** - Extract and export operations will write full-fidelity BCP data files into the .dacpac or .bacpac files.</span></span> <span data-ttu-id="ebe7a-189">制限を回避するには、SQL Server の BCP.exe コマンド ライン ユーティリティを使用して、完全に忠実なデータを DAC パッケージから対象データベースに配置します。</span><span class="sxs-lookup"><span data-stu-id="ebe7a-189">To avoid limitations, use the SQL Server BCP.exe command line utility to deploy full-fidelity data to a target database from a DAC package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe7a-190">参照</span><span class="sxs-lookup"><span data-stu-id="ebe7a-190">See Also</span></span>  
 [<span data-ttu-id="ebe7a-191">データ層アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ebe7a-191">Data-tier Applications</span></span>](data-tier-applications.md)  
  
  
