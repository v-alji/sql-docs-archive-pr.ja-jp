---
title: fill factor サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fill factor option [SQL Server]
ms.assetid: b920ec34-ba8b-4bb8-af53-a3ffd06bafa6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02258c92b4a09277d371e605fd4729ba9fda3461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641866"
---
# <a name="configure-the-fill-factor-server-configuration-option"></a><span data-ttu-id="857ca-102">fill factor サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="857ca-102">Configure the fill factor Server Configuration Option</span></span>
  <span data-ttu-id="857ca-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fill factor [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="857ca-103">This topic describes how to configure the **fill factor** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="857ca-104">FILL FACTOR は、インデックス データ ストレージとパフォーマンスの微調整を行うために用意されています。</span><span class="sxs-lookup"><span data-stu-id="857ca-104">Fill factor is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="857ca-105">インデックスの作成または再構築を行うとき、各リーフ レベルのページのデータを格納する領域の割合が FILL FACTOR 値によって決まり、今後インデックスのサイズが大きくなる場合に備えて指定した残りの空き領域が予約されます。</span><span class="sxs-lookup"><span data-stu-id="857ca-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the rest as free space for future growth.</span></span> <span data-ttu-id="857ca-106">詳細については、「 [インデックスの FILL FACTOR の指定](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="857ca-106">For more information, see [Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
 <span data-ttu-id="857ca-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="857ca-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="857ca-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="857ca-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="857ca-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="857ca-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="857ca-110">Security</span><span class="sxs-lookup"><span data-stu-id="857ca-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="857ca-111">**以下を使用して fill factor オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="857ca-111">**To configure the fill factor option, using:**</span></span>  
  
     [<span data-ttu-id="857ca-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="857ca-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="857ca-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="857ca-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="857ca-114">**補足情報:** [fill factor オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="857ca-114">**Follow Up:**  [After you configure the fill factor option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="857ca-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="857ca-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="857ca-116">推奨事項</span><span class="sxs-lookup"><span data-stu-id="857ca-116">Recommendations</span></span>  
  
-   <span data-ttu-id="857ca-117">このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="857ca-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="857ca-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="857ca-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="857ca-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="857ca-119">Permissions</span></span>  
 <span data-ttu-id="857ca-120">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="857ca-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="857ca-121">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="857ca-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="857ca-122">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="857ca-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="857ca-123">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="857ca-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="857ca-124">fill factor オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="857ca-124">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="857ca-125">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="857ca-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="857ca-126">**[データベースの設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="857ca-126">Click the **Database Settings** node.</span></span>  
  
3.  <span data-ttu-id="857ca-127">**[既定のインデックス FILL FACTOR]** ボックスに、必要なインデックス FILL FACTOR を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="857ca-127">In the **Default index fill factor** box, type or select the index fill factor that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="857ca-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="857ca-128">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="857ca-129">fill factor オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="857ca-129">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="857ca-130">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="857ca-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="857ca-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="857ca-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="857ca-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="857ca-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="857ca-133">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `fill factor` オプションの値を `100`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="857ca-133">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `fill factor` option to `100`.</span></span>  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="857ca-134">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="857ca-134">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-fill-factor-option"></a><a name="FollowUp"></a><span data-ttu-id="857ca-135">補足情報: fill factor オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="857ca-135">Follow Up: After you configure the fill factor option</span></span>  
 <span data-ttu-id="857ca-136">設定を有効にするには、サーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="857ca-136">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857ca-137">参照</span><span class="sxs-lookup"><span data-stu-id="857ca-137">See Also</span></span>  
 <span data-ttu-id="857ca-138">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="857ca-138">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="857ca-139">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="857ca-139">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="857ca-140">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="857ca-140">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="857ca-141">[インデックスの FILL FACTOR の指定](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="857ca-141">[Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span></span>  
 <span data-ttu-id="857ca-142">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="857ca-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="857ca-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="857ca-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="857ca-144">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="857ca-144">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
