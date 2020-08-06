---
title: レッスン 1:テーブルの階層構造への変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 196a546093786f9be4b88536763b3150ae750f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740794"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a><span data-ttu-id="6bb49-102">レッスン 1:テーブルの階層構造への変換</span><span class="sxs-lookup"><span data-stu-id="6bb49-102">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>
  <span data-ttu-id="6bb49-103">階層リレーションシップを表すために自己結合を使っているテーブルがある場合、このレッスンの説明に従って、それらのテーブルを階層構造に変換できます。</span><span class="sxs-lookup"><span data-stu-id="6bb49-103">Customers who have tables using self joins to express hierarchical relationships can convert their tables to a hierarchical structure using this lesson as a guide.</span></span> <span data-ttu-id="6bb49-104">現在の表示から、`hierarchyid` を使用した表示に移行するのは比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="6bb49-104">It is relatively easy to migrate from this representation to one using `hierarchyid`.</span></span> <span data-ttu-id="6bb49-105">移行後は、コンパクトで理解しやすい階層表示が可能になるため、ユーザーはさまざまな方法でインデックスを作成して効率的なクエリを実現できます。</span><span class="sxs-lookup"><span data-stu-id="6bb49-105">After migration, users will have a compact and easy to understand hierarchical representation, which can be indexed in several ways for efficient queries.</span></span>  
  
 <span data-ttu-id="6bb49-106">このレッスンでは、既存のテーブルを検証した後、`hierarchyid` 列を含む新しいテーブルを作成し、そのテーブルにソース テーブルのデータを取り込みます。さらに、3 とおりのインデックス作成方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="6bb49-106">This lesson, examines an existing table, creates a new table containing a `hierarchyid` column, populates the table with the data from the source table, and then demonstrates three indexing strategies.</span></span> <span data-ttu-id="6bb49-107">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6bb49-107">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="6bb49-108">Employee テーブルの現在の構造の確認</span><span class="sxs-lookup"><span data-stu-id="6bb49-108">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [<span data-ttu-id="6bb49-109">既存の階層データを使用したテーブルの設定</span><span class="sxs-lookup"><span data-stu-id="6bb49-109">Populating a Table with Existing Hierarchical Data</span></span>](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [<span data-ttu-id="6bb49-110">NewOrg テーブルの最適化</span><span class="sxs-lookup"><span data-stu-id="6bb49-110">Optimizing the NewOrg Table</span></span>](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [<span data-ttu-id="6bb49-111">概要: テーブルの階層構造への変換</span><span class="sxs-lookup"><span data-stu-id="6bb49-111">Summary: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a><span data-ttu-id="6bb49-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="6bb49-112">Prerequisites</span></span>  
 <span data-ttu-id="6bb49-113">このレッスンを学習するには、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="6bb49-113">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6bb49-114">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="6bb49-114">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6bb49-115">Employee テーブルの現在の構造の確認</span><span class="sxs-lookup"><span data-stu-id="6bb49-115">Examining the Current Structure of the Employee Table</span></span>](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="6bb49-116">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="6bb49-116">Next Lesson</span></span>  
 [<span data-ttu-id="6bb49-117">レッスン 2: 階層テーブルでのデータの作成と管理</span><span class="sxs-lookup"><span data-stu-id="6bb49-117">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
