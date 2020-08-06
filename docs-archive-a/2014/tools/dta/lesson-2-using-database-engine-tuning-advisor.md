---
title: 'レッスン 2: データベース エンジン チューニング アドバイザーの使用 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 3317d4f8-ed9e-4f2e-b5f1-a6bf3a9d6c8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ba0fc551fad5c67efa4dab2db27059e6946827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719202"
---
# <a name="lesson-2-using-database-engine-tuning-advisor"></a><span data-ttu-id="63b05-102">レッスン 2: データベース エンジン チューニング アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="63b05-102">Lesson 2: Using Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="63b05-103">データベース エンジン チューニング アドバイザーでは、データベースをチューニングできるほか、チューニング セッションを管理し、チューニング推奨設定を表示できます。</span><span class="sxs-lookup"><span data-stu-id="63b05-103">Database Engine Tuning Advisor enables you to tune databases, manage tuning sessions, and view tuning recommendations.</span></span> <span data-ttu-id="63b05-104">物理的な設計構造についての高度な知識があれば、このツールを使用して予備的なデータベース チューニング分析を実行できます。</span><span class="sxs-lookup"><span data-stu-id="63b05-104">Users with advanced knowledge of physical design structures can use this tool to perform exploratory database tuning analysis.</span></span> <span data-ttu-id="63b05-105">また、データベース チューニングの知識があまりない場合でも、チューニングするワークロードに最適な物理設計構造を見つけられます。</span><span class="sxs-lookup"><span data-stu-id="63b05-105">Database tuning novices can also use the tool to find the best configuration of physical design structures for the workloads they tune.</span></span> <span data-ttu-id="63b05-106">データベース エンジン チューニング アドバイザーのグラフィカル ユーザー インターフェイスを初めて使用するデータベース管理者、および物理設計構造についての広範な知識をお持ちでないシステム管理者のために、このレッスンでは基本的な操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="63b05-106">This lesson provides basic practice for database administrators who are new to the Database Engine Tuning Advisor graphical user interface and for system administrators who may not have extensive knowledge of physical design structures.</span></span>  
  
 <span data-ttu-id="63b05-107">ここで説明する内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="63b05-107">It contains the following topics:</span></span>  
  
-   <span data-ttu-id="63b05-108">ワークロードのチューニング</span><span class="sxs-lookup"><span data-stu-id="63b05-108">Tuning a Workload</span></span>  
  
-   <span data-ttu-id="63b05-109">チューニング推奨設定の表示</span><span class="sxs-lookup"><span data-stu-id="63b05-109">Viewing Tuning Recommendations</span></span>  
  
-   <span data-ttu-id="63b05-110">チューニング レポートの表示</span><span class="sxs-lookup"><span data-stu-id="63b05-110">Viewing Tuning Reports</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="63b05-111">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="63b05-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="63b05-112">ワークロードのチューニング</span><span class="sxs-lookup"><span data-stu-id="63b05-112">Tuning a Workload</span></span>](lesson-1-1-tuning-a-workload.md)  
  
  
