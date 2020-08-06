---
title: Analysis Services データベースを変更または削除する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6182e91bd95754fe639e8a48548b5cab1835bdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740554"
---
# <a name="modify-or-delete-an-analysis-services-database"></a><span data-ttu-id="38ec3-102">Analysis Services データベースの変更または削除</span><span class="sxs-lookup"><span data-stu-id="38ec3-102">Modify or Delete an Analysis Services Database</span></span>
  <span data-ttu-id="38ec3-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの名前と説明は、配置前には [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、配置後には [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で変更できます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-103">You can change the name and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database before deployment in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and after deployment in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="38ec3-104">また、環境に応じて [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの追加の設定を調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-104">You can also adjust additional settings on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, depending on the environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38ec3-105">オンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、データベースのプロパティを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="38ec3-105">You cannot change database properties using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span>  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a><span data-ttu-id="38ec3-106">SQL Server Management Studio を使用したデータベースの変更</span><span class="sxs-lookup"><span data-stu-id="38ec3-106">Modifying Databases Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="38ec3-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの配置後は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベース内のデータ ソースに接続するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用される権限借用モードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-107">Once an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change the impersonation mode used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when connecting to data sources contained by the database.</span></span> <span data-ttu-id="38ec3-108">権限借用モードを使用すると、処理、参照、またはドリルスルーの目的でデータ ソースに接続するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用されるセキュリティ コンテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-108">The impersonation mode allows you to specify the security context used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when attempting to connect to a data source for processing, browsing, or drillthrough purposes.</span></span>  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a><span data-ttu-id="38ec3-109">SQL Server データ ツールを使用したデータベースの変更</span><span class="sxs-lookup"><span data-stu-id="38ec3-109">Modifying Databases Using SQL Server Data Tools</span></span>  
 <span data-ttu-id="38ec3-110">プロジェクト モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用すると、データベースの定義に使用する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのキャプションや説明の翻訳を変更できます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-110">You can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in project mode to modify the translations for the caption and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project used to define a database.</span></span> <span data-ttu-id="38ec3-111">データベースでの翻訳の使用の詳細につい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ては、「 [Analysis Services multiidimensional のグローバリゼーションのシナリオ](../globalization-scenarios-for-analysis-services-multiidimensional.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38ec3-111">For more information about using translations in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, see [Globalization scenarios for Analysis Services Multiidimensional](../globalization-scenarios-for-analysis-services-multiidimensional.md).</span></span>  
  
 <span data-ttu-id="38ec3-112">データベースに含まれているディメンションの勘定科目属性で使用される勘定科目の種類に関連付けられている別名や集計関数を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-112">You can also set the aliases and aggregation functions associated with account types used by account attributes in dimensions contained by the database.</span></span> <span data-ttu-id="38ec3-113">別名を使用すると、勘定科目一覧表の勘定科目の種類に対して組織が使用するビジネス固有の用語を選択できます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-113">Aliases allow you to select the business-specific terminology used by your organization for the account types in a chart of accounts.</span></span> <span data-ttu-id="38ec3-114">勘定科目属性のメンバーは、勘定科目の種類を使用して、各メンバーのメジャーを集計する方法を示します。集計は、データベース内の各勘定科目の種類に指定されている集計関数を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="38ec3-114">The account types are used by members of an account attribute to indicate how to aggregate measures over each member by using the aggregation functions specified for each account type contained in the database.</span></span> <span data-ttu-id="38ec3-115">勘定科目属性の詳細については、「 [属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="38ec3-115">For more information about account attributes, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="deleting-databases"></a><span data-ttu-id="38ec3-116">消去、データベース</span><span class="sxs-lookup"><span data-stu-id="38ec3-116">Deleting Databases</span></span>  
 <span data-ttu-id="38ec3-117">既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを削除すると、データベースとすべてのキューブ、ディメンション、およびデータベース内のマイニング モデルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-117">Deleting an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database deletes the database and all cubes, dimensions, and mining models in the database.</span></span> <span data-ttu-id="38ec3-118">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、既存の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースのみを削除できます。</span><span class="sxs-lookup"><span data-stu-id="38ec3-118">You can only delete an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-an-analysis-services-database"></a><span data-ttu-id="38ec3-119">Analysis Services データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="38ec3-119">To delete an Analysis Services database</span></span>  
  
1.  <span data-ttu-id="38ec3-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="38ec3-120">Connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="38ec3-121">**オブジェクト エクスプローラー**で、接続した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのノードを展開し、削除するオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="38ec3-121">In **Object Explorer**, expand the node for the connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and ensure that the object to be deleted is visible.</span></span>  
  
3.  <span data-ttu-id="38ec3-122">削除するオブジェクトを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38ec3-122">Right-click the object to be deleted and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="38ec3-123">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38ec3-123">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ec3-124">参照</span><span class="sxs-lookup"><span data-stu-id="38ec3-124">See Also</span></span>  
 [<span data-ttu-id="38ec3-125">Analysis Services データベースのドキュメントとスクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="38ec3-125">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
  
