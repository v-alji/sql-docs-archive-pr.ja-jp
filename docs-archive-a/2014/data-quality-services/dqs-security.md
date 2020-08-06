---
title: DQS セキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3da3cdbe746b69c5c4cfe7c7c796827dd74a433c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715738"
---
# <a name="dqs-security"></a><span data-ttu-id="0f8af-102">DQS セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0f8af-102">DQS Security</span></span>
  <span data-ttu-id="0f8af-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のセキュリティ インフラストラクチャは、SQL Server のセキュリティ インフラストラクチャに基づいています。</span><span class="sxs-lookup"><span data-stu-id="0f8af-103">The [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) security infrastructure is based upon the SQL Server security infrastructure.</span></span> <span data-ttu-id="0f8af-104">データベース管理者は、ユーザーに DQS ロールを関連付けることによって、ユーザーに一連の権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="0f8af-104">A database administrator grants a user a set of permissions by associating the user with a DQS role.</span></span> <span data-ttu-id="0f8af-105">これにより、ユーザーがアクセスできる DQS リソースや、ユーザーが実行できる機能アクティビティを定義します。</span><span class="sxs-lookup"><span data-stu-id="0f8af-105">Doing so determines the DQS resources that the user has access to and the functional activities that the user is allowed to perform.</span></span>  
  
## <a name="dqs-roles"></a><span data-ttu-id="0f8af-106">DQS ロール</span><span class="sxs-lookup"><span data-stu-id="0f8af-106">DQS Roles</span></span>  
 <span data-ttu-id="0f8af-107">DQS には 4 つのロールがあります。</span><span class="sxs-lookup"><span data-stu-id="0f8af-107">There are four roles for DQS.</span></span> <span data-ttu-id="0f8af-108">1 つはデータベース管理者 (DBA) で、主に製品のインストール、データベースのメンテナンス、およびユーザー管理を行います。</span><span class="sxs-lookup"><span data-stu-id="0f8af-108">One is the database administrator (DBA) who deals primarily with product installation, database maintenance, and user management.</span></span> <span data-ttu-id="0f8af-109">このロールは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションよりも SQL Server Management Studio を主に使用します。</span><span class="sxs-lookup"><span data-stu-id="0f8af-109">This role primarily uses the SQL Server Management Studio, rather than within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="0f8af-110">このサーバー ロールは sysadmin です。</span><span class="sxs-lookup"><span data-stu-id="0f8af-110">Their server role is sysadmin.</span></span>  
  
 <span data-ttu-id="0f8af-111">その他の 3 つのロールは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションを使用して製品を直接使用するインフォメーション ワーカー、データ スチュワード用です。</span><span class="sxs-lookup"><span data-stu-id="0f8af-111">The three other roles are information workers, data stewards who use the product directly by working in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="0f8af-112">これらのロールには、次が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-112">These roles include the following:</span></span>  
  
-   <span data-ttu-id="0f8af-113">**DQS 管理者** (dqs_administrator ロール) は、製品のスコープ内のすべてを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-113">The **DQS Administrator** (dqs_administrator role) can do everything in the scope of the product.</span></span> <span data-ttu-id="0f8af-114">管理者は、プロジェクトの編集と実行、ナレッジ ベースの作成と編集、アクティビティの終了、アクティビティ内のプロセスの停止、および構成と参照データ サービス設定の変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-114">The administrator can edit and execute a project, create and edit a knowledge base, terminate an activity, stop a process within an activity, and can change the configuration and Reference Data Services settings.</span></span> <span data-ttu-id="0f8af-115">ただし、DQS 管理者は、サーバーのインストールや新しいユーザーの追加はできません。</span><span class="sxs-lookup"><span data-stu-id="0f8af-115">The DQS Administrator cannot, however, install the server or add new users.</span></span> <span data-ttu-id="0f8af-116">これらはデータベース管理者が行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f8af-116">The database administrator must do that.</span></span>  
  
-   <span data-ttu-id="0f8af-117">**DQS KB エディター** (dqs_kb_editor ロール) は、管理を除いて DQS アクティビティのすべてを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-117">The **DQS KB Editor** (dqs_kb_editor role) can perform all of the DQS activities, except for administration.</span></span> <span data-ttu-id="0f8af-118">KB エディターは、プロジェクトの編集と実行、およびナレッジ ベースの作成と編集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-118">The KB Editor can edit and execute a project, and create and edit a knowledge base.</span></span> <span data-ttu-id="0f8af-119">アクティビティ監視データを参照することはできますが、アクティビティの終了や停止、または管理業務の実行はできません。</span><span class="sxs-lookup"><span data-stu-id="0f8af-119">They can see the activity monitoring data, but cannot terminate or stop an activity or perform administrative duties.</span></span>  
  
-   <span data-ttu-id="0f8af-120">**DQS KB オペレーター** (dqs_kb_operator ロール) は、プロジェクトの編集や実行を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-120">The **DQS KB Operator** (dqs_kb_operator role) can edit and execute a project.</span></span> <span data-ttu-id="0f8af-121">どのようなナレッジ マネージメントも実行できず、ナレッジ ベースの作成や変更もできません。</span><span class="sxs-lookup"><span data-stu-id="0f8af-121">They cannot perform any kind of knowledge management; they cannot create or change a knowledge base.</span></span> <span data-ttu-id="0f8af-122">アクティビティ監視データを参照することはできますが、アクティビティの終了または管理業務の実行はできません。</span><span class="sxs-lookup"><span data-stu-id="0f8af-122">They can see the activity monitoring data, but cannot terminate an activity or perform administrative duties.</span></span>  
  
## <a name="user-management"></a><span data-ttu-id="0f8af-123">[ユーザー管理]</span><span class="sxs-lookup"><span data-stu-id="0f8af-123">User Management</span></span>  
 <span data-ttu-id="0f8af-124">データベース管理者 (DBA) は DQS ユーザーを作成し、SQL Server Management Studio の DQS ロールに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="0f8af-124">The database administrator (DBA) creates DQS users and associates them with DQS roles in SQL Server Management Studio.</span></span> <span data-ttu-id="0f8af-125">DBA は、DQS_MAIN データベースのユーザーとして SQL ログインを追加し、各ユーザーを DQS ロールの 1 つと関連付けることによってユーザーの権限を管理します。</span><span class="sxs-lookup"><span data-stu-id="0f8af-125">The DBA manages their permissions by adding SQL Logins as users of the DQS_MAIN database, and associating each user with one of the DQS roles.</span></span> <span data-ttu-id="0f8af-126">各ロールには、DQS_MAIN データベースの一連のストアド プロシージャに対する権限が付与されています。</span><span class="sxs-lookup"><span data-stu-id="0f8af-126">Each role is granted permissions to a set of stored procedures on the DQS_MAIN database.</span></span> <span data-ttu-id="0f8af-127">DQS_PROJECTS および DQS_STAGING_DATA データベースについては、3 つの DQS ロールは使用できません。</span><span class="sxs-lookup"><span data-stu-id="0f8af-127">The three DQS roles are not available for the DQS_PROJECTS and DQS_STAGING_DATA databases.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0f8af-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0f8af-128">Related Tasks</span></span>  
  
|<span data-ttu-id="0f8af-129">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="0f8af-129">Task Description</span></span>|<span data-ttu-id="0f8af-130">トピック</span><span class="sxs-lookup"><span data-stu-id="0f8af-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0f8af-131">SQL Server Management Studio を使用してユーザーを作成し、DQS ロールを付与する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0f8af-131">Describes how to create a user and grant DQS roles using SQL Server Management Studio.</span></span>|[<span data-ttu-id="0f8af-132">SSMS による DQS ユーザーの管理</span><span class="sxs-lookup"><span data-stu-id="0f8af-132">Manage DQS Users in SSMS</span></span>](../../2014/data-quality-services/manage-dqs-users-in-ssms.md)|  
  
  
