---
title: 'チュートリアル : SQL Server Management Studio | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8206fea828d6169975dc1d026a22e18e682f71e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644774"
---
# <a name="tutorial-sql-server-management-studio"></a><span data-ttu-id="9ed4b-102">チュートリアル:SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9ed4b-102">Tutorial: SQL Server Management Studio</span></span>
  <span data-ttu-id="9ed4b-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のチュートリアルでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インフラストラクチャを管理するための統合環境について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tutorial introduces you to the integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9ed4b-104">は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを構成、監視、および管理するためのグラフィカル インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-104">presents a graphical interface for configuring, monitoring, and administering instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ed4b-105">さらに、データベースやデータ ウェアハウスなどの、アプリケーションで使用されるデータ層コンポーネントを配置、監視、およびアップグレードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-105">It also allows you to deploy, monitor, and upgrade the data-tier components used by your applications, such as databases and data warehouses.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9ed4b-106">は、スクリプトを編集およびデバッグするための [!INCLUDE[tsql](../../includes/tsql-md.md)]、MDX、DMX、XML の各言語エディターも提供します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-106">also provides [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX, and XML language editors for editing and debugging scripts.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="9ed4b-107">学習する内容</span><span class="sxs-lookup"><span data-stu-id="9ed4b-107">What You Will Learn</span></span>  
 <span data-ttu-id="9ed4b-108">このチュートリアルでは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] での情報の操作方法と機能の活用方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-108">This tutorial will help you understand the presentation of information in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to take advantage of the features.</span></span> <span data-ttu-id="9ed4b-109">このチュートリアルは、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を除く [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションに同梱された [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] の完全インストールを想定した内容となっています。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-109">Note that this tutorial applies to the complete installation of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] that is included with all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="9ed4b-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の基本インストールや、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] に付属の [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] インストールは、このチュートリアルに書かれている内容とは、機能が若干異なります。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-110">Functionality for basic installations of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and for [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] installations that ship with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] is slightly different than what is presented in this tutorial.</span></span>  
  
 <span data-ttu-id="9ed4b-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] に慣れ親しむには、実践的な経験を積むのが最も効果的です。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-111">The best way to get acquainted with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is through hands-on practice.</span></span> <span data-ttu-id="9ed4b-112">このチュートリアルでは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のコンポーネントを管理する方法と、頻繁に使用する機能へのアクセス方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-112">This tutorial will teach you how to manage the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to find the features that you use regularly.</span></span>  
  
 <span data-ttu-id="9ed4b-113">このチュートリアルは、次の 3 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-113">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="9ed4b-114">レッスン 1:SQL Server Management Studio での基本操作</span><span class="sxs-lookup"><span data-stu-id="9ed4b-114">Lesson 1: Basic Navigation in SQL Server Management Studio</span></span>](lesson-1-basic-navigation-in-sql-server-management-studio.md)  
 <span data-ttu-id="9ed4b-115">このレッスンでは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のコンポーネントを使用する方法、環境レイアウトを再構成する方法、および既定のレイアウトを復元する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-115">In this lesson you will learn how to use the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], how to reconfigure the environment layout, and how to restore the default layout.</span></span>  
  
 [<span data-ttu-id="9ed4b-116">レッスン 2: Transact-SQL の記述</span><span class="sxs-lookup"><span data-stu-id="9ed4b-116">Lesson 2: Writing Transact-SQL</span></span>](lesson-2-writing-transact-sql.md)  
 <span data-ttu-id="9ed4b-117">このレッスンでは、クエリ エディターを開く方法、コードの管理方法、クエリ エディターのその他の新機能を使用する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-117">In this lesson, you will learn how to open Query Editor, how to manage code, and how to use the other new features of Query Editor.</span></span>  
  
 [<span data-ttu-id="9ed4b-118">レッスン 3:テンプレート、ソリューション、およびスクリプト プロジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="9ed4b-118">Lesson 3: Working with Templates, Solutions, and Script Projects</span></span>](lesson-3-working-with-templates-solutions-and-script-projects.md)  
 <span data-ttu-id="9ed4b-119">このレッスンでは、テンプレートを使用して、スクリプトをソリューションやプロジェクトにまとめる方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-119">In this lesson you will learn how to use templates, and organize scripts into solutions and projects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed4b-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ed4b-120">Requirements</span></span>  
 <span data-ttu-id="9ed4b-121">このチュートリアルは、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]には慣れていないが、データベースの概念と [!INCLUDE[tsql](../../includes/tsql-md.md)] 言語を理解している、熟練のデータベース管理者およびデータベース開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-121">This tutorial is intended for experienced database administrators and database developers who are not familiar with [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], but who are who are familiar with database concepts and the [!INCLUDE[tsql](../../includes/tsql-md.md)] language.</span></span>  
  
 <span data-ttu-id="9ed4b-122">このチュートリアルを使用するには、システムに以下のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-122">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="9ed4b-123">以降のバージョンおよび [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-123">or a later version with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample databases.</span></span> <span data-ttu-id="9ed4b-124">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-124">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="9ed4b-125">サンプル データベースをインストールするには、「 [SQL Server のサンプルとサンプル データベースのインストール](http://sqlserversamples.codeplex.com)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ed4b-125">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
-   <span data-ttu-id="9ed4b-126">Internet Explorer 9.0 以降</span><span class="sxs-lookup"><span data-stu-id="9ed4b-126">Internet Explorer 9.0 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed4b-127">参照</span><span class="sxs-lookup"><span data-stu-id="9ed4b-127">See Also</span></span>  
 [<span data-ttu-id="9ed4b-128">データベース エンジンのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9ed4b-128">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
