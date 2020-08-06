---
title: ソース管理にソリューションを追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding solutions
- solutions [SQL Server Management Studio], adding
ms.assetid: b9e36569-616d-4e47-9140-0978a9bfe923
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1c72949fd8257332a36af52ab287ed326eed5274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714577"
---
# <a name="add-solutions-to-source-control"></a><span data-ttu-id="94547-102">ソース管理へのソリューションの追加</span><span class="sxs-lookup"><span data-stu-id="94547-102">Add Solutions to Source Control</span></span>
  <span data-ttu-id="94547-103">通常、ソース管理にソリューションを追加する場合は、ソリューション全体、およびソリューションに含まれているすべてのプロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="94547-103">When you add a solution to source control, you usually want to add the entire solution and all the projects it contains.</span></span> <span data-ttu-id="94547-104">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、ソース管理にソリューションを追加できます。</span><span class="sxs-lookup"><span data-stu-id="94547-104">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to add a solution to source control.</span></span>  
  
 <span data-ttu-id="94547-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] プロジェクトは、全体がローカル ディスクに存在します。</span><span class="sxs-lookup"><span data-stu-id="94547-105">A [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] project resides completely on your local disk.</span></span> <span data-ttu-id="94547-106">プロジェクトの編集、保存、およびビルドはローカルで行います。</span><span class="sxs-lookup"><span data-stu-id="94547-106">You edit, save, and build projects locally.</span></span> <span data-ttu-id="94547-107">ソース管理にプロジェクトを追加した後、 **[チェックアウト] コマンドを**使用して、プロジェクトのファイルをソース管理からチェックアウトできます。</span><span class="sxs-lookup"><span data-stu-id="94547-107">After adding the project to source control, you can use the **Check Out** command to check the project's files out of source control.</span></span>  
  
### <a name="to-add-a-solution-to-source-control"></a><span data-ttu-id="94547-108">ソース管理にソリューションを追加するには</span><span class="sxs-lookup"><span data-stu-id="94547-108">To add a solution to source control</span></span>  
  
1.  <span data-ttu-id="94547-109">ソリューション エクスプローラーで、追加するソリューションを選択します。</span><span class="sxs-lookup"><span data-stu-id="94547-109">In Solution Explorer, select the solution you want to add.</span></span>  
  
2.  <span data-ttu-id="94547-110">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**ソリューションをソース管理に追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94547-110">On the **File** menu, point to **Source Control**, and then click **Add Solution to Source Control**.</span></span>  
  
3.  <span data-ttu-id="94547-111">ログオンを指示するメッセージが表示されたら、ソース管理プロバイダーにログオンします。</span><span class="sxs-lookup"><span data-stu-id="94547-111">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="94547-112">[ **Visual SourceSafe に追加**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="94547-112">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="94547-113">プロジェクトの名前が [**プロジェクト**] ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="94547-113">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="94547-114">[**フォルダー** ] ボックスの一覧で、プロジェクトを配置するフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="94547-114">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="94547-115">または、[**作成**] をクリックして、[**プロジェクト**] ボックスに表示された名前のフォルダーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="94547-115">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94547-116">参照</span><span class="sxs-lookup"><span data-stu-id="94547-116">See Also</span></span>  
 <span data-ttu-id="94547-117">[ソリューションとプロジェクトをソース管理に追加する](../../2014/database-engine/add-solutions-and-projects-to-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="94547-117">[Add Solutions and Projects to Source Control](../../2014/database-engine/add-solutions-and-projects-to-source-control.md) </span></span>  
 [<span data-ttu-id="94547-118">ソース管理へのプロジェクトの追加</span><span class="sxs-lookup"><span data-stu-id="94547-118">Add Projects to Source Control</span></span>](../../2014/database-engine/add-projects-to-source-control.md)  
  
  
