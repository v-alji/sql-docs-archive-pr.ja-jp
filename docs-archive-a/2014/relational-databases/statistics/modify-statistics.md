---
title: 統計の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6dd44da6d1a80050f37f08e49773f95af0e5a339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644376"
---
# <a name="modify-statistics"></a><span data-ttu-id="11225-102">統計の変更</span><span class="sxs-lookup"><span data-stu-id="11225-102">Modify Statistics</span></span>
  <span data-ttu-id="11225-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して既存の統計を変更できます。</span><span class="sxs-lookup"><span data-stu-id="11225-103">You can modify existing statistics in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="11225-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="11225-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="11225-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="11225-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="11225-106">Security</span><span class="sxs-lookup"><span data-stu-id="11225-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="11225-107">**統計を変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="11225-107">**To modify statistics, using:**</span></span>  
  
     [<span data-ttu-id="11225-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="11225-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="11225-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="11225-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="11225-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="11225-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="11225-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="11225-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="11225-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="11225-112">Permissions</span></span>  
 <span data-ttu-id="11225-113">以下の条件が必要です:</span><span class="sxs-lookup"><span data-stu-id="11225-113">Requires that:</span></span>  
  
-   <span data-ttu-id="11225-114">ユーザーは、テーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="11225-114">The user has ALTER permission on the table or view.</span></span>  
  
-   <span data-ttu-id="11225-115">ユーザーがテーブルまたはインデックス付きビューの所有者であるか、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、または **db_ddladmin** 固定データベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="11225-115">The user be the table or indexed view owner, or a member of one of the following roles: **sysadmin** fixed server role, **db_owner** fixed database role, or the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="11225-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="11225-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-statistics"></a><span data-ttu-id="11225-117">統計を変更するには</span><span class="sxs-lookup"><span data-stu-id="11225-117">To modify statistics</span></span>  
  
1.  <span data-ttu-id="11225-118">**オブジェクト エクスプローラー**で、統計を変更するデータベースをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="11225-118">In **Object Explorer**, click the plus sign to expand the database in which you want to modify a statistic.</span></span>  
  
2.  <span data-ttu-id="11225-119">プラス記号をクリックして **[テーブル]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="11225-119">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="11225-120">プラス記号をクリックして、統計を変更するテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="11225-120">Click the plus sign to expand the table in which you want to modify a statistic.</span></span>  
  
4.  <span data-ttu-id="11225-121">プラス記号をクリックして **[統計]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="11225-121">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="11225-122">変更する統計オブジェクトを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="11225-122">Right-click the statistics object that you wish to modify and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="11225-123">**[統計のプロパティ -**  *statistics_name*] ダイアログ ボックスの **[全般]** ページで **[追加]** 、 **[削除]** 、 **[上へ移動]** 、 **[下へ移動]** 、またはそれらを組み合わせて使い、統計のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="11225-123">In the **Statistics Properties -** *statistics_name* dialog box, on the **General** page, click **Add**, **Remove**, **Move Up**, or **Move Down**, or any combination, to alter the properties of the statistics.</span></span> <span data-ttu-id="11225-124">**[統計の列]** グリッド内の列の位置は、統計の使いやすさに影響する可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="11225-124">Remember that a column's location within the **Statistics Columns** grid can substantially impact the usefulness of the statistics.</span></span>  
  
7.  <span data-ttu-id="11225-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11225-125">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="11225-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="11225-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="11225-127">**統計を変更するには**</span><span class="sxs-lookup"><span data-stu-id="11225-127">**To modify statistics**</span></span>  
  
 <span data-ttu-id="11225-128">Transact-SQL ステートメントを使用して、このタスクを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="11225-128">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="11225-129">Transact-SQL を使用して統計を変更するには、既存の統計を削除してから新しい属性を再作成します。</span><span class="sxs-lookup"><span data-stu-id="11225-129">To modify statistics using Transact-SQL, you must first delete the existing statistic and then re-create it with new attributes.</span></span>  
  
 <span data-ttu-id="11225-130">詳細については、「[DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql)」および「[CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11225-130">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) and [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
  
