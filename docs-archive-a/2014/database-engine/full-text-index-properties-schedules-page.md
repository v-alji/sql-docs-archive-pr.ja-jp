---
title: '[フルテキストインデックスのプロパティ] ([スケジュール] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.schedule.f1
ms.assetid: a828e284-097e-4854-8c49-931934eb73bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f49fb37295f0b3eb2f1a2dd04d44ab86236f109a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645801"
---
# <a name="full-text-index-properties-schedules-page"></a><span data-ttu-id="3a251-102">[フルテキスト インデックスのプロパティ] ([スケジュール] ページ)</span><span class="sxs-lookup"><span data-stu-id="3a251-102">Full-Text Index Properties (Schedules Page)</span></span>
  <span data-ttu-id="3a251-103">このページでは、フルテキスト インデックスのベース テーブルに対する更新の増分作成を開始する SQL Server エージェント ジョブの実行スケジュールを表示および作成できます。</span><span class="sxs-lookup"><span data-stu-id="3a251-103">Use this page to view and create schedules for running a SQL Server Agent job that starts an incremental population of updates to the base table of the full-text index.</span></span> <span data-ttu-id="3a251-104">ベース テーブルまたはビューに `timestamp` データ型の列が含まれていない場合は、完全作成が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3a251-104">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
 <span data-ttu-id="3a251-105">**フルテキスト インデックスのプロパティを表示または変更するには**</span><span class="sxs-lookup"><span data-stu-id="3a251-105">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="3a251-106">フルテキスト インデックスの管理</span><span class="sxs-lookup"><span data-stu-id="3a251-106">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="3a251-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="3a251-107">UI element list</span></span>  
 <span data-ttu-id="3a251-108">**スケジュール**</span><span class="sxs-lookup"><span data-stu-id="3a251-108">**Schedules**</span></span>  
 <span data-ttu-id="3a251-109">フルテキスト インデックスのベース テーブルに対するスケジュールされた増分作成を一覧表示します (スケジュールされた増分作成が存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="3a251-109">Lists each scheduled incremental population, if any, on the base table for the full-text index.</span></span>  
  
 <span data-ttu-id="3a251-110">**名前**</span><span class="sxs-lookup"><span data-stu-id="3a251-110">**Name**</span></span>  
 <span data-ttu-id="3a251-111">スケジュールされた各作成の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="3a251-111">Displays the name of the each scheduled population.</span></span>  
  
 <span data-ttu-id="3a251-112">**[作成の種類]**</span><span class="sxs-lookup"><span data-stu-id="3a251-112">**Population Type**</span></span>  
 <span data-ttu-id="3a251-113">スケジュールされた各作成の種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="3a251-113">Displays the type of each scheduled population.</span></span>  
  
 <span data-ttu-id="3a251-114">**有効**</span><span class="sxs-lookup"><span data-stu-id="3a251-114">**Enabled**</span></span>  
 <span data-ttu-id="3a251-115">スケジュールされた作成が現在有効か無効かを示します。</span><span class="sxs-lookup"><span data-stu-id="3a251-115">Indicates whether the scheduled population is currently enabled or disabled.</span></span>  
  
 <span data-ttu-id="3a251-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="3a251-116">**Description**</span></span>  
 <span data-ttu-id="3a251-117">スケジュールの作成時に指定された説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="3a251-117">Displays the description that was specified when the schedule was created.</span></span>  
  
 <span data-ttu-id="3a251-118">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="3a251-118">**New**</span></span>  
 <span data-ttu-id="3a251-119">フルテキスト インデックスの作成スケジュールを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="3a251-119">Click to create a new schedule for populating the full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a251-120">参照</span><span class="sxs-lookup"><span data-stu-id="3a251-120">See Also</span></span>  
 <span data-ttu-id="3a251-121">[フルテキストインデックス作成ウィザードの使用](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3a251-121">[Use the Full-Text Indexing Wizard](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="3a251-122">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="3a251-122">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
