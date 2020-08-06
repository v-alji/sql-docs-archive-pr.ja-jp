---
title: スクリプティング ソリューションでの他のアセンブリの参照 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 685bbaa62da88e84cd848eb49dcf5bedb03d5390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633218"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a><span data-ttu-id="491af-102">スクリプティング ソリューションでの他のアセンブリの参照</span><span class="sxs-lookup"><span data-stu-id="491af-102">Referencing Other Assemblies in Scripting Solutions</span></span>
  <span data-ttu-id="491af-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリには、スクリプトの開発者が [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージにカスタム機能を実装するための強力なツール セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="491af-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library provides the script developer with a powerful set of tools for implementing custom functionality in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="491af-104">スクリプト タスクとスクリプト コンポーネントでは、カスタム マネージド アセンブリも使用できます。</span><span class="sxs-lookup"><span data-stu-id="491af-104">The Script task and the Script component can also use custom managed assemblies.</span></span>

> [!NOTE]
>  <span data-ttu-id="491af-105">Web サービスのオブジェクトやメソッドをパッケージで使用できるようにするには、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) の **[Web 参照の追加]** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="491af-105">To enable your packages to use the objects and methods from a Web service, use the **Add Web Reference** command available in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="491af-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のバージョンでは、Web サービスを使用するためにプロキシ クラスを生成する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="491af-106">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you had to generate a proxy class to use a Web service.</span></span>

## <a name="using-a-managed-assembly"></a><span data-ttu-id="491af-107">マネージド アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="491af-107">Using a Managed Assembly</span></span>
 <span data-ttu-id="491af-108">デザイン時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってマネージド アセンブリが検出されるようにするには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="491af-108">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find a managed assembly at design time, you must do the following steps:</span></span>

1.  <span data-ttu-id="491af-109">マネージド アセンブリをコンピューター上の任意のフォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="491af-109">Store the managed assembly in any folder on your computer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="491af-110">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のバージョンで追加できたのは、%windir%\Microsoft.NET\Framework\vx.x.xxxxx フォルダーか %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies フォルダーにあるマネージド アセンブリへの参照のみでした。</span><span class="sxs-lookup"><span data-stu-id="491af-110">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you could only add a reference to a managed assembly that was stored in the %windir%\Microsoft.NET\Framework\vx.x.xxxxx folder or the %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies folder.</span></span>

2.  <span data-ttu-id="491af-111">マネージド アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="491af-111">Add a reference to the managed assembly.</span></span>

     <span data-ttu-id="491af-112">参照を追加するには、VSTA の **[参照の追加]** ダイアログ ボックスにある **[参照]** タブで、マネージド アセンブリを探して追加します。</span><span class="sxs-lookup"><span data-stu-id="491af-112">To add the reference, in VSTA, in the **Add Reference** dialog box, on the **Browse** tab, locate and add the managed assembly.</span></span>

 <span data-ttu-id="491af-113">実行時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってマネージド アセンブリが検出されるようにするには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="491af-113">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find the managed assembly at run time, you must do the following steps:</span></span>

1.  <span data-ttu-id="491af-114">マネージド アセンブリに厳密な名前で署名します。</span><span class="sxs-lookup"><span data-stu-id="491af-114">Sign the managed assembly with a strong name.</span></span>

2.  <span data-ttu-id="491af-115">パッケージが実行されるコンピューターのグローバル アセンブリ キャッシュに、そのアセンブリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="491af-115">Install the assembly in the global assembly cache on the computer on which the package is run.</span></span>

     <span data-ttu-id="491af-116">詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="491af-116">For more information, see [Building, Deploying, and Debugging Custom Objects](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).</span></span>

## <a name="using-the-microsoft-net-framework-class-library"></a><span data-ttu-id="491af-117">Microsoft .NET Framework クラス ライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="491af-117">Using the Microsoft .NET Framework Class Library</span></span>
 <span data-ttu-id="491af-118">スクリプト タスクおよびスクリプト コンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリによって公開されている他のすべてのオブジェクトおよび機能を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="491af-118">The Script task and the Script component can take advantage of all the other objects and functionality exposed by the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="491af-119">たとえば、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用すると、ユーザーの環境に関する情報を取得し、パッケージを実行中のコンピューターとやり取りできます。</span><span class="sxs-lookup"><span data-stu-id="491af-119">For example, by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can retrieve information about your environment and interact with the computer that is running the package.</span></span>

 <span data-ttu-id="491af-120">使用頻度の高い [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="491af-120">This list describes several of the more frequently used [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes:</span></span>

-   <span data-ttu-id="491af-121">`System.Data`ADO.NET アーキテクチャが含まれています。</span><span class="sxs-lookup"><span data-stu-id="491af-121">`System.Data` Contains the ADO.NET architecture.</span></span>

-   <span data-ttu-id="491af-122">`System.IO`ファイルシステムおよびストリームへのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="491af-122">`System.IO` Provides an interface to the file system and streams.</span></span>

-   <span data-ttu-id="491af-123">`System.Windows.Forms`フォームの作成を提供します。</span><span class="sxs-lookup"><span data-stu-id="491af-123">`System.Windows.Forms` Provides form creation.</span></span>

-   <span data-ttu-id="491af-124">`System.Text.RegularExpressions`正規表現を操作するためのクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="491af-124">`System.Text.RegularExpressions` Provides classes for working with regular expressions.</span></span>

-   <span data-ttu-id="491af-125">`System.Environment`ローカルコンピューター、現在のユーザー、およびコンピューターとユーザー設定に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="491af-125">`System.Environment` Returns information about the local computer, the current user, and computer and user settings.</span></span>

-   <span data-ttu-id="491af-126">`System.Net`ネットワーク通信を提供します。</span><span class="sxs-lookup"><span data-stu-id="491af-126">`System.Net` Provides network communications.</span></span>

-   <span data-ttu-id="491af-127">`System.DirectoryServices`Active Directory を公開します。</span><span class="sxs-lookup"><span data-stu-id="491af-127">`System.DirectoryServices` Exposes Active Directory.</span></span>

-   <span data-ttu-id="491af-128">`System.Drawing`には、広範なイメージ操作ライブラリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="491af-128">`System.Drawing` Provides extensive image manipulation libraries.</span></span>

-   <span data-ttu-id="491af-129">`System.Threading`マルチスレッドプログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="491af-129">`System.Threading` Enables multithreaded programming.</span></span>

 <span data-ttu-id="491af-130">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の詳細については、MSDN ライブラリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="491af-130">For more information about the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see the MSDN Library.</span></span>

<span data-ttu-id="491af-131">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="491af-131">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="491af-132">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="491af-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="491af-133">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="491af-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="491af-134">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="491af-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="491af-135">参照</span><span class="sxs-lookup"><span data-stu-id="491af-135">See Also</span></span>
 [<span data-ttu-id="491af-136">スクリプトによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="491af-136">Extending Packages with Scripting</span></span>](extending-packages-with-scripting.md)


