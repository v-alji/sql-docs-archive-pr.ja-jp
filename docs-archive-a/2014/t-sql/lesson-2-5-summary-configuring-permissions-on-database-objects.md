---
title: '概要: データベース オブジェクトに対するアクセス許可の構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- configuring permissions on databases
ms.assetid: d0ecf297-27af-43a4-918c-31c354b3a96e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb6265513d467f352b0ae890dd3f119a7f5fffb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644733"
---
# <a name="summary-configuring-permissions-on-database-objects"></a><span data-ttu-id="3da98-102">概要 : データベース オブジェクトに対する権限の構成</span><span class="sxs-lookup"><span data-stu-id="3da98-102">Summary: Configuring Permissions on Database Objects</span></span>
  <span data-ttu-id="3da98-103">ユーザーはログインすることで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に接続する権限を与えられます。</span><span class="sxs-lookup"><span data-stu-id="3da98-103">Logins give users permissions to connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3da98-104">このログインで、ユーザーは特定のデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3da98-104">Users are logins that can access a specific database.</span></span> <span data-ttu-id="3da98-105">データの読み取り、アクセス、および変更を行う権限をユーザーに与えるには、GRANT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3da98-105">Use the GRANT statement to give users permission to read and to access and change the data.</span></span>  
  
 <span data-ttu-id="3da98-106">ビューとは、1 つの SELECT ステートメントであり、ユーザーにはテーブルのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="3da98-106">A view is a single SELECT statement and looks like a table to the user.</span></span> <span data-ttu-id="3da98-107">ストアド プロシージャは、バッチとして実行される 1 つ以上の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="3da98-107">A stored procedure is one or more [!INCLUDE[tsql](../includes/tsql-md.md)] statements that execute as a batch.</span></span>  
  
## <a name="next-lesson-in-tutorial"></a><span data-ttu-id="3da98-108">チュートリアルの次のレッスン</span><span class="sxs-lookup"><span data-stu-id="3da98-108">Next Lesson in Tutorial</span></span>  
 [<span data-ttu-id="3da98-109">レッスン 3: データベース オブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="3da98-109">Lesson 3: Deleting Database Objects</span></span>](lesson-3-1-deleting-database-objects.md)  
  
  
