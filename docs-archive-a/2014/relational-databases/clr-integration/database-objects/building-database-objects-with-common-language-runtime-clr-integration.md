---
title: 共通言語ランタイム (CLR) 統合によるデータベースオブジェクトの構築 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c849c095a3be1c590e6fcb3ce87a0725eb795c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642123"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a><span data-ttu-id="42212-102">CLR (共通言語ランタイム) 統合によるデータベース オブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="42212-102">Building Database Objects with Common Language Runtime (CLR) Integration</span></span>
  <span data-ttu-id="42212-103">[!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)]"CLR ルーチン" と呼ばれるを使用してデータベースオブジェクトを構築でき [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="42212-103">You can build database objects using the [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is referred to as a "CLR routine."</span></span> <span data-ttu-id="42212-104">CLR ルーチンには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="42212-104">These routines include:</span></span>  
  
-   <span data-ttu-id="42212-105">スカラー UDF (ユーザー定義スカラー値関数)</span><span class="sxs-lookup"><span data-stu-id="42212-105">Scalar-valued user-defined functions (scalar UDFs)</span></span>  
  
-   <span data-ttu-id="42212-106">ユーザー定義 TVF (テーブル値関数)</span><span class="sxs-lookup"><span data-stu-id="42212-106">Table-valued user-defined functions (TVFs)</span></span>  
  
-   <span data-ttu-id="42212-107">UDP (ユーザー定義プロシージャ)</span><span class="sxs-lookup"><span data-stu-id="42212-107">User-defined procedures (UDPs)</span></span>  
  
-   <span data-ttu-id="42212-108">ユーザー定義トリガー</span><span class="sxs-lookup"><span data-stu-id="42212-108">User-defined triggers</span></span>  
  
 <span data-ttu-id="42212-109">CLR ルーチンは、マネージド コード内ではそれぞれ同じ構造になります。</span><span class="sxs-lookup"><span data-stu-id="42212-109">CLR routines have the same structure in managed code.</span></span> <span data-ttu-id="42212-110">CLR ルーチンは、クラスの public static ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET では shared) メソッドにマップされます。</span><span class="sxs-lookup"><span data-stu-id="42212-110">They are mapped to public, static (shared in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) methods of a class.</span></span> <span data-ttu-id="42212-111">ルーチン以外に、.NET Framework を使用して UDT (ユーザー定義型) やユーザー定義集計関数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="42212-111">In addition to routines, user-defined types (UDTs) and user-defined aggregate functions can also be defined using the .NET Framework.</span></span> <span data-ttu-id="42212-112">UDT とユーザー定義集計は、.NET Framework クラス全体にマップされます。</span><span class="sxs-lookup"><span data-stu-id="42212-112">UDTs and user-defined aggregates are mapped to entire .NET Framework classes.</span></span>  
  
 <span data-ttu-id="42212-113">.NET Framework ルーチンの各型には、同等のを使用できるがあり [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="42212-113">Each type of .NET Framework routine has a [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] that the [!INCLUDE[tsql](../../../includes/tsql-md.md)] equivalent can be used.</span></span> <span data-ttu-id="42212-114">たとえば、スカラー UDF は任意のスカラー式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="42212-114">For instance, scalar UDFs can be used in any scalar expression.</span></span> <span data-ttu-id="42212-115">また、TVF は任意の FROM 句で使用できます。</span><span class="sxs-lookup"><span data-stu-id="42212-115">A TVF can be used in any FROM clause.</span></span> <span data-ttu-id="42212-116">プロシージャは、EXEC ステートメントやクライアント アプリケーションから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="42212-116">A procedure can be invoked in an EXEC statement or invoked from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42212-117">効果的であるとクエリ オプティマイザーで判断された場合は、共通言語ランタイムでの CLR オブジェクト (ユーザー定義関数、ユーザー定義型、またはトリガー) の実行を複数のスレッドで行うことができます (並列プラン)。</span><span class="sxs-lookup"><span data-stu-id="42212-117">Execution of a CLR object (user-defined function, user-defined type, or trigger) on the common language runtime can take place on multiple threads (parallel plan), if the query optimizer decides it is beneficial.</span></span> <span data-ttu-id="42212-118">ただし、ユーザー定義関数がデータにアクセスする場合は、直列プランで実行されます。</span><span class="sxs-lookup"><span data-stu-id="42212-118">However, if a user-defined function accesses data, execution will be  on a serial plan.</span></span> <span data-ttu-id="42212-119">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] よりも前のサーバー バージョンで実行したときに、ユーザー定義関数に LOB パラメーターが含まれていたり、ユーザー定義関数から値が返される場合も、直列プランで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42212-119">When executed on a server version prior to [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], if a user-defined function contains LOB parameters or return values, execution also must be on a serial plan.</span></span>  
  
 <span data-ttu-id="42212-120">次の表に、このセクションで説明するトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="42212-120">The following table lists the topics covered in this section.</span></span>  
  
 [<span data-ttu-id="42212-121">CLR 統合の概要</span><span class="sxs-lookup"><span data-stu-id="42212-121">Getting Started with CLR Integration</span></span>](getting-started-with-clr-integration.md)  
 <span data-ttu-id="42212-122">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と CLR との統合を使用したオブジェクトのコンパイルに必要なライブラリと名前空間の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="42212-122">Provides a brief overview of the libraries and namespaces required to compile object using CLR integration with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="42212-123">また、例として "Hello World" CLR ストアド プロシージャを紹介します。</span><span class="sxs-lookup"><span data-stu-id="42212-123">Includes an example "Hello World" CLR stored procedure.</span></span>  
  
 [<span data-ttu-id="42212-124">サポートされている .NET Framework ライブラリ</span><span class="sxs-lookup"><span data-stu-id="42212-124">Supported .NET Framework Libraries</span></span>](supported-net-framework-libraries.md)  
 <span data-ttu-id="42212-125">CLR 統合でサポートされる .NET Framework ライブラリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="42212-125">Provides information on the .NET Framework libraries supported by CLR integration.</span></span>  
  
 [<span data-ttu-id="42212-126">CLR 統合プログラミング モデルの制限事項</span><span class="sxs-lookup"><span data-stu-id="42212-126">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
 <span data-ttu-id="42212-127">CLR 統合プログラミング モデルの制限事項に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="42212-127">Provides information about CLR integration programming model restrictions.</span></span>  
  
 [<span data-ttu-id="42212-128">.NET Framework での SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="42212-128">SQL Server Data Types in the .NET Framework</span></span>](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 <span data-ttu-id="42212-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と、.NET Framework での同等のデータ型の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="42212-129">An overview of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types and their .NET Framework equivalents.</span></span>  
  
 [<span data-ttu-id="42212-130">CLR 統合のカスタム属性の概要</span><span class="sxs-lookup"><span data-stu-id="42212-130">Overview of CLR Integration Custom Attributes</span></span>](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 <span data-ttu-id="42212-131">CLR 統合のカスタム属性に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="42212-131">Provides information about CLR integration custom attributes.</span></span>  
  
 [<span data-ttu-id="42212-132">CLR ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="42212-132">CLR User-Defined Functions</span></span>](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 <span data-ttu-id="42212-133">テーブル値関数、スカラー関数、ユーザー定義集計関数など、さまざまな種類の CLR 関数の実装方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42212-133">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="42212-134">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="42212-134">CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="42212-135">CLR のユーザー定義型を実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42212-135">Describes how to implement and use CLR user-defined types.</span></span>  
  
 [<span data-ttu-id="42212-136">CLR ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="42212-136">CLR Stored Procedures</span></span>](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 <span data-ttu-id="42212-137">CLR のストアド プロシージャを実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42212-137">Describes how to implement and use CLR stored procedures.</span></span>  
  
 [<span data-ttu-id="42212-138">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="42212-138">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
 <span data-ttu-id="42212-139">CLR のトリガーを実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42212-139">Describes how to implement and use CLR triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42212-140">参照</span><span class="sxs-lookup"><span data-stu-id="42212-140">See Also</span></span>  
 [<span data-ttu-id="42212-141">CLR&#41; 統合の概要 &#40;共通言語ランタイム</span><span class="sxs-lookup"><span data-stu-id="42212-141">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](../common-language-runtime-integration-overview.md)  
  
  
