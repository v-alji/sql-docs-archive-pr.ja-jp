---
title: default full-text language サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec0736326a4da0708d125bfc480996d54bb86c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632103"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a><span data-ttu-id="bd866-102">default full-text language サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="bd866-102">Configure the default full-text language Server Configuration Option</span></span>
  <span data-ttu-id="bd866-103">このトピック `default full-text language` で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、のサーバー構成オプションを構成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bd866-103">This topic describes how to configure the `default full-text language` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="bd866-104">オプションでは、 `default full-text language` フルテキストインデックスの既定の言語値を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd866-104">The `default full-text language` option specifies a default language value for full-text indexes.</span></span> <span data-ttu-id="bd866-105">言語分析は、フルテキスト インデックスが作成されるすべてのデータに対して実行され、データの言語に依存します。</span><span class="sxs-lookup"><span data-stu-id="bd866-105">Linguistic analysis is performed on all data that is full-text indexed and is dependent on the language of the data.</span></span> <span data-ttu-id="bd866-106">このオプションの既定値は、サーバーの言語です。</span><span class="sxs-lookup"><span data-stu-id="bd866-106">The default value of this option is the language of the server.</span></span> <span data-ttu-id="bd866-107">のローカライズ版では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 適切な一致が存在する場合、セットアップによって `default full-text language` オプションがサーバーの言語に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd866-107">For a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup sets the `default full-text language` option to the language of the server if an appropriate match exists.</span></span> <span data-ttu-id="bd866-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズされていないバージョンでは、`default full-text language` オプションは英語になります。</span><span class="sxs-lookup"><span data-stu-id="bd866-108">For a non-localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the `default full-text language` option is English.</span></span>  
  
 <span data-ttu-id="bd866-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="bd866-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bd866-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="bd866-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bd866-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="bd866-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bd866-112">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="bd866-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="bd866-113">Security</span><span class="sxs-lookup"><span data-stu-id="bd866-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bd866-114">**以下を使用して default full-text language オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="bd866-114">**To configure the default full-text language option, using:**</span></span>  
  
     [<span data-ttu-id="bd866-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd866-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bd866-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd866-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="bd866-117">**補足情報:** [default full-text language オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="bd866-117">**Follow Up:**  [After you configure the default full-text language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bd866-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="bd866-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bd866-119">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="bd866-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bd866-120">フルテキストインデックスでは、オプションの値が使用されています。このオプションを使用し `default full-text language` て、列に言語が指定されていない場合、CREATE フルテキストインデックスまたは ALTER フルテキストインデックスステートメントの言語**language_term**オプションです。</span><span class="sxs-lookup"><span data-stu-id="bd866-120">The value of the `default full-text language` option is used in a full-text index when no language is specified for a column through the LANGUAGE **language_term** option in the CREATE FULLTEXT INDEX or ALTER FULLTEXT INDEX statements.</span></span> <span data-ttu-id="bd866-121">既定のフルテキスト言語がサポートされていない場合や、言語分析パッケージがない場合は、CREATE または ALTER 操作に失敗し、指定した言語が有効でないというエラー メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="bd866-121">If the default full-text language is not supported or the linguistic analysis package is not available, the CREATE or ALTER operation will fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will return an error message stating that the language specified is not valid.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="bd866-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bd866-122">Recommendations</span></span>  
  
-   <span data-ttu-id="bd866-123">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bd866-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="bd866-124">オプションには `default full-text language` LCID 値が必要です。</span><span class="sxs-lookup"><span data-stu-id="bd866-124">The `default full-text language` option requires an LCID value.</span></span> <span data-ttu-id="bd866-125">サポートされている LCID とその関連言語の一覧については、「 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd866-125">For a list of supported LCIDs and their related languages, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span> <span data-ttu-id="bd866-126">他の言語も独立ソフトウェア ベンダーから入手可能です。</span><span class="sxs-lookup"><span data-stu-id="bd866-126">Other languages may also be available from independent software vendors, for example.</span></span> <span data-ttu-id="bd866-127">特定の言語の方言が見つからない場合は、Full-Text Engine によって自動的にプライマリ言語に切り替えられます。</span><span class="sxs-lookup"><span data-stu-id="bd866-127">If no specific language dialect is found, the Full-Text Engine will automatically switch to the primary language.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bd866-128">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bd866-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bd866-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="bd866-129">Permissions</span></span>  
 <span data-ttu-id="bd866-130">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="bd866-130">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="bd866-131">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd866-131">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="bd866-132">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="bd866-132">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bd866-133">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="bd866-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="bd866-134">default full-text language オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="bd866-134">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="bd866-135">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd866-135">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="bd866-136">**[詳細設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd866-136">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="bd866-137">[その他] の **[既定のフルテキスト言語]** を使用して、フルテキスト インデックスが作成される列の既定の言語の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd866-137">Under Miscellaneous, use **Default Full Text Language** to specify a default language value for full-text indexed columns.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bd866-138">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="bd866-138">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="bd866-139">default full-text language オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="bd866-139">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="bd866-140">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="bd866-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd866-141">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd866-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bd866-142">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd866-142">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="bd866-143">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `default full-text` オプションの値をオランダ語 (`1043`) に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd866-143">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `default full-text` option to Dutch (`1043`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="bd866-144">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd866-144">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-full-text-language-option"></a><a name="FollowUp"></a><span data-ttu-id="bd866-145">補足情報: default full-text language オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="bd866-145">Follow Up: After you configure the default full-text language option</span></span>  
 <span data-ttu-id="bd866-146">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="bd866-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd866-147">参照</span><span class="sxs-lookup"><span data-stu-id="bd866-147">See Also</span></span>  
 <span data-ttu-id="bd866-148">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd866-148">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span></span>  
 <span data-ttu-id="bd866-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd866-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="bd866-150">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bd866-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="bd866-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd866-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="bd866-152">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bd866-152">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="bd866-153">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bd866-153">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
