---
title: '手順 2: 配置プロジェクトの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebfce8796f98628c2832c5ab7f4be665c7915d10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641103"
---
# <a name="step-2-creating-the-deployment-project"></a><span data-ttu-id="00196-102">手順 2:配置プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="00196-102">Step 2: Creating the Deployment Project</span></span>
  <span data-ttu-id="00196-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]では、配置可能な単位は [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="00196-103">In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the deployable unit is an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="00196-104">パッケージを配置するには、まず新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成し、すべてのパッケージと、これらのパッケージと共に配置する補助ファイルをそのプロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00196-104">Before you can deploy packages, you must create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and add all the packages and any ancillary files that you want to deploy with the packages to that project.</span></span>  
  
### <a name="to-create-the-integration-services-project"></a><span data-ttu-id="00196-105">Integration Services プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="00196-105">To create the Integration Services project</span></span>  
  
1.  <span data-ttu-id="00196-106">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントしてから、[SQL Server] の **[SQL Server Data Tools]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00196-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL ServerSQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="00196-107">新しい **プロジェクトを作成するため、** [ファイル] **メニューの**[新規作成] **をポイントし、** [プロジェクト] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00196-107">On the **File** menu, point to **New**, and then click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="00196-108">**[新しいプロジェクト]** ダイアログ ボックスの **[テンプレート]** ペインで、 **[Integration Services プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00196-108">In the **New Project** dialog box, select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="00196-109">**[名前]** ボックスに表示されている既定の名前を「 **Deployment Tutorial**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="00196-109">In the **Name** box, change the default name to **Deployment Tutorial**.</span></span> <span data-ttu-id="00196-110">必要に応じて、 **[ソリューションのディレクトリを作成]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="00196-110">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="00196-111">既定の場所をそのまま使用するか、 **[参照]** をクリックして使用するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="00196-111">Accept the default location, or click **Browse** to locate the folder you want to use.</span></span>  
  
6.  <span data-ttu-id="00196-112">**[プロジェクトの場所]** ダイアログ ボックスで、目的のフォルダーをクリックして **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00196-112">In the **Project Location** dialog box, click the folder, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="00196-113">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00196-113">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="00196-114">既定では、Package.dtsx という名前の空のパッケージが作成され、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="00196-114">By default, an empty package, named Package.dtsx, is created and added to your project.</span></span> <span data-ttu-id="00196-115">ただし、このパッケージはここでは使用しません。代わりに既存のパッケージをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="00196-115">However, you will not use this package; instead, you will add existing packages to the project.</span></span> <span data-ttu-id="00196-116">プロジェクト内のすべてのパッケージを配置に含めるので、Package.dtsx は削除してください。</span><span class="sxs-lookup"><span data-stu-id="00196-116">Because all the packages in a project will be included in the deployment, you should delete Package.dtsx.</span></span> <span data-ttu-id="00196-117">削除するには、Package.dtsx を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00196-117">To delete it, right-click it, and then click **Delete**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="00196-118">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="00196-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="00196-119">手順 3: パッケージとその他のファイルの追加</span><span class="sxs-lookup"><span data-stu-id="00196-119">Step 3: Adding Packages and Other Files</span></span>](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
<span data-ttu-id="00196-120">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="00196-120">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="00196-121">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="00196-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="00196-122">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="00196-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="00196-123">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="00196-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00196-124">参照</span><span class="sxs-lookup"><span data-stu-id="00196-124">See Also</span></span>  
 [<span data-ttu-id="00196-125">Integration Services (SSIS) プロジェクト</span><span class="sxs-lookup"><span data-stu-id="00196-125">Integration Services &#40;SSIS&#41; Projects</span></span>](integration-services-ssis-projects-and-solutions.md)  
  
  
