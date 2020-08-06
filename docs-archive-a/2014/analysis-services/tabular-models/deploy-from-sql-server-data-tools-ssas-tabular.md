---
title: SQL Server Data Tools からのデプロイ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8bc8008e7c79e1652b54b21e6afb116301d1700b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641882"
---
# <a name="deploy-from-sql-server-data-tools-ssas-tabular"></a><span data-ttu-id="461f9-102">SQL Server データ ツールからの配置 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="461f9-102">Deploy From SQL Server Data Tools (SSAS Tabular)</span></span>
  <span data-ttu-id="461f9-103">このトピックのタスクは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の Deploy コマンドを使用してテーブル モデル ソリューションを配置するために使用します。</span><span class="sxs-lookup"><span data-stu-id="461f9-103">Use the tasks in this topic to deploy a tabular model solution by using the Deploy command in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="461f9-104">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="461f9-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="461f9-105">配置オプションと配置サーバーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="461f9-105">Configure Deployment Options and Deployment Server Properties</span></span>](#bkmk_deploy)  
  
-   [<span data-ttu-id="461f9-106">テーブル モデル ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="461f9-106">Deploy a Tabular Model Solution</span></span>](#bkmk_deploy_proc)  
  
-   [<span data-ttu-id="461f9-107">デプロイステータス</span><span class="sxs-lookup"><span data-stu-id="461f9-107">Deploy Status</span></span>](#bkmk_deploy_status)  
  
##  <a name="configure-deployment-options-and-deployment-server-properties"></a><a name="bkmk_deploy"></a><span data-ttu-id="461f9-108">配置オプションと配置サーバーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="461f9-108">Configure Deployment Options and Deployment Server Properties</span></span>  
 <span data-ttu-id="461f9-109">テーブル モデル ソリューションを配置する前に、まず、配置オプションと配置サーバーのプロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="461f9-109">Before you deploy your tabular model solution, you must first specify the Deployment Options and Deployment Server properties.</span></span> <span data-ttu-id="461f9-110">配置のプロパティおよび設定の詳細については、「 [テーブル モデル ソリューションの配置 (SSAS テーブル)](tabular-model-solution-deployment-ssas-tabular.md)の Deploy コマンドを使用してテーブル モデル ソリューションを配置するために使用します。</span><span class="sxs-lookup"><span data-stu-id="461f9-110">For more information about deployment properties and settings, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
#### <a name="to-configure-deployment-options-and-deployment-server-properties"></a><span data-ttu-id="461f9-111">配置オプションおよび配置サーバー プロパティを構成するには</span><span class="sxs-lookup"><span data-stu-id="461f9-111">To configure Deployment Options and Deployment Server properties</span></span>  
  
1.  <span data-ttu-id="461f9-112">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **ソリューション エクスプローラー**で、プロジェクト名を右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="461f9-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="461f9-113">[ \*\* \<project name> プロパティ**] ダイアログボックスの [**配置オプション\*\*] で、既定の設定と異なる場合はプロパティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="461f9-113">In the **\<project name> Properties** dialog, in **Deployment Options**, specify property settings if different from the default settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="461f9-114">キャッシュ モードのモデルの場合、 **[クエリ モード]** は常に **[In-Memory]** です。</span><span class="sxs-lookup"><span data-stu-id="461f9-114">For models in cached mode, **Query Mode** is always **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="461f9-115">DirectQuery モードのモデルの場合、 **[権限借用設定]** は指定できません。</span><span class="sxs-lookup"><span data-stu-id="461f9-115">You cannot specify **Impersonation Settings** for models in DirectQuery mode.</span></span>  
  
3.  <span data-ttu-id="461f9-116">**[配置サーバー]** で、 **[サーバー]** (名前)、 **[エディション]**、 **[データベース]** (名前)、 **[キューブ名]** の各プロパティの設定を指定し (既定の設定と異なる場合)、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="461f9-116">In **Deployment Server**, specify the **Server** (name), **Edition**, **Database** (name), and **Cube Name** property settings, if different from the default settings, and then click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="461f9-117">作成した新しいプロジェクトが指定したサーバーに自動的に配置されるように、既定の配置サーバー プロパティの設定を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="461f9-117">You can also specify the Default Deployment Server property setting so any new projects you create will automatically be deployed to the specified server.</span></span> <span data-ttu-id="461f9-118">詳細については、「 [既定のデータ モデルと配置プロパティの構成 &#40;SSAS テーブル&#41;](properties-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="461f9-118">For more information, see [Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
##  <a name="deploy-a-tabular-model-solution"></a><a name="bkmk_deploy_proc"></a><span data-ttu-id="461f9-119">テーブルモデルソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="461f9-119">Deploy a Tabular Model Solution</span></span>  
  
#### <a name="to-deploy-a-tabular-model-solution"></a><span data-ttu-id="461f9-120">テーブル モデル ソリューションを配置するには</span><span class="sxs-lookup"><span data-stu-id="461f9-120">To deploy a tabular model solution</span></span>  
  
-   <span data-ttu-id="461f9-121">で、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] [**ビルド**] メニューの [\*\*配置 \<project name> \*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="461f9-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **Build** menu, click **Deploy \<project name>**.</span></span>  
  
     <span data-ttu-id="461f9-122">**[配置]** ダイアログ ボックスが表示され、メタデータの配置の状態とモデルに含まれる各テーブルの処理が示されます ([処理オプション] プロパティが [処理しない] に設定されている場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="461f9-122">The **Deploy** dialog box will appear and indicate the status of the metadata deployment and the processing (unless Processing Option property is set to Do Not Process) of each table included in the model.</span></span> <span data-ttu-id="461f9-123">配置プロセスが完了したら、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、Analysis Services インスタンスに接続し、新しい model データベース オブジェクトが作成されていることを確認するか、クライアント レポート アプリケーションを使用して配置済みモデルと接続します。</span><span class="sxs-lookup"><span data-stu-id="461f9-123">After the deployment process is complete, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to connect to the Analysis Services instance and verify the new model database object has been created or use a client reporting application to connect to the deployed model.</span></span>  
  
##  <a name="deploy-status"></a><a name="bkmk_deploy_status"></a> <span data-ttu-id="461f9-124">配置状態</span><span class="sxs-lookup"><span data-stu-id="461f9-124">Deploy Status</span></span>  
 <span data-ttu-id="461f9-125">**[配置]** ダイアログ ボックスでは、配置操作の進行状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="461f9-125">The **Deploy** dialog box enables you to monitor the progress of a Deploy operation.</span></span> <span data-ttu-id="461f9-126">配置操作を停止することもできます。</span><span class="sxs-lookup"><span data-stu-id="461f9-126">A deploy operation can also be stopped.</span></span>  
  
 <span data-ttu-id="461f9-127">**状態**</span><span class="sxs-lookup"><span data-stu-id="461f9-127">**Status**</span></span>  
 <span data-ttu-id="461f9-128">配置操作が正常に行われたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="461f9-128">Indicates whether the Deploy operation was successful or not.</span></span>  
  
 <span data-ttu-id="461f9-129">**詳細**</span><span class="sxs-lookup"><span data-stu-id="461f9-129">**Details**</span></span>  
 <span data-ttu-id="461f9-130">配置されたメタデータ項目と各メタデータ項目の状態を一覧表示し、何か問題があればメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="461f9-130">Lists the metadata items that were deployed, the status for each metadata item, and provides a message of any issues.</span></span>  
  
 <span data-ttu-id="461f9-131">**[展開の停止]**</span><span class="sxs-lookup"><span data-stu-id="461f9-131">**Stop Deploy**</span></span>  
 <span data-ttu-id="461f9-132">クリックすると、配置操作が停止されます。</span><span class="sxs-lookup"><span data-stu-id="461f9-132">Click to halt the Deploy operation.</span></span> <span data-ttu-id="461f9-133">このオプションは、配置操作に時間がかかりすぎる場合や、エラーが多すぎる場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="461f9-133">This option is useful if the Deploy operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461f9-134">参照</span><span class="sxs-lookup"><span data-stu-id="461f9-134">See Also</span></span>  
 <span data-ttu-id="461f9-135">[SSAS 表形式&#41;&#40;テーブルモデルソリューションの配置](tabular-model-solution-deployment-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="461f9-135">[Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="461f9-136">既定のデータ モデルと配置プロパティの構成 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="461f9-136">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
