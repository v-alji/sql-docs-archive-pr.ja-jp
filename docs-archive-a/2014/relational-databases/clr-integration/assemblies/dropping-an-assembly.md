---
title: アセンブリを削除する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: 45d02cbb57459a4c1c11330446021c32dc897353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720031"
---
# <a name="dropping-an-assembly"></a><span data-ttu-id="4e370-102">アセンブリの削除</span><span class="sxs-lookup"><span data-stu-id="4e370-102">Dropping an Assembly</span></span>
  <span data-ttu-id="4e370-103">CREATE ASSEMBLY ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に登録された各アセンブリは、そのアセンブリで提供される機能が不要になれば削除できます。</span><span class="sxs-lookup"><span data-stu-id="4e370-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement can be deleted, or dropped, when the functionality they provide is no longer needed.</span></span> <span data-ttu-id="4e370-104">アセンブリを削除すると、アセンブリと、デバッグ ファイルなどこれに関連するファイルがすべて、データベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="4e370-104">Dropping an assembly removes the assembly and all of its associated files, such as debug files, from the database.</span></span> <span data-ttu-id="4e370-105">アセンブリを削除するには、DROP ASSEMBLY ステートメントを次の構文で使用します。</span><span class="sxs-lookup"><span data-stu-id="4e370-105">To drop an assembly, use the DROP ASSEMBLY statement with the following syntax:</span></span>  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 <span data-ttu-id="4e370-106">DROP ASSEMBLY は、現在実行中のアセンブリを参照するコードに影響を与えることはありませんが、DROP ASSEMBLY を実行後は、アセンブリ コードを起動しようとすると失敗します。</span><span class="sxs-lookup"><span data-stu-id="4e370-106">DROP ASSEMBLY does not interfere with any code referencing the assembly that is currently running, but after DROP ASSEMBLY executes, any attempts to invoke the assembly code fail.</span></span>  
  
 <span data-ttu-id="4e370-107">アセンブリがデータベースに存在する別のアセンブリにより参照されている場合、または、アセンブリが現在のデータベースで共通言語ランタイム (CLR) 関数、プロシージャ、トリガー、ユーザー定義型 (UDT)、ユーザー定義集計 (UDA) により使用されている場合、DROP ASSEMBLY はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="4e370-107">DROP ASSEMBLY returns an error if the assembly is referenced by another assembly that exists in the database, or if it is used by common language runtime (CLR) functions, procedures, triggers, user-defined types (UDTs), or user-defined aggregates (UDAs) in the current database.</span></span> <span data-ttu-id="4e370-108">まず、DROP AGGREGATE、DROP FUNCTION、DROP PROCEDURE、DROP TRIGGER、および DROP TYPE ステートメントを使用して、アセンブリに含まれるすべてのマネージド データベース オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="4e370-108">First use the DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER, and DROP TYPE statements to delete any managed database objects contained in the assembly.</span></span>  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="4e370-109">データベースからの UDT の削除</span><span class="sxs-lookup"><span data-stu-id="4e370-109">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="4e370-110">DROP TYPE ステートメントを使用すると、現在のデータベースから UDT が削除されます。</span><span class="sxs-lookup"><span data-stu-id="4e370-110">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="4e370-111">UDT を削除すると、DROP ASSEMBLY ステートメントを使用してデータベースからアセンブリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="4e370-111">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="4e370-112">次の状況のように、オブジェクトが UDT に依存している場合、DROP TYPE ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="4e370-112">The DROP TYPE statement fails if objects depend on the UDT, as in the following situations:</span></span>  
  
-   <span data-ttu-id="4e370-113">UDT を使用して定義した列を含むデータベース内のテーブル。</span><span class="sxs-lookup"><span data-stu-id="4e370-113">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="4e370-114">WITH SCHEMABINDING 句を使用してデータベースに作成した UDT の変数またはパラメーターを使用する関数、ストアド プロシージャ、またはトリガー。</span><span class="sxs-lookup"><span data-stu-id="4e370-114">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="4e370-115">UDT 依存関係の検出</span><span class="sxs-lookup"><span data-stu-id="4e370-115">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="4e370-116">最初にすべての依存オブジェクトを削除してから、DROP TYPE ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e370-116">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span> <span data-ttu-id="4e370-117">次のクエリでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] **AdventureWorks**データベースで UDT を使用するすべての列とパラメーターを検索します。</span><span class="sxs-lookup"><span data-stu-id="4e370-117">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e370-118">参照</span><span class="sxs-lookup"><span data-stu-id="4e370-118">See Also</span></span>  
 <span data-ttu-id="4e370-119">[CLR 統合アセンブリの管理](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="4e370-119">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="4e370-120">[アセンブリを変更する](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="4e370-120">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="4e370-121">[アセンブリの作成](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="4e370-121">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="4e370-122">[Transact-sql&#41;の集計 &#40;削除](/sql/t-sql/statements/drop-aggregate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e370-122">[DROP AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span></span>  
 <span data-ttu-id="4e370-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e370-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span></span>  
 <span data-ttu-id="4e370-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e370-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="4e370-125">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e370-125">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="4e370-126">DROP TYPE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4e370-126">DROP TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
