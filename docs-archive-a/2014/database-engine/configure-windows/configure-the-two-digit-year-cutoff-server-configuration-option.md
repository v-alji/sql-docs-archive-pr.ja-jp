---
title: two digit year cutoff サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c31c1d87c8b743132dd90d495f73ef711dc1f813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634623"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a><span data-ttu-id="136af-102">two digit year cutoff サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="136af-102">Configure the two digit year cutoff Server Configuration Option</span></span>
  <span data-ttu-id="136af-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] two digit year cutoff [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="136af-103">This topic describes how to configure the **two digit year cutoff** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="136af-104">**two digit year cutoff** オプションでは、2 桁の年を 4 桁の西暦年として解釈する場合に世紀の区切りとする年 (終了年) を 1753 ～ 9999 の整数で指定します。</span><span class="sxs-lookup"><span data-stu-id="136af-104">The **two digit year cutoff** option specifies an integer from 1753 to 9999 that represents the cutoff year for interpreting two-digit years as four-digit years.</span></span> <span data-ttu-id="136af-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の期間は 1950 ～ 2049 です。これは、終了年が 2049 であることを表します。</span><span class="sxs-lookup"><span data-stu-id="136af-105">The default time span for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 1950-2049, which represents a cutoff year of 2049.</span></span> <span data-ttu-id="136af-106">つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、2 桁表記が 49 であれば 2049 年、50 は 1950 年、99 は 1999 年と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="136af-106">This means that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets a two-digit year of 49 as 2049, a two-digit year of 50 as 1950, and a two-digit year of 99 as 1999.</span></span> <span data-ttu-id="136af-107">旧バージョンとの互換性を保つため、この設定は既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="136af-107">To maintain backward compatibility, leave the setting at the default value.</span></span>  
  
 <span data-ttu-id="136af-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="136af-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="136af-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="136af-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="136af-110">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="136af-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="136af-111">Security</span><span class="sxs-lookup"><span data-stu-id="136af-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="136af-112">**以下を使用して two digit year cutoff オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="136af-112">**To configure the two digit year cutoff option, using:**</span></span>  
  
     [<span data-ttu-id="136af-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="136af-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="136af-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="136af-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="136af-115">**補足情報:** [two digit year cutoff オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="136af-115">**Follow Up:**  [After you configure the two digit year cutoff option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="136af-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="136af-116">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="136af-117">推奨事項</span><span class="sxs-lookup"><span data-stu-id="136af-117">Recommendations</span></span>  
  
-   <span data-ttu-id="136af-118">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="136af-118">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="136af-119">OLE オートメーション オブジェクトでは、2 桁の西暦の終了年として 2030 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="136af-119">OLE Automation objects use 2030 as the two-digit cutoff year.</span></span> <span data-ttu-id="136af-120">**two digit year cutoff** オプションを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とクライアント アプリケーションの間で日付値を一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="136af-120">You can use the **two digit year cutoff** option to provide consistency in date values between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and client applications.</span></span> <span data-ttu-id="136af-121">ただし、あいまいな日付で混乱するのを防ぐために、2 桁より 4 桁で年を表記することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="136af-121">However, to avoid ambiguity with dates, use four-digit years in your data.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="136af-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="136af-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="136af-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="136af-123">Permissions</span></span>  
 <span data-ttu-id="136af-124">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="136af-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="136af-125">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="136af-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="136af-126">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="136af-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="136af-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="136af-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="136af-128">two digit year cutoff オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="136af-128">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="136af-129">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="136af-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="136af-130">**[その他のサーバーの設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="136af-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="136af-131">**[2 桁の年のサポート]** の **[2 桁の年を** **以下の間にある年として解釈]** ボックスに、期間の終了する年を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="136af-131">Under **Two digit year support**, in the **When a two digit year is entered**, **interpret it as a year between** box, type or select a value that is the ending year of the time span.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="136af-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="136af-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="136af-133">two digit year cutoff オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="136af-133">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="136af-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="136af-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="136af-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="136af-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="136af-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="136af-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="136af-137">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `two digit year cutoff` オプションの値を `2030`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="136af-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `two digit year cutoff` option to `2030`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="136af-138">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="136af-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-two-digit-year-cutoff-option"></a><a name="FollowUp"></a><span data-ttu-id="136af-139">補足情報: two digit year cutoff オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="136af-139">Follow Up: After you configure the two digit year cutoff option</span></span>  
 <span data-ttu-id="136af-140">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="136af-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136af-141">参照</span><span class="sxs-lookup"><span data-stu-id="136af-141">See Also</span></span>  
 <span data-ttu-id="136af-142">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="136af-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="136af-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="136af-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="136af-144">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="136af-144">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
