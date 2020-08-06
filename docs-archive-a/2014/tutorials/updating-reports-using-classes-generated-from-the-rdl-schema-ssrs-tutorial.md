---
title: RDL スキーマから生成されたクラスを使用したレポートの更新 (SSRS チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f3972b8e1af6d50ccc6f5188c8f671fe333ebce8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632821"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a><span data-ttu-id="aacee-102">RDL スキーマから生成されたクラスを使ったレポートの更新 (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="aacee-102">Updating Reports Using Classes Generated from the RDL Schema (SSRS Tutorial)</span></span>
  <span data-ttu-id="aacee-103">このチュートリアルでは、XML スキーマ定義ツール (Xsd.exe) を使用して、クラスを使用してレポート定義ファイル (.rdl および .rdlc) をシリアル化および逆シリアル化できるクラスを生成する方法について説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="aacee-103">This tutorial illustrates how to use the XML Schema Definition Tool (Xsd.exe) to generate classes that allow you to serialize and deserialize report definition files (.rdl and .rdlc) with the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="aacee-104">学習する内容</span><span class="sxs-lookup"><span data-stu-id="aacee-104">What You Will Learn</span></span>  
 <span data-ttu-id="aacee-105">このチュートリアルの過程で、次のアクティビティを完了します。</span><span class="sxs-lookup"><span data-stu-id="aacee-105">During the course of this tutorial, you will complete the following activities:</span></span>  
  
-   <span data-ttu-id="aacee-106">[!INCLUDE[msCoName](../includes/msconame-md.md)]コンソールアプリケーションプロジェクトテンプレートを使用してアプリケーションを作成し [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="aacee-106">Create an application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="aacee-107">**Xsd**ツールを使用して、レポート定義言語 (RDL) スキーマからクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="aacee-107">Generate classes from the Report Definition Language (RDL) schema using the **xsd** tool.</span></span>  
  
-   <span data-ttu-id="aacee-108">レポート サーバーに接続し、レポート定義を取得する。</span><span class="sxs-lookup"><span data-stu-id="aacee-108">Connect to a report server and retrieve a report definition.</span></span>  
  
-   <span data-ttu-id="aacee-109">レポート定義ファイルを更新するコードを記述する。</span><span class="sxs-lookup"><span data-stu-id="aacee-109">Write code to update the report definition file.</span></span>  
  
-   <span data-ttu-id="aacee-110">更新したレポート定義をレポート サーバーに保存する。</span><span class="sxs-lookup"><span data-stu-id="aacee-110">Save the updated report definition back to the report server.</span></span>  
  
-   <span data-ttu-id="aacee-111">RDL スキーマ アプリケーション (VB/C#) を実行する。</span><span class="sxs-lookup"><span data-stu-id="aacee-111">Run the RDL Schema Application (VB/C#).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aacee-112">このチュートリアルのコード サンプルでは、レポートに説明がないため失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="aacee-112">The code samples provided in this tutorial might fail for reports having no description.</span></span> <span data-ttu-id="aacee-113">失敗する理由は、説明が指定されていないレポートには説明のプロパティが存在しないためです。</span><span class="sxs-lookup"><span data-stu-id="aacee-113">The failure is because the description property does not exist for the reports with description not specified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aacee-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="aacee-114">Requirements</span></span>  
 <span data-ttu-id="aacee-115">このチュートリアルを完了するには次の準備が必要です。</span><span class="sxs-lookup"><span data-stu-id="aacee-115">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="aacee-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aacee-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="aacee-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aacee-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="aacee-118">レポート サーバーが配置されているコンピューター上のレポート サーバー Web サービスにアクセスし、レポートをパブリッシュできる十分な権限。</span><span class="sxs-lookup"><span data-stu-id="aacee-118">Sufficient permissions to be able to access and publish reports to the Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="aacee-119">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] のインスタンスにインストールされた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="aacee-119">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database installed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="aacee-120">レポート サーバーにインストールされているレポート。</span><span class="sxs-lookup"><span data-stu-id="aacee-120">A report installed on your report server.</span></span> <span data-ttu-id="aacee-121">このチュートリアルでは、サンプル レポート Company Sales 2012 を使用します。</span><span class="sxs-lookup"><span data-stu-id="aacee-121">This tutorial uses the sample report, Company Sales 2012.</span></span> <span data-ttu-id="aacee-122">サンプルレポートの詳細については、「 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aacee-122">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aacee-123">サンプルはセットアップ中に自動的にインストールされませんが、いつでもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="aacee-123">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="aacee-124">サンプルの詳細については、「 [SQL Server Product samples](https://go.microsoft.com/fwlink/?LinkId=182887)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aacee-124">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="aacee-125">**チュートリアルの推定所要時間:** 30 分</span><span class="sxs-lookup"><span data-stu-id="aacee-125">**Estimated time to complete the tutorial:** 30 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="aacee-126">タスク</span><span class="sxs-lookup"><span data-stu-id="aacee-126">Tasks</span></span>  
 [<span data-ttu-id="aacee-127">レッスン 1 : RDL スキーマ Visual Studio プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="aacee-127">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [<span data-ttu-id="aacee-128">レッスン 2: xsd ツールを使用して RDL スキーマからクラスを作成</span><span class="sxs-lookup"><span data-stu-id="aacee-128">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [<span data-ttu-id="aacee-129">レッスン 3 : レポート サーバーからのレポート定義の読み込み</span><span class="sxs-lookup"><span data-stu-id="aacee-129">Lesson 3: Load a Report Definition from the Report Server</span></span>](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [<span data-ttu-id="aacee-130">レッスン 4: プログラムによるレポート定義の更新</span><span class="sxs-lookup"><span data-stu-id="aacee-130">Lesson 4: Update the Report Definition Programmatically</span></span>](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [<span data-ttu-id="aacee-131">レッスン 5: レポート サーバーへのレポート定義のパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="aacee-131">Lesson 5: Publish the Report Definition to the Report Server</span></span>](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [<span data-ttu-id="aacee-132">レッスン 6: RDL スキーマアプリケーションを実行する &#40;VB-C&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="aacee-132">Lesson 6: Run the RDL Schema Application &#40;VB-C&#35;&#41;</span></span>](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a><span data-ttu-id="aacee-133">参照</span><span class="sxs-lookup"><span data-stu-id="aacee-133">See Also</span></span>  
 [<span data-ttu-id="aacee-134">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aacee-134">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
