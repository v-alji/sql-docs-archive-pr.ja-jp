---
title: 'レッスン 3: ログ記録の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58fcc29759f19ad215a76a1b9ed9bf313b4c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640142"
---
# <a name="lesson-3-adding-logging"></a><span data-ttu-id="f3fdd-102">レッスン 3:ログ機能の追加</span><span class="sxs-lookup"><span data-stu-id="f3fdd-102">Lesson 3: Adding Logging</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f3fdd-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、パッケージの実行を監視し、問題を解決するためのログ機能があります。このログを使用して、タスクやコンテナー イベントを追跡できます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes logging features that let you troubleshoot and monitor package execution by providing a trace of task and container events.</span></span> <span data-ttu-id="f3fdd-104">柔軟性に優れたこのログ機能では、パッケージごと、またはパッケージ内のタスクやコンテナーごとにログ記録を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-104">The logging features are flexible, and can be enabled at the package level or on individual tasks and containers within the package.</span></span> <span data-ttu-id="f3fdd-105">ログを記録するイベントを複数選択すると、1 つのパッケージに対して複数のログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-105">You can select which events you want to log, and create multiple logs against a single package.</span></span>  
  
 <span data-ttu-id="f3fdd-106">ログ記録は、ログ プロバイダーにより供給されます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-106">Logging is provided by a log provider.</span></span> <span data-ttu-id="f3fdd-107">ログ プロバイダーごとに、異なる書式、および異なるファイル形式でログ情報を書き分けることができます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-107">Each log provider can write logging information to different formats and destination types.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="f3fdd-108">では、次のログ プロバイダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-108">provides the following log providers:</span></span>  
  
-   <span data-ttu-id="f3fdd-109">テキスト ファイル</span><span class="sxs-lookup"><span data-stu-id="f3fdd-109">Text file</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="f3fdd-110">Windows イベント ログ</span><span class="sxs-lookup"><span data-stu-id="f3fdd-110">Windows Event log</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   <span data-ttu-id="f3fdd-111">XML ファイル</span><span class="sxs-lookup"><span data-stu-id="f3fdd-111">XML file</span></span>  
  
 <span data-ttu-id="f3fdd-112">このレッスンでは、 [「レッスン 2: ループの追加](lesson-2-adding-looping-with-ssis.md)」で作成したパッケージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-112">In this lesson, you will create a copy of the package that you created in [Lesson 2: Adding Looping](lesson-2-adding-looping-with-ssis.md).</span></span> <span data-ttu-id="f3fdd-113">この新しいパッケージを操作しながら、パッケージの実行中に特定のイベントを監視するログ記録を追加し、構成します。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-113">Working with this new package, you will then add and configure logging to monitor specific events during package execution.</span></span> <span data-ttu-id="f3fdd-114">前のレッスンで完了していないものがある場合は、チュートリアルに含まれている、レッスン 2 を完了した状態のパッケージをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-114">If you have not completed any of the previous lessons, you can also copy the completed Lesson 2 package that is included with the tutorial.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f3fdd-115">このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="f3fdd-116">**AdventureWorksDW2012**をインストールしてデプロイする方法の詳細については、 [GitHub で Reporting Services 製品サンプル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-116">For more information about how to install and deploy **AdventureWorksDW2012**, [Reporting Services Product Samples on GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="f3fdd-117">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="f3fdd-117">Lesson Tasks</span></span>  
 <span data-ttu-id="f3fdd-118">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f3fdd-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="f3fdd-119">手順 1:レッスン 2 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="f3fdd-119">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [<span data-ttu-id="f3fdd-120">手順 2:ログ機能の追加と設定</span><span class="sxs-lookup"><span data-stu-id="f3fdd-120">Step 2: Adding and Configuring Logging</span></span>](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [<span data-ttu-id="f3fdd-121">手順 3:レッスン 3 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="f3fdd-121">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="f3fdd-122">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="f3fdd-122">Start the Lesson</span></span>  
 [<span data-ttu-id="f3fdd-123">手順 1:レッスン 2 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="f3fdd-123">Step 1: Copying the Lesson 2 Package</span></span>](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
