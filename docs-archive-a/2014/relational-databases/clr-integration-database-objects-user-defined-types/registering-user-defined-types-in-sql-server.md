---
title: SQL Server | でのユーザー定義型の登録Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [CLR integration], maintaining
- user-defined types [CLR integration], maintaining
- dependencies [CLR integration]
- deploying user-defined types [CLR integration]
- CurrencyConversion function
- user-defined types [CLR integration], deploying
- Transact-SQL deploying UDTs
- assemblies [CLR integration], user-defined types
- cross-database UDT support
- CREATE ASSEMBLY statement
- DROP TYPE statement
- Currency UDT
- CREATE TYPE statement
- registering user-defined types
- UDTs [CLR integration], deploying
- removing user-defined types
- user-defined types [CLR integration], registering
- ALTER ASSEMBLY statement
- UDTs [CLR integration], registering
- ADD FILE clause
ms.assetid: f7da3e92-e407-4f0b-b3a3-f214e442b37d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d24f7948e093335eff708f3c4a8a7361cfc156f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633170"
---
# <a name="registering-user-defined-types-in-sql-server"></a><span data-ttu-id="ee25c-102">SQL Server でのユーザー定義型の登録</span><span class="sxs-lookup"><span data-stu-id="ee25c-102">Registering User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="ee25c-103">でユーザー定義型 (UDT) を使用するには [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、それを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-103">In order to use a user-defined type (UDT) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must register it.</span></span> <span data-ttu-id="ee25c-104">UDT を登録するには、UDT を使用するデータベースにアセンブリを登録し、型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-104">Registering a UDT involves registering the assembly and creating the type in the database in which you wish to use it.</span></span> <span data-ttu-id="ee25c-105">UDT は、1 つのデータベースにスコープが設定されるので、同一のアセンブリと UDT を各データベースに登録しない限り、複数のデータベースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-105">UDTs are scoped to a single database, and cannot be used in multiple databases unless the identical assembly and UDT are registered with each database.</span></span> <span data-ttu-id="ee25c-106">UDT アセンブリを登録し、型を作成すると、[!INCLUDE[tsql](../../includes/tsql-md.md)] やクライアント コードでその UDT を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-106">Once the UDT assembly is registered and the type created, you can use the UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)] and in client code.</span></span> <span data-ttu-id="ee25c-107">詳細については、「 [CLR ユーザー定義型](clr-user-defined-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee25c-107">For more information, see [CLR User-Defined Types](clr-user-defined-types.md).</span></span>  
  
## <a name="using-visual-studio-to-deploy-udts"></a><span data-ttu-id="ee25c-108">Visual Studio を使用した UDT の配置</span><span class="sxs-lookup"><span data-stu-id="ee25c-108">Using Visual Studio to Deploy UDTs</span></span>  
 <span data-ttu-id="ee25c-109">UDT を配置する最も簡単な方法は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio を使用することです。</span><span class="sxs-lookup"><span data-stu-id="ee25c-109">The easiest way to deploy your UDT is by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="ee25c-110">ただし、より複雑な配置シナリオで最も優れた柔軟性を得るためには、このトピックで説明するように [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-110">For more complex deployment scenarios and the greatest flexibility, however, use [!INCLUDE[tsql](../../includes/tsql-md.md)] as discussed later in this topic.</span></span>  
  
 <span data-ttu-id="ee25c-111">Visual Studio を使用して UDT を作成および配置するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-111">Follow these steps to create and deploy a UDT using Visual Studio:</span></span>  
  
1.  <span data-ttu-id="ee25c-112">**Visual Basic**または**Visual C#** 言語ノードで新しい**データベース**プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-112">Create a new **Database** project in the **Visual Basic** or **Visual C#** language nodes.</span></span>  
  
2.  <span data-ttu-id="ee25c-113">UDT を格納する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-113">Add a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the UDT.</span></span>  
  
3.  <span data-ttu-id="ee25c-114">**ユーザー定義型**クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-114">Add a **User-Defined Type** class.</span></span>  
  
4.  <span data-ttu-id="ee25c-115">コードを記述して UDT を実装します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-115">Write code to implement the UDT.</span></span>  
  
5.  <span data-ttu-id="ee25c-116">[**ビルド**] メニューの [**配置**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee25c-116">From the **Build** menu, select **Deploy**.</span></span> <span data-ttu-id="ee25c-117">この結果、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにアセンブリが登録され、型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-117">This registers the assembly and creates the type in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
## <a name="using-transact-sql-to-deploy-udts"></a><span data-ttu-id="ee25c-118">Transact-SQL を使用した UDT の配置</span><span class="sxs-lookup"><span data-stu-id="ee25c-118">Using Transact-SQL to Deploy UDTs</span></span>  
 <span data-ttu-id="ee25c-119">[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 構文は、UDT を使用するデータベースにアセンブリを登録する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-119">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY syntax is used to register the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="ee25c-120">アセンブリは、ファイル システムに外部的に格納されるのではなく、データベース システム テーブルに内部的に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-120">It is stored internally in database system tables, not externally in the file system.</span></span> <span data-ttu-id="ee25c-121">UDT が外部アセンブリに依存する場合は、それらのアセンブリもデータベースに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-121">If the UDT is dependent on external assemblies, they too must be loaded into the database.</span></span> <span data-ttu-id="ee25c-122">CREATE TYPE ステートメントは、UDT を使用するデータベースに UDT を作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-122">The CREATE TYPE statement is used to create the UDT in the database in which it is to be used.</span></span> <span data-ttu-id="ee25c-123">詳細については、[CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql) と [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee25c-123">For more information, see [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql) and [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
### <a name="using-create-assembly"></a><span data-ttu-id="ee25c-124">CREATE ASSEMBLY の使用</span><span class="sxs-lookup"><span data-stu-id="ee25c-124">Using CREATE ASSEMBLY</span></span>  
 <span data-ttu-id="ee25c-125">CREATE ASSEMBLY 構文では、UDT を使用するデータベースにアセンブリが登録されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-125">The CREATE ASSEMBLY syntax registers the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="ee25c-126">アセンブリを登録すると、そのアセンブリに依存関係がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-126">Once the assembly is registered, it has no dependencies.</span></span>  
  
 <span data-ttu-id="ee25c-127">指定された 1 つのデータベースに複数のバージョンの同じアセンブリを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-127">Creating multiple versions of the same assembly in a given database is not allowed.</span></span> <span data-ttu-id="ee25c-128">ただし、特定の 1 つのデータベースに、カルチャに基づいて、複数のバージョンの同じアセンブリを作成することはできます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-128">However, it is possible to create multiple versions of the same assembly based on culture in a given database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee25c-129">では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに登録されているとおりに、異なる名前で、アセンブリの複数のカルチャ バージョンが区別されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-129">distinguishes multiple culture versions of an assembly by different names as registered in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ee25c-130">詳細については、.NET Framework SDK の「厳密な名前付きアセンブリの作成と使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee25c-130">For more information, see "Creating and Using Strong-Named Assemblies" in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="ee25c-131">SAFE 権限セットまたは EXTERNAL_ACCESS 権限セットを指定して CREATE ASSEMBLY を実行すると、アセンブリが検証可能でタイプ セーフであることを確認するためのチェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-131">When CREATE ASSEMBLY is executed with the SAFE or EXTERNAL_ACCESS permission sets, the assembly is checked to make sure that it is verifiable and type safe.</span></span> <span data-ttu-id="ee25c-132">権限セットを指定しないと、SAFE が指定されていると想定されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-132">If you omit specifying a permission set, SAFE is assumed.</span></span> <span data-ttu-id="ee25c-133">UNSAFE 権限セットを指定したコードはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-133">Code with the UNSAFE permission set is not checked.</span></span> <span data-ttu-id="ee25c-134">アセンブリの権限セットの詳細については、「[アセンブリのデザイン](../../relational-databases/clr-integration/assemblies-designing.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee25c-134">For more information about assembly permission sets, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="ee25c-135">例</span><span class="sxs-lookup"><span data-stu-id="ee25c-135">Example</span></span>  
 <span data-ttu-id="ee25c-136">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、AdventureWorks データベースのに Point アセンブリを登録し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SAFE 権限セットを設定します。 **AdventureWorks**</span><span class="sxs-lookup"><span data-stu-id="ee25c-136">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the Point assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the **AdventureWorks** database, with the SAFE permission set.</span></span> <span data-ttu-id="ee25c-137">WITH PERMISSION_SET 句を省略すると、SAFE 権限セットでアセンブリが登録されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-137">If the WITH PERMISSION_SET clause is omitted, the assembly is registered with the SAFE permission set.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM '\\ShareName\Projects\Point\bin\Point.dll'   
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="ee25c-138">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、from 句で *<assembly_bits>* 引数を使用してアセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-138">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the assembly using *<assembly_bits>* argument in the FROM clause.</span></span> <span data-ttu-id="ee25c-139">この `varbinary` 値は、ファイルをバイト ストリームで表しています。</span><span class="sxs-lookup"><span data-stu-id="ee25c-139">This `varbinary` value represents the file as a stream of bytes.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM 0xfeac4 ... 21ac78  
```  
  
### <a name="using-create-type"></a><span data-ttu-id="ee25c-140">CREATE TYPE の使用</span><span class="sxs-lookup"><span data-stu-id="ee25c-140">Using CREATE TYPE</span></span>  
 <span data-ttu-id="ee25c-141">アセンブリをデータベースに読み込むと、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE ステートメントを使用して型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-141">Once the assembly is loaded into the database, you can then create the type using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement.</span></span> <span data-ttu-id="ee25c-142">型を作成すると、そのデータベースで使用できる型のリストに、作成した型が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-142">This adds the type to the list of available types for that database.</span></span> <span data-ttu-id="ee25c-143">型にはデータベース スコープがあり、型はその型を作成したデータベースでしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-143">The type has database scope and the type can only be used in the database in which it was created.</span></span> <span data-ttu-id="ee25c-144">データベース内に UDT が既に存在する場合は、CREATE TYPE ステートメントがエラーで失敗します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-144">If the UDT already exists in the database, the CREATE TYPE statement fails with an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee25c-145">CREATE TYPE 構文は、ネイティブな [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 別名データ型を作成する場合にも使用され、別名データ型を作成する手段として `sp_addtype` に置き換わるものです。</span><span class="sxs-lookup"><span data-stu-id="ee25c-145">The CREATE TYPE syntax is also used for creating native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types, and is intended to replace `sp_addtype` as a means of creating alias data types.</span></span> <span data-ttu-id="ee25c-146">CREATE TYPE 構文の省略可能な一部の引数は CLR の UDT の作成に関係しており、(基本型などの) 別名データ型の作成には適用されません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-146">Some of the optional arguments in the CREATE TYPE syntax refer to creating UDTs, and are not applicable to creating alias data types (such as base type).</span></span>  
  
 <span data-ttu-id="ee25c-147">詳細については、[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee25c-147">For more information, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="ee25c-148">例</span><span class="sxs-lookup"><span data-stu-id="ee25c-148">Example</span></span>  
 <span data-ttu-id="ee25c-149">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、`Point` 型を作成します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-149">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates the `Point` type.</span></span> <span data-ttu-id="ee25c-150">外部名は、 *AssemblyName*の2部構成の名前付け構文を使用して指定されます。*Udtname*。</span><span class="sxs-lookup"><span data-stu-id="ee25c-150">The EXTERNAL NAME is specified using the two-part naming syntax of *AssemblyName*.*UDTName*.</span></span>  
  
```  
CREATE TYPE dbo.Point   
EXTERNAL NAME Point.[Point];  
```  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="ee25c-151">データベースからの UDT の削除</span><span class="sxs-lookup"><span data-stu-id="ee25c-151">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="ee25c-152">DROP TYPE ステートメントを使用すると、現在のデータベースから UDT が削除されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-152">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="ee25c-153">UDT を削除すると、DROP ASSEMBLY ステートメントを使用してデータベースからアセンブリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-153">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="ee25c-154">DROP TYPE ステートメントは、次の状況では実行されません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-154">The DROP TYPE statement does not execute in the following situations:</span></span>  
  
-   <span data-ttu-id="ee25c-155">UDT を使用して定義した列を含むデータベース内のテーブル。</span><span class="sxs-lookup"><span data-stu-id="ee25c-155">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="ee25c-156">WITH SCHEMABINDING 句を使用してデータベースに作成した UDT の変数またはパラメーターを使用する関数、ストアド プロシージャ、またはトリガー。</span><span class="sxs-lookup"><span data-stu-id="ee25c-156">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ee25c-157">例</span><span class="sxs-lookup"><span data-stu-id="ee25c-157">Example</span></span>  
 <span data-ttu-id="ee25c-158">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、この順序どおりに実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-158">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] must execute in the following order.</span></span> <span data-ttu-id="ee25c-159">最初に `Point` UDT を参照するテーブルを削除し、次に型を削除して、最後にアセンブリを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-159">First the table which references the `Point` UDT must be dropped, then the type, and finally the assembly.</span></span>  
  
```  
DROP TABLE dbo.Points;  
DROP TYPE dbo.Point;  
DROP ASSEMBLY Point;  
```  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="ee25c-160">UDT 依存関係の検出</span><span class="sxs-lookup"><span data-stu-id="ee25c-160">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="ee25c-161">UDT の列定義を含むテーブルなどの依存オブジェクトがある場合、DROP TYPE ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-161">If there are dependent objects, such as tables with UDT column definitions, the DROP TYPE statement fails.</span></span> <span data-ttu-id="ee25c-162">また、WITH SCHEMABINDING 句を使用してデータベースに作成した関数、ストアド プロシージャ、またはトリガーがあり、これらのルーチンでユーザー定義型の変数やパラメーターが使用される場合にも失敗します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-162">It also fails if there are functions, stored procedures, or triggers created in the database using the WITH SCHEMABINDING clause, if these routines use variables or parameters of the user-defined type.</span></span> <span data-ttu-id="ee25c-163">最初にすべての依存オブジェクトを削除してから、DROP TYPE ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-163">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span>  
  
 <span data-ttu-id="ee25c-164">次のクエリでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **AdventureWorks**データベースで UDT を使用するすべての列とパラメーターを検索します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-164">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;  
```  
  
## <a name="maintaining-udts"></a><span data-ttu-id="ee25c-165">UDT の管理</span><span class="sxs-lookup"><span data-stu-id="ee25c-165">Maintaining UDTs</span></span>  
 <span data-ttu-id="ee25c-166">UDT を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに作成した後は、型の基になるアセンブリを変更することはできますが、UDT は変更できません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-166">You cannot modify a UDT once it is created in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, although you can alter the assembly on which the type is based.</span></span> <span data-ttu-id="ee25c-167">ほとんどの場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE ステートメントを使用してデータベースから UDT を削除し、基になるアセンブリに変更を加えて、ALTER ASSEMBLY ステートメントを使用してアセンブリを再読み込みする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-167">In most cases, you must remove the UDT from the database with the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE statement, make changes to the underlying assembly, and reload it using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="ee25c-168">その後、UDT とすべての依存オブジェクトを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-168">You then need to re-create the UDT and any dependent objects.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ee25c-169">例</span><span class="sxs-lookup"><span data-stu-id="ee25c-169">Example</span></span>  
 <span data-ttu-id="ee25c-170">ALTER ASSEMBLY ステートメントは、UDT アセンブリのソース コードに変更を加え、ソース コードを再コンパイルした後に使用します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-170">The ALTER ASSEMBLY statement is used after you have made changes to the source code in your UDT assembly and recompiled it.</span></span> <span data-ttu-id="ee25c-171">ALTER ASSEMBLY ステートメントを使用すると、サーバーに .dll ファイルがコピーされ、新しいアセンブリに再バインドされます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-171">It copies the .dll file to the server and rebinds to the new assembly.</span></span> <span data-ttu-id="ee25c-172">完全な構文については、「 [ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee25c-172">For the complete syntax, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
 <span data-ttu-id="ee25c-173">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントでは、ディスク上の指定された場所から Point.dll アセンブリを再読み込みしています。</span><span class="sxs-lookup"><span data-stu-id="ee25c-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement reloads the Point.dll assembly from the specified location on disk.</span></span>  
  
```  
ALTER ASSEMBLY Point  
FROM '\\Projects\Point\bin\Point.dll'  
```  
  
### <a name="using-alter-assembly-to-add-source-code"></a><span data-ttu-id="ee25c-174">ALTER ASSEMBLY を使用したソース コードの追加</span><span class="sxs-lookup"><span data-stu-id="ee25c-174">Using ALTER ASSEMBLY to Add Source Code</span></span>  
 <span data-ttu-id="ee25c-175">ALTER ASSEMBLY 構文の ADD FILE 句は、CREATE ASSEMBLY 構文には存在しません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-175">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="ee25c-176">ADD FILE 句を使用すると、アセンブリに関連付けられるソース コードやその他のファイルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-176">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="ee25c-177">ファイルは元の場所からコピーされ、データベース内のシステム テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-177">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="ee25c-178">これにより、現在のバージョンの UDT を再作成またはドキュメント化する必要があれば、ソース コードや他のファイルをいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-178">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="ee25c-179">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントでは、UDT の Point.cs クラスのソースコードを追加し `Point` ます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-179">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement adds the Point.cs class source code for the `Point` UDT.</span></span> <span data-ttu-id="ee25c-180">Point.cs ファイルに含まれているテキストがコピーされ、"PointSource" という名前でデータベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-180">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
```  
ALTER ASSEMBLY Point  
ADD FILE FROM '\\Projects\Point\Point.cs' AS PointSource;  
```  
  
 <span data-ttu-id="ee25c-181">アセンブリ情報は、アセンブリがインストールされているデータベースの**assembly_files**テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-181">Assembly information is stored in the **sys.assembly_files** table in the database where the assembly has been installed.</span></span> <span data-ttu-id="ee25c-182">**Assembly_files**テーブルには、次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee25c-182">The **sys.assembly_files** table contains the following columns.</span></span>  
  
 <span data-ttu-id="ee25c-183">**assembly_id**</span><span class="sxs-lookup"><span data-stu-id="ee25c-183">**assembly_id**</span></span>  
 <span data-ttu-id="ee25c-184">アセンブリに定義される ID。</span><span class="sxs-lookup"><span data-stu-id="ee25c-184">The identifier defined for the assembly.</span></span> <span data-ttu-id="ee25c-185">この番号は、同じアセンブリに関連するすべてのオブジェクトに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-185">This number is assigned to all objects relating to the same assembly.</span></span>  
  
 <span data-ttu-id="ee25c-186">**name**</span><span class="sxs-lookup"><span data-stu-id="ee25c-186">**name**</span></span>  
 <span data-ttu-id="ee25c-187">オブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="ee25c-187">The name of the object.</span></span>  
  
 <span data-ttu-id="ee25c-188">**file_id**</span><span class="sxs-lookup"><span data-stu-id="ee25c-188">**file_id**</span></span>  
 <span data-ttu-id="ee25c-189">各オブジェクトを識別する番号。特定の**assembly_id**に関連付けられた最初のオブジェクトは、値1を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-189">A number identifying each object, with the first object associated with a given **assembly_id** being given the value of 1.</span></span> <span data-ttu-id="ee25c-190">同じ**assembly_id**に複数のオブジェクトが関連付けられている場合は、その後の各**file_id**値が1ずつインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-190">If there are multiple objects associated with the same **assembly_id**, then each subsequent **file_id** value is incremented by 1.</span></span>  
  
 <span data-ttu-id="ee25c-191">**content**</span><span class="sxs-lookup"><span data-stu-id="ee25c-191">**content**</span></span>  
 <span data-ttu-id="ee25c-192">アセンブリまたはファイルの 16 進数表記。</span><span class="sxs-lookup"><span data-stu-id="ee25c-192">The hexadecimal representation of the assembly or file.</span></span>  
  
 <span data-ttu-id="ee25c-193">CAST 関数または CONVERT 関数を使用すると、**コンテンツ**列の内容を読み取り可能なテキストに変換できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-193">You can use the CAST or CONVERT function to convert the contents of the **content** column to readable text.</span></span> <span data-ttu-id="ee25c-194">次のクエリでは、結果セットを 1 行に制限するために WHERE 句で name を使用して、Point.cs ファイルの内容を読み取り可能なテキストに変換しています。</span><span class="sxs-lookup"><span data-stu-id="ee25c-194">The following query converts the contents of the Point.cs file to readable text, using the name in the WHERE clause to restrict the result set to a single row.</span></span>  
  
```  
SELECT CAST(content AS varchar(8000))   
  FROM sys.assembly_files   
  WHERE name='PointSource';  
```  
  
 <span data-ttu-id="ee25c-195">結果をテキスト エディターにコピーして貼り付けると、元のファイルに含まれていた改行とスペースが保持されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-195">If you copy and paste the results in to a text editor, you will see that the line breaks and spaces that existed in the original have been preserved.</span></span>  
  
## <a name="managing-udts-and-assemblies"></a><span data-ttu-id="ee25c-196">UDT とアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="ee25c-196">Managing UDTs and Assemblies</span></span>  
 <span data-ttu-id="ee25c-197">UDT の実装を計画するときは、どのメソッドが UDT アセンブリ自体に必要であり、どのメソッドを独立したアセンブリに作成してユーザー定義関数やストアド プロシージャとして実装する必要があるかを検討します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-197">When planning your implementation of UDTs, consider which methods are needed in the UDT assembly itself, and which methods should be created in separate assemblies and implemented as user-defined functions or stored procedures.</span></span> <span data-ttu-id="ee25c-198">メソッドを個別のアセンブリに分離すると、テーブルの UDT 列に格納されるデータに影響を与えずに、コードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-198">Separating methods into separate assemblies allows you to update code without affecting data that may be stored in a UDT column in a table.</span></span> <span data-ttu-id="ee25c-199">新しい定義で UDT 列の以前の値を読み取ることができ、型の署名が変更されない場合にのみ、UDT 列や他の依存オブジェクトを削除しないで UDT アセンブリを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-199">You can modify UDT assemblies without dropping UDT columns and other dependent objects only when the new definition can read the former values and the signature of the type does not change.</span></span>  
  
 <span data-ttu-id="ee25c-200">UDT の実装に必要なコードから、変更される可能性がある手続き型コードを分離すると、メンテナンスが大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-200">Separating procedural code that may change from the code required to implement the UDT greatly simplifies maintenance.</span></span> <span data-ttu-id="ee25c-201">UDT が機能するのに必要なコードのみを含め、UDT の定義をできる限り単純にしておくと、コード リビジョンやバグ修正のために UDT 自体をデータベースから削除する必要が生じるリスクが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-201">Including only code that is necessary for the UDT to function, and keeping your UDT definitions as simple as possible, reduces the risk that the UDT itself may need to be dropped from the database for code revisions or bug fixes.</span></span>  
  
### <a name="the-currency-udt-and-currency-conversion-function"></a><span data-ttu-id="ee25c-202">Currency UDT と通貨換算関数</span><span class="sxs-lookup"><span data-stu-id="ee25c-202">The Currency UDT and Currency Conversion Function</span></span>  
 <span data-ttu-id="ee25c-203">**AdventureWorks**サンプルデータベースの**Currency** UDT には、udt とそれに関連付けられた関数を構造化するための推奨される方法の例が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ee25c-203">The **Currency** UDT in the **AdventureWorks** sample database provides a useful example of the recommended way to structure a UDT and its associated functions.</span></span> <span data-ttu-id="ee25c-204">**通貨**UDT は、特定のカルチャの通貨システムに基づいて金額を処理するために使用され、ドル、ユーロなどのさまざまな通貨の種類を格納できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-204">The **Currency** UDT is used for handling money based on the monetary system of a particular culture, and allows for storage of different currency types, such as dollars, euros, and so forth.</span></span> <span data-ttu-id="ee25c-205">UDT クラスでは、カルチャ名を文字列として、金額を `decimal` データ型として公開します。</span><span class="sxs-lookup"><span data-stu-id="ee25c-205">The UDT class exposes a culture name as a string, and an amount of money as a `decimal` data type.</span></span> <span data-ttu-id="ee25c-206">必要なシリアル化メソッドは、クラスを定義するアセンブリ内にすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-206">All of the necessary serialization methods are contained within the assembly defining the class.</span></span> <span data-ttu-id="ee25c-207">あるカルチャから別のカルチャへの通貨変換を実装する関数は、 **Convertcurrency**という外部関数として実装され、この関数は別のアセンブリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-207">The function that implements currency conversion from one culture to another is implemented as an external function named **ConvertCurrency**, and this function is located in a separate assembly.</span></span> <span data-ttu-id="ee25c-208">**Convertcurrency**関数は、 **AdventureWorks**データベースのテーブルから換算率を取得することによって作業を行います。</span><span class="sxs-lookup"><span data-stu-id="ee25c-208">The **ConvertCurrency** function does its work by retrieving the conversion rate from a table in the **AdventureWorks** database.</span></span> <span data-ttu-id="ee25c-209">変換レートのソースが変化する場合、または既存のコードに他の変更が加えられた場合は、**通貨**UDT に影響を与えずにアセンブリを簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-209">If the source of the conversion rates should ever change, or if there should be any other changes to the existing code, the assembly can be easily modified without affecting the **Currency** UDT.</span></span>  
  
 <span data-ttu-id="ee25c-210">**Currency** UDT 関数と**convertcurrency**関数のコードリストは、共通言語ランタイム (CLR) のサンプルをインストールすることによって確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-210">The code listing for the **Currency** UDT and **ConvertCurrency** functions can be found by installing the common language runtime (CLR) samples.</span></span>  
  
### <a name="using-udts-across-databases"></a><span data-ttu-id="ee25c-211">複数のデータベース間での UDT の使用</span><span class="sxs-lookup"><span data-stu-id="ee25c-211">Using UDTs Across Databases</span></span>  
 <span data-ttu-id="ee25c-212">定義上、UDT のスコープは 1 つのデータベースに設定されています。</span><span class="sxs-lookup"><span data-stu-id="ee25c-212">UDTs are by definition scoped to a single database.</span></span> <span data-ttu-id="ee25c-213">このため、あるデータベースで定義されている UDT を別のデータベースの列定義に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-213">Therefore, a UDT defined in one database cannot be used in a column definition in another database.</span></span> <span data-ttu-id="ee25c-214">UDT を複数のデータベースで使用するには、各データベースで同一のアセンブリに対して CREATE ASSEMBLY ステートメントと CREATE TYPE ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-214">In order to use UDTs in multiple databases, you must execute the CREATE ASSEMBLY and CREATE TYPE statements in each database on identical assemblies.</span></span> <span data-ttu-id="ee25c-215">アセンブリの名前、厳密な名前、カルチャ、バージョン、権限セット、およびバイナリの内容が同じ場合、それらのアセンブリは同一であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-215">Assemblies are considered identical if they have the same name, strong name, culture, version, permission set, and binary contents.</span></span>  
  
 <span data-ttu-id="ee25c-216">両方のデータベースに UDT を登録し、UDT にアクセスできるようになると、あるデータベースの UDT 値を別のデータベースで使用するために変換できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-216">Once the UDT is registered and accessible in both databases, you can convert a UDT value from one database for use in another.</span></span> <span data-ttu-id="ee25c-217">次のシナリオでは、同一の UDT を複数のデータベース間で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-217">Identical UDTs can be used across databases in the following scenarios:</span></span>  
  
-   <span data-ttu-id="ee25c-218">異なるデータベースで定義されているストアド プロシージャの呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ee25c-218">Calling stored procedure defined in different databases.</span></span>  
  
-   <span data-ttu-id="ee25c-219">異なるデータベースで定義されているテーブルのクエリ。</span><span class="sxs-lookup"><span data-stu-id="ee25c-219">Querying tables defined in different databases.</span></span>  
  
-   <span data-ttu-id="ee25c-220">あるデータベース テーブルの UDT 列から UDT データを選択し、その UDT データを同一の UDT 列を使用して 2 つ目のデータベースに挿入する場合。</span><span class="sxs-lookup"><span data-stu-id="ee25c-220">Selecting UDT data from one database table UDT column and inserting it into a second database with an identical UDT column.</span></span>  
  
 <span data-ttu-id="ee25c-221">このような状況では、必要なすべての変換がサーバーで自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-221">In these situations, any conversion required by the server occurs automatically.</span></span> <span data-ttu-id="ee25c-222">[!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 関数または CONVERT 関数を使用して、明示的に変換を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-222">You are not able to perform the conversions explicitly using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions.</span></span>  
  
 <span data-ttu-id="ee25c-223">では、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **tempdb**システムデータベースに作業テーブルを作成するときに、udt を使用するための操作を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ee25c-223">Note that you do not need to take any action for using UDTs when [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] creates work tables in the **tempdb** system database.</span></span> <span data-ttu-id="ee25c-224">これには、カーソル、テーブル変数、および Udt を含み、 **tempdb**を透過的に使用するユーザー定義テーブル値関数の処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee25c-224">This includes the handling of cursors, table variables, and user-defined table-valued functions that include UDTs and that transparently make use of **tempdb**.</span></span> <span data-ttu-id="ee25c-225">ただし、UDT 列を定義する**tempdb**に一時テーブルを明示的に作成する場合は、ユーザーデータベースの場合と同じように、udt を**tempdb**に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee25c-225">However, if you explicitly create a temporary table in **tempdb** that defines a UDT column, then the UDT must be registered in **tempdb** the same way as for a user database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee25c-226">参照</span><span class="sxs-lookup"><span data-stu-id="ee25c-226">See Also</span></span>  
 [<span data-ttu-id="ee25c-227">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="ee25c-227">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
