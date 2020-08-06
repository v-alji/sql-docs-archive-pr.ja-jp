---
title: プロジェクトのインポートウィザード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81a990995d7e98c21b61f484372d31c9a1773102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641156"
---
# <a name="import-project-wizard"></a><span data-ttu-id="9c1ae-102">プロジェクトのインポート ウィザード</span><span class="sxs-lookup"><span data-stu-id="9c1ae-102">Import Project Wizard</span></span>
  <span data-ttu-id="9c1ae-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトのインポート ウィザードを使用すると、既存のプロジェクトに基づいて新しい Integration Services プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Import Project Wizard create a new Integration Services project based on an existing one.</span></span> <span data-ttu-id="9c1ae-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログに既に配置されているプロジェクトをインポートするか、またはプロジェクト配置ファイル (拡張子は .ispac) からプロジェクトをインポートします。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-104">Import projects that have already been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog or import projects from a project deployment file (.ispac extension).</span></span>  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a><span data-ttu-id="9c1ae-105">.ispac ファイルまたはカタログ内のプロジェクトに基づいてプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="9c1ae-105">To create a project based on a project in .ispac file or in catalog</span></span>  
  
1.  <span data-ttu-id="9c1ae-106">[**ファイル**]、[**新規作成**] の順にポイントし、[プロジェクト] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-106">Click **File**, point to **New**, and click Project.</span></span>  
  
2.  <span data-ttu-id="9c1ae-107">**[ビジネス インテリジェンス]** を展開し、 **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-107">Expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="9c1ae-108">中央のペインで **[Integration Services インポート ウィザード]** を選択し、ソリューションの **[名前]** 、およびプロジェクトを入力し、プロジェクトの **[フォルダー]** を指定してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-108">Select **Integration Services Import Wizard** in the middle pane, type a **name** for the solution, project, and specify the **folder** for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9c1ae-109">**Integration Services プロジェクトのインポート ウィザード**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-109">You should see the **Integration Services Import Project Wizard**.</span></span> <span data-ttu-id="9c1ae-110">このウィザードを使用すると、既存のプロジェクトに基づいて新しい Integration Services プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-110">This wizard creates a new Integration Services project based on an existing one</span></span>  
  
4.  <span data-ttu-id="9c1ae-111">**[説明]** ページで **[次へ]** をクリックすると、 **[ソースの選択]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-111">Click **Next** on the **Introduction** page to see the **Select Source** page.</span></span>  
  
5.  <span data-ttu-id="9c1ae-112">.ispac ファイルからプロジェクトをインポートするのか、カタログからプロジェクトをインポートするのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-112">Specify whether you want to import project from an .ispac file or from a catalog.</span></span>  
  
    -   <span data-ttu-id="9c1ae-113">**[プロジェクト配置ファイル]** オプションを選択した場合は、.ispac ファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-113">If you select **Project deployment file** option, specify the path to the .ispac file.</span></span>  
  
    -   <span data-ttu-id="9c1ae-114">**[Integration Services カタログ]** オプションを選択した場合は、カタログが存在するデータベース サーバー インスタンスの名前とカタログ内のプロジェクトのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-114">If you select **Integration Services Catalog** option, specify the name of database server instance on which the catalog exists, and the path to the project in the catalog.</span></span>  
  
6.  <span data-ttu-id="9c1ae-115">**[ソースの選択]** ページで **[次へ]** をクリックすると、 **[確認]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-115">Click **Next** on the **Select Source** page to see the **Review** page.</span></span> <span data-ttu-id="9c1ae-116">ページに表示される、ウィザードが実行するインポート処理に関する情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-116">Review the information displayed on the page about the import operation the wizard is going to perform.</span></span>  
  
7.  <span data-ttu-id="9c1ae-117">**[インポート]** をクリックすると、選択したプロジェクトに基づいて新しい Integration Services プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-117">Click **Import** to create a new Integration Services project based on the one you selected.</span></span>  
  
8.  <span data-ttu-id="9c1ae-118">**[結果]** ページに、ウィザードが実行したインポート処理の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-118">The **Results** page should display the results from import operation the wizard performed.</span></span> <span data-ttu-id="9c1ae-119">**[レポートの保存]** をクリックして、レポートを XML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-119">Click **Save Report** to save the report to an XML file.</span></span>  
  
9. <span data-ttu-id="9c1ae-120">**[閉じる]** をクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9c1ae-120">Click **Close** to close the wizard.</span></span>  
  
  
