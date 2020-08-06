---
title: ユーザー定義集計の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
ms.openlocfilehash: c91179cb194bbfb79e8e7a8476e9725877b88afa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740782"
---
# <a name="create-user-defined-aggregates"></a><span data-ttu-id="5b384-102">ユーザー定義集計の作成</span><span class="sxs-lookup"><span data-stu-id="5b384-102">Create User-defined Aggregates</span></span>
  <span data-ttu-id="5b384-103">CLR アセンブリでプログラミングされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部にデータベース オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5b384-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in a CLR assembly.</span></span> <span data-ttu-id="5b384-104">CLR が提供する豊富なプログラミング モデルを利用できるデータベース オブジェクトには、トリガー、ストアド プロシージャ、関数、集計関数、型などがあります。</span><span class="sxs-lookup"><span data-stu-id="5b384-104">Database objects that can leverage the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="5b384-105">[!INCLUDE[tsql](../../includes/tsql-md.md)]が提供する組み込みの集計関数と同様に、ユーザー定義集計関数も一連の値に対して計算を実行し、その結果 1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="5b384-105">Like the built-in aggregate functions provided in [!INCLUDE[tsql](../../includes/tsql-md.md)], user-defined aggregate functions perform a calculation on a set of values and return a single value.</span></span>  
  
 <span data-ttu-id="5b384-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのユーザー定義集計関数の作成は、次の手順で行われます。</span><span class="sxs-lookup"><span data-stu-id="5b384-106">Creating a user-defined aggregate function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="5b384-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework でサポートされる言語のクラスとしてユーザー定義集計関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="5b384-107">Define the user-defined aggregate function as a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-supported language.</span></span> <span data-ttu-id="5b384-108">CLR でのユーザー定義集計のプログラミング方法の詳細については、「 [CLR ユーザー定義集計](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b384-108">For more information about how to program user-defined aggregates in the CLR, see [CLR User-Defined Aggregates](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md).</span></span> <span data-ttu-id="5b384-109">適切な言語コンパイラを使用してこのクラスをコンパイルし、CLR アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b384-109">Compile this class to build a CLR assembly using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="5b384-110">CREATE ASSEMBLY ステートメントを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="5b384-110">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="5b384-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアセンブリの詳細については、「[アセンブリ &#40;データベース エンジン&#41;](../clr-integration/assemblies-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b384-111">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="5b384-112">CREATE AGGREGATE ステートメントを使用して、登録済みのアセンブリを参照するユーザー定義集計を作成します。</span><span class="sxs-lookup"><span data-stu-id="5b384-112">Create the user-defined aggregate that references the registered assembly using the CREATE AGGREGATE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b384-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] で SQL Server プロジェクトを配置すると、そのプロジェクトで指定されたデータベースにアセンブリが登録されます。</span><span class="sxs-lookup"><span data-stu-id="5b384-113">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="5b384-114">また、プロジェクトを配置することで、`SqlUserDefinedAggregate` 属性で注釈が付けられたすべてのクラス定義に対応するユーザー定義集計がデータベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="5b384-114">Deploying the project also creates a user-defined aggregate in the database for all class definitions annotated with the `SqlUserDefinedAggregate` attribute.</span></span> <span data-ttu-id="5b384-115">詳細については、「 [CLR データベース オブジェクトの配置](../clr-integration/deploying-clr-database-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b384-115">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b384-116">CLR コードを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能は、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="5b384-116">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="5b384-117">マネージド コード モジュールを参照するデータベース オブジェクトを作成、変更、削除することはできますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure (Transact-SQL) [を使用して](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) clr enabled オプション [を有効にしないと、](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)では、これらの参照が実行されません。</span><span class="sxs-lookup"><span data-stu-id="5b384-117">You can create, alter and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="5b384-118">**アセンブリを作成、変更、または削除するには**</span><span class="sxs-lookup"><span data-stu-id="5b384-118">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="5b384-119">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b384-119">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="5b384-120">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b384-120">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="5b384-121">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b384-121">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="5b384-122">**ユーザー定義集計を作成するには**</span><span class="sxs-lookup"><span data-stu-id="5b384-122">**To create a user-defined aggregate**</span></span>  
  
-   [<span data-ttu-id="5b384-123">CREATE AGGREGATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b384-123">CREATE AGGREGATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="5b384-124">参照</span><span class="sxs-lookup"><span data-stu-id="5b384-124">See Also</span></span>  
 [<span data-ttu-id="5b384-125">CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="5b384-125">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
