---
title: 既存の項目をプロジェクトに追加する| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cffa683bfa2a2c81c059d887231531f03d5c892b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645292"
---
# <a name="add-existing-items-to-a-project"></a><span data-ttu-id="a8a9d-102">既存の項目をプロジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="a8a9d-102">Add Existing Items to a Project</span></span>
  <span data-ttu-id="a8a9d-103">プロジェクトに新しい項目を追加して、アプリケーションの機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="a8a9d-104">既存の項目は、クエリやその他のファイルです。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-104">An existing item can be a query or a miscellaneous file.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a8a9d-105">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトおよび Analysis Services スクリプト プロジェクトという 2 種類のプロジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="a8a9d-106">プロジェクトの種類によって、プロジェクトに追加できるクエリ ファイルが決まります。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-106">The project type determines the query files that you can add to the project.</span></span> <span data-ttu-id="a8a9d-107">たとえば、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ (拡張子が .sql のファイル) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトには追加できますが、Analysis Services スクリプト プロジェクトには追加できません。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span> <span data-ttu-id="a8a9d-108">追加のファイル拡張子をプロジェクトの種類に関連付ける方法については、「[ファイル拡張子をコードエディターに関連付ける](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-108">To associate additional file extensions to a project type, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a><span data-ttu-id="a8a9d-109">既存のクエリまたはその他のファイルをプロジェクトに追加するには</span><span class="sxs-lookup"><span data-stu-id="a8a9d-109">To add an existing query or a miscellaneous file to a project</span></span>  
  
1.  <span data-ttu-id="a8a9d-110">ソリューション エクスプローラーで、対象のプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-110">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="a8a9d-111">**[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-111">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
     <span data-ttu-id="a8a9d-112">**Look in**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-112">**Look in**</span></span>  
     <span data-ttu-id="a8a9d-113">プロジェクトに追加するファイルまたはフォルダーをこの一覧から指定します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-113">Locate the files or folders to add to your project from this list.</span></span> <span data-ttu-id="a8a9d-114">XML Web サービスや ASP.NET Web アプリケーションの場合、ファイルは Web サーバーに置かれています。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-114">For XML Web services and ASP.NET Web applications, the files are located on the Web server.</span></span>  
  
     <span data-ttu-id="a8a9d-115">**[デスクトップ]**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-115">**Desktop**</span></span>  
     <span data-ttu-id="a8a9d-116">デスクトップに存在するファイルおよびフォルダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-116">Displays the files and folders located on the desktop.</span></span>  
  
     <span data-ttu-id="a8a9d-117">**[マイ プロジェクト]**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-117">**My Projects**</span></span>  
     <span data-ttu-id="a8a9d-118">既定の **[マイ プロジェクト]** の場所にあるファイルとフォルダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-118">Displays the files and folders at the default **My Projects** location.</span></span>  
  
     <span data-ttu-id="a8a9d-119">**[マイ コンピューター]**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-119">**My Computer**</span></span>  
     <span data-ttu-id="a8a9d-120">**[マイ コンピューター]** フォルダーの内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-120">Displays the contents of your **My Computer** folder.</span></span>  
  
     <span data-ttu-id="a8a9d-121">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-121">**File name**</span></span>  
     <span data-ttu-id="a8a9d-122">このオプションを使用すると、表示するファイルとフォルダーをフィルター選択できます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-122">Use this option to filter the files and folders that are displayed.</span></span> <span data-ttu-id="a8a9d-123">フィルター選択するファイル名またはファイル名の一部を入力します。ワイルドカードとしてアスタリスク (`*`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-123">Enter the full or partial file name on which to filter; use an asterisk (`*`) as a wildcard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a8a9d-124">Web およびネットワークの場所に移動するには、 **[ファイル名]** ボックスに URL またはネットワーク パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-124">Navigate to Web and network locations by entering the URL or network path in the **File name** box.</span></span> <span data-ttu-id="a8a9d-125">たとえば、「 **http://mywebsite** 」と入力した場合は、"mywebsite" という Web の場所で利用可能なファイルが表示され、「 **\\\myserver\myshare**」と入力した場合は、"myserver" の "myshare" という場所で利用可能なファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-125">For example, **http://mywebsite** displays the files available at the mywebsite Web location, and **\\\myserver\myshare** displays the files available at the myshare location on myserver.</span></span>  
  
     <span data-ttu-id="a8a9d-126">**ファイルの種類**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-126">**Files of type**</span></span>  
     <span data-ttu-id="a8a9d-127">ファイルの拡張子に基づいてファイルをフィルター選択するときに、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-127">Use this option to filter files based on file extension.</span></span> <span data-ttu-id="a8a9d-128">各製品について、最も一般的なファイルの種類を対象とする既定のフィルターが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-128">Each product lists default filters of the most common file types.</span></span>  
  
     <span data-ttu-id="a8a9d-129">**追加**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-129">**Add**</span></span>  
     <span data-ttu-id="a8a9d-130">このドロップダウン ボタンを使用すると、プロジェクトに項目を追加し、その項目を既定のエディターで開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-130">Use this drop-down button to add the item to the project and open the item in its default editor.</span></span>  
  
    -   <span data-ttu-id="a8a9d-131">**追加**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-131">**Add**</span></span>  
  
         <span data-ttu-id="a8a9d-132">既存の項目をディスク上のプロジェクト フォルダーにコピーし、その項目をソリューション エクスプローラーで選択したプロジェクトの下に追加します。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-132">Copies the existing item to your project folder on disk and adds the item under the selected project in Solution Explorer.</span></span> <span data-ttu-id="a8a9d-133">項目に加えられた変更は、元の場所の項目には反映されません。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-133">Any changes made to the item are not reflected in the item at the original location.</span></span> <span data-ttu-id="a8a9d-134">これは、この種類のファイルの既定のエディターです。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-134">This is the default editor for the file type.</span></span>  
  
    -   <span data-ttu-id="a8a9d-135">**[リンクとして追加]**</span><span class="sxs-lookup"><span data-stu-id="a8a9d-135">**Add As Link**</span></span>  
  
         <span data-ttu-id="a8a9d-136">選択したファイルをプロジェクトに追加し、そのファイルを、ファイルの種類に対応した既定のエディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-136">Adds the selected file to the project and opens it with the default editor for the file type.</span></span> <span data-ttu-id="a8a9d-137">このオプションでは、最初に選択したファイルが開きます。ファイルがプロジェクト フォルダーにコピーされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-137">This option opens the originally selected file and does not copy the file to the project folder.</span></span>  
  
3.  <span data-ttu-id="a8a9d-138">クエリ ファイルを追加する場合は、接続ダイアログが表示され、クエリの接続を指定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-138">If you are adding query files, the connection dialog will prompt you to specify a connection for the query.</span></span> <span data-ttu-id="a8a9d-139">クエリに接続を関連付けない場合には、接続ダイアログで **[キャンセル]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-139">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the query.</span></span>  
  
4.  <span data-ttu-id="a8a9d-140">ファイルがプロジェクトの **[クエリ]** または **[その他]** フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a8a9d-140">The file will be added to the **Queries** or **Miscellaneous Files** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a9d-141">参照</span><span class="sxs-lookup"><span data-stu-id="a8a9d-141">See Also</span></span>  
 <span data-ttu-id="a8a9d-142">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="a8a9d-142">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="a8a9d-143">[プロジェクトに新しい項目を追加する](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="a8a9d-143">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="a8a9d-144">アイテムやプロジェクトのクリアまたは削除</span><span class="sxs-lookup"><span data-stu-id="a8a9d-144">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
