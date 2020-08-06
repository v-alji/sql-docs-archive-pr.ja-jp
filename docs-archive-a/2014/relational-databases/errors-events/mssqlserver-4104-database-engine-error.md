---
title: MSSQLSERVER_4104 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4104 (Database Engine error)
ms.assetid: 52dc32d8-97ad-4ef0-834d-2e68f215d007
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbbc28a3e15af6fdc8fd44633ccbdfc46e49149d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643394"
---
# <a name="mssqlserver_4104"></a><span data-ttu-id="c84fd-102">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="c84fd-102">MSSQLSERVER_4104</span></span>
    
## <a name="details"></a><span data-ttu-id="c84fd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c84fd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c84fd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c84fd-104">Product Name</span></span>|<span data-ttu-id="c84fd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c84fd-105">SQL Server</span></span>|  
|<span data-ttu-id="c84fd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c84fd-106">Event ID</span></span>|<span data-ttu-id="c84fd-107">4104</span><span class="sxs-lookup"><span data-stu-id="c84fd-107">4104</span></span>|  
|<span data-ttu-id="c84fd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c84fd-108">Event Source</span></span>|<span data-ttu-id="c84fd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c84fd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c84fd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c84fd-110">Component</span></span>|<span data-ttu-id="c84fd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c84fd-111">SQLEngine</span></span>|  
|<span data-ttu-id="c84fd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c84fd-112">Symbolic Name</span></span>|<span data-ttu-id="c84fd-113">ALG_MULTI_ID_BAD</span><span class="sxs-lookup"><span data-stu-id="c84fd-113">ALG_MULTI_ID_BAD</span></span>|  
|<span data-ttu-id="c84fd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c84fd-114">Message Text</span></span>|<span data-ttu-id="c84fd-115">マルチパート識別子 "%.\*ls" をバインドできませんでした。</span><span class="sxs-lookup"><span data-stu-id="c84fd-115">The multi-part identifier "%.\*ls" could not be bound.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c84fd-116">説明</span><span class="sxs-lookup"><span data-stu-id="c84fd-116">Explanation</span></span>  
 <span data-ttu-id="c84fd-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのエンティティの名前は、そのエンティティの "*識別子*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-117">The name of an entity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is referred to as its *identifier*.</span></span> <span data-ttu-id="c84fd-118">識別子は、クエリ内で列やテーブルの名前を指定する場合など、エンティティを参照するときは必ず使用します。</span><span class="sxs-lookup"><span data-stu-id="c84fd-118">You use identifiers whenever you reference entities, for example, by specifying column and table names in a query.</span></span> <span data-ttu-id="c84fd-119">マルチパート識別子には、1 つ以上の修飾子が識別子のプレフィックスとして含まれます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-119">A multi-part identifier contains one or more qualifiers as a prefix for the identifier.</span></span> <span data-ttu-id="c84fd-120">たとえば、テーブル識別子は、そのテーブルが含まれるデータベースの名前やスキーマの名前などの修飾子をプレフィックスとして持つことができます。また列識別子は、テーブル名やテーブル別名などの修飾子をプレフィックスとして持つことができます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-120">For example, a table identifier may be prefixed with qualifiers such as the database name and schema name in which the table is contained, or a column identifier may be prefixed with qualifiers such as a table name or table alias.</span></span>  
  
 <span data-ttu-id="c84fd-121">エラー 4104 は、指定されたマルチパート識別子を既存のエンティティにマップできなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="c84fd-121">Error 4104 indicates that the specified multi-part identifier could not be mapped to an existing entity.</span></span> <span data-ttu-id="c84fd-122">このエラーは、次のような状況で返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c84fd-122">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="c84fd-123">列名のプレフィックスとして指定された修飾子と、クエリで使用されているテーブル名または別名が一致しない。</span><span class="sxs-lookup"><span data-stu-id="c84fd-123">The qualifier supplied as a prefix for a column name does not correspond to any table or alias name used in the query.</span></span>  
  
     <span data-ttu-id="c84fd-124">たとえば、次のステートメントでは、テーブル別名 (`Dept`) を列プレフィックスとして使用していますが、このテーブル別名は FROM 句で参照されていません。</span><span class="sxs-lookup"><span data-stu-id="c84fd-124">For example, the following statement uses a table alias (`Dept`) as a column prefix, but the table alias is not referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department;  
    ```  
  
     <span data-ttu-id="c84fd-125">次のステートメントでは、WHERE 句で 2 つのテーブル間の JOIN 条件の一部としてマルチパート列識別子 `TableB.KeyCol` を指定していますが、`TableB` はクエリで明示的に参照されていません。</span><span class="sxs-lookup"><span data-stu-id="c84fd-125">In the following statements, a multi-part column identifier `TableB.KeyCol` is specified in the WHERE clause as part of a JOIN condition between two tables, however, `TableB` is not explicitly referenced in the query.</span></span>  
  
    ```  
    DELETE FROM TableA WHERE TableA.KeyCol = TableB.KeyCol;  
    ```  
  
    ```  
    SELECT 'X' FROM TableA WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="c84fd-126">FROM 句でテーブルの別名を指定しているが、列のプレフィックスとして指定しているのはテーブル名である。</span><span class="sxs-lookup"><span data-stu-id="c84fd-126">An alias name for the table is supplied in the FROM clause, but the qualifier supplied for a column is the table name.</span></span> <span data-ttu-id="c84fd-127">たとえば、次のステートメントでは、FROM 句でテーブルの別名 (`Department`) を参照しているにもかかわらず、テーブル名 `Dept` を列プレフィックスとして使用しています。</span><span class="sxs-lookup"><span data-stu-id="c84fd-127">For example, the following statement uses the table name `Department` as the column prefix; however, the table has an alias (`Dept`) referenced in the FROM clause.</span></span>  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department AS Dept;  
    ```  
  
     <span data-ttu-id="c84fd-128">別名を使用する場合、テーブル名をステートメントの他の部分で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c84fd-128">When an alias is used, the table name cannot be used elsewhere in the statement.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c84fd-129">では、マルチパート識別子がテーブルをプレフィックスとする列を参照しているか、または列をプレフィックスとする CLR ユーザー定義データ型 (UDT) のプロパティを参照しているかを判断できない。</span><span class="sxs-lookup"><span data-stu-id="c84fd-129">is unable to determine if the multi-part identifier refers to a column prefixed by a table or to a property of a CLR user-defined data type (UDT) prefixed by a column.</span></span> <span data-ttu-id="c84fd-130">このような状況が発生するのは、UDT 列のプロパティを参照するとき、列名にテーブル名をプレフィックスとして加える場合と同じように、列名とプロパティ名の間に区切り文字としてピリオド (.) を使用するためです。</span><span class="sxs-lookup"><span data-stu-id="c84fd-130">This happens because properties of UDT columns are referenced by using the period separator (.) between the column name and the property name in the same way that a column name is prefixed with a table name.</span></span> <span data-ttu-id="c84fd-131">次の例では、`a` と `b` という 2 つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c84fd-131">The following example creates two tables, `a` and `b`.</span></span> <span data-ttu-id="c84fd-132">テーブル `b` は列 `a` を含み、この列は CLR UDT の `dbo.myudt2` をデータ型として使用します。</span><span class="sxs-lookup"><span data-stu-id="c84fd-132">Table `b` contains column `a`, which uses a CLR UDT `dbo.myudt2` as its data type.</span></span> <span data-ttu-id="c84fd-133">SELECT ステートメントはマルチパート識別子 `a.c2` を含みます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-133">The SELECT statement contains a multi-part identifier `a.c2`.</span></span>  
  
    ```  
    CREATE TABLE a (c2 int);   
    GO  
    ```  
  
    ```  
    CREATE TABLE b (a dbo.myudt2);   
    GO  
    ```  
  
    ```  
    SELECT a.c2 FROM a, b;   
    ```  
  
     <span data-ttu-id="c84fd-134">UDT `myudt2` が `c2` という名前のプロパティを持たないと仮定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、識別子 `a.c2` がテーブル `a` の列 `c2` を参照するのか、テーブル `b` の列 `a` のプロパティ `c2` を参照するのかを判断できません。</span><span class="sxs-lookup"><span data-stu-id="c84fd-134">Assuming that the UDT `myudt2` does not have a property named `c2`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot determine whether identifier `a.c2`refers to column `c2` in table `a` or to the column `a`, property `c2` in table `b`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c84fd-135">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c84fd-135">User Action</span></span>  
  
-   <span data-ttu-id="c84fd-136">列プレフィックスとクエリの FROM 句で指定したテーブル名または別名を一致させます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-136">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="c84fd-137">FROM 句でテーブルの別名を定義した場合、テーブルに関連する列の修飾子として使用できるのはその別名だけです。</span><span class="sxs-lookup"><span data-stu-id="c84fd-137">If an alias is defined for a table name in the FROM clause, you can only use the alias as a qualifier for columns associated with that table.</span></span>  
  
     <span data-ttu-id="c84fd-138">`HumanResources.Department` テーブルを参照する上記のステートメントは、次のように修正できます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-138">The statements above that reference the `HumanResources.Department` table can be corrected as follows:</span></span>  
  
    ```  
    SELECT Dept.Name FROM HumanResources.Department AS Dept;  
    GO  
    ```  
  
    ```  
    SELECT Department.Name FROM HumanResources.Department;  
    GO  
    ```  
  
-   <span data-ttu-id="c84fd-139">すべてのテーブルがクエリで指定されていること、およびテーブル間の JOIN 条件が正しく指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c84fd-139">Ensure that all tables are specified in the query and that the JOIN conditions between tables are specified correctly.</span></span> <span data-ttu-id="c84fd-140">上記の DELETE ステートメントは次のように修正できます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-140">The DELETE statement above can be corrected as follows:</span></span>  
  
    ```  
    DELETE FROM dbo.TableA  
    WHERE TableA.KeyCol = (SELECT TableB.KeyCol   
                            FROM TableB   
                            WHERE TableA.KeyCol = TableB.KeyCol);  
    GO  
    ```  
  
     <span data-ttu-id="c84fd-141">`TableA` に対する上記の SELECT ステートメントは次のように修正できます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-141">The SELECT statement above for `TableA` can be corrected as follows:</span></span>  
  
    ```  
    SELECT 'X' FROM TableA, TableB WHERE TableB.KeyCol = TableA.KeyCol;  
    ```  
  
     <span data-ttu-id="c84fd-142">or</span><span class="sxs-lookup"><span data-stu-id="c84fd-142">or</span></span>  
  
    ```  
    SELECT 'X' FROM TableA INNER JOIN TableB ON TableB.KeyCol = TableA.KeyCol;  
    ```  
  
-   <span data-ttu-id="c84fd-143">明確に定義された一意の名前を識別子に使用します。</span><span class="sxs-lookup"><span data-stu-id="c84fd-143">Use unique, clearly defined names for identifiers.</span></span> <span data-ttu-id="c84fd-144">こうすることにより、コードの読みやすさと管理性が向上し、複数のエンティティをあいまいに参照する危険性も最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="c84fd-144">Doing so makes your code easier to read and maintain, and it also minimizes the risk of ambiguous references to multiple entities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84fd-145">参照</span><span class="sxs-lookup"><span data-stu-id="c84fd-145">See Also</span></span>  
 <span data-ttu-id="c84fd-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="c84fd-146">[MSSQLSERVER_107](mssqlserver-107-database-engine-error.md) </span></span>  
 [<span data-ttu-id="c84fd-147">データベース識別子</span><span class="sxs-lookup"><span data-stu-id="c84fd-147">Database Identifiers</span></span>](../databases/database-identifiers.md)  
  
  
