---
title: Visual Basic または Visual C# を使用したレポートサーバー Web サービスへのアクセス (SSRS チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- walkthroughs [Reporting Services]
- Reporting Services, Web service
- Web service [Reporting Services], tutorials
ms.assetid: cf688163-4ac0-475b-b6dd-6f2f05b553c6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3dc2599b4fafe682d74089d637918e04db9ed219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720564"
---
# <a name="accessing-the-report-server-web-service-using-visual-basic-or-visual-c-ssrs-tutorial"></a><span data-ttu-id="4a398-102">Visual Basic または Visual C# を使用したレポート サーバー Web サービスへのアクセス (SSRS チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="4a398-102">Accessing the Report Server Web Service Using Visual Basic or Visual C# (SSRS Tutorial)</span></span>
  <span data-ttu-id="4a398-103">次のチュートリアルでは、またはで作成されたアプリケーションからレポートサーバー Web サービスにアクセスする方法を説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4a398-103">The following tutorial shows you how to access the Report Server Web service from an application created with [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] or [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="4a398-104">学習する内容</span><span class="sxs-lookup"><span data-stu-id="4a398-104">What You Will Learn</span></span>  
 <span data-ttu-id="4a398-105">このチュートリアルでは次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="4a398-105">During the course of this tutorial, you will complete the following:</span></span>  
  
-   <span data-ttu-id="4a398-106">[!INCLUDE[msCoName](../includes/msconame-md.md)]コンソールアプリケーションプロジェクトテンプレートを使用して、クライアントアプリケーションを作成し [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4a398-106">Create a client application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="4a398-107">レポート サーバー Web サービスの Web 参照を追加する。</span><span class="sxs-lookup"><span data-stu-id="4a398-107">Add a Web reference for the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="4a398-108">Web サービスにアクセスするコードを記述する。</span><span class="sxs-lookup"><span data-stu-id="4a398-108">Write code to access the Web service.</span></span>  
  
-   <span data-ttu-id="4a398-109">デバッグ モードでコンソール アプリケーションを実行する。</span><span class="sxs-lookup"><span data-stu-id="4a398-109">Run the console application in debug mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a398-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="4a398-110">Requirements</span></span>  
 <span data-ttu-id="4a398-111">このチュートリアルを完了するには次の準備が必要です。</span><span class="sxs-lookup"><span data-stu-id="4a398-111">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="4a398-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a398-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="4a398-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]または同様 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の互換性のある開発ツール。</span><span class="sxs-lookup"><span data-stu-id="4a398-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] or a similar [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-compatible development tool.</span></span>  
  
-   <span data-ttu-id="4a398-114">レポート サーバーが配置されているコンピューター上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート サーバー Web サービスにアクセスできる十分な権限。</span><span class="sxs-lookup"><span data-stu-id="4a398-114">Sufficient permissions to be able to access the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="4a398-115">レポート サーバーにインストールされているレポート。</span><span class="sxs-lookup"><span data-stu-id="4a398-115">A report installed on your report server.</span></span> <span data-ttu-id="4a398-116">このチュートリアルでは、サンプル レポート Company Sales を使用します。</span><span class="sxs-lookup"><span data-stu-id="4a398-116">This tutorial uses the sample report, Company Sales.</span></span> <span data-ttu-id="4a398-117">サンプルレポートの詳細については、「 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a398-117">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a398-118">サンプルはセットアップ中に自動的にインストールされませんが、いつでもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="4a398-118">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="4a398-119">サンプルの詳細については、「 [SQL Server Product samples](https://go.microsoft.com/fwlink/?LinkId=182887)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a398-119">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="4a398-120">**チュートリアルの推定所要時間:** 60 分</span><span class="sxs-lookup"><span data-stu-id="4a398-120">**Estimated time to complete the tutorial:** 60 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="4a398-121">タスク</span><span class="sxs-lookup"><span data-stu-id="4a398-121">Tasks</span></span>  
 [<span data-ttu-id="4a398-122">レッスン 1: Web サービス クライアント プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="4a398-122">Lesson 1: Creating the Web Service Client Project</span></span>](../../2014/tutorials/lesson-1-creating-the-web-service-client-project.md)  
  
 [<span data-ttu-id="4a398-123">レッスン 2: Web 参照の追加</span><span class="sxs-lookup"><span data-stu-id="4a398-123">Lesson 2: Adding a Web Reference</span></span>](../../2014/tutorials/lesson-2-adding-a-web-reference.md)  
  
 [<span data-ttu-id="4a398-124">レッスン 3 : Web サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="4a398-124">Lesson 3: Accessing the Web Service</span></span>](../../2014/tutorials/lesson-3-accessing-the-web-service.md)  
  
 [<span data-ttu-id="4a398-125">レッスン 4: アプリケーションの実行 &#40;VB-VC&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="4a398-125">Lesson 4: Running the Application &#40;VB-VC&#35;&#41;</span></span>](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)  
  
  
