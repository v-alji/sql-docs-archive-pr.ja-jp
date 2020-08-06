---
title: user options サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- global default for all users [SQL Server]
- users [SQL Server], global defaults
- user options option [SQL Server]
ms.assetid: cfed8f86-6bcf-4b90-88eb-9656e22d5dc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7ee40d0f6de532b93ce9d8075b609c80f09df7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740423"
---
# <a name="configure-the-user-options-server-configuration-option"></a><span data-ttu-id="d1d97-102">user options サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="d1d97-102">Configure the user options Server Configuration Option</span></span>
  <span data-ttu-id="d1d97-103">このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user options [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-103">This topic describes how to configure the **user options** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d1d97-104">**user options** オプションは、すべてのユーザーに対するグローバルな既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-104">The **user options** option specifies global defaults for all users.</span></span> <span data-ttu-id="d1d97-105">ユーザーの作業セッション中に、一連の既定のクエリ処理オプションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="d1d97-105">A list of default query processing options is established for the duration of a user's work session.</span></span> <span data-ttu-id="d1d97-106">**user options** オプションを使用すると、SET オプションの既定値を変更できます (サーバーの既定の設定が適切でない場合)。</span><span class="sxs-lookup"><span data-stu-id="d1d97-106">The **user options** option allows you to change the default values of the SET options (if the server's default settings are not appropriate).</span></span>  
  
 <span data-ttu-id="d1d97-107">各ユーザーは、SET ステートメントを使用してこれらの既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d1d97-107">A user can override these defaults by using the SET statement.</span></span> <span data-ttu-id="d1d97-108">新しいログインについては **user options** を動的に構成できます。</span><span class="sxs-lookup"><span data-stu-id="d1d97-108">You can configure **user options** dynamically for new logins.</span></span> <span data-ttu-id="d1d97-109">**user options**の設定を変更した場合、新しい設定は新しいログイン セッションで使用され、現在のログイン セッションには影響しません。</span><span class="sxs-lookup"><span data-stu-id="d1d97-109">After you change the setting of **user options**, new login sessions use the new setting; current login sessions are not affected.</span></span>  
  
 <span data-ttu-id="d1d97-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d1d97-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d1d97-111">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d1d97-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d1d97-112">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="d1d97-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d1d97-113">Security</span><span class="sxs-lookup"><span data-stu-id="d1d97-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d1d97-114">**user connections 構成オプションを構成する方法:**</span><span class="sxs-lookup"><span data-stu-id="d1d97-114">**To configure the user options configuration option, using:**</span></span>  
  
     [<span data-ttu-id="d1d97-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d1d97-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d1d97-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d1d97-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d1d97-117">**補足情報:** [user options 構成オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d1d97-117">**Follow Up:**  [After you configure the user options configuration option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d1d97-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="d1d97-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d1d97-119">推奨事項</span><span class="sxs-lookup"><span data-stu-id="d1d97-119">Recommendations</span></span>  
  
-   <span data-ttu-id="d1d97-120">次の表は、 **user options**の構成値と説明の一覧です。</span><span class="sxs-lookup"><span data-stu-id="d1d97-120">The following table lists and describes the configuration values for **user options**.</span></span> <span data-ttu-id="d1d97-121">すべての構成値が他の構成値と両立するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d1d97-121">Not all configuration values are compatible with each other.</span></span> <span data-ttu-id="d1d97-122">たとえば、ANSI_NULL_DFLT_ON と ANSI_NULL_DFLT_OFF を同時に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d1d97-122">For example, ANSI_NULL_DFLT_ON and ANSI_NULL_DFLT_OFF cannot be set at the same time.</span></span>  
  
    |<span data-ttu-id="d1d97-123">値</span><span class="sxs-lookup"><span data-stu-id="d1d97-123">Value</span></span>|<span data-ttu-id="d1d97-124">構成</span><span class="sxs-lookup"><span data-stu-id="d1d97-124">Configuration</span></span>|<span data-ttu-id="d1d97-125">説明</span><span class="sxs-lookup"><span data-stu-id="d1d97-125">Description</span></span>|  
    |-----------|-------------------|-----------------|  
    |<span data-ttu-id="d1d97-126">1</span><span class="sxs-lookup"><span data-stu-id="d1d97-126">1</span></span>|<span data-ttu-id="d1d97-127">DISABLE_DEF_CNST_CHK</span><span class="sxs-lookup"><span data-stu-id="d1d97-127">DISABLE_DEF_CNST_CHK</span></span>|<span data-ttu-id="d1d97-128">中間制約チェックまたは遅延制約チェックを制御します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-128">Controls interim or deferred constraint checking.</span></span>|  
    |<span data-ttu-id="d1d97-129">2</span><span class="sxs-lookup"><span data-stu-id="d1d97-129">2</span></span>|<span data-ttu-id="d1d97-130">IMPLICIT_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="d1d97-130">IMPLICIT_TRANSACTIONS</span></span>|<span data-ttu-id="d1d97-131">dblib ネットワーク ライブラリ接続の場合、ステートメントの実行時にトランザクションを暗黙的に開始するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-131">For dblib network library connections, controls whether a transaction is started implicitly when a statement is executed.</span></span> <span data-ttu-id="d1d97-132">IMPLICIT_TRANSACTIONS の設定は、ODBC または OLEDB 接続には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="d1d97-132">The IMPLICIT_TRANSACTIONS setting has no effect on ODBC or OLEDB connections.</span></span>|  
    |<span data-ttu-id="d1d97-133">4</span><span class="sxs-lookup"><span data-stu-id="d1d97-133">4</span></span>|<span data-ttu-id="d1d97-134">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="d1d97-134">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="d1d97-135">コミット実行後のカーソルの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-135">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
    |<span data-ttu-id="d1d97-136">8</span><span class="sxs-lookup"><span data-stu-id="d1d97-136">8</span></span>|<span data-ttu-id="d1d97-137">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="d1d97-137">ANSI_WARNINGS</span></span>|<span data-ttu-id="d1d97-138">集計警告の切り詰めと NULL を制御します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-138">Controls truncation and NULL in aggregate warnings.</span></span>|  
    |<span data-ttu-id="d1d97-139">16</span><span class="sxs-lookup"><span data-stu-id="d1d97-139">16</span></span>|<span data-ttu-id="d1d97-140">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="d1d97-140">ANSI_PADDING</span></span>|<span data-ttu-id="d1d97-141">固定長変数の埋め込みを制御します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-141">Controls padding of fixed-length variables.</span></span>|  
    |<span data-ttu-id="d1d97-142">32</span><span class="sxs-lookup"><span data-stu-id="d1d97-142">32</span></span>|<span data-ttu-id="d1d97-143">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="d1d97-143">ANSI_NULLS</span></span>|<span data-ttu-id="d1d97-144">等価演算を使用する場合に NULL 処理を制御します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-144">Controls NULL handling when using equality operators.</span></span>|  
    |<span data-ttu-id="d1d97-145">64</span><span class="sxs-lookup"><span data-stu-id="d1d97-145">64</span></span>|<span data-ttu-id="d1d97-146">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="d1d97-146">ARITHABORT</span></span>|<span data-ttu-id="d1d97-147">クエリ実行中にオーバーフローまたは 0 除算のエラーが発生した場合に、クエリを終了します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-147">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
    |<span data-ttu-id="d1d97-148">128</span><span class="sxs-lookup"><span data-stu-id="d1d97-148">128</span></span>|<span data-ttu-id="d1d97-149">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="d1d97-149">ARITHIGNORE</span></span>|<span data-ttu-id="d1d97-150">クエリ実行中にオーバーフローまたは 0 除算エラーが発生した場合に、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-150">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
    |<span data-ttu-id="d1d97-151">256</span><span class="sxs-lookup"><span data-stu-id="d1d97-151">256</span></span>|<span data-ttu-id="d1d97-152">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="d1d97-152">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="d1d97-153">式を評価するときに、単一引用符と二重引用符を区別します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-153">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
    |<span data-ttu-id="d1d97-154">512</span><span class="sxs-lookup"><span data-stu-id="d1d97-154">512</span></span>|<span data-ttu-id="d1d97-155">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="d1d97-155">NOCOUNT</span></span>|<span data-ttu-id="d1d97-156">各ステートメントの最後に返される、何行処理されたかを示すメッセージを表示しないようにします。</span><span class="sxs-lookup"><span data-stu-id="d1d97-156">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
    |<span data-ttu-id="d1d97-157">1024</span><span class="sxs-lookup"><span data-stu-id="d1d97-157">1024</span></span>|<span data-ttu-id="d1d97-158">ANSI_NULL_DFLT_ON</span><span class="sxs-lookup"><span data-stu-id="d1d97-158">ANSI_NULL_DFLT_ON</span></span>|<span data-ttu-id="d1d97-159">ANSI 互換の NULL 値の許可属性を使用するようにセッションの動作を変更します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-159">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="d1d97-160">新しい列で、NULL 値を許可するかどうかが明示的に定義されていない場合は、NULL 値を許可するように定義されます。</span><span class="sxs-lookup"><span data-stu-id="d1d97-160">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
    |<span data-ttu-id="d1d97-161">2048</span><span class="sxs-lookup"><span data-stu-id="d1d97-161">2048</span></span>|<span data-ttu-id="d1d97-162">ANSI_NULL_DFLT_OFF</span><span class="sxs-lookup"><span data-stu-id="d1d97-162">ANSI_NULL_DFLT_OFF</span></span>|<span data-ttu-id="d1d97-163">ANSI 互換の NULL 値の許可属性を使用しないようにセッションの動作を変更します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-163">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="d1d97-164">新しい列で、NULL 値を許可するかどうかが明示的に定義されていない場合は、NULL 値が許可されません。</span><span class="sxs-lookup"><span data-stu-id="d1d97-164">New columns defined without explicit nullability do not allow nulls.</span></span>|  
    |<span data-ttu-id="d1d97-165">4096</span><span class="sxs-lookup"><span data-stu-id="d1d97-165">4096</span></span>|<span data-ttu-id="d1d97-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="d1d97-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="d1d97-167">NULL 値を文字列と連結した場合に、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-167">Returns NULL when concatenating a NULL value with a string.</span></span>|  
    |<span data-ttu-id="d1d97-168">8192</span><span class="sxs-lookup"><span data-stu-id="d1d97-168">8192</span></span>|<span data-ttu-id="d1d97-169">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="d1d97-169">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="d1d97-170">式の精度が低下した場合にエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-170">Generates an error when a loss of precision occurs in an expression.</span></span>|  
    |<span data-ttu-id="d1d97-171">16384</span><span class="sxs-lookup"><span data-stu-id="d1d97-171">16384</span></span>|<span data-ttu-id="d1d97-172">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="d1d97-172">XACT_ABORT</span></span>|<span data-ttu-id="d1d97-173">Transact-SQL ステートメントで実行時エラーが発生した場合、トランザクションをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="d1d97-173">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
-   <span data-ttu-id="d1d97-174">**user options** のビット位置は、@@OPTIONS のビット位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="d1d97-174">The bit positions in **user options** are identical to those in @@OPTIONS.</span></span> <span data-ttu-id="d1d97-175">接続にはそれぞれの構成環境を表す @@OPTIONS 関数があります。</span><span class="sxs-lookup"><span data-stu-id="d1d97-175">Each connection has its own @@OPTIONS function, which represents the configuration environment.</span></span> <span data-ttu-id="d1d97-176">\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにログインすると、ユーザーは **user options** の現在の値が @@OPTIONS に代入される既定の環境を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d1d97-176">When logging in to an instance of \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a user receives a default environment that assigns the current **user options** value to @@OPTIONS.</span></span> <span data-ttu-id="d1d97-177">**user options** について SET ステートメントを実行すると、そのセッションの @@OPTIONS 関数の対応する値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d1d97-177">Executing SET statements for **user options** affects the corresponding value in the session's @@OPTIONS function.</span></span> <span data-ttu-id="d1d97-178">この設定の変更後に作成された接続は、すべて新しい値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d1d97-178">All connections created after this setting is changed receive the new value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d1d97-179">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d1d97-179">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d1d97-180">Permissions</span><span class="sxs-lookup"><span data-stu-id="d1d97-180">Permissions</span></span>  
 <span data-ttu-id="d1d97-181">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="d1d97-181">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="d1d97-182">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1d97-182">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="d1d97-183">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="d1d97-183">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d1d97-184">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d1d97-184">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="d1d97-185">user connections 構成オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="d1d97-185">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="d1d97-186">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1d97-186">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="d1d97-187">**[接続]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1d97-187">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="d1d97-188">**[既定の接続オプション]** ボックスで、1 つ以上の属性を選択し、すべての接続済みユーザーの既定のクエリ処理オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-188">In the **Default connection options** box, select one or more attributes to configure the default query-processing options for all connected users.</span></span>  
  
     <span data-ttu-id="d1d97-189">既定では、ユーザー オプションは構成されていません。</span><span class="sxs-lookup"><span data-stu-id="d1d97-189">By default, no user options are configured.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d1d97-190">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d1d97-190">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="d1d97-191">user connections 構成オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="d1d97-191">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="d1d97-192">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="d1d97-192">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d1d97-193">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1d97-193">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d1d97-194">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1d97-194">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d1d97-195">次の例は、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、ANSI_WARNINGS サーバー オプションの設定を変更する `user options` を構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1d97-195">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `user options` to change the setting for the ANSI_WARNINGS server option.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'user options', 8 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-user-options-configuration-option"></a><a name="FollowUp"></a><span data-ttu-id="d1d97-196">補足情報: user options 構成オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="d1d97-196">Follow Up: After you configure the user options configuration option</span></span>  
 <span data-ttu-id="d1d97-197">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="d1d97-197">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d97-198">参照</span><span class="sxs-lookup"><span data-stu-id="d1d97-198">See Also</span></span>  
 <span data-ttu-id="d1d97-199">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1d97-199">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="d1d97-200">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1d97-200">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="d1d97-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1d97-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="d1d97-202">SET ステートメント &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d97-202">SET Statements &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statements-transact-sql)  
  
  
