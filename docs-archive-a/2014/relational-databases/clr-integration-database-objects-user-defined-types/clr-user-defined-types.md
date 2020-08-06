---
title: CLR ユーザー定義型 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: e4e19323eeac9e0a1148924543f71aa7de5619b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645669"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="3b777-102">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="3b777-102">CLR User-Defined Types</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3b777-103">では、.NET Framework CLR (共通言語ランタイム) で作成されているアセンブリでプログラミングしたデータベース オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b777-103">gives you the ability to create database objects that are programmed against an assembly created in the.NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="3b777-104">CLR で用意された豊富なプログラミング モデルを使用できるデータベース オブジェクトには、トリガー、ストアド プロシージャ、関数、集計関数、型などがあります。</span><span class="sxs-lookup"><span data-stu-id="3b777-104">Database objects that can take advantage of the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b777-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CLR コードを実行する機能が既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="3b777-105">The ability to execute CLR code is set to OFF by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3b777-106">CLR を有効にするには、 **sp_configure**システムストアドプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b777-106">The CLR can be enabled by using the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="3b777-107">以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、ユーザー定義型 (udt) を使用してサーバーのスカラー型システムを拡張し、データベース内の CLR オブジェクトのストレージを有効にすることができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3b777-107">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can use user-defined types (UDTs) to extend the scalar type system of the server, enabling storage of CLR objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="3b777-108">1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型で構成される従来の別名データ型とは異なり、UDT には複数の要素や複数の動作を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3b777-108">UDTs can contain multiple elements and can have behaviors, differentiating them from the traditional alias data types which consist of a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system data type.</span></span>  
  
 <span data-ttu-id="3b777-109">UDT はシステム全体からアクセスされるので、UDT を複合データ型に使用すると、パフォーマンスに悪影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="3b777-109">Because UDTs are accessed by the system as a whole, their use for complex data types may negatively impact performance.</span></span> <span data-ttu-id="3b777-110">通常、複合データは従来の行やテーブルを使用する場合に最適になるようにモデル化されています。</span><span class="sxs-lookup"><span data-stu-id="3b777-110">Complex data is generally best modeled using traditional rows and tables.</span></span> <span data-ttu-id="3b777-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の UDT は、次のような場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="3b777-111">UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are well suited to the following:</span></span>  
  
-   <span data-ttu-id="3b777-112">日付型、時刻型、通貨型、および拡張数値型</span><span class="sxs-lookup"><span data-stu-id="3b777-112">Date, time, currency, and extended numeric types</span></span>  
  
-   <span data-ttu-id="3b777-113">地理空間アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3b777-113">Geospatial applications</span></span>  
  
-   <span data-ttu-id="3b777-114">エンコードされたデータまたは暗号化されたデータ</span><span class="sxs-lookup"><span data-stu-id="3b777-114">Encoded or encrypted data</span></span>  
  
 <span data-ttu-id="3b777-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で UDT を開発する処理は、次の手順から構成されています。</span><span class="sxs-lookup"><span data-stu-id="3b777-115">The process of developing UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="3b777-116">**UDT を定義するアセンブリをコーディングしてビルドします。**</span><span class="sxs-lookup"><span data-stu-id="3b777-116">**Code and build the assembly that defines the UDT.**</span></span> <span data-ttu-id="3b777-117">UDT は、検証可能なコードを生成する .NET Framework 共通言語ランタイム (CLR) でサポートされる任意の言語を使用して定義されます。</span><span class="sxs-lookup"><span data-stu-id="3b777-117">UDTs are defined using any of the languages supported by the.NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="3b777-118">このような言語には、Visual C# や Visual Basic .NET があります。</span><span class="sxs-lookup"><span data-stu-id="3b777-118">This includes Visual C# and Visual Basic .NET.</span></span> <span data-ttu-id="3b777-119">データは、.NET Framework のクラスまたは構造体のフィールドやプロパティとして公開され、動作はクラスまたは構造体のメソッドによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="3b777-119">The data is exposed as fields and properties of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span>  
  
2.  <span data-ttu-id="3b777-120">**アセンブリを登録します。**</span><span class="sxs-lookup"><span data-stu-id="3b777-120">**Register the assembly.**</span></span> <span data-ttu-id="3b777-121">UDT は、Visual Studio のユーザー インターフェイスを使用してデータベース プロジェクトに配置することも、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY ステートメントを使用して、クラスまたは構造体を含むアセンブリをデータベースにコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3b777-121">UDTs can be deployed through the Visual Studio user interface in a database project, or by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, which copies the assembly containing the class or structure into a database.</span></span>  
  
3.  <span data-ttu-id="3b777-122">**SQL Server で UDT を作成します。**</span><span class="sxs-lookup"><span data-stu-id="3b777-122">**Create the UDT in SQL Server.**</span></span> <span data-ttu-id="3b777-123">アセンブリがホスト データベースに読み込まれた後、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE ステートメントを使用して UDT を作成し、UDT のメンバーとしてクラスまたは構造体のメンバーを公開します。</span><span class="sxs-lookup"><span data-stu-id="3b777-123">Once an assembly is loaded into a host database, you use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement to create a UDT and expose the members of the class or structure as members of the UDT.</span></span> <span data-ttu-id="3b777-124">UDT は 1 つのデータベースのコンテキストにのみ存在します。UDT はいったん登録されると、作成時のベースとなっていた外部ファイルに対する依存関係がなくなります。</span><span class="sxs-lookup"><span data-stu-id="3b777-124">UDTs exist only in the context of a single database, and, once registered, have no dependencies on the external files from which they were created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3b777-125">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは、.NET Framework アセンブリから作成された UDT がサポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="3b777-125">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], UDTs created from .NET Framework assemblies were not supported.</span></span> <span data-ttu-id="3b777-126">ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_addtype**を使用して別名データ型を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3b777-126">However, you can still use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types by using **sp_addtype**.</span></span> <span data-ttu-id="3b777-127">CREATE TYPE 構文を使用すると、ネイティブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー定義データ型と UDT の両方を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b777-127">The CREATE TYPE syntax can be used for creating both native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined data types and UDTs.</span></span>  
  
4.  <span data-ttu-id="3b777-128">**UDT を使用してテーブル、変数、またはパラメーターを作成する**以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、ユーザー定義型は、テーブルの列定義、バッチ内の変数、 [!INCLUDE[tsql](../../includes/tsql-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数やストアドプロシージャの引数として使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b777-128">**Create tables, variables, or parameters using the UDT** Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user-defined type can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b777-129">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3b777-129">In This Section</span></span>  
 [<span data-ttu-id="3b777-130">ユーザー定義型の作成</span><span class="sxs-lookup"><span data-stu-id="3b777-130">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
 <span data-ttu-id="3b777-131">UDT の作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b777-131">Describes how to create UDTs.</span></span>  
  
 [<span data-ttu-id="3b777-132">SQL Server でのユーザー定義型の登録</span><span class="sxs-lookup"><span data-stu-id="3b777-132">Registering User-Defined Types in SQL Server</span></span>](registering-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="3b777-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での UDT の登録方法と管理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b777-133">Describes how to register and manage UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="3b777-134">SQL Server でのユーザー定義型の使用</span><span class="sxs-lookup"><span data-stu-id="3b777-134">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="3b777-135">UDT を使用してクエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b777-135">Describes how to create queries using UDTs.</span></span>  
  
 [<span data-ttu-id="3b777-136">ADO.NET でのユーザー定義型へのアクセス</span><span class="sxs-lookup"><span data-stu-id="3b777-136">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
 <span data-ttu-id="3b777-137">ADO.NET の .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して UDT を操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b777-137">Describes how to work with UDTs using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ADO.NET.</span></span>  
  
  
