---
title: 実行プランの表示と保存 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e236ed2a298bc8fc9a829948a864f6f5c27a2ba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714230"
---
# <a name="display-and-save-execution-plans"></a><span data-ttu-id="e8575-102">実行プランの表示と保存</span><span class="sxs-lookup"><span data-stu-id="e8575-102">Display and Save Execution Plans</span></span>
  <span data-ttu-id="e8575-103">ここでは、実行プランを表示する方法、および Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して実行プランを XML 形式でファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8575-103">This section explains how to display execution plans and how to save execution plans to a file in XML format by using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e8575-104">実行プランでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーによって選択されたデータ取得方法がグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8575-104">Execution plans graphically display the data retrieval methods chosen by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer.</span></span> <span data-ttu-id="e8575-105">実行プランでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のステートメントやクエリの実行コストがアイコンで表されます。この点が、表形式で表す SET SHOWPLAN_ALL ステートメントまたは SET SHOWPLAN_TEXT ステートメントとは異なります。</span><span class="sxs-lookup"><span data-stu-id="e8575-105">Execution plans represent the execution cost of specific statements and queries in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using icons rather than the tabular representation produced by the SET SHOWPLAN_ALL or SET SHOWPLAN_TEXT statements.</span></span> <span data-ttu-id="e8575-106">グラフィカルな実行プランの表示は、クエリのパフォーマンスの特徴を理解するうえで非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e8575-106">This graphical approach is very useful for understanding the performance characteristics of a query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8575-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e8575-107">In This Section</span></span>  
  
-   [<span data-ttu-id="e8575-108">推定実行プランの表示</span><span class="sxs-lookup"><span data-stu-id="e8575-108">Display the Estimated Execution Plan</span></span>](display-the-estimated-execution-plan.md)  
  
-   [<span data-ttu-id="e8575-109">実際の実行プランの表示</span><span class="sxs-lookup"><span data-stu-id="e8575-109">Display an Actual Execution Plan</span></span>](display-an-actual-execution-plan.md)  
  
-   [<span data-ttu-id="e8575-110">XML 形式での実行プランの保存</span><span class="sxs-lookup"><span data-stu-id="e8575-110">Save an Execution Plan in XML Format</span></span>](save-an-execution-plan-in-xml-format.md)  
  
  
