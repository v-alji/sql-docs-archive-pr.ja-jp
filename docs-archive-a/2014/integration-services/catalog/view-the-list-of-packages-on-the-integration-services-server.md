---
title: Integration Services サーバー上のパッケージの一覧を表示する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47b30f9ea0b2abae73f9260b873b7c8436c423eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710994"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a><span data-ttu-id="7e826-102">Integration Services サーバー上のパッケージの一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="7e826-102">View the List of Packages on the Integration Services Server</span></span>
  <span data-ttu-id="7e826-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに格納されているパッケージの一覧は、次の 2 つの方法のいずれかで表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e826-103">You can view the list of packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server in one of two ways.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="7e826-104">アクセス</span><span class="sxs-lookup"><span data-stu-id="7e826-104">access</span></span>  
 <span data-ttu-id="7e826-105">サーバーに格納されているパッケージの一覧を表示するには、ビュー [catalog.packages (SSISDB データベース)](/sql/integration-services/system-views/catalog-packages-ssisdb-database) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="7e826-105">To view the list of packages that are stored on the server, query the view, [catalog.packages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database).</span></span>  
  
 <span data-ttu-id="7e826-106">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e826-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="7e826-107">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーを使用して、サーバーに格納されているパッケージを表示するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e826-107">To view packages stored on the server by using Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], follow the procedure below.</span></span>  
  
### <a name="to-view-packages-using-ssmanstudiofull"></a><span data-ttu-id="7e826-108">パッケージを表示するには - [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e826-108">To view packages using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>  
  
1.  <span data-ttu-id="7e826-109">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="7e826-109">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="7e826-110">つまり、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] データベースをホストする [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7e826-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="7e826-111">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7e826-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="7e826-112">**[Integration Services カタログ]** ノードを展開して、 **[SSISDB]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7e826-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="7e826-113">**[SSISDB]** ノードを展開して、1 つ以上のフォルダーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e826-113">Expand the **SSISDB** node to display a list of one or more folders.</span></span> <span data-ttu-id="7e826-114">各フォルダーの **[プロジェクト]** フォルダーには、1 つ以上のプロジェクトが格納されています。各プロジェクトの **[パッケージ]** フォルダーには、1 つ以上のパッケージが格納されています。</span><span class="sxs-lookup"><span data-stu-id="7e826-114">Each folder contains one or more projects in the **Projects** folder, and each project contains one more packages in the **Packages** folder.</span></span>  
  
  
