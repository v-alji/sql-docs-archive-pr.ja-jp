---
title: 多次元データベースの名前の変更 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3974e7671aff5d1cba22b10563bbc85a129a1dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642367"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a><span data-ttu-id="fbde4-102">多次元データベース名の変更 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="fbde4-102">Rename a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="fbde4-103">データベースの名前を変更する方法は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースへの接続方法によって異なり [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fbde4-103">The manner in which you change the name of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database depends upon how you connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="fbde4-104">既存のデータベースの名前を変更するには、オンライン モードでデータベースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbde4-104">To change the name of an existing database, you must connect in online mode.</span></span> <span data-ttu-id="fbde4-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内のオブジェクトがインスタンス化されるデータベースの名前を変更するには、プロジェクト モードで接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbde4-105">To change the name of the database into which objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project will be instantiated, you must connect in project mode.</span></span>  
  
### <a name="to-change-the-database-name-in-online-mode"></a><span data-ttu-id="fbde4-106">オンライン モードでデータベース名を変更するには</span><span class="sxs-lookup"><span data-stu-id="fbde4-106">To change the database name in online mode</span></span>  
  
1.  <span data-ttu-id="fbde4-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに直接接続します。</span><span class="sxs-lookup"><span data-stu-id="fbde4-107">Using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], connect directly to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="fbde4-108">ソリューション エクスプローラーでデータベースを右クリックし、 **[データベースの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbde4-108">In Solution Explorer, right-click the database and then click **Edit Database**.</span></span>  
  
3.  <span data-ttu-id="fbde4-109">**[データベース名]** ボックスでデータベース名を変更します。</span><span class="sxs-lookup"><span data-stu-id="fbde4-109">In the **Database name** text box, change the database name.</span></span>  
  
4.  <span data-ttu-id="fbde4-110">ツール バーの **[保存]** または **[すべてを保存]** をクリックし、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** または **[すべてを保存]** をクリックします。あるいは、 **データベース デザイナー** を終了し、メッセージが表示されたら **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbde4-110">Click **Save** or **Save All** on the toolbar, click **Save Selected Items** or **Save All** on the **File** menu, or close the **Database Designer** and then click **Save** when prompted.</span></span>  
  
     <span data-ttu-id="fbde4-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのデータベース名が更新され、ソリューション エクスプローラーのデータベース オブジェクトが更新されます。</span><span class="sxs-lookup"><span data-stu-id="fbde4-111">The database name is updated in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the database object in Solution Explorer is refreshed.</span></span>  
  
### <a name="to-change-the-database-name-in-project-mode"></a><span data-ttu-id="fbde4-112">プロジェクト モードでデータベース名を変更するには</span><span class="sxs-lookup"><span data-stu-id="fbde4-112">To change the database name in project mode</span></span>  
  
1.  <span data-ttu-id="fbde4-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbde4-113">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="fbde4-114">ソリューション エクスプローラーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbde4-114">In Solution Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="fbde4-115">**[プロパティ ページ]** ダイアログ ボックスで、 **[構成プロパティ]** セクションの **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbde4-115">In the **Property Pages** dialog box, click **Deployment** in the **Configuration Properties** section.</span></span>  
  
4.  <span data-ttu-id="fbde4-116">**[データベース]** プロパティを新しいデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="fbde4-116">Change the **Database** property to the new database name.</span></span>  
  
     <span data-ttu-id="fbde4-117">次回 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトが配置されるときには、この新しい名前のデータベースにプロジェクトが配置されます。</span><span class="sxs-lookup"><span data-stu-id="fbde4-117">The next time the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is deployed, it will be deployed to this new database name.</span></span> <span data-ttu-id="fbde4-118">この名前のデータベースが既に存在する場合は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="fbde4-118">If this database already exists, it will be overwritten.</span></span>  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a><span data-ttu-id="fbde4-119">SQL Server Management Studio を使用してデータベース名を変更するには</span><span class="sxs-lookup"><span data-stu-id="fbde4-119">To change the database name using SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="fbde4-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを右クリックし、Name プロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="fbde4-120">Right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and edit the Name property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbde4-121">参照</span><span class="sxs-lookup"><span data-stu-id="fbde4-121">See Also</span></span>  
 <span data-ttu-id="fbde4-122">[Analysis Services でのサーバープロパティの構成](../server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="fbde4-122">[Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="fbde4-123">[多次元データベースのプロパティを設定 &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="fbde4-123">[Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="fbde4-124">[SSDT&#41;&#40;Analysis Services プロジェクトのプロパティを構成する](configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="fbde4-124">[Configure Analysis Services Project Properties &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md) </span></span>  
 [<span data-ttu-id="fbde4-125">Analysis Services プロジェクトの配置 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="fbde4-125">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](deploy-analysis-services-projects-ssdt.md)  
  
  
