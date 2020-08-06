---
title: SQLXML 4.0 | でアップデートグラムを使用してデータを変更するMicrosoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a2397668ed08df91377cc35dea22fd52788580
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642694"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="fa4fa-102">SQLXML 4.0 での、アップデートグラムを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="fa4fa-102">Using Updategrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="fa4fa-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アップデートグラムまたは OPENXML 関数を使用して、既存の XML ドキュメントからデータベースを変更 (挿入、更新、または削除) することができ [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="fa4fa-104">ここでは、アップデートグラムについての情報と、その使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-104">This section provides information about updategrams and examples of their usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa4fa-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fa4fa-105">In This Section</span></span>  
 [<span data-ttu-id="fa4fa-106">アップデートグラムの概要 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-106">Introduction to Updategrams &#40;SQLXML 4.0&#41;</span></span>](introduction-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-107">アップデートグラムについての基本情報と使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-107">Provides basic information and examples of updategrams.</span></span>  
  
 [<span data-ttu-id="fa4fa-108">アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-108">Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;</span></span>](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-109">アップデートグラムの注釈付きマッピング スキーマについて説明し、使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-109">Explains and provides examples of annotated mapping schemas in updategrams.</span></span>  
  
 [<span data-ttu-id="fa4fa-110">&#40;SQLXML 4.0&#41;の NULL 処理</span><span class="sxs-lookup"><span data-stu-id="fa4fa-110">NULL Handling &#40;SQLXML 4.0&#41;</span></span>](null-handling-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-111">要素値と属性値に NULL を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-111">Describes how to specify NULL for element and attribute values.</span></span>  
  
 [<span data-ttu-id="fa4fa-112">XML アップデートグラムを使用したデータの挿入 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-112">Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-113">アップデートグラムを使用したデータの挿入について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-113">Describes and provides examples of using updategrams to insert data.</span></span>  
  
 [<span data-ttu-id="fa4fa-114">XML アップデートグラムを使用したデータの削除 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-114">Deleting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-115">アップデートグラムを使用したデータの削除について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-115">Describes and provides examples of using updategrams to delete data.</span></span>  
  
 [<span data-ttu-id="fa4fa-116">XML アップデートグラムを使用したデータの更新 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-116">Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-117">アップデートグラムを使用した既存データの変更について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-117">Describes and provides examples of using updategrams to modify existing data.</span></span>  
  
 [<span data-ttu-id="fa4fa-118">アップデートグラムへのパラメーターの引き渡し &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-118">Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;</span></span>](passing-parameters-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-119">アップデートグラムへのパラメーターの引き渡しについて説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-119">Describes and provides examples of passing parameters to updategrams.</span></span>  
  
 [<span data-ttu-id="fa4fa-120">アップデートグラムでのデータベースの同時実行に関する問題の処理 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-120">Handling Database Concurrency Issues in Updategrams &#40;SQLXML 4.0&#41;</span></span>](handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-121">アップデートグラムでのコンカレンシーの問題に対応するために可能なさまざまなレベルの保護について説明し、例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-121">Describes the various levels of protection possible for handling concurrency issues in updategrams, and provides examples.</span></span>  
  
 [<span data-ttu-id="fa4fa-122">アップデートグラムサンプルアプリケーション &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-122">Updategram Sample Applications &#40;SQLXML 4.0&#41;</span></span>](../../../database-engine/dev-guide/updategram-sample-applications-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-123">アップデートグラムを使用したサンプル アプリケーションを提供します。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-123">Provides sample applications that use updategrams.</span></span>  
  
 [<span data-ttu-id="fa4fa-124">XML アップデートグラムのガイドラインと制限 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4fa-124">Guidelines and Limitations of XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="fa4fa-125">アップデートグラムを使用する場合の注意点をいくつか挙げます。</span><span class="sxs-lookup"><span data-stu-id="fa4fa-125">Lists some things to remember when working with updategrams.</span></span>  
  
  
