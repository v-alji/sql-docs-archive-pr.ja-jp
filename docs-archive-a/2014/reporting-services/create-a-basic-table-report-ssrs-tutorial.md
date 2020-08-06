---
title: 基本的なテーブル レポートの作成 (SSRS チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e0f42869a3bfa88e0c6646fd447968c8ba3a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630803"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a><span data-ttu-id="177dc-102">基本的なテーブル レポートの作成 (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="177dc-102">Create a Basic Table Report (SSRS Tutorial)</span></span>
  <span data-ttu-id="177dc-103">このチュートリアルは、レポート デザイナーを使用して、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースを基にした基本的なテーブル レポートを作成することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="177dc-103">This tutorial is designed to help you create a basic table report based on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database using Report Designer.</span></span> <span data-ttu-id="177dc-104">レポートの作成には、レポート ビルダーまたはレポート ウィザードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="177dc-104">You can also use Report Builder or the Report Wizard to create reports.</span></span> <span data-ttu-id="177dc-105">ここでは、レポート プロジェクトの作成、接続情報の設定、クエリの定義、表のデータ領域、グループ フィールド、および合計フィールドの追加、レポートのプレビュー表示を行います。</span><span class="sxs-lookup"><span data-stu-id="177dc-105">In this tutorial, you will create a report project, set up connection information, define a query, add a Table data region, group and total some fields, and preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="177dc-106">このチュートリアルを完了するには、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] をネイティブ モードで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="177dc-106">To complete this tutorial, you must be running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode.</span></span> <span data-ttu-id="177dc-107">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を SharePoint 統合モードで実行していると、レポート サーバーの URL を使用するステップを実行できません。</span><span class="sxs-lookup"><span data-stu-id="177dc-107">If you are running [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint integrated mode, the steps that use report server URLs do not work.</span></span> <span data-ttu-id="177dc-108">モードの詳細について [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は、「[レポートサーバーの Reporting Services](reporting-services-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177dc-108">For more information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] modes, see [Reporting Services Report Server](reporting-services-report-server.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177dc-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="177dc-109">Requirements</span></span>  
 <span data-ttu-id="177dc-110">このチュートリアルを使用するには、システムに以下のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="177dc-110">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="177dc-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]データベースエンジン。</span><span class="sxs-lookup"><span data-stu-id="177dc-111">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database engine.</span></span>  
  
-   <span data-ttu-id="177dc-112">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース。</span><span class="sxs-lookup"><span data-stu-id="177dc-112">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  <span data-ttu-id="177dc-113">詳細については、「 [Adventure works for SQL Server 2012 (adventure works for SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) 」 (を参照してください https://go.microsoft.com/fwlink/?LinkId=245471). 。</span><span class="sxs-lookup"><span data-stu-id="177dc-113">For more information, see [Adventure Works for SQL Server 2012 (Adventure Works for SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) (https://go.microsoft.com/fwlink/?LinkId=245471)..</span></span> <span data-ttu-id="177dc-114">のサンプルデータベースとサンプルコードのサポートの詳細については [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 、CodePlex Web サイトの「[データベースとサンプルの概要](https://go.microsoft.com/fwlink/?LinkId=110391)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177dc-114">For more information about support for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sample databases and sample code for [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], see [Databases and Samples Overview](https://go.microsoft.com/fwlink/?LinkId=110391) on the CodePlex Web site.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="177dc-115">.</span><span class="sxs-lookup"><span data-stu-id="177dc-115">.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="177dc-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="177dc-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 <span data-ttu-id="177dc-117">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースからデータを取得するには読み取り専用権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="177dc-117">You must also have read-only permissions to retrieve data from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="177dc-118">タスク</span><span class="sxs-lookup"><span data-stu-id="177dc-118">Tasks</span></span>  
 [<span data-ttu-id="177dc-119">レッスン 1: レポート サーバー プロジェクトの作成 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="177dc-119">Lesson 1: Creating a Report Server Project &#40;Reporting Services&#41;</span></span>](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [<span data-ttu-id="177dc-120">レッスン 2: 接続情報の指定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="177dc-120">Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;</span></span>](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [<span data-ttu-id="177dc-121">レッスン 3: テーブル レポートのデータセットの定義 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="177dc-121">Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;</span></span>](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [<span data-ttu-id="177dc-122">レッスン 4: レポートへのテーブルの追加 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="177dc-122">Lesson 4: Adding a Table to the Report &#40;Reporting Services&#41;</span></span>](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [<span data-ttu-id="177dc-123">レッスン 5: レポートの書式設定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="177dc-123">Lesson 5: Formatting a Report &#40;Reporting Services&#41;</span></span>](lesson-5-formatting-a-report-reporting-services.md)  
  
 [<span data-ttu-id="177dc-124">レッスン 6: グループと合計の追加 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="177dc-124">Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;</span></span>](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="177dc-125">チュートリアルを確認するときは、ドキュメントビューアーのツールバーに **[次へ**] ボタンと [**前**へ] ボタンを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="177dc-125">When reviewing tutorials, we recommend that you add **Next** and **Previous** buttons to the document viewer toolbar.</span></span> <span data-ttu-id="177dc-126">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177dc-126">For more information, see.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177dc-127">参照</span><span class="sxs-lookup"><span data-stu-id="177dc-127">See Also</span></span>  
 [<span data-ttu-id="177dc-128">Reporting Services チュートリアル &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="177dc-128">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](reporting-services-tutorials-ssrs.md)  
  
  
