---
title: '[プロジェクトのバージョン] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 998dd194c2a056121fd6f7a404e75c7080b85aa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736679"
---
# <a name="project-versions-dialog-box"></a><span data-ttu-id="a2ace-102">[プロジェクトのバージョン] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="a2ace-102">Project Versions Dialog Box</span></span>
  <span data-ttu-id="a2ace-103">**[プロジェクトのバージョン]** ダイアログ ボックスを使用して、プロジェクトのバージョンの表示および以前のバージョンへの復元を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a2ace-103">Use the **Project Versions** dialog box to view versions of a project and to restore a previous version.</span></span>  
  
 <span data-ttu-id="a2ace-104">また、[catalog.object_versions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) ビューで以前のバージョンを表示し、[catalog.restore_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) ストアド プロシージャを使用して以前のバージョンを復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2ace-104">You can also view previous versions in the [catalog.object_versions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) view, and use the [catalog.restore_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) stored procedure to restore previous versions.</span></span>  
  
 <span data-ttu-id="a2ace-105">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="a2ace-105">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="a2ace-106">[[プロジェクトのバージョン] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="a2ace-106">[Open the Project Versions dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="a2ace-107">プロジェクトのバージョンの復元</span><span class="sxs-lookup"><span data-stu-id="a2ace-107">Restore a Project Version</span></span>](#restore)  
  
##  <a name="open-the-project-versions-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="a2ace-108">[プロジェクトのバージョン] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="a2ace-108">Open the Project Versions dialog box</span></span>  
  
1.  <span data-ttu-id="a2ace-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a2ace-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="a2ace-110">つまり、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] データベースをホストする [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="a2ace-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="a2ace-111">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2ace-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="a2ace-112">**[Integration Services カタログ]** ノードを展開して、 **[SSISDB]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2ace-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="a2ace-113">**[SSISDB]** ノードには 1 つ以上のフォルダーが含まれており、各フォルダーには 1 つ以上のプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a2ace-113">The **SSISDB** node contains one or more folders that each contain one or more projects.</span></span> <span data-ttu-id="a2ace-114">対象とするプロジェクトを含むフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2ace-114">Expand the folder that contains the project you are interested in.</span></span>  
  
5.  <span data-ttu-id="a2ace-115">このプロジェクトを右クリックし、 **[バージョン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2ace-115">Right-click the project, and then click **Versions**.</span></span>  
  
 <span data-ttu-id="a2ace-116">**[プロジェクトのバージョン]** ダイアログ ボックスの **[バージョン]** テーブルには、サーバー上に配置されたプロジェクトのバージョン、バージョンが配置された日時、バージョンが復元された日時 (復元された場合)、バージョンの説明、およびバージョンの識別子の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2ace-116">In the **Project Versions** dialog box, the **Versions** table displays the list of versions of the project that have been deployed on the server, with the date and time the version was deployed, the date and time the version was restored (if it was restored), the version description, and a version identifier.</span></span> <span data-ttu-id="a2ace-117">このテーブルでは、現在アクティブなバージョンの **[現在]** 列にチェック マークが付きます。</span><span class="sxs-lookup"><span data-stu-id="a2ace-117">The currently active version is indicated with a check mark in the **Current** column of the table.</span></span>  
  
##  <a name="restore-a-project-version"></a><a name="restore"></a> <span data-ttu-id="a2ace-118">プロジェクトのバージョンの復元</span><span class="sxs-lookup"><span data-stu-id="a2ace-118">Restore a Project Version</span></span>  
 <span data-ttu-id="a2ace-119">以前のバージョンのプロジェクトを復元するには、 **[バージョン]** テーブルでバージョンを選択し、 **[選択したバージョンに復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2ace-119">To restore a previous version of a project, select the version in the **Versions** table, and then click **Restore to Selected Version**.</span></span> <span data-ttu-id="a2ace-120">プロジェクトが選択したバージョンに復元され、 **[バージョン]** テーブルでは、そのバージョンの **[現在]** 列にチェック マークが付きます。</span><span class="sxs-lookup"><span data-stu-id="a2ace-120">The project is restored to the selected version and that version is indicated with a check mark in the **Current** column of the **Versions** table.</span></span>  
  
  
