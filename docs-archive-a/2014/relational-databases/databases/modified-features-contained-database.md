---
title: 変更された機能 (包含データベース) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc52821deeb879022881f838c61823b23c0c10c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742158"
---
# <a name="modified-features-contained-database"></a><span data-ttu-id="a0edf-102">変更された機能 (包含データベース)</span><span class="sxs-lookup"><span data-stu-id="a0edf-102">Modified Features (Contained Database)</span></span>
  <span data-ttu-id="a0edf-103">次の機能は、部分的包含データベースでサポートされるように変更されました。</span><span class="sxs-lookup"><span data-stu-id="a0edf-103">The following features have been modified to be supported by a partially contained database.</span></span> <span data-ttu-id="a0edf-104">通常、機能の変更は、データベース境界を越えないように行われます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-104">Features are usually modified so they do not cross the database boundary.</span></span>  
  
 <span data-ttu-id="a0edf-105">詳細については、「 [包含データベース](contained-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0edf-105">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
## <a name="alter-database"></a><span data-ttu-id="a0edf-106">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="a0edf-106">ALTER DATABASE</span></span>  
  
### <a name="application-level"></a><span data-ttu-id="a0edf-107">アプリケーション レベル</span><span class="sxs-lookup"><span data-stu-id="a0edf-107">Application Level</span></span>  
 <span data-ttu-id="a0edf-108">ALTER DATABASE ステートメントを包含データベース内から使用する場合の構文は、非包含データベースに使用する構文と異なります。</span><span class="sxs-lookup"><span data-stu-id="a0edf-108">When using the ALTER DATABASE statement from inside of a contained database, the syntax differs from that used for a non-contained database.</span></span> <span data-ttu-id="a0edf-109">この相違点には、データベースを超えてインスタンスにまで拡張されるステートメントの要素に関する制限が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-109">This difference includes restrictions of elements of the statement that extend beyond the database to the instance.</span></span> <span data-ttu-id="a0edf-110">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0edf-110">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="instance-level"></a><span data-ttu-id="a0edf-111">インスタンス レベル</span><span class="sxs-lookup"><span data-stu-id="a0edf-111">Instance Level</span></span>  
 <span data-ttu-id="a0edf-112">ALTER DATABASE ステートメントを包含データベース外で使用する場合の構文は、非包含データベースに使用する構文と異なります。</span><span class="sxs-lookup"><span data-stu-id="a0edf-112">The syntax for the ALTER DATABASE when used outside of a contained database differs from that used for non-contained databases.</span></span> <span data-ttu-id="a0edf-113">これらの変更を防ぐためには、データベースの境界を越えます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-113">These changes prevent crossing the database boundary.</span></span> <span data-ttu-id="a0edf-114">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0edf-114">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="create-database"></a><span data-ttu-id="a0edf-115">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="a0edf-115">CREATE DATABASE</span></span>  
 <span data-ttu-id="a0edf-116">CREATE DATABASE の構文は、包含データベースを使用する場合と非包含データベースを使用する場合とで異なります。</span><span class="sxs-lookup"><span data-stu-id="a0edf-116">The CREATE DATABASE syntax for a contained database differs from that for a non-contained database.</span></span> <span data-ttu-id="a0edf-117">新しい構文の要件と許容値の詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0edf-117">See [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)for information about new syntax requirements and allowances.</span></span>  
  
## <a name="temporary-tables"></a><span data-ttu-id="a0edf-118">一時テーブル</span><span class="sxs-lookup"><span data-stu-id="a0edf-118">Temporary Tables</span></span>  
 <span data-ttu-id="a0edf-119">包含データベース内でローカル一時テーブルを使用することはできますが、その動作は非包含データベース内のローカル一時テーブルの動作と異なります。</span><span class="sxs-lookup"><span data-stu-id="a0edf-119">Local temporary tables are permitted within a contained database, but their behavior differs from those in non-contained databases.</span></span> <span data-ttu-id="a0edf-120">非包含データベースでは、一時テーブル データは **tempdb**の照合順序で照合されます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-120">In non-contained databases, temporary table data is collated in the collation of **tempdb**.</span></span> <span data-ttu-id="a0edf-121">包含データベースでは、一時テーブル データは包含データベースの照合順序で照合されます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-121">In a contained database temporary table data is collated in the collation of the contained database.</span></span>  
  
 <span data-ttu-id="a0edf-122">一時テーブルに関連付けられているすべてのメタデータ (テーブル名、列名、インデックスなど) には、カタログの照合順序が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-122">All metadata associated with temporary tables (for example, table and column names, indexes, and so on) will be in the catalog collation.</span></span>  
  
 <span data-ttu-id="a0edf-123">一時テーブル内では名前付き制約を使用できません。</span><span class="sxs-lookup"><span data-stu-id="a0edf-123">Named constraints may not be used in temporary tables.</span></span>  
  
 <span data-ttu-id="a0edf-124">一時テーブルでは、ユーザー定義型、XML スキーマ コレクション、またはユーザー定義関数を参照できません。</span><span class="sxs-lookup"><span data-stu-id="a0edf-124">Temporary tables may not refer to user-defined types, XML schema collections, or user-defined functions.</span></span>  
  
## <a name="collation"></a><span data-ttu-id="a0edf-125">照合順序</span><span class="sxs-lookup"><span data-stu-id="a0edf-125">Collation</span></span>  
 <span data-ttu-id="a0edf-126">非包含データベースのモデルには、データベースの照合順序、インスタンスの照合順序、および tempdb の照合順序の 3 種類の照合順序があります。</span><span class="sxs-lookup"><span data-stu-id="a0edf-126">In the non-contained database model, there are three separate types of collation: Database collation, Instance collation, and tempdb collation.</span></span> <span data-ttu-id="a0edf-127">包含データベースでは、データベースの照合順序と新しいカタログの照合順序の 2 種類の照合順序のみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0edf-127">Contained databases use only two collations, database collation and the new catalog collation.</span></span> <span data-ttu-id="a0edf-128">包含データベースの照合順序の詳細については、「 [包含データベースの照合順序](contained-database-collations.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0edf-128">See [Contained Database Collations](contained-database-collations.md) for more details on contained database collation.</span></span>  
  
## <a name="user-options"></a><span data-ttu-id="a0edf-129">ユーザー オプション</span><span class="sxs-lookup"><span data-stu-id="a0edf-129">User Options</span></span>  
 <span data-ttu-id="a0edf-130">包含データベースを有効にする場合、 [のインスタンスに対して](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) user options オプション [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0edf-130">When enabling contained databases, the [user options Option](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) must be set to 0 for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0edf-131">参照</span><span class="sxs-lookup"><span data-stu-id="a0edf-131">See Also</span></span>  
 <span data-ttu-id="a0edf-132">[包含データベースの照合順序](contained-database-collations.md) </span><span class="sxs-lookup"><span data-stu-id="a0edf-132">[Contained Database Collations](contained-database-collations.md) </span></span>  
 [<span data-ttu-id="a0edf-133">包含データベース</span><span class="sxs-lookup"><span data-stu-id="a0edf-133">Contained Databases</span></span>](contained-databases.md)  
  
  
