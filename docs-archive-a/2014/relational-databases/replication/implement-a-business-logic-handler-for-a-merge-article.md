---
title: マージ アーティクルのビジネス ロジック ハンドラーの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2996a8ca8471ef59d4781e21239a72262daa759
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632343"
---
# <a name="implement-a-business-logic-handler-for-a-merge-article"></a><span data-ttu-id="4f85a-102">マージ アーティクルのビジネス ロジック ハンドラーの実装</span><span class="sxs-lookup"><span data-stu-id="4f85a-102">Implement a Business Logic Handler for a Merge Article</span></span>
  <span data-ttu-id="4f85a-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でレプリケーション プログラミングまたはレプリケーション管理オブジェクト (RMO) を使用して、マージ アーティクルにビジネス ロジック ハンドラーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-103">This topic describes how to implement a business logic handler for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using replication programming or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="4f85a-104"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 名前空間は、マージ レプリケーションの同期処理中に発生するイベントを処理する、複雑なビジネス ロジックを記述するためのインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-104">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="4f85a-105">ビジネス ロジック ハンドラーのメソッドは、同期中にレプリケートされる変更行ごとに、レプリケーション処理から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-105">Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization.</span></span>  
  
 <span data-ttu-id="4f85a-106">ビジネス ロジック ハンドラーを実装するための一般的な手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-106">The general process for implementing a business logic handler is:</span></span>  
  
1.  <span data-ttu-id="4f85a-107">ビジネス ロジック ハンドラーのアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-107">Create the business logic hander assembly.</span></span>  
  
2.  <span data-ttu-id="4f85a-108">ディストリビューターにアセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-108">Register the assembly at the Distributor.</span></span>  
  
3.  <span data-ttu-id="4f85a-109">マージ エージェントが実行されるサーバーにアセンブリを配置します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-109">Deploy the assembly at the server on which the Merge Agent runs.</span></span> <span data-ttu-id="4f85a-110">プル サブスクリプションの場合、エージェントはサブスクライバー上で実行されます。プッシュ サブスクリプションの場合、エージェントはディストリビューター上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-110">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="4f85a-111">Web 同期を使用した場合、エージェントは Web サーバー上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-111">When you are using Web synchronization, the agent runs on the Web server.</span></span>  
  
4.  <span data-ttu-id="4f85a-112">ビジネス ロジック ハンドラーを使用するアーティクルを作成するか、またはビジネス ロジック ハンドラーを使用する既存のアーティクルを変更します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-112">Create an article that uses the business logic handler or modify an existing article to use the business logic handler.</span></span>  
  
 <span data-ttu-id="4f85a-113">指定するビジネス ロジック ハンドラーは、同期されるすべての行に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-113">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="4f85a-114">その他のアプリケーションまたはネットワーク サービスに対する複雑なロジックおよび呼び出しは、パフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-114">Complex logic and calls to other applications or network services can impact performance.</span></span> <span data-ttu-id="4f85a-115">ビジネス ロジック ハンドラーについて詳しくは、「[Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f85a-115">For more information about business logic handlers, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="4f85a-116">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4f85a-116">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4f85a-117">**マージ アーティクルにビジネス ロジック ハンドラーを実装するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="4f85a-117">**To implement a business logic handler for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="4f85a-118">レプリケーションプログラミング</span><span class="sxs-lookup"><span data-stu-id="4f85a-118">Replication Programming</span></span>](#ReplProg)  
  
     [<span data-ttu-id="4f85a-119">レプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="4f85a-119">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-replication-programming"></a><a name="ReplProg"></a> <span data-ttu-id="4f85a-120">レプリケーション プログラミングの使用</span><span class="sxs-lookup"><span data-stu-id="4f85a-120">Using Replication Programming</span></span>  
  
#### <a name="to-create-and-deploy-a-business-logic-handler"></a><span data-ttu-id="4f85a-121">ビジネス ロジック ハンドラーを作成および配置するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-121">To create and deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="4f85a-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio で、.NET アセンブリの新しいプロジェクトを作成し、ビジネス ロジック ハンドラーの実装コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-122">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="4f85a-123">次の名前空間の参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-123">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="4f85a-124">アセンブリ参照</span><span class="sxs-lookup"><span data-stu-id="4f85a-124">Assembly Reference</span></span>|<span data-ttu-id="4f85a-125">場所</span><span class="sxs-lookup"><span data-stu-id="4f85a-125">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="4f85a-126">COM (既定インストール)</span><span class="sxs-lookup"><span data-stu-id="4f85a-126">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="4f85a-127">GAC (.NET Framework のコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="4f85a-127">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="4f85a-128">GAC (.NET Framework のコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="4f85a-128">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="4f85a-129"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラスをオーバーライドするクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-129">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="4f85a-130">処理対象の変更の種類を指定する <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-130">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="4f85a-131"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラスのメソッドのうち、次のいずれかまたは複数のメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="4f85a-131">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="4f85a-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 同期中、データ変更がコミットされたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="4f85a-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - DELETE ステートメントをアップロードまたはダウンロードするときにエラーが発生すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked when an error occurs when a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - DELETE ステートメントをアップロードまたはダウンロードするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - INSERT ステートメントをアップロードまたはダウンロードするときにエラーが発生すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked when an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - INSERT ステートメントをアップロードまたはダウンロードするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - パブリッシャーおよびサブスクライバーで、UPDATE ステートメントの競合が発生した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="4f85a-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - パブリッシャーおよびサブスクライバーで、UPDATE ステートメントと DELETE ステートメントが競合した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="4f85a-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - UPDATE ステートメントをアップロードまたはダウンロードするときにエラーが発生すると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - UPDATE ステートメントをアップロードまたはダウンロードするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
6.  <span data-ttu-id="4f85a-141">プロジェクトをビルドして、ビジネス ロジック ハンドラー アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-141">Build the project to create the business logic handler assembly.</span></span>  
  
7.  <span data-ttu-id="4f85a-142">アセンブリを、マージ エージェント実行可能ファイル (replmerg.exe) を含むディレクトリ (既定のインストールの場合は [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM) に配置するか、.NET グローバル アセンブリ キャッシュ (GAC) にインストールします。</span><span class="sxs-lookup"><span data-stu-id="4f85a-142">Deploy the assembly in the directory that contains the Merge Agent executable file (replmerg.exe), which for a default installation is [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, or install it in the .NET global assembly cache (GAC).</span></span> <span data-ttu-id="4f85a-143">マージ エージェント以外のアプリケーションがアセンブリへのアクセスを必要とする場合は、アセンブリを GAC にのみインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="4f85a-143">You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly.</span></span> <span data-ttu-id="4f85a-144">アセンブリを GAC にインストールするには、.NET Framework SDK のグローバル アセンブリ キャッシュ ツール (**Gacutil.exe** ) を使用します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-144">The assembly can be installed into the GAC using the Global Assembly Cache tool (**Gacutil.exe)** provided in the .NET Framework SDK.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f85a-145">ビジネス ロジック ハンドラーは、Web 同期を使用するときに replisapi.dll をホストする IIS サーバーなど、マージ エージェントを実行する各サーバーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-145">A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="4f85a-146">ビジネス ロジック ハンドラーを登録するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-146">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="4f85a-147">パブリッシャーで、[sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行して、アセンブリがまだビジネス ロジック ハンドラーとして登録されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-147">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the assembly has not already been registered as a business logic handler.</span></span>  
  
2.  <span data-ttu-id="4f85a-148">ディストリビューターで、のビジネス[sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)ロジックハンドラーのフレンドリ名を指定し、に値を、にアセンブリの名前を、にを **@article_resolver** `true` **@is_dotnet_assembly** **@dotnet_assembly_name** オーバーライドするクラスの完全修飾名を <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 指定して、sp_registercustomresolver &#40;transact-sql&#41;を実行し **@dotnet_class_name** ます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-148">At the Distributor, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), specifying a friendly name for the business logic handler for **@article_resolver**, a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f85a-149">アセンブリがマージエージェント実行可能ファイルと同じディレクトリに配置されていない場合、マージエージェントを同期的に起動するアプリケーションと同じディレクトリ、またはグローバルアセンブリキャッシュ (GAC) 内に存在する場合は、のアセンブリ名を使用して完全パスを指定する必要があり **@dotnet_assembly_name** ます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-149">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span> <span data-ttu-id="4f85a-150">Web 同期を使用する場合は、Web サーバーでアセンブリの位置を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-150">When using Web synchronization, you must specify the location of assembly at the Web server.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="4f85a-151">新しいテーブル アーティクルでビジネス ロジック ハンドラーを使用するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-151">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="4f85a-152">[sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行してアーティクルを定義し、**@article_resolver** にビジネス ロジック ハンドラーの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-152">Execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying the friendly name of the business logic handler for **@article_resolver**.</span></span> <span data-ttu-id="4f85a-153">詳しくは、「 [アーティクルを定義](publish/define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f85a-153">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="4f85a-154">既存のテーブル アーティクルでビジネス ロジック ハンドラーを使用するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-154">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="4f85a-155">を指定して[&#41;&#40;sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。これには、、、 **@publication** **@article** の**article_resolver**の値、 **@property** およびのビジネスロジックハンドラーの表示名を指定し **@value** ます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-155">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the business logic handler for **@value**.</span></span>  
  
###  <a name="examples-replication-programming"></a><a name="TsqlExample"></a><span data-ttu-id="4f85a-156">例 (レプリケーションプログラミング)</span><span class="sxs-lookup"><span data-stu-id="4f85a-156">Examples (Replication Programming)</span></span>  
 <span data-ttu-id="4f85a-157">次の例に、監査ログを作成するビジネス ロジック ハンドラーを示します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-157">This example shows a business logic handler that creates an audit log.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="4f85a-158">次の例では、ビジネス ロジック ハンドラー アセンブリをディストリビューターに登録し、カスタム ビジネス ロジックを使用するように既存のマージ アーティクルを変更します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-158">The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.</span></span>  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../snippets/tsql/SQL15/replication/howto/tsql/registerblh_10.sql#sp_registerblh_10)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4f85a-159">レプリケーション管理オブジェクト (RMO) の使用</span><span class="sxs-lookup"><span data-stu-id="4f85a-159">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-create-a-business-logic-handler"></a><span data-ttu-id="4f85a-160">ビジネス ロジック ハンドラーを作成するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-160">To create a business logic handler</span></span>  
  
1.  <span data-ttu-id="4f85a-161">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio で、.NET アセンブリの新しいプロジェクトを作成し、ビジネス ロジック ハンドラーの実装コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="4f85a-162">次の名前空間の参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-162">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="4f85a-163">アセンブリ参照</span><span class="sxs-lookup"><span data-stu-id="4f85a-163">Assembly Reference</span></span>|<span data-ttu-id="4f85a-164">場所</span><span class="sxs-lookup"><span data-stu-id="4f85a-164">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="4f85a-165">COM (既定インストール)</span><span class="sxs-lookup"><span data-stu-id="4f85a-165">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="4f85a-166">GAC (.NET Framework のコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="4f85a-166">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="4f85a-167">GAC (.NET Framework のコンポーネント)</span><span class="sxs-lookup"><span data-stu-id="4f85a-167">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="4f85a-168"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラスをオーバーライドするクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-168">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="4f85a-169">処理対象の変更の種類を指定する <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-169">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="4f85a-170"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラスのメソッドのうち、次のいずれかまたは複数のメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="4f85a-170">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="4f85a-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 同期中、データ変更がコミットされたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="4f85a-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - DELETE ステートメントのアップロードまたはダウンロード時、エラーが発生した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked if an error occurs while a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - DELETE ステートメントをアップロードまたはダウンロードするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - INSERT ステートメントのアップロードまたはダウンロード時、エラーが発生した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked if an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - INSERT ステートメントをアップロードまたはダウンロードするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - パブリッシャーおよびサブスクライバーで、UPDATE ステートメントの競合が発生した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="4f85a-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - パブリッシャーおよびサブスクライバーで、UPDATE ステートメントと DELETE ステートメントが競合した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="4f85a-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - UPDATE ステートメントのアップロードまたはダウンロード時、エラーが発生した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="4f85a-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - UPDATE ステートメントをアップロードまたはダウンロードするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f85a-180">アーティクル競合時の処理がカスタム ビジネス ロジックによって明示的に定義されていない場合は、アーティクルの既定の競合回避モジュールによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-180">Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.</span></span>  
  
6.  <span data-ttu-id="4f85a-181">プロジェクトをビルドして、ビジネス ロジック ハンドラー アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-181">Build the project to create the business logic handler assembly.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="4f85a-182">ビジネス ロジック ハンドラーを登録するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-182">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="4f85a-183"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-183">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4f85a-184"><xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-184">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="4f85a-185">手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-185">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
3.  <span data-ttu-id="4f85a-186"><xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> を呼び出し、返された <xref:System.Collections.ArrayList> オブジェクトをチェックして、そのアセンブリがビジネス ロジック ハンドラーとしてまだ登録されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-186">Call <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> and check the returned <xref:System.Collections.ArrayList> object to ensure that the assembly has not already been registered as a business logic handler.</span></span>  
  
4.  <span data-ttu-id="4f85a-187"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> class.</span></span> <span data-ttu-id="4f85a-188">次のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-188">Specify the following properties:</span></span>  
  
    -   <span data-ttu-id="4f85a-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - .NET アセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="4f85a-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - the name of the .NET assembly.</span></span> <span data-ttu-id="4f85a-190">マージ エージェントの実行可能ファイルがあるディレクトリ、マージ エージェントを同期的に起動するアプリケーションがあるディレクトリ、および GAC の、いずれとも異なる場所にアセンブリが配置されている場合は、アセンブリ名に完全パスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-190">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name.</span></span> <span data-ttu-id="4f85a-191">ビジネス ロジック ハンドラーを Web 同期で使用する場合は、アセンブリ名に完全パスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-191">You must include the full path with the assembly name when using a business logic handler with Web synchronization.</span></span>  
  
    -   <span data-ttu-id="4f85a-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> をオーバーライドし、ビジネス ロジック ハンドラーを実装するクラスの完全修飾名です。</span><span class="sxs-lookup"><span data-stu-id="4f85a-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> and implements the business logic handler.</span></span>  
  
    -   <span data-ttu-id="4f85a-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - ビジネス ロジック ハンドラーへのアクセス時に使用する表示名です。</span><span class="sxs-lookup"><span data-stu-id="4f85a-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - a friendly name you use when you access the business logic handler.</span></span>  
  
    -   <span data-ttu-id="4f85a-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - `true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - a value of `true`.</span></span>  
  
#### <a name="to-deploy-a-business-logic-handler"></a><span data-ttu-id="4f85a-195">ビジネス ロジック ハンドラーを配置するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-195">To deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="4f85a-196">マージ エージェントが実行されるサーバーにアセンブリを配置します。格納場所は、ディストリビューターにビジネス ロジック ハンドラーを登録したときに指定した場所になります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-196">Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor.</span></span> <span data-ttu-id="4f85a-197">プル サブスクリプションの場合、エージェントはサブスクライバー上で実行されます。プッシュ サブスクリプションの場合、エージェントはディストリビューター上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-197">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="4f85a-198">Web 同期を使用した場合、エージェントは Web サーバー上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4f85a-198">When you are using Web synchronization, the agent runs on the Web server.</span></span> <span data-ttu-id="4f85a-199">ビジネス ロジック ハンドラーの登録時、アセンブリ名に完全パスを含めなかった場合は、マージ エージェントの実行可能ファイルがあるディレクトリ (マージ エージェントを同期的に起動するアプリケーションがあるディレクトリ) にアセンブリを配置してください。</span><span class="sxs-lookup"><span data-stu-id="4f85a-199">If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent.</span></span> <span data-ttu-id="4f85a-200">同じアセンブリを使用するアプリケーションが複数存在する場合は、アセンブリを GAC にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-200">You may install the assembly in the GAC if there are multiple applications that use the same assembly.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="4f85a-201">新しいテーブル アーティクルでビジネス ロジック ハンドラーを使用するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-201">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="4f85a-202"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-202">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4f85a-203"><xref:Microsoft.SqlServer.Replication.MergeArticle> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span> <span data-ttu-id="4f85a-204">次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-204">Set the following properties:</span></span>  
  
    -   <span data-ttu-id="4f85a-205"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>にアーティクル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-205">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="4f85a-206"><xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>にパブリケーション名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-206">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="4f85a-207"><xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>にパブリケーション データベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-207">The name of the publication database for <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="4f85a-208"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>にビジネス ロジック ハンドラーの表示名 ( <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>) を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-208">The friendly name of the business logic handler (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span>  
  
3.  <span data-ttu-id="4f85a-209"><xref:Microsoft.SqlServer.Replication.Article.Create%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-209">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span> <span data-ttu-id="4f85a-210">詳しくは、「 [アーティクルを定義](publish/define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f85a-210">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="4f85a-211">既存のテーブル アーティクルでビジネス ロジック ハンドラーを使用するには</span><span class="sxs-lookup"><span data-stu-id="4f85a-211">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="4f85a-212"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-212">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4f85a-213"><xref:Microsoft.SqlServer.Replication.MergeArticle> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-213">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="4f85a-214"><xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-214">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="4f85a-215">手順 1. で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-215">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="4f85a-216"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-216">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="4f85a-217">このメソッドから `false` が返された場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。</span><span class="sxs-lookup"><span data-stu-id="4f85a-217">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span> <span data-ttu-id="4f85a-218">詳しくは、「 [View and Modify Article Properties](publish/view-and-modify-article-properties.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f85a-218">For more information, see [View and Modify Article Properties](publish/view-and-modify-article-properties.md).</span></span>  
  
6.  <span data-ttu-id="4f85a-219"><xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>にビジネス ロジック ハンドラーの表示名を設定します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-219">Set the friendly name of the business logic handler for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span> <span data-ttu-id="4f85a-220">これは、ビジネス ロジック ハンドラーの登録時に指定した <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> プロパティの値になります。</span><span class="sxs-lookup"><span data-stu-id="4f85a-220">This is the value of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> property specified when registering the business logic handler.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="4f85a-221">例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4f85a-221">Examples (RMO)</span></span>  
 <span data-ttu-id="4f85a-222">次のビジネス ロジック ハンドラーの例では、サブスクライバーでの挿入、更新、および削除に関する情報をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-222">This example is a business logic handler that logs information about inserts, updates, and deletes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="4f85a-223">次の例では、ディストリビューターにビジネス ロジック ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-223">This example registers a business logic handler at the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 <span data-ttu-id="4f85a-224">次の例では、既存のアーティクルを変更してビジネス ロジック ハンドラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f85a-224">This example changes an existing article to use the business logic handler.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="4f85a-225">参照</span><span class="sxs-lookup"><span data-stu-id="4f85a-225">See Also</span></span>  
 <span data-ttu-id="4f85a-226">[マージアーティクルのカスタム競合回避モジュールの実装](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="4f85a-226">[Implement a Custom Conflict Resolver for a Merge Article](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="4f85a-227">[ビジネスロジックハンドラーのデバッグ &#40;レプリケーションプログラミング&#41;](debug-a-business-logic-handler-replication-programming.md) </span><span class="sxs-lookup"><span data-stu-id="4f85a-227">[Debug a Business Logic Handler &#40;Replication Programming&#41;](debug-a-business-logic-handler-replication-programming.md) </span></span>  
 <span data-ttu-id="4f85a-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="4f85a-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="4f85a-229">レプリケーション管理オブジェクトの概念</span><span class="sxs-lookup"><span data-stu-id="4f85a-229">Replication Management Objects Concepts</span></span>](concepts/replication-management-objects-concepts.md)  
  
  
