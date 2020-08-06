---
title: ネイティブ コンパイル ストアド プロシージャの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e8e8139427c7f2ad92eea856be8da542f65e344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633846"
---
# <a name="creating-natively-compiled-stored-procedures"></a><span data-ttu-id="d1c36-102">ネイティブ コンパイル ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="d1c36-102">Creating Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="d1c36-103">ネイティブ コンパイル ストアド プロシージャには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のプログラミングとクエリのセキュリティ構成が完全には実装されていません。</span><span class="sxs-lookup"><span data-stu-id="d1c36-103">Natively compiled stored procedures do not implement the full [!INCLUDE[tsql](../../includes/tsql-md.md)] programmability and query surface area.</span></span> <span data-ttu-id="d1c36-104">ネイティブ コンパイル ストアド プロシージャ内部で使用できない特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] 構造が存在します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-104">There are certain [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs that cannot be used inside natively compiled stored procedures.</span></span> <span data-ttu-id="d1c36-105">詳細については、「[ネイティブコンパイルストアドプロシージャでサポートされる構造](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c36-105">For more information, see [Supported Constructs in Natively Compiled Stored Procedures](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).</span></span>  
  
 <span data-ttu-id="d1c36-106">ただし、ネイティブ コンパイル ストアド プロシージャに対してのみサポートされる [!INCLUDE[tsql](../../includes/tsql-md.md)] 機能がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-106">There are, however, several [!INCLUDE[tsql](../../includes/tsql-md.md)] features that are only supported for natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="d1c36-107">ATOMIC ブロック。</span><span class="sxs-lookup"><span data-stu-id="d1c36-107">Atomic blocks.</span></span> <span data-ttu-id="d1c36-108">詳細については、「 [Atomic Blocks](atomic-blocks-in-native-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c36-108">For more information, see [Atomic Blocks](atomic-blocks-in-native-procedures.md).</span></span>  
  
-   <span data-ttu-id="d1c36-109">ネイティブ コンパイル ストアド プロシージャのパラメーターおよび変数の `NOT NULL` 制約。</span><span class="sxs-lookup"><span data-stu-id="d1c36-109">`NOT NULL` constraints on parameters of and variables in natively compiled stored procedures.</span></span> <span data-ttu-id="d1c36-110">`NULL` として宣言されているパラメーターまたは変数に `NOT NULL` 値を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="d1c36-110">You cannot assign `NULL` values to parameters or variables declared as `NOT NULL`.</span></span> <span data-ttu-id="d1c36-111">詳細については、「[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c36-111">For more information, see [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).</span></span>  
  
-   <span data-ttu-id="d1c36-112">ネイティブ コンパイル ストアド プロシージャのスキーマ バインド。</span><span class="sxs-lookup"><span data-stu-id="d1c36-112">Schema binding of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="d1c36-113">ネイティブ コンパイル ストアド プロシージャは、[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) を使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-113">Natively compiled stored procedures are created using [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span> <span data-ttu-id="d1c36-114">次の例は、メモリ最適化テーブルと、このテーブルに行を挿入するために使用されるネイティブ コンパイル ストアド プロシージャを示します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-114">The following example shows a memory-optimized table and a natively compiled stored procedure used for inserting rows into the table.</span></span>  
  
```sql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 <span data-ttu-id="d1c36-115">コード サンプルの `NATIVE_COMPILATION` は、この [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャがネイティブ コンパイル ストアド プロシージャであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="d1c36-115">In the code sample, `NATIVE_COMPILATION` indicates that this [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure is a natively compiled stored procedure.</span></span> <span data-ttu-id="d1c36-116">以下のオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="d1c36-116">The following options are required:</span></span>  
  
|<span data-ttu-id="d1c36-117">オプション</span><span class="sxs-lookup"><span data-stu-id="d1c36-117">Option</span></span>|<span data-ttu-id="d1c36-118">説明</span><span class="sxs-lookup"><span data-stu-id="d1c36-118">Description</span></span>|  
|------------|-----------------|  
|`SCHEMABINDING`|<span data-ttu-id="d1c36-119">ネイティブコンパイルストアドプロシージャは、参照するオブジェクトのスキーマにバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-119">Natively compiled stored procedures must be bound to the schema of the objects it references.</span></span> <span data-ttu-id="d1c36-120">これは、プロシージャによるテーブル参照を削除できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-120">This means that table references by the procedure cannot be dropped.</span></span> <span data-ttu-id="d1c36-121">プロシージャで参照されるテーブルにはスキーマ名が含まれている必要があり、 \* クエリではワイルドカード () は使用できません。</span><span class="sxs-lookup"><span data-stu-id="d1c36-121">Tables referenced in the procedure must include their schema name, and wildcards (\*) are not allowed in queries.</span></span> <span data-ttu-id="d1c36-122">このバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、ネイティブ コンパイル ストアド プロシージャに対してのみ `SCHEMABINDING` がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d1c36-122">`SCHEMABINDING` is only supported for natively compiled stored procedures in this version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|`EXECUTE AS`|<span data-ttu-id="d1c36-123">ネイティブ コンパイル ストアド プロシージャでは、既定の実行コンテキストである `EXECUTE AS CALLER` はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d1c36-123">Natively compiled stored procedures do not support `EXECUTE AS CALLER`, which is the default execution context.</span></span> <span data-ttu-id="d1c36-124">したがって、実行コンテキストの指定は必須です。</span><span class="sxs-lookup"><span data-stu-id="d1c36-124">Therefore, specifying the execution context is required.</span></span> <span data-ttu-id="d1c36-125">オプション `EXECUTE AS OWNER` 、 `EXECUTE AS` *user*、および `EXECUTE AS SELF` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d1c36-125">The options `EXECUTE AS OWNER`, `EXECUTE AS`*user*, and `EXECUTE AS SELF` are supported.</span></span>|  
|`BEGIN ATOMIC`|<span data-ttu-id="d1c36-126">ネイティブ コンパイル ストアド プロシージャの本体は、厳密に 1 つの ATOMIC ブロックで構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-126">The natively compiled stored procedure body must consist of exactly one atomic block.</span></span> <span data-ttu-id="d1c36-127">ATOMIC ブロックでは、ストアド プロシージャのアトミック実行が保証されます。</span><span class="sxs-lookup"><span data-stu-id="d1c36-127">Atomic blocks guarantee atomic execution of the stored procedure.</span></span> <span data-ttu-id="d1c36-128">プロシージャをアクティブなトランザクションのコンテキストの外部で呼び出した場合、新しいトランザクションが開始され、ATOMIC ブロックの末尾でコミットされます。</span><span class="sxs-lookup"><span data-stu-id="d1c36-128">If the procedure is invoked outside the context of an active transaction, it will start a new transaction, which commits at the end of the atomic block.</span></span> <span data-ttu-id="d1c36-129">ネイティブ コンパイル ストアド プロシージャの ATOMIC ブロックには、次の 2 つの必須オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-129">Atomic blocks in natively compiled stored procedures have two required options:</span></span><br /><br /> <span data-ttu-id="d1c36-130">`TRANSACTION ISOLATION LEVEL`.</span><span class="sxs-lookup"><span data-stu-id="d1c36-130">`TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="d1c36-131">サポートされる分離レベルについては、「[トランザクション分離レベル](../../database-engine/transaction-isolation-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c36-131">See [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for supported isolation levels.</span></span><br /><br /> <span data-ttu-id="d1c36-132">`LANGUAGE`.</span><span class="sxs-lookup"><span data-stu-id="d1c36-132">`LANGUAGE`.</span></span> <span data-ttu-id="d1c36-133">ストアド プロシージャの言語は、使用可能な言語または言語の別名の 1 つに設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-133">The language for the stored procedure must be set to one of the available languages or language aliases.</span></span>|  
  
 <span data-ttu-id="d1c36-134">`EXECUTE AS` と Windows ログインについては、`EXECUTE AS` を通じて行われた権限借用によって、エラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-134">Regarding `EXECUTE AS` and Windows logins, an error can occur because of the impersonation done through `EXECUTE AS`.</span></span> <span data-ttu-id="d1c36-135">ユーザー アカウントに対して Windows 認証が使用される場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに使用されるサービス アカウントと Windows ログインのドメインとの間に完全信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="d1c36-135">If a user account uses Windows Authentication, there must be full trust between the service account used for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and the domain of the Windows login.</span></span> <span data-ttu-id="d1c36-136">完全に信頼されていない場合、ネイティブコンパイルストアドプロシージャの作成時に、メッセージ15404、Windows NT グループ/ユーザー ' username ' に関する情報を取得できませんでした。エラーコード0x5 が返されます。</span><span class="sxs-lookup"><span data-stu-id="d1c36-136">If there is not full trust, the following error message is returned when creating a natively compiled stored procedure: Msg 15404, Could not obtain information about Windows NT group/user 'username', error code 0x5.</span></span>  
  
 <span data-ttu-id="d1c36-137">このエラーを解決するには、次のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-137">To resolve this error, use one of the following:</span></span>  
  
-   <span data-ttu-id="d1c36-138">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスの Windows ユーザーと同じドメインからのアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-138">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="d1c36-139">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]が Network Service や Local System などのコンピューターアカウントを使用している場合、そのコンピューターは Windows ユーザーを含むドメインによって信頼されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-139">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows user.</span></span>  
  
-   <span data-ttu-id="d1c36-140">認証を使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-140">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="d1c36-141">ネイティブ コンパイル ストアド プロシージャを作成するときに、エラー 15517 が発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-141">You may also see error 15517 when creating a natively compiled stored procedure.</span></span> <span data-ttu-id="d1c36-142">詳細については、「 [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1c36-142">For more information, see [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).</span></span>  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a><span data-ttu-id="d1c36-143">ネイティブ コンパイル ストアド プロシージャの更新</span><span class="sxs-lookup"><span data-stu-id="d1c36-143">Updating a Natively Compiled Stored Procedure</span></span>  
 <span data-ttu-id="d1c36-144">ネイティブ コンパイル ストアド プロシージャに対する変更操作はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1c36-144">Performing alter operations on natively compiled stored procedures is not supported.</span></span> <span data-ttu-id="d1c36-145">ネイティブ コンパイル ストアド プロシージャを変更する方法の 1 つは、ストアド プロシージャを削除してから再作成することです。</span><span class="sxs-lookup"><span data-stu-id="d1c36-145">One way to modify a natively compiled stored procedure is to drop and recreate the stored procedure:</span></span>  
  
1.  <span data-ttu-id="d1c36-146">ストアド プロシージャに対する権限用のスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-146">Generate script for the permissions on the stored procedure.</span></span>  
  
2.  <span data-ttu-id="d1c36-147">ストアド プロシージャ用のスクリプトを生成し、バックアップとして保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1c36-147">Optional, generate script for the stored procedure and save as a backup.</span></span>  
  
3.  <span data-ttu-id="d1c36-148">ストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-148">Drop the stored procedure.</span></span>  
  
4.  <span data-ttu-id="d1c36-149">変更したストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-149">Create the altered stored procedure.</span></span>  
  
5.  <span data-ttu-id="d1c36-150">ストアド プロシージャにスクリプト化した権限を再適用します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-150">Re-apply the scripted permissions to the stored procedure.</span></span>  
  
 <span data-ttu-id="d1c36-151">この手順の欠点は、手順 3. を開始して手順 5. を完了するまでアプリケーションがオフラインになることです。</span><span class="sxs-lookup"><span data-stu-id="d1c36-151">The disadvantage to this procedure is the application will be offline from the start of step 3 through the completion of step 5.</span></span> <span data-ttu-id="d1c36-152">これには数秒かかる場合があり、アプリケーションを使用するクライアントに対してエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-152">This may take a few seconds and the client using the application may see error messages.</span></span>  
  
 <span data-ttu-id="d1c36-153">ネイティブ コンパイル ストアド プロシージャを効率的に変更する別の方法は、まずストアド プロシージャの新しいバージョンを作成することです。</span><span class="sxs-lookup"><span data-stu-id="d1c36-153">Another way to (effectively) modify a natively compiled stored procedure is to first create a new version of the stored procedure.</span></span> <span data-ttu-id="d1c36-154">ネイティブ コンパイル ストアド プロシージャには関連付けられたバージョン番号があります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-154">Here, the natively compiled stored procedure has an associated version number.</span></span> <span data-ttu-id="d1c36-155">古いバージョンを SP_Vold、新しいバージョンを SP_Vnew とします。</span><span class="sxs-lookup"><span data-stu-id="d1c36-155">We will call the old version SP_Vold and the new version SP_Vnew.</span></span>  
  
1.  <span data-ttu-id="d1c36-156">SP_Vold に対する権限用のスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-156">Generate script for the permissions on SP_Vold.</span></span>  
  
2.  <span data-ttu-id="d1c36-157">SP_Vnew を作成します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-157">Create SP_Vnew.</span></span>  
  
3.  <span data-ttu-id="d1c36-158">SP_Vold の権限を SP_Vnew に適用します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-158">Apply the permissions of SP_Vold to SP_Vnew.</span></span>  
  
4.  <span data-ttu-id="d1c36-159">SP_Vold への参照を SP_Vnew を指すように更新します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-159">Update references to SP_Vold to point to SP_Vnew.</span></span> <span data-ttu-id="d1c36-160">これは別の方法でも行うことができます。たとえば次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d1c36-160">This can be accomplished in different of ways, for example:</span></span>  
  
     <span data-ttu-id="d1c36-161">ラッパー (ディスク ベース) ストアド プロシージャを使用し、SP_Vnew を指すようにそのプロシージャを変更します。</span><span class="sxs-lookup"><span data-stu-id="d1c36-161">Use a wrapper (disk-based) stored procedure, and alter that procedure to point to SP_Vnew.</span></span> <span data-ttu-id="d1c36-162">この方法の欠点は、間接指定によってパフォーマンスに影響することです。</span><span class="sxs-lookup"><span data-stu-id="d1c36-162">The disadvantage of this approach is the performance impact of the indirection.</span></span>  
  
    ```sql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  <span data-ttu-id="d1c36-163">SP_Vold を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1c36-163">Optional, drop SP_Vold.</span></span>  
  
 <span data-ttu-id="d1c36-164">この方法の利点は、アプリケーションがオフラインにならないことです。</span><span class="sxs-lookup"><span data-stu-id="d1c36-164">The advantage of this approach is that the application does not go offline.</span></span> <span data-ttu-id="d1c36-165">しかし、参照の保持と、ストアド プロシージャの最新バージョンを常にポイントさせるために、より多くの作業が必要となります。</span><span class="sxs-lookup"><span data-stu-id="d1c36-165">However, more work is required to maintain the references and make sure they always point to the latest version of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c36-166">参照</span><span class="sxs-lookup"><span data-stu-id="d1c36-166">See Also</span></span>  
 [<span data-ttu-id="d1c36-167">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="d1c36-167">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
