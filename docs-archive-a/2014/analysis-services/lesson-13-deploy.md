---
title: 'レッスン 14: Deploy |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1a55960a0c33a386d978f3c15e489ed7bd861ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631292"
---
# <a name="lesson-14-deploy"></a><span data-ttu-id="6fcf3-102">レッスン 14:配置</span><span class="sxs-lookup"><span data-stu-id="6fcf3-102">Lesson 14: Deploy</span></span>
  <span data-ttu-id="6fcf3-103">このレッスンでは、配置プロパティを構成します。具体的には、テーブル モードで実行されている Analysis Services の配置サーバー インスタンスと、配置するモデルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-103">In this lesson, you will configure deployment properties; specifying a deployment server instance of Analysis Services running in Tabular mode, and a name for the model you deploy.</span></span> <span data-ttu-id="6fcf3-104">その後、そのインスタンスにモデルを配置します。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-104">You will then deploy the model to that instance.</span></span> <span data-ttu-id="6fcf3-105">配置が完了すると、ユーザーはレポート クライアント アプリケーションを使用してモデルに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-105">After it is deployed, users can connect to the model by using a reporting client application.</span></span> <span data-ttu-id="6fcf3-106">詳細については、[「テーブル モデル ソリューションの配置 (SSAS テーブル)」](tabular-models/tabular-model-solution-deployment-ssas-tabular.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-106">To learn more, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="6fcf3-107">このレッスンの推定所要時間: **5 分**</span><span class="sxs-lookup"><span data-stu-id="6fcf3-107">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6fcf3-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="6fcf3-108">Prerequisites</span></span>  
 <span data-ttu-id="6fcf3-109">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="6fcf3-110">このレッスンの実習を行う前に、前のレッスン [「レッスン 13: Excel での分析」](lesson-12-analyze-in-excel.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
## <a name="deploy-the-model"></a><span data-ttu-id="6fcf3-111">モデルの配置</span><span class="sxs-lookup"><span data-stu-id="6fcf3-111">Deploy the Model</span></span>  
  
#### <a name="to-configure-deployment-properties"></a><span data-ttu-id="6fcf3-112">デプロイ関連のパラメータを設定する</span><span class="sxs-lookup"><span data-stu-id="6fcf3-112">To configure deployment properties</span></span>  
  
1.  <span data-ttu-id="6fcf3-113">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の **ソリューション エクスプローラー**で、 **Adventure Works Internet Sales Tabular Model** プロジェクトを右クリックし、コンテキスト メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-113">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click on the **Adventure Works Internet Sales Tabular Model** project, and then in the context menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6fcf3-114">**[AW Internet Sales Tabular Model プロパティ ページ]** ダイアログ ボックスで、 **[配置サーバー]** の **[サーバー]** プロパティに、テーブル モードで実行されている Analysis Services インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-114">In the **AW Internet Sales Tabular Model Property Pages** dialog box, under **Deployment Server**, in the **Server** property, type the name of an Analysis Services instance running in Tabular mode.</span></span> <span data-ttu-id="6fcf3-115">これが、モデルの配置先のインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-115">This will be the instance your model will be deployed to.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6fcf3-116">配置を行うには、リモート Analysis Services インスタンスに対する管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-116">You must have Administrator permissions on a remote Analysis Services instance in-order to deploy to it.</span></span>  
  
3.  <span data-ttu-id="6fcf3-117">"**クエリモード**" プロパティが**メモリ内**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-117">Verify the **Query Mode** property is set to **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6fcf3-118">このチュートリアルを使用して作成されたモデルは、DirectQuery モードではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-118">The model created by using this tutorial is not supported in DirectQuery mode.</span></span>  
  
4.  <span data-ttu-id="6fcf3-119">[**データベース**] プロパティで、「」と入力 `Adventure Works Internet Sales Model` します。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-119">In the **Database** property, type `Adventure Works Internet Sales Model`.</span></span>  
  
5.  <span data-ttu-id="6fcf3-120">[**キューブ**名] プロパティに「」と入力 `Adventure Works Internet Sales Model` します。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-120">In the **Cube** Name property, type `Adventure Works Internet Sales Model`.</span></span>  
  
6.  <span data-ttu-id="6fcf3-121">選択内容を確認し､**[OK]** をクリックします｡</span><span class="sxs-lookup"><span data-stu-id="6fcf3-121">Verify your selections and then click **OK**.</span></span>  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a><span data-ttu-id="6fcf3-122">Adventure Works Internet Sales テーブル モデルを配置するには</span><span class="sxs-lookup"><span data-stu-id="6fcf3-122">To deploy the Adventure Works Internet Sales tabular model</span></span>  
  
1.  <span data-ttu-id="6fcf3-123">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[ビルド]** メニューをクリックし、 **[AW Internet Sales Tabular Model の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-123">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Build** menu, and then click **Deploy AW Internet Sales Tabular Model**.</span></span>  
  
     <span data-ttu-id="6fcf3-124">[配置] ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-124">The Deploy dialog box appears and displays the deployment status of the metadata as well as each table included in the model.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="6fcf3-125">まとめ</span><span class="sxs-lookup"><span data-stu-id="6fcf3-125">Conclusion</span></span>  
 <span data-ttu-id="6fcf3-126">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-126">Congratulations!</span></span> <span data-ttu-id="6fcf3-127">最初の Analysis Services テーブル モデルの作成と配置が完了しました。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-127">You are finished authoring and deploying your first Analysis Services tabular model.</span></span> <span data-ttu-id="6fcf3-128">このチュートリアルでは､表形式モデルの作成で一般的な作業の手順をご案内しました｡</span><span class="sxs-lookup"><span data-stu-id="6fcf3-128">This tutorial has helped guide you through completing the most common tasks in creating a tabular model.</span></span> <span data-ttu-id="6fcf3-129">Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-129">Now that your Adventure Works Internet Sales Model is deployed, you can use SQL Server Management Studio to manage the model; create process scripts and a backup plan.</span></span> <span data-ttu-id="6fcf3-130">ユーザーは、Microsoft Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]などのレポート クライアント アプリケーションを使用して、モデルに接続できます。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-130">Users can connect to the model using a reporting client application such as Microsoft Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="6fcf3-131">その他の情報</span><span class="sxs-lookup"><span data-stu-id="6fcf3-131">Additional Resources</span></span>  
 <span data-ttu-id="6fcf3-132">[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートをサポートするテーブル モデル プロパティの詳細については、[「Power View レポート プロパティ (SSAS テーブル)」](tabular-models/properties-ssas-tabular.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fcf3-132">To learn more about tabular model properties that support [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] reports, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](tabular-models/properties-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcf3-133">参照</span><span class="sxs-lookup"><span data-stu-id="6fcf3-133">See Also</span></span>  
 <span data-ttu-id="6fcf3-134">[SSAS テーブル &#40;の DirectQuery モード&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="6fcf3-134">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 <span data-ttu-id="6fcf3-135">[SSAS 表形式&#41;&#40;既定のデータモデルと配置プロパティの構成](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="6fcf3-135">[Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="6fcf3-136">表形式モデルのデータベース (SSAS 表形式)</span><span class="sxs-lookup"><span data-stu-id="6fcf3-136">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
