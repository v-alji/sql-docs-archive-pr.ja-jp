---
title: UDT テーブルと列の定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: aa9596629ed8b4877b1793fa0c56956c52989499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646174"
---
# <a name="defining-udt-tables-and-columns"></a><span data-ttu-id="b433f-102">UDT テーブルと UDT 列の定義</span><span class="sxs-lookup"><span data-stu-id="b433f-102">Defining UDT Tables and Columns</span></span>
  <span data-ttu-id="b433f-103">ユーザー定義型 (UDT) 定義を含むアセンブリがデータベースに登録されると [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、列定義で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b433f-103">Once the assembly containing the user-defined type (UDT) definition has been registered in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, it can be used in a column definition.</span></span>  
  
## <a name="creating-tables-with-udts"></a><span data-ttu-id="b433f-104">UDT を含むテーブルの作成</span><span class="sxs-lookup"><span data-stu-id="b433f-104">Creating Tables with UDTs</span></span>  
 <span data-ttu-id="b433f-105">テーブルに UDT 列を作成するために特別な構文は用意されていません。</span><span class="sxs-lookup"><span data-stu-id="b433f-105">There is no special syntax for creating a UDT column in a table.</span></span> <span data-ttu-id="b433f-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のデータ型であるかのように、列定義に UDT の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b433f-106">You can use the name of the UDT in a column definition as though it were one of the intrinsic [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="b433f-107">次の CREATE TABLE ステートメントでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **Points**という名前のテーブルを作成します。この列は**id**列として定義され、テーブルの主キーとして定義されてい `int` ます。</span><span class="sxs-lookup"><span data-stu-id="b433f-107">The following CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates a table named **Points**, with a column named **ID,** which is defined as an `int` identity column and \ the primary key for the table.</span></span> <span data-ttu-id="b433f-108">2番目の列は**Pointvalue**という名前で、データ型は**point**です。</span><span class="sxs-lookup"><span data-stu-id="b433f-108">The second column is named **PointValue**, with a data type of **Point**.</span></span> <span data-ttu-id="b433f-109">この例で使用するスキーマ名は**dbo**です。</span><span class="sxs-lookup"><span data-stu-id="b433f-109">The schema name used in this example is **dbo**.</span></span> <span data-ttu-id="b433f-110">この操作には、スキーマ名を指定する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b433f-110">Note that you must have the necessary permissions to specify a schema name.</span></span> <span data-ttu-id="b433f-111">スキーマ名を省略すると、データベース ユーザーの既定のスキーマが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b433f-111">If you omit the schema name, the default schema for the database user is used.</span></span>  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a><span data-ttu-id="b433f-112">UDT 列でのインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="b433f-112">Creating Indexes on UDT Columns</span></span>  
 <span data-ttu-id="b433f-113">UDT 列のインデックスの作成には次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="b433f-113">There are two options for indexing a UDT column:</span></span>  
  
-   <span data-ttu-id="b433f-114">完全な値のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b433f-114">Index the full value.</span></span> <span data-ttu-id="b433f-115">この場合、UDT がバイナリ順であれば、CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して UDT 列全体のインデックスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b433f-115">In this case, if the UDT is binary ordered, you can create an index over the entire UDT column by using the CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="b433f-116">UDT 式のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b433f-116">Index UDT expressions.</span></span> <span data-ttu-id="b433f-117">保存される計算列のインデックスを UDT 式を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="b433f-117">You can create indexes on persisted computed columns over UDT expressions.</span></span> <span data-ttu-id="b433f-118">UDT のフィールド、メソッド、またはプロパティを UDT 式にできます。</span><span class="sxs-lookup"><span data-stu-id="b433f-118">The UDT expression can be a field, method, or property of a UDT.</span></span> <span data-ttu-id="b433f-119">この式は決定的である必要があり、この式でデータ アクセスを実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="b433f-119">The expression must be deterministic and must not perform data access.</span></span>  
  
 <span data-ttu-id="b433f-120">詳細については、「 [CLR ユーザー定義型](clr-user-defined-types.md)」および「 [CREATE INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b433f-120">For more information, see [CLR User-Defined Types](clr-user-defined-types.md) and [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b433f-121">参照</span><span class="sxs-lookup"><span data-stu-id="b433f-121">See Also</span></span>  
 [<span data-ttu-id="b433f-122">SQL Server でのユーザー定義型の使用</span><span class="sxs-lookup"><span data-stu-id="b433f-122">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
