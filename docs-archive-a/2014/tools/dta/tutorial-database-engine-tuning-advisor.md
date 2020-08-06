---
title: 'チュートリアル: データベース エンジン チューニング アドバイザー | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], tutorials
- tutorials [Database Engine Tuning Advisor]
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68e026cb28b875b834f20c906232285ede8e217b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632248"
---
# <a name="tutorial-database-engine-tuning-advisor"></a><span data-ttu-id="81fe2-102">チュートリアル:Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="81fe2-102">Tutorial: Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="81fe2-103">データベース エンジン チューニング アドバイザーのチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="81fe2-103">Welcome to the Database Engine Tuning Advisor tutorial.</span></span> <span data-ttu-id="81fe2-104">データベース エンジン チューニング アドバイザーは、指定されたデータベースでクエリがどのように処理されるのかを調査し、インデックス、インデックス付きビュー、パーティション分割などのデータベース構造を更新することによって、クエリ処理のパフォーマンスを強化するようユーザーに提案します。</span><span class="sxs-lookup"><span data-stu-id="81fe2-104">Database Engine Tuning Advisor examines how queries are processed in the databases you specify, and then recommends how you can improve query processing performance by modifying database structures such as indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="81fe2-105">データベース エンジン チューニング アドバイザーには、グラフィカル ユーザー インターフェイス (GUI) および **dta** コマンド プロンプト ユーティリティの 2 つのユーザー インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="81fe2-105">Database Engine Tuning Advisor provides two user interfaces: a graphical user interface (GUI) and the **dta** command prompt utility.</span></span> <span data-ttu-id="81fe2-106">GUI では、チューニング セッションの結果をすばやく簡単に表示できます。一方、 **dta** ユーティリティでは、データベース エンジン チューニング アドバイザーの機能をスクリプトへ簡単に組み込み、チューニングを自動化することができます。</span><span class="sxs-lookup"><span data-stu-id="81fe2-106">The GUI makes it easy to quickly view the results of tuning sessions, and the **dta** utility makes it easy to incorporate Database Engine Tuning Advisor functionality into scripts for automated tuning.</span></span> <span data-ttu-id="81fe2-107">また、XML 入力の取り込みが可能なので、より詳細にチューニング処理を制御できます。</span><span class="sxs-lookup"><span data-stu-id="81fe2-107">In addition, Database Engine Tuning Advisor can take XML input, which offers more control over the tuning process.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="81fe2-108">学習する内容</span><span class="sxs-lookup"><span data-stu-id="81fe2-108">What You Will Learn</span></span>  
 <span data-ttu-id="81fe2-109">このチュートリアルでは、データベース エンジン チューニング アドバイザー GUI の操作方法、および基本的な作業を GUI と **dta** ユーティリティの両方で実行する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="81fe2-109">This tutorial will teach you how to navigate the Database Engine Tuning Advisor GUI, and how to perform some basic tasks with both the GUI and the **dta** utility.</span></span> <span data-ttu-id="81fe2-110">ここで学習する内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="81fe2-110">It contains the following lessons:</span></span>  
  
 [<span data-ttu-id="81fe2-111">レッスン 1:データベース エンジン チューニング アドバイザーでの基本操作</span><span class="sxs-lookup"><span data-stu-id="81fe2-111">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
 <span data-ttu-id="81fe2-112">このレッスンでは、データベース エンジン チューニング アドバイザーの新しい GUI に慣れ親しみ、表示オプションとレイアウトの設定方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="81fe2-112">In this lesson, you will familiarize yourself with the new Database Engine Tuning Advisor GUI and learn how to set display options and layout.</span></span>  
  
 [<span data-ttu-id="81fe2-113">レッスン 2:データベース エンジン チューニング アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="81fe2-113">Lesson 2: Using Database Engine Tuning Advisor</span></span>](lesson-2-using-database-engine-tuning-advisor.md)  
 <span data-ttu-id="81fe2-114">このレッスンでは、データベース エンジン チューニング アドバイザーの GUI を使った基本的なチューニング タスクの実行方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="81fe2-114">In this lesson, you will learn how to perform basic tuning tasks with the Database Engine Tuning Advisor GUI.</span></span>  
  
 [<span data-ttu-id="81fe2-115">レッスン 3:dta コマンド プロンプト ユーティリティの使用</span><span class="sxs-lookup"><span data-stu-id="81fe2-115">Lesson 3: Using the dta Command Prompt Utility</span></span>](lesson-3-using-the-dta-command-prompt-utility.md)  
 <span data-ttu-id="81fe2-116">このレッスンでは、 **dta** コマンド プロンプト ユーティリティを起動する方法と、いくつかの簡単なチューニング コマンドを実行する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="81fe2-116">In this lesson, you learn how to start the **dta** command prompt utility and how to run some simple tuning commands.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81fe2-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="81fe2-117">Requirements</span></span>  
 <span data-ttu-id="81fe2-118">このチュートリアルは、データベース管理の経験はあるが、データベース エンジン チューニング アドバイザーの GUI または **dta** コマンド プロンプト ユーティリティに不慣れなデータベース管理者を対象としています。インデックスやインデックス付きビューなどデータベースの概念や構造は理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="81fe2-118">This tutorial is intended for database administrators who are not familiar with the Database Engine Tuning Advisor GUI or the **dta** command prompt utility, but who are experienced with database concepts and structures, such as indexes and indexed views.</span></span>  
  
 <span data-ttu-id="81fe2-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (または以降のバージョン) および [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="81fe2-119">You must install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (or a later version) with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="81fe2-120">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="81fe2-120">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="81fe2-121">サンプル データベースをインストールするには、「 [SQL Server のサンプルとサンプル データベースのインストール](http://sqlserversamples.codeplex.com)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81fe2-121">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="81fe2-122">このチュートリアルが終了したら</span><span class="sxs-lookup"><span data-stu-id="81fe2-122">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="81fe2-123">このチュートリアルのレッスンが終了したら、次のトピックを参照し、データベース エンジン チューニング アドバイザーの詳細を学習してください。</span><span class="sxs-lookup"><span data-stu-id="81fe2-123">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="81fe2-124">このツールを使用した作業の実行方法の説明については、「[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81fe2-124">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="81fe2-125">コマンド プロンプト ユーティリティおよびユーティリティの動作の制御に使用できるオプションの XML ファイルに関するリファレンス情報については、「[dta Utility](dta-utility.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81fe2-125">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="81fe2-126">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="81fe2-126">Next Lesson</span></span>  
 [<span data-ttu-id="81fe2-127">レッスン 1:データベース エンジン チューニング アドバイザーでの基本操作</span><span class="sxs-lookup"><span data-stu-id="81fe2-127">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
