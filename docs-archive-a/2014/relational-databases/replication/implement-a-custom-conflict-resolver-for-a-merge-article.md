---
title: マージ アーティクルのカスタム競合回避モジュールの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e684213114f3c9bb2f1ad56de06fcfc89b819a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632341"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a><span data-ttu-id="d469f-102">マージ アーティクルのカスタム競合回避モジュールの実装</span><span class="sxs-lookup"><span data-stu-id="d469f-102">Implement a Custom Conflict Resolver for a Merge Article</span></span>
  <span data-ttu-id="d469f-103"> このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)] または [COM ベースのカスタム競合回避モジュール](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)を使用して、マージ アーティクルのカスタム競合回避モジュールを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d469f-103">This topic describes how to implement custom conflict resolver for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or a [COM-based custom resolver](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
 <span data-ttu-id="d469f-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d469f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d469f-105">**マージ アーティクルのカスタム競合回避モジュールを実装するためにに使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="d469f-105">**To implement custom conflict resolver for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="d469f-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d469f-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="d469f-107">COM ベースの競合回避モジュール</span><span class="sxs-lookup"><span data-stu-id="d469f-107">COM-based Resolver</span></span>](#COM)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d469f-108">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d469f-108">Using Transact-SQL</span></span>  
 <span data-ttu-id="d469f-109">各パブリッシャーで、固有のカスタム競合回避モジュールを [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャとして記述できます。</span><span class="sxs-lookup"><span data-stu-id="d469f-109">You can write your own custom conflict resolver as a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure at each Publisher.</span></span> <span data-ttu-id="d469f-110">同期中に、このストアド プロシージャは、競合回避モジュールが登録されているアーティクル内で競合が発生した場合に呼び出されます。競合する行の情報は、マージ エージェントによってプロシージャの必須パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d469f-110">During synchronization, this stored procedure is invoked when conflicts are encountered in an article to which the resolver was registered, and information on the conflict row is passed by the Merge Agent to the required parameters of the procedure.</span></span> <span data-ttu-id="d469f-111">ストアド プロシージャ ベースのカスタム競合回避モジュールは、常にパブリッシャーで作成されます。</span><span class="sxs-lookup"><span data-stu-id="d469f-111">Stored procedure-based custom conflict resolvers are always created at the Publisher.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="d469f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアドプロシージャ競合回避モジュールは、行の変更に基づく競合を処理するためにのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d469f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure resolvers are only invoked to handle row change-based conflicts.</span></span> <span data-ttu-id="d469f-113">このモジュールは、他の種類の競合 (PRIMARY KEY 違反による挿入の失敗や一意インデックス制約違反) の処理には使用できません。</span><span class="sxs-lookup"><span data-stu-id="d469f-113">They cannot be used to handle other types of conflicts such as insert failures due to PRIMARY KEY violations or unique index constraint violations.</span></span>  
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a><span data-ttu-id="d469f-114">ストアド プロシージャ ベースのカスタム競合回避モジュールを作成するには</span><span class="sxs-lookup"><span data-stu-id="d469f-114">To create a stored procedure-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="d469f-115">パブリッシャーのパブリケーションまたは **msdb** データベースで、次の必須パラメーターを実装する新しいシステム ストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="d469f-115">At the Publisher in either the publication or **msdb** database, create a new system stored procedure that implements the following required parameters:</span></span>  
  
    |<span data-ttu-id="d469f-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d469f-116">Parameter</span></span>|<span data-ttu-id="d469f-117">データ型</span><span class="sxs-lookup"><span data-stu-id="d469f-117">Data type</span></span>|<span data-ttu-id="d469f-118">説明</span><span class="sxs-lookup"><span data-stu-id="d469f-118">Description</span></span>|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|`sysname`|<span data-ttu-id="d469f-119">競合を解決する対象のテーブルの所有者名。</span><span class="sxs-lookup"><span data-stu-id="d469f-119">Name of the owner of the table for which a conflict is being resolved.</span></span> <span data-ttu-id="d469f-120">これは、パブリケーション データベース内のテーブルの所有者です。</span><span class="sxs-lookup"><span data-stu-id="d469f-120">This is the owner for the table in the publication database.</span></span>|  
    |**@tablename**|`sysname`|<span data-ttu-id="d469f-121">競合を解決する対象のテーブル名。</span><span class="sxs-lookup"><span data-stu-id="d469f-121">Name of the table for which a conflict is being resolved.</span></span>|  
    |**@rowguid**|`uniqueidentifier`|<span data-ttu-id="d469f-122">競合している行の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="d469f-122">Unique identifier for the row having the conflict.</span></span>|  
    |**@subscriber**|`sysname`|<span data-ttu-id="d469f-123">競合する変更の反映元であるサーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="d469f-123">Name of the server from where a conflicting change is being propagated.</span></span>|  
    |**@subscriber_db**|`sysname`|<span data-ttu-id="d469f-124">競合する変更の反映元であるデータベースの名前。</span><span class="sxs-lookup"><span data-stu-id="d469f-124">Name of the database from where conflicting change is being propagated.</span></span>|  
    |<span data-ttu-id="d469f-125">**@log_conflictOUTPUT**</span><span class="sxs-lookup"><span data-stu-id="d469f-125">**@log_conflict OUTPUT**</span></span>|`int`|<span data-ttu-id="d469f-126">競合を後で解決できるように、マージ処理で競合をログに記録するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d469f-126">Whether the merge process should log a conflict for later resolution:</span></span><br /><br /> <span data-ttu-id="d469f-127">**0** = 競合をログに記録しない。</span><span class="sxs-lookup"><span data-stu-id="d469f-127">**0** = Do not log the conflict.</span></span><br /><br /> <span data-ttu-id="d469f-128">**1** = サブスクライバーは競合で優先されない。</span><span class="sxs-lookup"><span data-stu-id="d469f-128">**1** = Subscriber is the conflict loser.</span></span><br /><br /> <span data-ttu-id="d469f-129">**2** = パブリッシャーは競合で優先されない。</span><span class="sxs-lookup"><span data-stu-id="d469f-129">**2** = Publisher is the conflict loser.</span></span>|  
    |<span data-ttu-id="d469f-130">**@conflict_messageOUTPUT**</span><span class="sxs-lookup"><span data-stu-id="d469f-130">**@conflict_message OUTPUT**</span></span>|`nvarchar(512)`|<span data-ttu-id="d469f-131">競合をログに記録する場合の解決に関するメッセージ。</span><span class="sxs-lookup"><span data-stu-id="d469f-131">Message to be given about the resolution if the conflict is logged.</span></span>|  
    |**@destowner**|`sysname`|<span data-ttu-id="d469f-132">サブスクライバー側でパブリッシュされたテーブルの所有者。</span><span class="sxs-lookup"><span data-stu-id="d469f-132">The owner of the published table at the Subscriber.</span></span>|  
  
     <span data-ttu-id="d469f-133">このストアド プロシージャは、マージ エージェントからパラメーターに渡された値を使用して、カスタム競合回避ロジックを実装します。このロジックでは、ベース テーブルと同じ構造を持ち、競合で優先されたバージョンの行のデータ値を含んでいる、単一行の結果セットを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d469f-133">This stored procedure uses the values passed by the Merge Agent to these parameters to implement your custom conflict resolution logic; it must return a single row result set that is identical in structure to the base table and contains the data values for the winning version of the row.</span></span>  
  
2.  <span data-ttu-id="d469f-134">サブスクライバーでパブリッシャーへの接続に使用される任意のログインに対して、ストアド プロシージャの EXECUTE 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="d469f-134">Grant EXECUTE permissions on the stored procedure to any logins used by Subscribers to connect to the Publisher.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="d469f-135">新しいテーブル アーティクルにカスタム競合回避モジュールを使用するには</span><span class="sxs-lookup"><span data-stu-id="d469f-135">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="d469f-136">\*\*\*\* パラメーターに **MicrosoftSQL@article_resolver** **Server ストアド プロシージャ競合回避モジュール**の値を、**@resolver_info** パラメーターに競合回避ロジックを実装するストアド プロシージャの名前を指定し、[sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行してアーティクルを定義します。</span><span class="sxs-lookup"><span data-stu-id="d469f-136">Execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying a value of **MicrosoftSQL** **Server Stored Procedure Resolver** for the **@article_resolver** parameter and the name of the stored procedure that implements the conflict resolver logic for the **@resolver_info** parameter.</span></span> <span data-ttu-id="d469f-137">詳しくは、「 [アーティクルを定義](publish/define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d469f-137">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="d469f-138">既存のテーブル アーティクルにカスタム競合回避モジュールを使用するには</span><span class="sxs-lookup"><span data-stu-id="d469f-138">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="d469f-139">[Sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。を指定します。には article_resolver の値を指定し、には **@publication** **@article** **article_resolver** **@property** **microsoft Sql** **Server に格納され**ている ProcedureResolver の値を指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="d469f-139">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and a value of **MicrosoftSQL** **Server Stored ProcedureResolver** for **@value**.</span></span>  
  
2.  <span data-ttu-id="d469f-140">[Sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。を指定し、に resolver_info を指定し、に **@publication** **@article** **resolver_info** **@property** 競合回避モジュールのロジックを実装するストアドプロシージャの名前を指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="d469f-140">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **resolver_info** for **@property**, and the name of the stored procedure that implements the conflict resolver logic for **@value**.</span></span>  
  
##  <a name="using-a-com-based-custom-resolver"></a><a name="COM"></a><span data-ttu-id="d469f-141">COM ベースのカスタム競合回避モジュールの使用</span><span class="sxs-lookup"><span data-stu-id="d469f-141">Using a COM-based Custom Resolver</span></span>  
 <span data-ttu-id="d469f-142"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 名前空間により実装されるインターフェイスを利用して、マージ レプリケーション同期処理で発生するイベントを処理し、競合を回避するための複雑なビジネス ロジックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d469f-142">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events and resolve conflicts that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="d469f-143">詳細については、「 [マージ アーティクルのビジネス ロジック ハンドラーの実装](implement-a-business-logic-handler-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d469f-143">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span> <span data-ttu-id="d469f-144">また、ネイティブ コード ベースのカスタム ビジネス ロジックを独自に作成して、競合を回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="d469f-144">You can also write your own native code-based custom business logic to resolve conflicts.</span></span> <span data-ttu-id="d469f-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++ などの製品を使用して、このロジックを COM コンポーネントとしてビルドし、ダイナミック リンク ライブラリ (DLL) にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d469f-145">This logic is built as a COM component and compiled into dynamic-link libraries (DLL), using products such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++.</span></span> <span data-ttu-id="d469f-146">このような COM ベースのカスタム競合回避モジュールは、競合解決のために特別に設計された**ICustomResolver**インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d469f-146">Such a COM-based custom conflict resolver must implement the **ICustomResolver** interface, which is designed specifically for conflict resolution.</span></span>  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a><span data-ttu-id="d469f-147">COM ベース カスタム競合回避モジュールを作成して登録するには</span><span class="sxs-lookup"><span data-stu-id="d469f-147">To create and register a COM-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="d469f-148">COM 互換のオーサリング環境で、カスタム競合回避モジュール ライブラリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="d469f-148">In a COM-compatible authoring environment, add references to the Custom Conflict Resolver library.</span></span>  
  
2.  <span data-ttu-id="d469f-149">Visual C++ プロジェクトの場合は、#import ディレクティブを使用してこのライブラリをプロジェクトにインポートします。</span><span class="sxs-lookup"><span data-stu-id="d469f-149">For a Visual C++ project, use the #import directive to import this library into your project.</span></span>  
  
3.  <span data-ttu-id="d469f-150">**ICustomResolver** インターフェイスを実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d469f-150">Create a class that implements the **ICustomResolver** interface.</span></span>  
  
4.  <span data-ttu-id="d469f-151">メソッドとプロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="d469f-151">Implement certain methods and properties.</span></span>  
  
5.  <span data-ttu-id="d469f-152">プロジェクトをビルドして、カスタム競合回避モジュール ライブラリ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d469f-152">Build the project to create the custom conflict resolver library file.</span></span>  
  
6.  <span data-ttu-id="d469f-153">マージ エージェントの実行可能ファイルが置かれているディレクトリ (通常は \Microsoft SQL Server\100\COM) に、そのライブラリを配置します。</span><span class="sxs-lookup"><span data-stu-id="d469f-153">Deploy the library in the directory containing the merge agent executable (usually \Microsoft SQL Server\100\COM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d469f-154">カスタム競合回避モジュールは、プル サブスクリプションの場合はサブスクライバーに、プッシュ サブスクリプションの場合はディストリビューターに、Web 同期に使用する場合は Web サーバーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d469f-154">A custom conflict resolver must be deployed at the Subscriber for a pull subscription, at the Distributor for a push subscription, or at the Web server used with Web synchronization.</span></span>  
  
7.  <span data-ttu-id="d469f-155">次のように、配置先のディレクトリから regsvr32.exe を使用してカスタム競合回避モジュール ライブラリを登録します。</span><span class="sxs-lookup"><span data-stu-id="d469f-155">Register the custom conflict resolver library using regsvr32.exe from the deployment directory as follows:</span></span>  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  <span data-ttu-id="d469f-156">パブリッシャーで [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行し、そのライブラリがカスタム競合回避モジュールとしてまだ登録されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d469f-156">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the library is not already registered as a custom conflict resolver.</span></span>  
  
9. <span data-ttu-id="d469f-157">カスタム競合回避モジュールとしてライブラリを登録するには、ディストリビューターで [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="d469f-157">To register the library as a custom conflict resolver, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), at the Distributor.</span></span> <span data-ttu-id="d469f-158">に COM オブジェクトのフレンドリ名を、に **@article_resolver** ライブラリの ID (CLSID) を、に値を指定し **@resolver_clsid** `false` **@is_dotnet_assembly** ます。</span><span class="sxs-lookup"><span data-stu-id="d469f-158">Specify the friendly name of the COM object for **@article_resolver**, the library's ID (CLSID) for **@resolver_clsid**, and a value of `false` for **@is_dotnet_assembly**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d469f-159">カスタム競合回避モジュールが不要になったら、[sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) を使用して登録を解除できます。</span><span class="sxs-lookup"><span data-stu-id="d469f-159">When no longer needed, a custom conflict resolver can be unregistered using [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql).</span></span>  
  
10. <span data-ttu-id="d469f-160">(省略可) クラスターで手順 5. ～ 8. を繰り返して、クラスターの全ノードにカスタム競合回避モジュールを登録します。</span><span class="sxs-lookup"><span data-stu-id="d469f-160">(Optional) On a cluster, repeat steps 5-8 to register the custom resolver on all nodes of the cluster.</span></span> <span data-ttu-id="d469f-161">この手順は、フェールオーバーの後にカスタム競合回避モジュールに調整エージェントを適切に読み込むために必要です。</span><span class="sxs-lookup"><span data-stu-id="d469f-161">This is required to ensure that the custom resolver will be able to properly load the reconciler following a failover.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="d469f-162">新しいテーブル アーティクルにカスタム競合回避モジュールを使用するには</span><span class="sxs-lookup"><span data-stu-id="d469f-162">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="d469f-163">パブリッシャーで [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行し、目的の競合回避モジュールの表示名をメモします。</span><span class="sxs-lookup"><span data-stu-id="d469f-163">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="d469f-164">パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行してアーティクルを定義します。</span><span class="sxs-lookup"><span data-stu-id="d469f-164">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article.</span></span> <span data-ttu-id="d469f-165">手順 1. で説明したアーティクル競合回避モジュールの表示名をに指定し **@article_resolver** ます。</span><span class="sxs-lookup"><span data-stu-id="d469f-165">Specify the friendly name of the article resolver from step 1 for **@article_resolver**.</span></span> <span data-ttu-id="d469f-166">詳しくは、「 [アーティクルを定義](publish/define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d469f-166">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="d469f-167">既存のテーブル アーティクルにカスタム競合回避モジュールを使用するには</span><span class="sxs-lookup"><span data-stu-id="d469f-167">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="d469f-168">パブリッシャーで [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行し、目的の競合回避モジュールの表示名をメモします。</span><span class="sxs-lookup"><span data-stu-id="d469f-168">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="d469f-169">[Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を指定し、、、 **@publication** **@article** の**article_resolver**の値、 **@property** および手順 1. のアーティクル競合回避モジュールのフレンドリ名を指定して &#40;sp_changemergearticle を実行 **@value** します。</span><span class="sxs-lookup"><span data-stu-id="d469f-169">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the article resolver from step 1 for **@value**.</span></span>  
  
#### <a name="viewing-a-sample-custom-resolver"></a><span data-ttu-id="d469f-170">サンプルのカスタム競合回避モジュールの表示</span><span class="sxs-lookup"><span data-stu-id="d469f-170">Viewing a Sample Custom Resolver</span></span>  
  
1.  <span data-ttu-id="d469f-171">SQL Server 2000 サンプル ファイルにサンプルが提供されています。</span><span class="sxs-lookup"><span data-stu-id="d469f-171">A sample is available in the SQL Server 2000 sample files.</span></span> <span data-ttu-id="d469f-172">[**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d469f-172">Download the [**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip).</span></span> <span data-ttu-id="d469f-173">これで、3つのファイルが 6.9 MB よっにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="d469f-173">This downloads 3 files amounting to 6.9 MB.</span></span>  
  
2.  <span data-ttu-id="d469f-174">ダウンロードされた圧縮済み .cab ファイルからファイルを抽出します。</span><span class="sxs-lookup"><span data-stu-id="d469f-174">Extract the files from downloaded compressed .cab file.</span></span>  
  
3.  <span data-ttu-id="d469f-175">実行**setup.exe**</span><span class="sxs-lookup"><span data-stu-id="d469f-175">Run **setup.exe**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d469f-176">インストール オプションを選択する場合は、 **レプリケーション** サンプルをインストールするだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="d469f-176">When choosing the installation options, it is only necessary to install the **Replication** samples.</span></span> <span data-ttu-id="d469f-177">(既定のインストールパスは\*\*C:\Program files (x86) \Microsoft SQL Server 2000 Samples\1033 \\ \*\*)</span><span class="sxs-lookup"><span data-stu-id="d469f-177">(The default installation path is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\\**)</span></span>  
  
4.  <span data-ttu-id="d469f-178">インストール フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="d469f-178">Go to installation folder.</span></span> <span data-ttu-id="d469f-179">(既定のフォルダーは **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)</span><span class="sxs-lookup"><span data-stu-id="d469f-179">(The default folder is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)</span></span>  
  
5.  <span data-ttu-id="d469f-180">**unzip_sqlreplSP3.exe** プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="d469f-180">Run the **unzip_sqlreplSP3.exe** program.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d469f-181">サンプルの com 競合回避モジュールが (既定で) **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** フォルダーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="d469f-181">The sample com resolver will install (by default) to the **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** folder.</span></span>  
  
6.  <span data-ttu-id="d469f-182">**subspres** フォルダーで、すべてのソース ファイルで **#include sqlres.h** を検出し、 **#import "replrec.dll" no_namespace, raw_interfaces_only**で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d469f-182">In the **subspres** folder, find all occurrences of **#include sqlres.h** in all of the source files and replace them with **#import "replrec.dll" no_namespace, raw_interfaces_only**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d469f-183">参照</span><span class="sxs-lookup"><span data-stu-id="d469f-183">See Also</span></span>  
 <span data-ttu-id="d469f-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="d469f-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 <span data-ttu-id="d469f-185">[COM ベースのカスタム競合回避モジュール](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span><span class="sxs-lookup"><span data-stu-id="d469f-185">[COM-Based Custom Resolvers](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span></span>  
 [<span data-ttu-id="d469f-186">レプリケーション セキュリティの推奨事項</span><span class="sxs-lookup"><span data-stu-id="d469f-186">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
