---
title: マージパブリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f669a1f7132aa0f588fd89fb9747a7dc9017fcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741857"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a><span data-ttu-id="37ba3-102">マージ レプリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="37ba3-102">Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="37ba3-103">[bcp ユーティリティ](../../tools/bcp-utility.md)または [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) コマンドを使用してテーブルにデータを読み込むと、既定では、[MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) システム テーブル内の追跡データを維持するマージ レプリケーション トリガーが起動されなくなります。</span><span class="sxs-lookup"><span data-stu-id="37ba3-103">When data is loaded into tables using the [bcp Utility](../../tools/bcp-utility.md) or the [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) command, by default, the merge replication triggers that maintain tracking data in the [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) system table are not fired.</span></span> <span data-ttu-id="37ba3-104">データが読み込まれたときにマージ レプリケーション トリガーを強制的に起動するか、一括コピー操作の後にレプリケーション ストアド プロシージャを使用して、生成されたレプリケーション メタデータをプログラムによって挿入できます。</span><span class="sxs-lookup"><span data-stu-id="37ba3-104">You can either force the merge replication triggers to fire as the data is loaded, or you can insert the generated replication metadata programmatically after the bulk copy operation using replication stored procedures.</span></span>  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a><span data-ttu-id="37ba3-105">マージ レプリケーションによってパブリッシュされたテーブルに bcp ユーティリティを使用してデータを一括読み込みするには</span><span class="sxs-lookup"><span data-stu-id="37ba3-105">To bulk-load data into tables published by merge replication using the bcp utility</span></span>  
  
1.  <span data-ttu-id="37ba3-106">マージ レプリケーションを使用してパブリッシュされたテーブルにデータを挿入するには、パブリッシャーまたはサブスクライバーで [bcp Utility](../../tools/bcp-utility.md) または [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="37ba3-106">At either the Publisher or Subscriber, execute the [bcp Utility](../../tools/bcp-utility.md) or [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) to insert data into a table published using merge replication.</span></span>  
  
2.  <span data-ttu-id="37ba3-107">挿入されたデータ用のレプリケーション メタデータが生成されようにするには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="37ba3-107">Use one of the following methods to ensure that replication metadata is generated for the inserted data.</span></span>  
  
    -   <span data-ttu-id="37ba3-108">FIRE_TRIGGERS オプションを使用して一括コピーを実行する。</span><span class="sxs-lookup"><span data-stu-id="37ba3-108">Execute the bulk copy using the FIRE_TRIGGERS option.</span></span>  
  
    -   <span data-ttu-id="37ba3-109">データの挿入先のデータベースで、[sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql) を実行する。</span><span class="sxs-lookup"><span data-stu-id="37ba3-109">On the database into which data was inserted, execute [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql).</span></span> <span data-ttu-id="37ba3-110">データの挿入先のテーブル名を指定し **@table_name** ます。</span><span class="sxs-lookup"><span data-stu-id="37ba3-110">Specify the table name into which the data was inserted for **@table_name**.</span></span>  
  
  
