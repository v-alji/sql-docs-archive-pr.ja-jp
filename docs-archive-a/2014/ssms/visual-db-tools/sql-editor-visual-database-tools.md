---
title: SQL エディター (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.sqleditor
helpviewer_keywords:
- SQL Editor
- modifying triggers
- modifying functions
- modifying stored procedures
- modifying statements
- Query Designer [SQL Server], SQL Editor
- View Designer, SQL Editor
ms.assetid: 029abf7d-6414-47ca-a3a7-b3a057efb6c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf3d69608e8508fcc314fe67315de86da98ed53f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720739"
---
# <a name="sql-editor-visual-database-tools"></a><span data-ttu-id="6f08e-102">SQL エディター (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f08e-102">SQL Editor (Visual Database Tools)</span></span>
  <span data-ttu-id="6f08e-103">SQL エディターを使用すると、既存のストアド プロシージャ、関数、トリガー、および SQL スクリプトを編集できます。</span><span class="sxs-lookup"><span data-stu-id="6f08e-103">Use the SQL Editor to edit existing stored procedures, functions, triggers, and SQL scripts.</span></span> <span data-ttu-id="6f08e-104">これらのオブジェクトのいずれかを開くと、このウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="6f08e-104">This window opens when you open any of those objects.</span></span> <span data-ttu-id="6f08e-105">データ ソースに対して実行する SQL ステートメントを新しく作成する場合は、クエリ デザイナーの [SQL ペイン](visual-database-tools.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="6f08e-105">If you want to create a new SQL statement to run against your data source, use the [SQL Pane](visual-database-tools.md) of Query Designer.</span></span>  
  
 <span data-ttu-id="6f08e-106">SQL エディターには、次に示す便利な SQL テキスト編集機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="6f08e-106">The SQL editor provides many useful SQL text-editing features, including:</span></span>  
  
-   <span data-ttu-id="6f08e-107">構文エラーおよびスペル ミスを減らすために SQL のキーワードをカラーで表示するカラー コーディング。</span><span class="sxs-lookup"><span data-stu-id="6f08e-107">Color coding of SQL keywords to minimize syntax and spelling errors.</span></span>  
  
-   <span data-ttu-id="6f08e-108">スケルトンのストアド プロシージャおよびトリガーの生成。</span><span class="sxs-lookup"><span data-stu-id="6f08e-108">Generating skeletal stored procedures and triggers.</span></span>  
  
-   <span data-ttu-id="6f08e-109">切り取り、コピー、貼り付け、ドラッグなどの便利な編集機能。</span><span class="sxs-lookup"><span data-stu-id="6f08e-109">Providing useful editing functions, including cut, copy, paste, and dragging operations.</span></span>  
  
-   <span data-ttu-id="6f08e-110">**[ツール]** メニューの **[オプション]** によるエディターの動作の変更。仮想空間、ワード ラップ、行番号、およびタブ サイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="6f08e-110">Changing the editor's behavior (by selecting **Options** from the **Tools** menu) to modify virtual spaces, word wrap, line numbers, and tab size.</span></span>  
  
-   <span data-ttu-id="6f08e-111">デバッグ用のブレークポイントの管理機能。</span><span class="sxs-lookup"><span data-stu-id="6f08e-111">Helping manage debugging breakpoints.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f08e-112">SQL エディターでは、IntelliSense のプロンプトは機能しません。</span><span class="sxs-lookup"><span data-stu-id="6f08e-112">The SQL Editor does not have IntelliSense prompting.</span></span>  
  
 <span data-ttu-id="6f08e-113">SQL ステートメントを編集するときは、細い線の枠で囲まれた Transact-SQL ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="6f08e-113">When editing SQL statements, certain Transact-SQL statements are enclosed in a box surrounded by a thin line.</span></span> <span data-ttu-id="6f08e-114">この枠によって、SQL コードを視覚的に複数のコマンド セクションに分類できます。また、クエリ デザイナーでグラフィカルにデザインできる SQL ステートメントのブロックを識別できます。</span><span class="sxs-lookup"><span data-stu-id="6f08e-114">This helps to visually break the SQL code into command sections, and identifies blocks of SQL statements that can be graphically designed using Query Designer.</span></span> <span data-ttu-id="6f08e-115">クエリ デザイナーの使用の詳細については、「 [クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](design-queries-and-views-how-to-topics-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f08e-115">For more information on using Query Designer, see [Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f08e-116">参照</span><span class="sxs-lookup"><span data-stu-id="6f08e-116">See Also</span></span>  
 [<span data-ttu-id="6f08e-117">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f08e-117">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
