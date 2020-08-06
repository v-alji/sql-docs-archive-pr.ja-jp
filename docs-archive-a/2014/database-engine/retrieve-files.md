---
title: ファイルの取得 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebced9ea69f304344893289140687cd6d511e923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644120"
---
# <a name="retrieve-files"></a><span data-ttu-id="55185-102">ファイルの取得</span><span class="sxs-lookup"><span data-stu-id="55185-102">Retrieve Files</span></span>
  <span data-ttu-id="55185-103">ソース管理の対象プロジェクトを開いた後、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、ソース管理の格納場所からプロジェクトがあるローカル ディレクトリに、プロジェクト ファイルのローカル コピーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="55185-103">After you have opened a source-controlled project, you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to retrieve local copies of project files from the source control store to the local directory in which the project resides.</span></span>  
  
 <span data-ttu-id="55185-104">統合ソース管理を使用してファイルを取得するには、以下の方法があります。</span><span class="sxs-lookup"><span data-stu-id="55185-104">You can use integrated source control to retrieve files in the following ways:</span></span>  
  
-   <span data-ttu-id="55185-105">**最新バージョンの取得 (再帰)** コマンド</span><span class="sxs-lookup"><span data-stu-id="55185-105">**Get Latest Version (Recursive)** command</span></span>  
  
     <span data-ttu-id="55185-106">選択したファイルの最新のチェックイン バージョンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="55185-106">Retrieves the latest checked in version of the selected files.</span></span> <span data-ttu-id="55185-107">ソリューションまたはプロジェクトを選択した場合は、ソリューションとプロジェクトのすべてのファイルの最新バージョンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="55185-107">If a solution or project is selected, this command retrieves the latest version of all solution and project files.</span></span>  
  
-   <span data-ttu-id="55185-108">**Get**コマンド</span><span class="sxs-lookup"><span data-stu-id="55185-108">**Get** command</span></span>  
  
     <span data-ttu-id="55185-109">[**取得**] ダイアログボックスが表示されます。このダイアログボックスでは、選択したファイルの最新バージョンを取得したり、選択したソリューションまたはプロジェクト内のファイルのサブセットを取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="55185-109">Displays the **Get** dialog box, which you can use to retrieve the latest version of a selected file, or to retrieve a subset of the files in the selected solution or project.</span></span>  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a><span data-ttu-id="55185-110">プロジェクト内のすべてのファイルの最新バージョンを取得するには</span><span class="sxs-lookup"><span data-stu-id="55185-110">To retrieve the latest version of all the files in a project</span></span>  
  
1.  <span data-ttu-id="55185-111">ソリューション エクスプローラーでプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="55185-111">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="55185-112">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**最新バージョンの取得 (再帰)**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55185-112">On the **File** menu, point to **Source Control**, and then click **Get Latest Version (Recursive)**.</span></span>  
  
 <span data-ttu-id="55185-113">プロジェクト内のファイルの最新のバージョンが、ローカル ディスクのプロジェクトが存在する場所に取得されます。</span><span class="sxs-lookup"><span data-stu-id="55185-113">The most recent versions of the files in the project are retrieved to the project location on your local disk.</span></span>  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a><span data-ttu-id="55185-114">プロジェクト内の特定のファイルだけを取得するには</span><span class="sxs-lookup"><span data-stu-id="55185-114">To retrieve only certain files in a project</span></span>  
  
1.  <span data-ttu-id="55185-115">ソリューション エクスプローラーで、取得する項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="55185-115">In Solution Explorer, select the item you want to retrieve.</span></span>  
  
2.  <span data-ttu-id="55185-116">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**取得**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55185-116">On the **File** menu, point to **Source Control**, and then click **Get**.</span></span>  
  
3.  <span data-ttu-id="55185-117">[**取得**] ダイアログボックスで、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55185-117">In the **Get** dialog box, click **OK**.</span></span> <span data-ttu-id="55185-118">または、ソリューション エクスプローラーでソリューションまたはプロジェクトを選択した場合は、取得しない項目の横にあるチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="55185-118">Alternatively, if you selected a solution or project in Solution Explorer, clear the check boxes that appear next to the items you do not want to retrieve.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55185-119">参照</span><span class="sxs-lookup"><span data-stu-id="55185-119">See Also</span></span>  
 <span data-ttu-id="55185-120">[[取得] ダイアログボックス &#40;ソース管理&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="55185-120">[Get Dialog Box &#40;Source Control&#41;](../../2014/database-engine/get-dialog-box-source-control.md) </span></span>  
 <span data-ttu-id="55185-121">[バージョン情報の設定と取得](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="55185-121">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="55185-122">[プロジェクト履歴の表示](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="55185-122">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 [<span data-ttu-id="55185-123">ファイルの状態の表示</span><span class="sxs-lookup"><span data-stu-id="55185-123">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
  
