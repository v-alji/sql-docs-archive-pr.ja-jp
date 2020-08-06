---
title: 対象サーバー&#39;の場所を指定します (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], location
ms.assetid: 511ff311-21f5-4f2f-839f-b4deee26ec98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 938528ab78f0f457cde69d8fd4d5432cc14a79b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643068"
---
# <a name="specify-a-target-server39s-location-sql-server-management-studio"></a><span data-ttu-id="ed655-102">ターゲット サーバーの場所を指定する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ed655-102">Specify a Target Server&#39;s Location (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ed655-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のマルチサーバー管理の構成でターゲット サーバーの場所を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed655-103">This topic describes how to specify the location of a target server in a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ed655-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ed655-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ed655-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ed655-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ed655-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ed655-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ed655-107">Security</span><span class="sxs-lookup"><span data-stu-id="ed655-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ed655-108">**ターゲット サーバーの場所を指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="ed655-108">**To specify a target server's location, using:**</span></span>  
  
     [<span data-ttu-id="ed655-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed655-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ed655-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed655-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ed655-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="ed655-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ed655-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="ed655-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ed655-113">このアクションを実行すると、レジストリが編集されます。</span><span class="sxs-lookup"><span data-stu-id="ed655-113">Performing this action edits the registry.</span></span> <span data-ttu-id="ed655-114">レジストリは手動で編集しないでください。不適切または不正確な変更を加えると、システム構成に重大な問題が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed655-114">Manual editing of the registry is not recommended because inappropriate or incorrect changes can cause serious configuration problems for your system.</span></span> <span data-ttu-id="ed655-115">熟練したユーザーのみがレジストリ エディターを使用してレジストリを編集することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed655-115">Therefore, only experienced users should use the Registry Editor program to edit the registry.</span></span> <span data-ttu-id="ed655-116">詳細については、Microsoft Windows のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed655-116">For more information, see the Microsoft Windows documentation.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ed655-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ed655-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ed655-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="ed655-118">Permissions</span></span>  
 <span data-ttu-id="ed655-119">**sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ed655-119">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ed655-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ed655-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="ed655-121">ターゲット サーバーの場所を指定するには</span><span class="sxs-lookup"><span data-stu-id="ed655-121">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="ed655-122">**オブジェクト エクスプローラー**で、ターゲット サーバーの場所として指定するマスター サーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="ed655-122">In **Object Explorer**, click the plus sign to expand the master server on which you want to specify a target server's location.</span></span>  
  
2.  <span data-ttu-id="ed655-123">**[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed655-123">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="ed655-124">ターゲット サーバーを右クリックし、**[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed655-124">Right-click a target server and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="ed655-125">**[場所]** ボックスにサーバーの場所を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed655-125">In the **Location** box, enter a location for the server, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ed655-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ed655-126">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="ed655-127">ターゲット サーバーの場所を指定するには</span><span class="sxs-lookup"><span data-stu-id="ed655-127">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="ed655-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ed655-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ed655-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed655-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ed655-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed655-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- enlists the current server into the AdventureWorks1 master server.   
    -- The location for the current server is Building 21, Room 309, Rack 5  
    EXEC dbo.sp_msx_enlist N'AdventureWorks2012',   
        N'Building 21, Room 309, Rack 5' ;  
    GO  
    ```  
  
 <span data-ttu-id="ed655-131">詳細については、「 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed655-131">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
  
