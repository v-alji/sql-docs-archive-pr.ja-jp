---
title: カスタム アセンブリの配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d88e1db844304b5cbb51f4af52b4715ef7e8c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741638"
---
# <a name="deploying-a-custom-assembly"></a><span data-ttu-id="de6bf-102">カスタム アセンブリの配置</span><span class="sxs-lookup"><span data-stu-id="de6bf-102">Deploying a Custom Assembly</span></span>
  <span data-ttu-id="de6bf-103">でカスタムアセンブリを配置するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、レポートデザイナーとレポートサーバーの両方のアプリケーションフォルダーにアセンブリを配置します。</span><span class="sxs-lookup"><span data-stu-id="de6bf-103">To deploy a custom assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], place the assembly in the application folders of both Report Designer and the report server.</span></span> <span data-ttu-id="de6bf-104">既定では、カスタム アセンブリには [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の `Execution` 権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-104">By default, custom assemblies are granted `Execution` permission in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="de6bf-105">カスタム アセンブリに Execute アクセス許可よりも上位のアクセス許可を付与するには、レポート サーバーの rssrvpolicy.config 構成ファイルとレポート デザイナー プレビュー ウィンドウの rspreviewpolicy.config 構成ファイルを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-105">To grant custom assemblies privileges beyond Execute permission, you will need to edit the rssrvpolicy.config configuration file for the report server and the rspreviewpolicy.config configuration file for the Report Designer preview window.</span></span> <span data-ttu-id="de6bf-106">または、グローバル アセンブリ キャッシュ (GAC) にカスタム アセンブリをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-106">Alternatively, you can install your custom assembly in the global assembly cache (GAC).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de6bf-107">レポート デザイナーには 2 種類のプレビュー モードがあります。1 つは [プレビュー] タブ。もう 1 つは、レポート プロジェクトを `DebugLocal` モードで開始したときに起動されるポップアップ プレビュー ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="de6bf-107">There are two preview modes for Report Designer: the Preview tab and the pop-up preview window that is launched when your report project is started in `DebugLocal` mode.</span></span> <span data-ttu-id="de6bf-108">[プレビュー] タブでは、`FullTrust` 権限セットを使用してすべてのレポート式を実行します。セキュリティ ポリシー設定は適用しません。</span><span class="sxs-lookup"><span data-stu-id="de6bf-108">The Preview tab executes all report expressions using the `FullTrust` permission set and does not apply security policy settings.</span></span> <span data-ttu-id="de6bf-109">レポート サーバー機能のシミュレーションを目的としているプレビュー ウィンドウには、ポリシー構成ファイルが備わっています。レポート デザイナーでカスタム アセンブリを使用する場合、ユーザーまたは管理者はこの構成ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-109">The pop-up preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies in Report Designer.</span></span> <span data-ttu-id="de6bf-110">また、このポップアップ プレビュー ウィンドウでは、カスタム アセンブリがロックされます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-110">This pop-up preview also locks the custom assembly.</span></span> <span data-ttu-id="de6bf-111">したがって、カスタム アセンブリ コードを変更または更新するには、プレビュー ウィンドウを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-111">Therefore, you need to close the preview window in order to modify or update your custom assembly code.</span></span>  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a><span data-ttu-id="de6bf-112">カスタム アセンブリを Reporting Services に配置するには</span><span class="sxs-lookup"><span data-stu-id="de6bf-112">To deploy a custom assembly in Reporting Services</span></span>  
  
1.  <span data-ttu-id="de6bf-113">カスタム アセンブリを構築場所からレポート サーバーの bin フォルダーまたはレポート デザイナーのフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="de6bf-113">Copy your custom assembly from your build location to the report server bin folder or the Report Designer folder.</span></span> <span data-ttu-id="de6bf-114">レポート サーバーの bin フォルダーの既定の場所は、%ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin です。</span><span class="sxs-lookup"><span data-stu-id="de6bf-114">The default location of the bin folder for the report server is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span> <span data-ttu-id="de6bf-115">レポート デザイナー フォルダーの既定の場所は、%ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。</span><span class="sxs-lookup"><span data-stu-id="de6bf-115">The default location of the Report Designer is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
     <span data-ttu-id="de6bf-116">カスタム アセンブリをレポート サーバーの bin フォルダーに配置した場合は、このカスタム アセンブリを参照するレポートをパブリッシュできます。レポート デザイナー フォルダーに配置した場合は、このカスタム アセンブリを参照するレポートをレポート デザイナーで実行およびデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-116">Placing your custom assembly in the report server bin folder enables you to publish reports that reference your custom assembly, and placing it in the Report Designer folder enables you to run and debug reports that reference your custom assembly in Report Designer.</span></span>  
  
     <span data-ttu-id="de6bf-117">カスタム アセンブリ コードに既定の実行権限よりも上位の権限を付与するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="de6bf-117">If you need to grant your custom assembly code permissions beyond the default execute permissions:</span></span>  
  
2.  <span data-ttu-id="de6bf-118">適切な構成ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-118">Open the appropriate configuration file.</span></span> <span data-ttu-id="de6bf-119">rssrvpolicy.config の既定の場所は、%ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer です。</span><span class="sxs-lookup"><span data-stu-id="de6bf-119">The default location of rssrvpolicy.config is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer.</span></span> <span data-ttu-id="de6bf-120">rspreviewpolicy.config の既定の場所は、%ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。</span><span class="sxs-lookup"><span data-stu-id="de6bf-120">The default location of rspreviewpolicy.config is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
3.  <span data-ttu-id="de6bf-121">カスタム アセンブリのコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="de6bf-121">Add a code group for your custom assembly.</span></span> <span data-ttu-id="de6bf-122">詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de6bf-122">For more information, see [Secure Development &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="updating-custom-assemblies"></a><span data-ttu-id="de6bf-123">カスタム アセンブリの更新</span><span class="sxs-lookup"><span data-stu-id="de6bf-123">Updating Custom Assemblies</span></span>  
 <span data-ttu-id="de6bf-124">ある時点では、パブリッシュされた複数のレポートが参照するカスタム アセンブリのバージョンの更新が必要なことがあります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-124">At some point, you may need to update a version of a custom assembly that is currently being referenced by several published reports.</span></span> <span data-ttu-id="de6bf-125">このようなアセンブリがレポート サーバーまたはレポート デザイナーの bin ディレクトリに既に存在し、アセンブリのバージョン番号が何らかの方法で増加するか変わった場合は、現在パブリッシュされているレポートが適切に機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-125">If that assembly already exists in the bin directory of the report server or Report Designer and the version number of the assembly is incremented or changed in some way, the currently published reports will no longer work properly.</span></span> <span data-ttu-id="de6bf-126">レポート定義の `CodeModules` 要素で参照されているアセンブリのバージョンを更新し、レポートを再度パブリッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-126">You will need to update the version of the assembly that is referenced in the `CodeModules` element of the report definition and republish the reports.</span></span> <span data-ttu-id="de6bf-127">カスタム アセンブリを頻繁に更新することがあらかじめわかっていて、現在パブリッシュされているレポートが新しいアセンブリを参照する必要がある場合は、特定のアセンブリのすべての更新に同じバージョン番号を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="de6bf-127">If you know that you will frequently update a custom assembly and your currently published reports need to reference the new assembly, you may want to consider using the same version number across all updates of a particular assembly.</span></span>  
  
 <span data-ttu-id="de6bf-128">現在パブリッシュされているレポートがアセンブリの新バージョンを参照する必要がない場合は、カスタム アセンブリをグローバル アセンブリ キャッシュに配置できます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-128">If you do not need your currently published reports to reference the new version of the assembly, you can deploy your custom assembly to the global assembly cache.</span></span> <span data-ttu-id="de6bf-129">グローバル アセンブリ キャッシュは同じアセンブリのバージョンを複数保持できるため、現在のレポートがアセンブリの旧バージョンを参照し、新しくパブリッシュされたレポートが更新されたアセンブリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-129">The global assembly cache can maintain multiple versions of the same assembly, so that your current reports can reference the previous version of your assembly and your newly published reports can reference the updated assembly.</span></span> <span data-ttu-id="de6bf-130">別の方法として、レポート サーバーのリダイレクトのバインドを設定し、旧アセンブリの全要求を新しいアセンブリに強制的にリダイレクトすることもできます。</span><span class="sxs-lookup"><span data-stu-id="de6bf-130">Yet another approach would be to set the binding redirect of the report server to force a redirect of all requests for the old assembly to the new assembly.</span></span> <span data-ttu-id="de6bf-131">レポート サーバーの Web.config ファイルとレポート サーバーの ReportService.exe.config ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-131">You would need to modify the report server Web.config file and the report server ReportService.exe.config file.</span></span> <span data-ttu-id="de6bf-132">エントリは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="de6bf-132">The entry might look like the following:</span></span>  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de6bf-133">参照</span><span class="sxs-lookup"><span data-stu-id="de6bf-133">See Also</span></span>  
 <span data-ttu-id="de6bf-134">[レポートでのカスタムアセンブリの使用](using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="de6bf-134">[Using Custom Assemblies with Reports](using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="de6bf-135">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="de6bf-135">Working with Assemblies and the Global Assembly Cache</span></span>](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
