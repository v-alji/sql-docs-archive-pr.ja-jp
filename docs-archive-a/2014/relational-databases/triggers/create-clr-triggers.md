---
title: CLR トリガーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 3afd841b4f1f9ca567a93c0a20c0a7609a5b45e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644912"
---
# <a name="create-clr-triggers"></a><span data-ttu-id="40097-102">CLR トリガーの作成</span><span class="sxs-lookup"><span data-stu-id="40097-102">Create CLR Triggers</span></span>
  <span data-ttu-id="40097-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR (共通言語ランタイム) で作成されたアセンブリでプログラミングされたデータベース オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="40097-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR).</span></span> <span data-ttu-id="40097-104">CLR で提供される豊富なプログラミング モデルを利用できるデータベース オブジェクトには、DML トリガー、DDL トリガー、ストアド プロシージャ、関数、集計関数、型などがあります。</span><span class="sxs-lookup"><span data-stu-id="40097-104">Database objects that can leverage the rich programming model provided by the CLR include DML triggers, DDL triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="40097-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の CLR トリガー (DML トリガーまたは DDL トリガー) を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="40097-105">Creating a CLR trigger (DML or DDL) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="40097-106">トリガーを .NET Framework でサポートされる言語でクラスとして定義します。</span><span class="sxs-lookup"><span data-stu-id="40097-106">Define the trigger as a class in a .NET Framework-supported language.</span></span> <span data-ttu-id="40097-107">CLR でのトリガーのプログラミング方法の詳細については、「 [CLR トリガー](../../database-engine/dev-guide/clr-triggers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40097-107">For more information about how to program triggers in the CLR, see [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span> <span data-ttu-id="40097-108">次に、適切な言語コンパイラを使用してクラスをコンパイルし、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] のアセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="40097-108">Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="40097-109">CREATE ASSEMBLY ステートメントを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="40097-109">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="40097-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアセンブリの詳細については、「[アセンブリ &#40;データベース エンジン&#41;](../clr-integration/assemblies-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40097-110">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="40097-111">登録したアセンブリを参照するトリガーを作成します。</span><span class="sxs-lookup"><span data-stu-id="40097-111">Create the trigger that references the registered assembly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40097-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] で SQL Server プロジェクトを配置すると、そのプロジェクトで指定されたデータベースにアセンブリが登録されます。</span><span class="sxs-lookup"><span data-stu-id="40097-112">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="40097-113">また、プロジェクトを配置することで、`SqlTrigger` 属性で注釈が付けられたすべてのメソッドの CLR トリガーがデータベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="40097-113">Deploying the project also creates CLR triggers in the database for all methods annotated with the `SqlTrigger` attribute.</span></span> <span data-ttu-id="40097-114">詳細については、「 [CLR データベース オブジェクトの配置](../clr-integration/deploying-clr-database-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40097-114">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40097-115">CLR コードを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能は、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="40097-115">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="40097-116">マネージド コード モジュールを参照するデータベース オブジェクトを作成、変更、削除することはできますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure (Transact-SQL) [を使用して](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) clr enabled オプション [を有効にしないと、](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)では、これらの参照が実行されません。</span><span class="sxs-lookup"><span data-stu-id="40097-116">You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="40097-117">**アセンブリを作成、変更、または削除するには**</span><span class="sxs-lookup"><span data-stu-id="40097-117">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="40097-118">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40097-118">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="40097-119">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40097-119">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="40097-120">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40097-120">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="40097-121">**CLR トリガーを作成するには**</span><span class="sxs-lookup"><span data-stu-id="40097-121">**To create a CLR trigger**</span></span>  
  
-   [<span data-ttu-id="40097-122">CREATE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40097-122">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="40097-123">参照</span><span class="sxs-lookup"><span data-stu-id="40097-123">See Also</span></span>  
 <span data-ttu-id="40097-124">[DML トリガー](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="40097-124">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="40097-125">[CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="40097-125">[Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span></span>  
 [<span data-ttu-id="40097-126">CLR データベース オブジェクトからのデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="40097-126">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
