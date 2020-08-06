---
title: Reporting Services セキュリティ ポリシー ファイルの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- CodeGroup elements
- configuration files [Reporting Services]
- code access security [Reporting Services], security policies
- security policies [Reporting Services]
- security configuration files [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: 2280fff6-3de7-44b1-87da-5db0ec975928
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15c5422741137505bc29a2de861fca1420e455d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645399"
---
# <a name="using-reporting-services-security-policy-files"></a><span data-ttu-id="38ca0-102">Reporting Services セキュリティ ポリシー ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="38ca0-102">Using Reporting Services Security Policy Files</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="38ca0-103">は、セットアップ時にファイル システムにコピーされる 3 つの構成ファイルにコンポーネントのセキュリティ ポリシーを格納します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-103">stores component security policy information in three configuration files that are copied to the file system during setup.</span></span> <span data-ttu-id="38ca0-104">これらの構成ファイルには、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のコード アセンブリについて、内部用セキュリティ ポリシーとユーザー定義セキュリティ ポリシーの組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-104">These configuration files can contain a combination of internal-use and user-defined security policies for code assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="38ca0-105">3 つの構成ファイルは、セキュリティ保護可能な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の 3 つのコンポーネント (レポート サーバーと Windows サービス、レポート マネージャー Web アプリケーション、レポート デザイナー プレビュー ウィンドウ) に対応しています。</span><span class="sxs-lookup"><span data-stu-id="38ca0-105">The three configuration files correspond to three securable components in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]: The report server and Windows service, the Report Manager Web application, and the Report Designer preview window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38ca0-106">レポート デザイナーには 2 種類のプレビュー モードがあります。1 つは [プレビュー] タブ、もう 1 つは、レポート プロジェクトを **DebugLocal** モードで開始したときに起動されるポップアップ プレビュー ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="38ca0-106">There are two preview modes for Report Designer: the preview tab and the pop-up preview window that is launched when your Report Project is started in **DebugLocal** mode.</span></span> <span data-ttu-id="38ca0-107">**[プレビュー]** タブはセキュリティ保護可能なコンポーネントではなく、セキュリティ ポリシー設定が適用されません。</span><span class="sxs-lookup"><span data-stu-id="38ca0-107">The **Preview** tab is not a securable component and does not apply security policy settings.</span></span> <span data-ttu-id="38ca0-108">レポート サーバー機能のシミュレーションを目的としているプレビュー ウィンドウには、ポリシー構成ファイルが備わっています。レポート デザイナーでカスタム アセンブリやカスタム拡張機能を使用する場合、ユーザーまたは管理者はこの構成ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38ca0-108">The preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies and custom extensions in Report Designer.</span></span>  
  
 <span data-ttu-id="38ca0-109">セキュリティ ポリシー構成ファイルには、セキュリティ クラス情報、一部の既定の名前付き権限セット、および [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のアセンブリで使用するコード グループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="38ca0-109">The security policy configuration files contain security class information, some default named permission sets, and the code groups for assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="38ca0-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のポリシー構成ファイルは Security.config ファイルと似ており、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のコンピューター レベル ポリシーおよびエンタープライズ レベル ポリシーに基づいてコード グループ階層と権限セットを決定します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-110">The policy configuration files of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are similar to the Security.config file that determines the code group hierarchy and permission sets associated with machine and enterprise level policies in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="38ca0-111">このファイルの場所は、C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config です。</span><span class="sxs-lookup"><span data-stu-id="38ca0-111">The location of this file is C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config.</span></span>  
  
## <a name="policy-files-in-reporting-services"></a><span data-ttu-id="38ca0-112">Reporting Services のポリシー ファイル</span><span class="sxs-lookup"><span data-stu-id="38ca0-112">Policy Files in Reporting Services</span></span>  
 <span data-ttu-id="38ca0-113">次の表は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のポリシー構成ファイル、既定インストールでの場所、および各機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="38ca0-113">The following table lists the policy configuration files in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], their locations (assuming a default installation), and their respective functions.</span></span>  
  
|<span data-ttu-id="38ca0-114">ファイル名</span><span class="sxs-lookup"><span data-stu-id="38ca0-114">File name</span></span>|<span data-ttu-id="38ca0-115">場所 (既定インストール)</span><span class="sxs-lookup"><span data-stu-id="38ca0-115">Location (default installation)</span></span>|<span data-ttu-id="38ca0-116">説明</span><span class="sxs-lookup"><span data-stu-id="38ca0-116">Description</span></span>|  
|---------------|---------------------------------------|-----------------|  
|<span data-ttu-id="38ca0-117">rssrvpolicy.config</span><span class="sxs-lookup"><span data-stu-id="38ca0-117">rssrvpolicy.config</span></span>|<span data-ttu-id="38ca0-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span><span class="sxs-lookup"><span data-stu-id="38ca0-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span></span>|<span data-ttu-id="38ca0-119">レポート サーバーのポリシー構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="38ca0-119">The report server policy configuration file.</span></span> <span data-ttu-id="38ca0-120">これらのセキュリティ ポリシーは、レポートがレポート サーバーに配置された後のレポートの式とカスタム アセンブリに主に影響します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-120">These security policies primarily affect report expressions and custom assemblies once a report is deployed to a report server.</span></span> <span data-ttu-id="38ca0-121">このポリシー ファイルは、カスタム データ、配信、表示、およびレポート サーバーに配置されるセキュリティ拡張機能にも影響します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-121">This policy file also affects custom data, delivery, rendering and security extensions deployed to the report server.</span></span>|  
|<span data-ttu-id="38ca0-122">rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="38ca0-122">rsmgrpolicy.config</span></span>|<span data-ttu-id="38ca0-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span><span class="sxs-lookup"><span data-stu-id="38ca0-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span></span>|<span data-ttu-id="38ca0-124">レポート マネージャーのポリシー構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="38ca0-124">Report Manager policy configuration file.</span></span> <span data-ttu-id="38ca0-125">これらのセキュリティ ポリシーは、カスタム配信用のサブスクリプション ユーザー インターフェイス拡張機能など、レポート マネージャーを拡張するすべてのアセンブリに影響します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-125">These security policies affect all assemblies that extend Report Manager; for example, subscription user interface extensions for custom delivery.</span></span>|  
|<span data-ttu-id="38ca0-126">rspreviewpolicy.config</span><span class="sxs-lookup"><span data-stu-id="38ca0-126">rspreviewpolicy.config</span></span>|<span data-ttu-id="38ca0-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span><span class="sxs-lookup"><span data-stu-id="38ca0-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span></span>|<span data-ttu-id="38ca0-128">レポート デザイナーのスタンドアロン プレビュー ポリシー構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="38ca0-128">The Report Designer stand-alone preview policy configuration file.</span></span> <span data-ttu-id="38ca0-129">これらのセキュリティ ポリシーは、プレビューおよび開発中にレポートに使用するカスタム アセンブリとレポートの式に影響します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-129">These security policies affect custom assemblies and report expressions that are used in reports during preview and development.</span></span> <span data-ttu-id="38ca0-130">これらのポリシーは、レポート デザイナーに配置されるデータ処理拡張機能などのカスタム拡張機能にも影響します。</span><span class="sxs-lookup"><span data-stu-id="38ca0-130">These policies also affect custom extensions, such as data processing extensions, that are deployed to Report Designer.</span></span>|  
  
## <a name="modifying-configuration-files"></a><span data-ttu-id="38ca0-131">構成ファイルの変更</span><span class="sxs-lookup"><span data-stu-id="38ca0-131">Modifying Configuration Files</span></span>  
 <span data-ttu-id="38ca0-132">構成設定は、XML 要素または XML 属性のいずれかとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-132">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="38ca0-133">XML ファイルおよび構成ファイルを理解している場合は、テキスト エディターまたはコード エディターを使用して、ユーザーが定義可能な設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-133">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span> <span data-ttu-id="38ca0-134">セキュリティ構成ファイルには、コード グループ階層構造に関する情報と、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のポリシー レベルに関連付けたアクセス許可セットを含めます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-134">Security configuration files contain information about the code group hierarchy and permission sets associated with a policy level in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="38ca0-135">最初に Security.config ファイルのセキュリティ ポリシーを変更する場合は、.NET Framework 構成ユーティリティ (Mscorcfg.msc) またはコード アクセス セキュリティ ポリシー ユーティリティ (Caspol.exe) を使用して、ポリシーの変更をポリシー ファイルの有効な XML 構成要素に対応させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="38ca0-135">It is recommended that you use the .NET Framework Configuration Utility (Mscorcfg.msc) or Code Access Security Policy Utility (Caspol.exe) to modify security policies in the Security.config file first, so that policy changes correspond to valid XML configuration elements for policy files.</span></span> <span data-ttu-id="38ca0-136">その後で、新しいコード グループと権限セットを Security.config から切り取って、コードと権限追加先のコンポーネントのポリシーに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-136">Once you have done that, you can cut and paste the new code groups and permission sets from Security.config to the policy file for the component to which you are adding code permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="38ca0-137">ポリシー構成ファイルをバックアップした後で変更を行ってください。</span><span class="sxs-lookup"><span data-stu-id="38ca0-137">You should backup your policy configuration files prior to making any changes.</span></span>  
  
 <span data-ttu-id="38ca0-138">この方法を実行すると、2 つの結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-138">Using this approach accomplishes two things.</span></span> <span data-ttu-id="38ca0-139">まず、仮想ツールを使用して [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] にコード グループと権限セットを構築できます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-139">First, it enables you to use a visual tool to build your code groups and permission sets for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="38ca0-140">最初から XML 構成ファイル要素を記述するよりもこの方がはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="38ca0-140">This is much easier than writing XML configuration elements from scratch.</span></span> <span data-ttu-id="38ca0-141">次に、不適切な形式の XML 要素と属性によってセキュリティ ポリシー構成ファイルが破損することがありません。</span><span class="sxs-lookup"><span data-stu-id="38ca0-141">Secondly, it ensures that you do not corrupt the security policy configuration files with malformed XML elements and attributes.</span></span> <span data-ttu-id="38ca0-142">コード アクセス セキュリティ ポリシー ユーティリティの詳細については、MSDN の「Reporting Services セキュリティ ポリシー ファイルの使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38ca0-142">For more information about the Code Access Security Policy Utility, see Using Reporting Services Security Policy Files on MSDN.</span></span>  
  
 <span data-ttu-id="38ca0-143">ポリシー構成ファイルを変更する前に、このセクションおよび関連項目で入手できるすべての情報を読んでおく必要があります。</span><span class="sxs-lookup"><span data-stu-id="38ca0-143">Before modifying policy configuration files, you should read all the information available in this section and related topics.</span></span> <span data-ttu-id="38ca0-144">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のポリシー構成ファイルを変更すると、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] コンポーネントによる外部コード モジュール実行にセキュリティ上の重大な影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38ca0-144">Modifying the policy configuration of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] can have a significant security impact on how [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components execute external code modules.</span></span>  
  
## <a name="placement-of-codegroup-elements-for-extensions"></a><span data-ttu-id="38ca0-145">拡張機能の CodeGroup 要素の配置</span><span class="sxs-lookup"><span data-stu-id="38ca0-145">Placement of CodeGroup Elements for Extensions</span></span>  
 <span data-ttu-id="38ca0-146">セキュリティ ポリシー ファイル内の CodeGroup 要素の配置は重要です。</span><span class="sxs-lookup"><span data-stu-id="38ca0-146">The placement of CodeGroup elements in a security policy file is important.</span></span> <span data-ttu-id="38ca0-147">開発した拡張機能とカスタム アセンブリの場合は、次のように URL メンバーシップ "$CodeGen$/\*" の既存エントリのすぐ下にカスタム コード グループを配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="38ca0-147">For extensions and custom assemblies that you develop, it is recommended that you place your custom code groups directly below the existing entry for the URL membership "$CodeGen$/\*", as indicated by the following:</span></span>  
  
```  
<CodeGroup  
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust">  
    <IMembershipCondition   
        class="UrlMembershipCondition"  
        version="1"  
        Url="$CodeGen$/*"  
    />  
</CodeGroup>  
<CodeGroup   
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust"  
    Name="MyCustomCodeGroup"  
    Description="Code group for my custom extension">  
        <IMembershipCondition class="UrlMembershipCondition"  
        version="1"  
        Url="C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\bin\MyAssembly.dll"  
        />  
</CodeGroup>  
```  
  
 <span data-ttu-id="38ca0-148">コード グループを順次追加できます。</span><span class="sxs-lookup"><span data-stu-id="38ca0-148">Additional code groups can be added one after another.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ca0-149">参照</span><span class="sxs-lookup"><span data-stu-id="38ca0-149">See Also</span></span>  
 [<span data-ttu-id="38ca0-150">セキュリティ ポリシーの概要</span><span class="sxs-lookup"><span data-stu-id="38ca0-150">Understanding Security Policies</span></span>](understanding-security-policies.md)  
  
  
