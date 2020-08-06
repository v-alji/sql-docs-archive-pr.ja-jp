---
title: プロジェクトを作成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
author: stevestein
ms.author: sstein
ms.openlocfilehash: 269feee7225ceb09b1c2ed86419b19ec4001c1f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642484"
---
# <a name="create-a-project"></a><span data-ttu-id="c6ee4-102">プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="c6ee4-102">Create a Project</span></span>
  <span data-ttu-id="c6ee4-103">既存のソリューション内に、1 つ以上のプロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-103">You can create one or more projects within an existing solution.</span></span>  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a><span data-ttu-id="c6ee4-104">新しいプロジェクトを作成してソリューションに追加するには</span><span class="sxs-lookup"><span data-stu-id="c6ee4-104">To create a new project and add it to a solution</span></span>  
  
1.  <span data-ttu-id="c6ee4-105">ソリューション エクスプローラーで、ソリューションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-105">In Solution Explorer, select the solution.</span></span>  
  
2.  <span data-ttu-id="c6ee4-106">**[ファイル]** メニューの **[追加]** をポイントし、 **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-106">On the **File** menu, point to **Add**, and click **New Project**.</span></span>  
  
3.  <span data-ttu-id="c6ee4-107">**[新しいプロジェクト]** ダイアログ ボックスで、プロジェクトの種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-107">In the  **New Project** dialog box, click a type of project.</span></span>  
  
     <span data-ttu-id="c6ee4-108">**テンプレート**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-108">**Templates**</span></span>  
     <span data-ttu-id="c6ee4-109">**[テンプレート]** ボックスで、テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-109">In the **Templates** box, select a template.</span></span> <span data-ttu-id="c6ee4-110">**[テンプレート]** ボックスの下に、選択したプロジェクト テンプレートの簡単な説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-110">A brief description of the selected project template appears beneath the **Templates** box.</span></span>  
  
     <span data-ttu-id="c6ee4-111">**Name**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-111">**Name**</span></span>  
     <span data-ttu-id="c6ee4-112">作成するスクリプト プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-112">Enter the name of the script project you want to create.</span></span> <span data-ttu-id="c6ee4-113">**[場所]** フィールドに表示された場所に、プロジェクトと同じ名前のフォルダーも作成されます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-113">A folder with the same name as the project is also created in the location displayed in the **Location** field.</span></span> <span data-ttu-id="c6ee4-114">プロジェクトによっては、ソース ファイルなどのサポート ファイルが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] によって作成され、新しいプロジェクト フォルダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-114">For some projects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates source and other supporting files and adds them to the new project folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6ee4-115">一部の種類のプロジェクトでは、場所を指定すると名前が設定されるため、 **[名前]** テキスト ボックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-115">For some project types, the **Name** text box is unavailable because specifying the location sets the name.</span></span> <span data-ttu-id="c6ee4-116">たとえば、Web アプリケーションや Web サービスは Web サーバーに置かれ、名前はそのサーバーに指定されている仮想ディレクトリから付けられます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-116">For example, Web applications and Web services are located on a Web server and derive their name from the virtual directory specified on that server.</span></span>  
  
     <span data-ttu-id="c6ee4-117">次の文字は名前に使用できません。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-117">Names cannot contain the following characters:</span></span>  
  
    -   <span data-ttu-id="c6ee4-118">シャープ記号 (#)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-118">Pound (#)</span></span>  
  
    -   <span data-ttu-id="c6ee4-119">パーセント (%)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-119">Percent (%)</span></span>  
  
    -   <span data-ttu-id="c6ee4-120">アンパサンド (&)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-120">Ampersand (&)</span></span>  
  
    -   <span data-ttu-id="c6ee4-121">アスタリスク (\*)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-121">Asterisk (\*)</span></span>  
  
    -   <span data-ttu-id="c6ee4-122">縦棒 (|)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-122">Vertical bar (|)</span></span>  
  
    -   <span data-ttu-id="c6ee4-123">円記号 (\\)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-123">Backslash (\\)</span></span>  
  
    -   <span data-ttu-id="c6ee4-124">コロン (:)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-124">Colon (:)</span></span>  
  
    -   <span data-ttu-id="c6ee4-125">引用符 (")</span><span class="sxs-lookup"><span data-stu-id="c6ee4-125">Quotation mark (")</span></span>  
  
    -   <span data-ttu-id="c6ee4-126">より小さい (\<)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-126">Less than (\<)</span></span>  
  
    -   <span data-ttu-id="c6ee4-127">より大きい (>)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-127">Greater than (>)</span></span>  
  
    -   <span data-ttu-id="c6ee4-128">疑問符 (?)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-128">Question mark (?)</span></span>  
  
    -   <span data-ttu-id="c6ee4-129">スラッシュ (/)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-129">Forward slash (/)</span></span>  
  
    -   <span data-ttu-id="c6ee4-130">先頭または末尾の空白 (' ')</span><span class="sxs-lookup"><span data-stu-id="c6ee4-130">Leading or trailing spaces (' ')</span></span>  
  
    -   <span data-ttu-id="c6ee4-131">Microsoft Windows や MS-DOS で予約されている名前 ("nul"、"aux"、"con"、"com1"、"lpt1" など)</span><span class="sxs-lookup"><span data-stu-id="c6ee4-131">Names reserved for Microsoft Windows or MS-DOS, such as ("nul", "aux", "con", "com1", "lpt1", and so on)</span></span>  
  
     <span data-ttu-id="c6ee4-132">**Location**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-132">**Location**</span></span>  
     <span data-ttu-id="c6ee4-133">プロジェクトを作成する場所を入力するか、一覧から場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-133">Enter the location where you want to create your project, or choose one from the list.</span></span>  
  
     <span data-ttu-id="c6ee4-134">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-134">**Browse**</span></span>  
     <span data-ttu-id="c6ee4-135">**[プロジェクトの場所]** ダイアログ ボックスを表示します。ここで、プロジェクトを保存する新しいディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-135">Displays the **Project Location** dialog box, allowing you to navigate to a new directory in which to save the project.</span></span>  
  
     <span data-ttu-id="c6ee4-136">**ソリューション**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-136">**Solution**</span></span>  
     <span data-ttu-id="c6ee4-137">ソリューション エクスプローラーでソリューションを作成するには、 **[新しいソリューションを作成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-137">Select **Create new Solution** to create a solution in Solution Explorer.</span></span> <span data-ttu-id="c6ee4-138">ソリューション エクスプローラーで現在開いているソリューションに新しいプロジェクトを追加するには、 **[ソリューションに追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-138">Select **Add to Solution** to add the new project to the solution currently open in Solution Explorer.</span></span>  
  
     <span data-ttu-id="c6ee4-139">**[ソリューションのディレクトリを作成]**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-139">**Create directory for Solution**</span></span>  
     <span data-ttu-id="c6ee4-140">オンにすると、 **[ソリューション名]** テキスト ボックスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-140">Select to enable the **(Solution) Name** text box.</span></span> <span data-ttu-id="c6ee4-141">プロジェクトとソリューションに指定した名前で新しいディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-141">This option creates a new directory of the name you choose for your project and solution.</span></span>  
  
     <span data-ttu-id="c6ee4-142">**[ソリューション名]**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-142">**Solution Name**</span></span>  
     <span data-ttu-id="c6ee4-143">プロジェクトを作成する、新しいソリューションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-143">Enter the name of the new solution in which you want your project to be created.</span></span> <span data-ttu-id="c6ee4-144">既定では、 **[名前]** フィールドに入力されている名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-144">By default, this field uses the same name as entered in the **Name** field.</span></span>  
  
     <span data-ttu-id="c6ee4-145">**注** このオプションを使用するには、 **[ソリューション]** の **[新しいソリューションを作成する]** を選択し、 **[ソリューションのディレクトリを作成]** チェック ボックスをオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-145">**Note** To access this option, you must select both the **Create New Solution** in the **Solution** and the **Create directory for Solution** check boxes.</span></span> <span data-ttu-id="c6ee4-146">Web アプリケーションなど、一部のプロジェクト テンプレートでは、このオプションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-146">Some project templates do not support this option, such as Web applications.</span></span>  
  
     <span data-ttu-id="c6ee4-147">**[ソース管理に追加]**</span><span class="sxs-lookup"><span data-stu-id="c6ee4-147">**Add to Source Control**</span></span>  
     <span data-ttu-id="c6ee4-148">このチェック ボックスをオンにすると、 **[OK]** をクリックしたときにソース管理アプリケーションが開きます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-148">When this check box is selected, your source control application opens when you click **OK**.</span></span> <span data-ttu-id="c6ee4-149">ソース管理アプリケーションにより求められる情報をすべて入力します。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-149">Complete any information required by your source control application to continue.</span></span> <span data-ttu-id="c6ee4-150">このオプションを使用するには、ソース管理クライアント アプリケーションをインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-150">You must have a source control client application installed to use this option.</span></span>  
  
4.  <span data-ttu-id="c6ee4-151">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-151">Click **OK**.</span></span>  
  
 <span data-ttu-id="c6ee4-152">スクリプト プロジェクトの名前は設定できますが、フォルダー名は [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によって設定され、変更できません。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-152">You can set a name for the script project, but the folder names are established by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot be changed.</span></span> <span data-ttu-id="c6ee4-153">**[新しいプロジェクトの追加]** ダイアログ ボックスを使用すると、共通のフォルダーのセットを示すドライブとパスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-153">You can configure the drive and path specification for the common set of folders by using the **Add New Project** dialog box.</span></span> <span data-ttu-id="c6ee4-154">**ソリューション エクスプローラー**でソリューション アイコンを右クリックし、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-154">Right-click the solution icon in **Solution Explorer**, and then click **Add**.</span></span> <span data-ttu-id="c6ee4-155">スクリプト プロジェクト フォルダーの既定の場所は、C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\です。</span><span class="sxs-lookup"><span data-stu-id="c6ee4-155">The default location for script project folders is: C:\Documents and Settings\\*username*\My Documents\SQL Server Management Studio\Projects\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ee4-156">参照</span><span class="sxs-lookup"><span data-stu-id="c6ee4-156">See Also</span></span>  
 <span data-ttu-id="c6ee4-157">[ソリューション エクスプローラー](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee4-157">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="c6ee4-158">[既存のプロジェクトをソリューションに追加する](add-an-existing-project-to-a-solution.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee4-158">[Add an Existing Project to a Solution](add-an-existing-project-to-a-solution.md) </span></span>  
 <span data-ttu-id="c6ee4-159">[プロジェクトに新しい項目を追加する](add-new-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee4-159">[Add New Items to a Project](add-new-items-to-a-project.md) </span></span>  
 <span data-ttu-id="c6ee4-160">[既存の項目をプロジェクトに追加する](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee4-160">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 <span data-ttu-id="c6ee4-161">[プロジェクトの既定の場所の変更](change-the-default-location-for-projects.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee4-161">[Change the Default Location for Projects](change-the-default-location-for-projects.md) </span></span>  
 <span data-ttu-id="c6ee4-162">[項目またはプロジェクトを削除または削除する](remove-or-delete-an-item-or-project.md) </span><span class="sxs-lookup"><span data-stu-id="c6ee4-162">[Remove or Delete an Item or Project](remove-or-delete-an-item-or-project.md) </span></span>  
 [<span data-ttu-id="c6ee4-163">ソリューションを削除する</span><span class="sxs-lookup"><span data-stu-id="c6ee4-163">Delete a Solution</span></span>](delete-a-solution.md)  
  
  
