---
title: Integration Services のプロジェクトのインポート |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a98219f3a04d11e086957d64a62e7c64cd51418
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632589"
---
# <a name="import-an-integration-services-project"></a><span data-ttu-id="74006-102">Integration Services プロジェクトのインポート</span><span class="sxs-lookup"><span data-stu-id="74006-102">Import an Integration Services Project</span></span>
  <span data-ttu-id="74006-103">既存の配置ファイル (.ispac) または Integration Services カタログに配置されたプロジェクトからプロジェクトを作成するには、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の**プロジェクトのインポート ウィザード**を使用します。</span><span class="sxs-lookup"><span data-stu-id="74006-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]**Import Project Wizard** to create a project from an existing deployment file (.ispac) or from a project deployed to Integration services catalog.</span></span> <span data-ttu-id="74006-104">この機能は、プロジェクトの元のコピーがない状態で、.ispac ファイルまたは SSISDB カタログからプロジェクトを作成する場合に、特に便利です。</span><span class="sxs-lookup"><span data-stu-id="74006-104">This feature is especially useful when you do not have the original copy of the project but you want to create one from an .ispac file or SSISDB catalog.</span></span>  
  
### <a name="to-import-a-project"></a><span data-ttu-id="74006-105">プロジェクトをインポートするには</span><span class="sxs-lookup"><span data-stu-id="74006-105">To Import a Project</span></span>  
  
1.  <span data-ttu-id="74006-106">で、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [ **New**  >  **ファイル**] メニューの [新しい**プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74006-106">In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New** > **Project** on the **File** menu.</span></span>  
  
2.  <span data-ttu-id="74006-107">**[新しいプロジェクト]** ウィンドウの **[インストールされているテンプレート]** 領域で **[ビジネス インテリジェンス]** を展開し、 **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74006-107">In the **Installed Templates** area of the **New Project** window, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="74006-108">プロジェクトの種類の一覧から **Integration Services プロジェクトのインポート ウィザード** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74006-108">Select **Integration Services Import Project Wizard** from the project types list.</span></span>  
  
4.  <span data-ttu-id="74006-109">作成する新しいプロジェクトの名前を、 **[名前]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="74006-109">Type a name for the new project to be created in the **Name** text box.</span></span>  
  
5.  <span data-ttu-id="74006-110">プロジェクトのパスまたは場所を **[場所]** ボックスに入力するか、または **[参照]** をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="74006-110">Type the path or location for the project in the **Location** text box, or click **Browse** to select one.</span></span>  
  
6.  <span data-ttu-id="74006-111">**[ソリューション名]** ボックスにソリューションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="74006-111">Type a name for the solution in the **Solution name** text box.</span></span>  
  
7.  <span data-ttu-id="74006-112">**[OK]** をクリックして **[Integration Services プロジェクトのインポート ウィザード]** ダイアログ ボックスを起動します。</span><span class="sxs-lookup"><span data-stu-id="74006-112">Click **OK** to launch the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
8.  <span data-ttu-id="74006-113">**[次へ]** をクリックして、 **[ソースの選択]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="74006-113">Click **Next** to switch to the **Select Source** page.</span></span>  
  
9. <span data-ttu-id="74006-114">**.ispac** ファイルからインポートする場合は、ファイル名を含むパスを **[パス]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="74006-114">If you are importing from an **.ispac** file, type the path including file name in the **Path** text box.</span></span> <span data-ttu-id="74006-115">**[参照]** をクリックして、ソリューションを格納するフォルダーに移動し、 **[ファイル名]** ボックスにファイル名を入力して、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74006-115">Click **Browse** to navigate to the folder where you want the solution to be stored and type file name in the **File name** text box, and click **Open**.</span></span>  
  
     <span data-ttu-id="74006-116">**Integration Services カタログ**からインポートする場合は、データベース インスタンス名を **[サーバー名]** ボックスに入力するか、または **[参照]** をクリックしてカタログを含むデータベース インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="74006-116">If you are importing from an **Integration Services Catalog**, type the database instance name in the **Server name** text box or click **Browse** and select the database instance that contains the catalog.</span></span>  
  
     <span data-ttu-id="74006-117">**[パス]** ボックスの横にある **[参照]** をクリックし、カタログのフォルダーを展開して、インポートするプロジェクトを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74006-117">Click **Browse** next to **Path** text box, expand folder in the catalog, select the project you want to import, and click **OK**.</span></span>  
  
     <span data-ttu-id="74006-118">**[次へ]** をクリックして **[確認]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="74006-118">Click **Next** to switch to the **Review** page.</span></span>  
  
10. <span data-ttu-id="74006-119">情報を確認し、 **[インポート]** をクリックして、選択した既存のプロジェクトに基づくプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="74006-119">Review the information and click **Import** to create a project based on the existing project you selected.</span></span>  
  
11. <span data-ttu-id="74006-120">省略可能: **[レポートの保存]** をクリックして、結果をファイルに保存します</span><span class="sxs-lookup"><span data-stu-id="74006-120">Optional: click **Save Report** to save the results to a file</span></span>  
  
12. <span data-ttu-id="74006-121">**[閉じる]** をクリックして **[Integration Services プロジェクトのインポート ウィザード]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="74006-121">Click **Close** to close the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
  
