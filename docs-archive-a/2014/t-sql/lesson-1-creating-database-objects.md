---
title: 'レッスン 1: データベース オブジェクトの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 172fdbcaedc10f9c359befd48ed09ec825aea9bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720684"
---
# <a name="lesson-1-creating-database-objects"></a><span data-ttu-id="c50b2-102">レッスン 1: データベース オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c50b2-102">Lesson 1: Creating Database Objects</span></span>
  <span data-ttu-id="c50b2-103">このレッスンでは、データベースを作成する方法、データベースにテーブルを作成する方法、およびテーブル内のデータにアクセスして変更する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c50b2-103">This lesson shows you how to create a database, create a table in the database, and then access and change the data in the table.</span></span> <span data-ttu-id="c50b2-104">これは [!INCLUDE[tsql](../includes/tsql-md.md)]の入門レッスンであるため、これらのステートメントの各種オプションは使用せず、その説明も含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c50b2-104">Because this lesson is an introduction to using [!INCLUDE[tsql](../includes/tsql-md.md)], it does not use or describe the many options that are available for these statements.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="c50b2-105">ステートメントは次の方法で作成して [!INCLUDE[ssDE](../includes/ssde-md.md)] に送信できます。</span><span class="sxs-lookup"><span data-stu-id="c50b2-105">statements can be written and submitted to the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="c50b2-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用する。</span><span class="sxs-lookup"><span data-stu-id="c50b2-106">By using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c50b2-107">このチュートリアルでは、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]を使用することを前提としていますが、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express も使用できます。これは [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=14630)から無料でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c50b2-107">This tutorial assumes that you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], but you can also use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express, which is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630).</span></span>  
  
-   <span data-ttu-id="c50b2-108">[sqlcmd ユーティリティ](../tools/sqlcmd-utility.md)を使用する。</span><span class="sxs-lookup"><span data-stu-id="c50b2-108">By using the [sqlcmd utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="c50b2-109">作成したアプリケーションから接続する。</span><span class="sxs-lookup"><span data-stu-id="c50b2-109">By connecting from an application that you create.</span></span>  
  
 <span data-ttu-id="c50b2-110">コードは、そのステートメントを送信する方法にかかわらず、 [!INCLUDE[ssDE](../includes/ssde-md.md)] で同じ権限を使用して同様に実行します。</span><span class="sxs-lookup"><span data-stu-id="c50b2-110">The code executes on the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the same way and with the same permissions, regardless of how you submit the code statements.</span></span>  
  
 <span data-ttu-id="c50b2-111">[!INCLUDE[tsql](../includes/tsql-md.md)] で [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]ステートメントを実行するには、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] を開き、 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c50b2-111">To run [!INCLUDE[tsql](../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], open [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c50b2-112">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c50b2-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="c50b2-113">データベースの作成 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c50b2-113">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
-   [<span data-ttu-id="c50b2-114">テーブルの作成 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c50b2-114">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
-   [<span data-ttu-id="c50b2-115">テーブルのデータの挿入と更新 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c50b2-115">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
-   [<span data-ttu-id="c50b2-116">テーブルのデータの読み取り (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c50b2-116">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
-   [<span data-ttu-id="c50b2-117">要約 : データベース オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c50b2-117">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c50b2-118">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="c50b2-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c50b2-119">データベースの作成 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="c50b2-119">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
  
