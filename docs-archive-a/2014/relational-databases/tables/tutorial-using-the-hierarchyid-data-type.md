---
title: 'チュートリアル: hierarchyid データ型の使用 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
author: stevestein
ms.author: sstein
ms.openlocfilehash: a735b4c2b51e1c680c8129647733ce1efd9f9984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634369"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a><span data-ttu-id="61d97-102">チュートリアル : hierarchyid データ型の使用</span><span class="sxs-lookup"><span data-stu-id="61d97-102">Tutorial: Using the hierarchyid Data Type</span></span>
  <span data-ttu-id="61d97-103">このチュートリアルは、[!INCLUDE[tsql](../../includes/tsql-md.md)] については理解しているが、`hierarchyid` データ型は初めて使用するユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="61d97-103">This tutorial is intended for users who are experienced with [!INCLUDE[tsql](../../includes/tsql-md.md)], but are new to the `hierarchyid` data type.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="61d97-104">学習する内容</span><span class="sxs-lookup"><span data-stu-id="61d97-104">What You Will Learn</span></span>  
 <span data-ttu-id="61d97-105">このチュートリアルは、次の 2 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="61d97-105">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="61d97-106">レッスン 1: テーブルの階層構造への変換</span><span class="sxs-lookup"><span data-stu-id="61d97-106">Lesson 1: Converting a Table to a Hierarchical Structure</span></span>](lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
 <span data-ttu-id="61d97-107">このレッスンでは、親子階層として構成されている既存の従業員テーブルを使用し、`hierarchyid` データ型を使用して階層を表す新しいテーブルにデータを移動します。</span><span class="sxs-lookup"><span data-stu-id="61d97-107">In this lesson, you take an existing employee table that is structured as a parent/child hierarchy and move the data into a new table that represents the hierarchy by using the `hierarchyid` data type.</span></span> <span data-ttu-id="61d97-108">このレッスンを学習するには、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="61d97-108">This lesson requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [<span data-ttu-id="61d97-109">レッスン 2: 階層テーブルでのデータの作成と管理</span><span class="sxs-lookup"><span data-stu-id="61d97-109">Lesson 2: Creating and Managing Data in a Hierarchical Table</span></span>](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
 <span data-ttu-id="61d97-110">このレッスンでは、`hierarchyid` データ型を使用して階層構造を表すテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="61d97-110">In this lesson, you create a table by using the `hierarchyid` data type to represent the hierarchy structure.</span></span> <span data-ttu-id="61d97-111">その後、階層的な手法を使用して、テーブル内のデータを操作します。</span><span class="sxs-lookup"><span data-stu-id="61d97-111">Then, you manipulate the data in the table by using the hierarchical methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61d97-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="61d97-112">Requirements</span></span>  
 <span data-ttu-id="61d97-113">システムには次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d97-113">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="61d97-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の任意のエディション。</span><span class="sxs-lookup"><span data-stu-id="61d97-114">Any edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="61d97-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="61d97-115">Either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.</span></span>  
  
-   <span data-ttu-id="61d97-116">Internet Explorer 6 以降。</span><span class="sxs-lookup"><span data-stu-id="61d97-116">Internet Explorer 6 or a later version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d97-117">参照</span><span class="sxs-lookup"><span data-stu-id="61d97-117">See Also</span></span>  
 <span data-ttu-id="61d97-118">[チュートリアル: データベースエンジンを使用したはじめに](../tutorial-getting-started-with-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="61d97-118">[Tutorial: Getting Started with the Database Engine](../tutorial-getting-started-with-the-database-engine.md) </span></span>  
 <span data-ttu-id="61d97-119">[チュートリアル: Transact-sql ステートメントの記述](../../t-sql/tutorial-writing-transact-sql-statements.md) </span><span class="sxs-lookup"><span data-stu-id="61d97-119">[Tutorial: Writing Transact-SQL Statements](../../t-sql/tutorial-writing-transact-sql-statements.md) </span></span>  
 <span data-ttu-id="61d97-120">[hierarchyid データ型メソッドリファレンス](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="61d97-120">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="61d97-121">[階層データ &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="61d97-121">[Hierarchical Data &#40;SQL Server&#41;](../hierarchical-data-sql-server.md) </span></span>  
 [<span data-ttu-id="61d97-122">hierarchyid &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="61d97-122">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
