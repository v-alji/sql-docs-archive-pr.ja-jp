---
title: カスタム レポート アイテムの実装要件 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69fdf58eb385e819b524b9c5b5178997257c797c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741642"
---
# <a name="custom-report-item-implementation-requirements"></a><span data-ttu-id="dae67-102">カスタム レポート アイテムの実装要件</span><span class="sxs-lookup"><span data-stu-id="dae67-102">Custom Report Item Implementation Requirements</span></span>
  <span data-ttu-id="dae67-103">このトピックでは、カスタム レポート アイテムの開発と配置の前提条件について説明します。</span><span class="sxs-lookup"><span data-stu-id="dae67-103">This topic will discuss the prerequisites for developing and deploying custom report items.</span></span>  
  
## <a name="development-and-deployment-requirements"></a><span data-ttu-id="dae67-104">開発と配置の要件</span><span class="sxs-lookup"><span data-stu-id="dae67-104">Development and Deployment Requirements</span></span>  
 <span data-ttu-id="dae67-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のカスタム レポート アイテムを開発するには、次の条件が必要です。</span><span class="sxs-lookup"><span data-stu-id="dae67-105">Developing a custom report item for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requires the following:</span></span>  
  
-   <span data-ttu-id="dae67-106">およびを使用してを実行しているサーバーへの管理アクセス [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dae67-106">Administrative access to a server running [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]<span data-ttu-id="dae67-107">以上の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ソフトウェア開発キット (SDK) がインストールされている。</span><span class="sxs-lookup"><span data-stu-id="dae67-107">or above with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] software development kit (SDK) installed.</span></span>  
  
-   <span data-ttu-id="dae67-108">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントへのアクセス権を持つこと。</span><span class="sxs-lookup"><span data-stu-id="dae67-108">Access to the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
-   <span data-ttu-id="dae67-109">コンポーネントの作成および [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のコンポーネント モデル名前空間について理解していること。</span><span class="sxs-lookup"><span data-stu-id="dae67-109">Familiarity with component authoring and the component model namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="dae67-110">詳細については、msdn.microsoft.com の「コンポーネントの作成」および「Visual Studio のコンポーネント モデルの名前空間」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dae67-110">For more information, see "Component Authoring" and "Component Model Namespaces in Visual Studio" on msdn.microsoft.com.</span></span>  
  
## <a name="language-and-namespace-requirements"></a><span data-ttu-id="dae67-111">言語と名前空間の要件</span><span class="sxs-lookup"><span data-stu-id="dae67-111">Language and Namespace Requirements</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dae67-112">カスタム レポート アイテムは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を完全にサポートしています。</span><span class="sxs-lookup"><span data-stu-id="dae67-112">custom report items fully support the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="dae67-113">任意の .NET 準拠の言語を使用してカスタム レポート アイテムを開発できます。</span><span class="sxs-lookup"><span data-stu-id="dae67-113">You can develop custom report items using your choice of .NET-compliant languages.</span></span>  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="dae67-114">には、反復的なコーディング、デバッグ、テストのサイクルを簡素化および高速化し、開発を容易にするための多数のツールと機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="dae67-114">offers the developer many tools and features to simplify and accelerate the iterative cycles of coding, debugging, and testing and to make deployment easier.</span></span> <span data-ttu-id="dae67-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK には、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コンパイラと C# コンパイラ、および関連ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dae67-115">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK includes [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] and C# compilers and related tools.</span></span>  
  
-   <span data-ttu-id="dae67-116">カスタム レポート アイテムは、`Microsoft.ReportDesigner` 名前空間と <xref:Microsoft.ReportingServices.Interfaces> 名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="dae67-116">Custom report items use the `Microsoft.ReportDesigner` and <xref:Microsoft.ReportingServices.Interfaces> namespaces.</span></span> <span data-ttu-id="dae67-117">これらは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の一部としてインストールされた Microsoft.ReportingServices.Designer.DLL アセンブリと Microsoft.ReportingServices.Interfaces.DLL アセンブリに格納されています。</span><span class="sxs-lookup"><span data-stu-id="dae67-117">These are stored in the Microsoft.ReportingServices.Designer.DLL and Microsoft.ReportingServices.Interfaces.DLL assemblies, which are installed as part of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="dae67-118">カスタム レポート アイテムのデザイン時コンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 内の <xref:System.ComponentModel> 名前空間からインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dae67-118">Custom report item design-time components need to implement interfaces from the <xref:System.ComponentModel> namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="dae67-119"><xref:System.ComponentModel> は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントに記載されています。</span><span class="sxs-lookup"><span data-stu-id="dae67-119">The <xref:System.ComponentModel> is documented in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dae67-120">既定では、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と共にインストールされますが、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK はインストールされません。</span><span class="sxs-lookup"><span data-stu-id="dae67-120">By default, the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK is not.</span></span> <span data-ttu-id="dae67-121">SDK がコンピューターにインストールされておらず、SDK ドキュメントがオンライン ブック コレクションにも含まれていない場合、このセクションの SDK コンテンツへのリンクは機能しません。</span><span class="sxs-lookup"><span data-stu-id="dae67-121">Unless the SDK is installed on the computer and the SDK documentation is included in the Books Online collection, links to SDK content in this section will not work.</span></span> <span data-ttu-id="dae67-122">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK をインストールしたら、「[SQL Server の製品ドキュメントの追加または削除](../../index.yml)」の手順に従って、SDK ドキュメントをオンライン ブック コレクションと目次に追加できます。</span><span class="sxs-lookup"><span data-stu-id="dae67-122">After you have installed the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, you can add the SDK documentation to the Books Online collection and table of contents by following the instructions in [Add or Remove Product Documentation for SQL Server](../../index.yml).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae67-123">参照</span><span class="sxs-lookup"><span data-stu-id="dae67-123">See Also</span></span>  
 <span data-ttu-id="dae67-124">[カスタムレポートアイテムの実行時コンポーネントの作成](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="dae67-124">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="dae67-125">[カスタムレポートアイテムのデザイン時コンポーネントの作成](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="dae67-125">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="dae67-126">[カスタムレポートアイテムを配置する方法](how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="dae67-126">[How to: Deploy a Custom Report Item](how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="dae67-127">カスタム レポート アイテムのクラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="dae67-127">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
