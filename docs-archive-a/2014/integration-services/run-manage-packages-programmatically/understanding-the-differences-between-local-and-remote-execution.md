---
title: ローカル実行とリモート実行の相違点について | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 399584c790f4c5a5dd136121c58a5ff7743f4969
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714517"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a><span data-ttu-id="28335-102">ローカル実行とリモート実行の相違点について</span><span class="sxs-lookup"><span data-stu-id="28335-102">Understanding the Differences between Local and Remote Execution</span></span>
  <span data-ttu-id="28335-103">パッケージの開発者および管理者は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行場所に関連する制限があることを知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="28335-103">Package developers and administrators should be aware that there are restrictions related to where an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package runs.</span></span>  
  
-   <span data-ttu-id="28335-104">**パッケージは、パッケージを起動するプログラムと同じコンピューターで実行されます**。</span><span class="sxs-lookup"><span data-stu-id="28335-104">**A package runs on the same computer as the program that launches it**.</span></span> <span data-ttu-id="28335-105">プログラムが別のサーバー上にリモートに格納されたパッケージを読み込む場合であっても、そのパッケージはローカル コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="28335-105">Even when a program loads a package that is stored remotely on another server, the package runs on the local computer.</span></span>  
  
-   <span data-ttu-id="28335-106">**パッケージを開発環境の外部で実行することができるのは、そのコンピューターに Integration Services がインストールされている場合のみです**。</span><span class="sxs-lookup"><span data-stu-id="28335-106">**You can only run a package outside the development environment on a computer that has Integration Services installed**.</span></span> <span data-ttu-id="28335-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がインストールされていないクライアント コンピューターでは、パッケージを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の外部で実行することはできません。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ライセンスの条項により、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を他のコンピューターにインストールすることは許可されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="28335-107">You cannot run packages outside of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing may not permit you to install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="28335-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はサーバー コンポーネントであるため、クライアント コンピューターに再配布できません。</span><span class="sxs-lookup"><span data-stu-id="28335-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is a server component and is not redistributable to client computers.</span></span> <span data-ttu-id="28335-109">クライアント コンピューターからパッケージを実行するには、パッケージが確実にサーバー上で実行される方法で、パッケージを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28335-109">To run packages from a client computer, you need to launch them in a manner that ensures that the packages run on the server.</span></span>  
  
 <span data-ttu-id="28335-110">保存済みパッケージの読み込みと実行の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="28335-110">For more information about loading and running a saved package, see:</span></span>  
  
-   [<span data-ttu-id="28335-111">プログラムによるローカル パッケージの読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="28335-111">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [<span data-ttu-id="28335-112">プログラムによるリモート パッケージの読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="28335-112">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 <span data-ttu-id="28335-113">保存済みパッケージの実行と、その出力のカスタム プログラムへの読み込みの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="28335-113">For more information about running a package and loading its output into a custom program, see:</span></span>  
  
-   [<span data-ttu-id="28335-114">ローカル パッケージの出力の読み込み</span><span class="sxs-lookup"><span data-stu-id="28335-114">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
<span data-ttu-id="28335-115">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="28335-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="28335-116">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="28335-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="28335-117">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="28335-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="28335-118">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="28335-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28335-119">参照</span><span class="sxs-lookup"><span data-stu-id="28335-119">See Also</span></span>  
 <span data-ttu-id="28335-120">[プログラムによるローカルパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="28335-120">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 <span data-ttu-id="28335-121">[プログラムによるリモートパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="28335-121">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="28335-122">ローカル パッケージの出力の読み込み</span><span class="sxs-lookup"><span data-stu-id="28335-122">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
