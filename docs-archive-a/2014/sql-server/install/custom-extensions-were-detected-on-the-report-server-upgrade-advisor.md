---
title: レポートサーバーでカスタム拡張機能が検出されました (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rendering extensions [Reporting Services], custom extensions
- security extensions [Reporting Services]
- custom extensions [Reporting Services]
- data processing extensions [Reporting Services], custom extensions
- delivery extensions [Reporting Services]
ms.assetid: fa184bd7-11d6-4ea3-9249-bc1b13db49e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e4be596ff0f110515155f2aa14dc00aceaf85efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634228"
---
# <a name="custom-extensions-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="574d0-102">レポート サーバーでカスタム拡張機能が検出された (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="574d0-102">Custom extensions were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="574d0-103">構成ファイル内のカスタム拡張機能の設定がアップグレード アドバイザーによって検出されました。これは、データ処理、配信、表示、セキュリティ、または認証用のカスタム拡張機能が 1 つ以上インストールに含まれていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="574d0-103">Upgrade Advisor detected custom extension settings in the configuration files, indicating that your installation includes one or more custom extensions for data processing, delivery, rendering, security, or authentication.</span></span> <span data-ttu-id="574d0-104">アップグレードによって、拡張機能の構成設定はアップグレード後のレポート サーバーに移動されます。</span><span class="sxs-lookup"><span data-stu-id="574d0-104">Upgrade will move the extension configuration settings with the upgraded report server.</span></span> <span data-ttu-id="574d0-105">ただし、カスタム拡張機能を既存のレポート サーバーのインストール フォルダーにインストールした場合、アップグレードの処理中に、これらのカスタム拡張機能のアセンブリ ファイルは新しいインストール フォルダーに移動されません。</span><span class="sxs-lookup"><span data-stu-id="574d0-105">However, if the custom extensions are installed in the existing report server installation folder, the assembly files for those custom extensions will not be moved to the new installation folder during the upgrade process.</span></span> <span data-ttu-id="574d0-106">アップグレードの完了後、アセンブリ ファイルを新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストール フォルダーに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="574d0-106">After upgrade completes, you must move the assembly files to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
||  
|-|  
|<span data-ttu-id="574d0-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="574d0-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="574d0-108">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="574d0-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="574d0-109">説明</span><span class="sxs-lookup"><span data-stu-id="574d0-109">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="574d0-110">に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は拡張可能なアーキテクチャが用意されており、開発者はデータの処理、配信、表示、セキュリティ、および認証用のカスタム拡張機能を作成できます。</span><span class="sxs-lookup"><span data-stu-id="574d0-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides an extensible architecture that allows developers to create custom extensions for data processing, delivery, rendering, security, and authentication.</span></span>  
  
 <span data-ttu-id="574d0-111">現在インストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でカスタム拡張機能またはアセンブリを使用している場合、セットアップを使用してアップグレードを実行できますが、アップグレードの完了後に拡張機能を新しいインストール場所に移動するか、アップグレードの前に手順を実行する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="574d0-111">If custom extensions or assemblies are used in your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can use Setup to perform an upgrade, but you may need to move extensions to the new installation location after upgrade completes, or you may need to perform steps prior to upgrade.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="574d0-112">アイテムの値、スタイル、および書式設定を計算するためにレポートで使用するようにカスタム コード アセンブリが設定されているかどうかは、アップグレード アドバイザーによって検出されません。</span><span class="sxs-lookup"><span data-stu-id="574d0-112">Upgrade Advisor does not detect whether custom code assemblies are configured for use in reports to calculate item values, styles, and formatting.</span></span> <span data-ttu-id="574d0-113">詳細については、「[その他の Reporting Services アップグレードに関する問題](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-113">For more information, see [Other Reporting Services Upgrade Issues](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="574d0-114">カスタム拡張機能をソフトウェア ベンダーから購入した場合、ベンダーに問い合わせて、そのカスタム機能のアップグレードに関する詳細を確認してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-114">If you purchased custom extensions from a software vendor, check with the vendor for additional information about upgrading your custom functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="574d0-115">修正措置</span><span class="sxs-lookup"><span data-stu-id="574d0-115">Corrective Action</span></span>  
 <span data-ttu-id="574d0-116">次のセクションに従って、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のアップグレードに加えて、またはアップグレードの前に実行する手順を確認してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-116">Use the following sections to determine steps to perform in addition to or prior to performing an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
 [<span data-ttu-id="574d0-117">データ処理または配信のカスタム拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-117">Custom data processing or delivery extensions</span></span>](#dataprocdeliver)  
  
 [<span data-ttu-id="574d0-118">カスタム表示拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-118">Custom rendering extensions</span></span>](#render)  
  
 [<span data-ttu-id="574d0-119">SQL Server 2000 レポートサーバーでのカスタムセキュリティまたは認証の拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-119">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>](#secauth2000)  
  
 [<span data-ttu-id="574d0-120">SQL Server 2005 レポート サーバーのセキュリティまたは認証のカスタム拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-120">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>](#secauth2005)  
  
 <span data-ttu-id="574d0-121">アップグレードの完了後、拡張機能アセンブリを新しいインストール フォルダーに移動し、カスタム拡張機能が想定どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="574d0-121">After upgrade completes, move the extension assemblies to the new installation folder and then verify that the custom extensions work as expected.</span></span> <span data-ttu-id="574d0-122">拡張機能が動作しない場合は、再コンパイルが必要なことがあります。</span><span class="sxs-lookup"><span data-stu-id="574d0-122">If your extension does not work, you might have to recompile it.</span></span>  
  
#### <a name="to-recompile-an-extension"></a><span data-ttu-id="574d0-123">拡張機能を再コンパイルするには</span><span class="sxs-lookup"><span data-stu-id="574d0-123">To recompile an extension</span></span>  
  
1.  <span data-ttu-id="574d0-124">Microsoft.ReportingServices.Interfaces.dll ファイルをソース コードが含まれるフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="574d0-124">Copy the Microsoft.ReportingServices.Interfaces.dll file to the folder that contains your source code.</span></span>  
  
2.  <span data-ttu-id="574d0-125">ソース ファイルが含まれるプロジェクトを開き、Microsoft.ReportingServices.Interfaces.dll ファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="574d0-125">Open the project that contains your source files and add a reference to the Microsoft.ReportingServices.Interfaces.dll file.</span></span>  
  
3.  <span data-ttu-id="574d0-126">ソリューションを再構築して拡張機能をバインドします。</span><span class="sxs-lookup"><span data-stu-id="574d0-126">Rebuild the solution to bind the extension.</span></span>  
  
 <span data-ttu-id="574d0-127">アップグレードを続行しない場合、代わりに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を移行できます。</span><span class="sxs-lookup"><span data-stu-id="574d0-127">If you decide not to continue with upgrade, you might decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="574d0-128">カスタム拡張機能の移行手順については、このトピックの「[カスタム拡張機能の移行](#migrcustext)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-128">For steps on migrating custom extensions, see [Migrating custom extensions](#migrcustext) in this topic.</span></span>  
  
###  <a name="custom-data-processing-or-delivery-extensions"></a><a name="dataprocdeliver"></a><span data-ttu-id="574d0-129">カスタムデータ処理または配信拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-129">Custom data processing or delivery extensions</span></span>  
 <span data-ttu-id="574d0-130">データ処理または配信のカスタム拡張機能がアップグレード アドバイザーによって検出された場合、アップグレード プロセスはブロックされません。</span><span class="sxs-lookup"><span data-stu-id="574d0-130">If Upgrade Advisor detects custom data processing or delivery extensions, the upgrade process is not blocked.</span></span> <span data-ttu-id="574d0-131">ただし、アップグレードの完了後、これらの拡張機能によって提供されるカスタム機能を使用する前に、追加の手順を実行する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="574d0-131">However, after upgrade completes, you might need to perform additional steps before the custom functionality provided by these extensions will work.</span></span> <span data-ttu-id="574d0-132">たとえば、カスタム拡張機能ファイルが [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストール フォルダーにインストールされている場合は、追加の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="574d0-132">For example, you must perform additional steps when the custom extension files are installed in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
##### <a name="post-upgrade-steps-for-custom-data-processing-or-delivery-extensions"></a><span data-ttu-id="574d0-133">データ処理または配信のカスタム拡張機能のアップグレード後に行う手順</span><span class="sxs-lookup"><span data-stu-id="574d0-133">Post-upgrade steps for custom data processing or delivery extensions</span></span>  
  
1.  <span data-ttu-id="574d0-134">1 つまたは複数の拡張機能ファイルを、レポート サーバーの新しいプログラム フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="574d0-134">Move the extension file or files to the new program folder for the report server.</span></span> <span data-ttu-id="574d0-135">既定では、レポートサーバーのプログラムフォルダーは、SQL Server \ MSRS10_50 にあります。 \<*instance_name*>\ レポートサーバー。</span><span class="sxs-lookup"><span data-stu-id="574d0-135">By default, the report server program folder is in \Program Files\Microsoft SQL Server\MSRS10_50.\<*instance_name*>\report server.</span></span>  
  
 <span data-ttu-id="574d0-136">詳細については、SQL Server オンライン ブックの「データ処理拡張機能の配置」および「配信拡張機能の実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-136">For more information, see "Deploying a Data Processing Extension" and "Implementing a Delivery Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-rendering-extensions"></a><a name="render"></a><span data-ttu-id="574d0-137">カスタム表示拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-137">Custom rendering extensions</span></span>  
 <span data-ttu-id="574d0-138">カスタム表示拡張機能がアップグレード アドバイザーによって検出された場合、アップグレード プロセスはブロックされます。</span><span class="sxs-lookup"><span data-stu-id="574d0-138">If Upgrade Advisor detects custom rendering extensions, the upgrade process is blocked.</span></span> <span data-ttu-id="574d0-139">アップグレード プロセスを続行するには、カスタム拡張機能の構成エントリを構成ファイルから削除します。</span><span class="sxs-lookup"><span data-stu-id="574d0-139">You can continue with the upgrade process by removing the custom extension configuration entries from the configuration file.</span></span> <span data-ttu-id="574d0-140">ただし、アップグレードの完了後にカスタム拡張機能を使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="574d0-140">However, this will cause the custom extensions to be unavailable to users after upgrade completes.</span></span> <span data-ttu-id="574d0-141">アップグレード後にカスタム表示拡張機能が必要な場合は、更新された表示拡張機能をビルドするか、更新された表示拡張機能をカスタム拡張機能ベンダーから入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="574d0-141">If you need custom rendering extensions after upgrade, you must build updated rendering extensions or obtain updated rendering extensions from a custom extension vendor.</span></span>  
  
 <span data-ttu-id="574d0-142">アップグレードを可能にするための手順を実行する必要があります。または、代わりに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の移行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="574d0-142">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="574d0-143">更新された表示拡張機能が想定どおりに動作することをテストして確認するまで、レポート サーバーをアップグレードまたは移行しないでください。</span><span class="sxs-lookup"><span data-stu-id="574d0-143">Do not upgrade or migrate your report server until you have tested and verified that the updated rendering extension works as expected.</span></span>  
  
##### <a name="to-upgrade-custom-rendering-extensions"></a><span data-ttu-id="574d0-144">カスタム表示拡張機能をアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="574d0-144">To upgrade custom rendering extensions</span></span>  
  
1.  <span data-ttu-id="574d0-145">最新のインターフェイスを備えた表示拡張機能を入手します。</span><span class="sxs-lookup"><span data-stu-id="574d0-145">Obtain rendering extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="574d0-146">RSReportServer.config から 1 つまたは複数の古いカスタム表示拡張機能エントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="574d0-146">Remove the old custom rendering extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="574d0-147">レポート サーバーをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="574d0-147">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="574d0-148">アップグレードが完了したら、更新された拡張機能をレポート サーバーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="574d0-148">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="574d0-149">詳細については、SQL Server オンライン ブックの「表示拡張機能の実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-149">For more information, see "Implementing a Rendering Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2000-report-server"></a><a name="secauth2000"></a><span data-ttu-id="574d0-150">SQL Server 2000 レポートサーバーでのカスタムセキュリティまたは認証の拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-150">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>  
 <span data-ttu-id="574d0-151">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] レポート サーバーのセキュリティまたは認証のカスタム拡張機能がアップグレード アドバイザーによって検出された場合、アップグレード プロセスはブロックされます。</span><span class="sxs-lookup"><span data-stu-id="574d0-151">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="574d0-152">アップグレードを可能にするための手順を実行する必要があります。または、代わりに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の移行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="574d0-152">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="574d0-153">いずれの場合も、Microsoft.ReportingServices.Interfaces.dll の最新のインターフェイスを使用して、拡張機能を更新および再コンパイルする必要があります。これは、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] と [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ではインターフェイスが異なるためです。</span><span class="sxs-lookup"><span data-stu-id="574d0-153">In either case, you must update and recompile the extensions with the latest interfaces in Microsoft.ReportingServices.Interfaces.dll, because the interfaces have changed between [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="574d0-154">更新されたセキュリティまたは認証の拡張機能が想定どおりに動作することをテストして確認するまで、レポート サーバーをアップグレードまたは移行しないでください。</span><span class="sxs-lookup"><span data-stu-id="574d0-154">Do not upgrade or migrate your report server until you have tested and verified that the updated security or authentication extension works as expected.</span></span>  
  
 <span data-ttu-id="574d0-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用に作成したカスタム認証拡張機能を使用する場合は、モデル ドリブン レポート用に導入された新しいクラスとメンバーをサポートするようにソース コードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="574d0-155">If you are using a custom authentication extension that you created for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the source code to support new classes and members introduced for model-driven reporting.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2000-report-server"></a><span data-ttu-id="574d0-156">SQL Server 2000 レポートサーバーからカスタムセキュリティまたは認証の拡張機能をアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="574d0-156">To upgrade custom security or authentication extensions from a SQL Server 2000 report server</span></span>  
  
1.  <span data-ttu-id="574d0-157">最新のインターフェイスを使用して、すべてのセキュリティまたは認証の拡張機能を更新および再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="574d0-157">Update and recompile any security or authentication extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="574d0-158">RSReportServer.config から 1 つまたは複数のセキュリティまたは認証の拡張機能エントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="574d0-158">Remove the security or authentication extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="574d0-159">レポート サーバーをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="574d0-159">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="574d0-160">アップグレードが完了したら、更新された拡張機能をレポート サーバーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="574d0-160">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="574d0-161">詳細については、SQL Server オンライン ブックの「セキュリティ拡張機能の実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-161">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2005-report-server"></a><a name="secauth2005"></a><span data-ttu-id="574d0-162">SQL Server 2005 レポートサーバーでのカスタムセキュリティまたは認証の拡張機能</span><span class="sxs-lookup"><span data-stu-id="574d0-162">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>  
 <span data-ttu-id="574d0-163">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポート サーバーのセキュリティまたは認証のカスタム拡張機能がアップグレード アドバイザーによって検出された場合、アップグレード プロセスはブロックされます。</span><span class="sxs-lookup"><span data-stu-id="574d0-163">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="574d0-164">アップグレードを可能にするための手順を実行する必要があります。または、代わりに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の移行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="574d0-164">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2005-report-server"></a><span data-ttu-id="574d0-165">SQL Server 2005 レポート サーバーのセキュリティまたは認証のカスタム拡張機能をアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="574d0-165">To upgrade custom security or authentication extensions from a SQL Server 2005 report server</span></span>  
  
1.  <span data-ttu-id="574d0-166">RSReportServer.config からセキュリティまたは認証の拡張機能の構成エントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="574d0-166">Remove the security or authentication extension configuration entries from RSReportServer.config.</span></span>  
  
2.  <span data-ttu-id="574d0-167">レポート サーバーをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="574d0-167">Upgrade the report server.</span></span>  
  
3.  <span data-ttu-id="574d0-168">アップグレードの完了後、構成エントリを再び RSReportServer.config に追加します。</span><span class="sxs-lookup"><span data-stu-id="574d0-168">After upgrade completes, add the configuration entries back in RSReportServer.config.</span></span>  
  
4.  <span data-ttu-id="574d0-169">拡張機能アセンブリが古い [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストール フォルダーにインストールされている場合、これを新しいインストール フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="574d0-169">If the extension assemblies were installed in the old [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder, move then to the new installation folder.</span></span>  
  
 <span data-ttu-id="574d0-170">詳細については、SQL Server オンライン ブックの「セキュリティ拡張機能の実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="574d0-170">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="migrating-custom-extensions"></a><a name="migrcustext"></a><span data-ttu-id="574d0-171">カスタム拡張機能の移行</span><span class="sxs-lookup"><span data-stu-id="574d0-171">Migrating custom extensions</span></span>  
 <span data-ttu-id="574d0-172">アップグレードを実行する代わりに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を移行する場合は、カスタム拡張機能を新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスに移行する手順に従います。</span><span class="sxs-lookup"><span data-stu-id="574d0-172">If you decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead performing an upgrade, use the steps to migrate custom extensions to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance.</span></span>  
  
##### <a name="to-migrate-custom-extensions-to-a-new-reporting-services-instance"></a><span data-ttu-id="574d0-173">カスタム拡張機能を新しい Reporting Services インスタンスに移行するには</span><span class="sxs-lookup"><span data-stu-id="574d0-173">To migrate custom extensions to a new Reporting Services instance</span></span>  
  
1.  <span data-ttu-id="574d0-174">最新の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インターフェイスを使用して更新された拡張機能をビルドまたは入手します。</span><span class="sxs-lookup"><span data-stu-id="574d0-174">Build or obtain updated extensions with the latest [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] interfaces.</span></span>  
  
2.  <span data-ttu-id="574d0-175">レポート サーバーを新しいインスタンスに移行します。</span><span class="sxs-lookup"><span data-stu-id="574d0-175">Migrate the report server to a new instance.</span></span>  
  
3.  <span data-ttu-id="574d0-176">新しいインスタンスで拡張機能を構成します。</span><span class="sxs-lookup"><span data-stu-id="574d0-176">Configure the extensions on the new instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="574d0-177">参照</span><span class="sxs-lookup"><span data-stu-id="574d0-177">See Also</span></span>  
 [<span data-ttu-id="574d0-178">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="574d0-178">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
