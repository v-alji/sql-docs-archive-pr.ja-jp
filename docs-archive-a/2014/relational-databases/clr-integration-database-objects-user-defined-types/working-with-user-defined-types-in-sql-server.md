---
title: SQL Server | でのユーザー定義型の使用Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- user-defined types [CLR integration], queries
- UDTs [CLR integration], queries
- user-defined types [CLR integration], Transact-SQL
- UDTs [CLR integration], Transact-SQL
- queries [CLR integration]
ms.assetid: 807376fb-1f1a-4f2a-8cf8-a622c5858634
author: rothja
ms.author: jroth
ms.openlocfilehash: c9fed9ad4e73102eadd1374ff87d2a46d0ff4126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714433"
---
# <a name="working-with-user-defined-types-in-sql-server"></a><span data-ttu-id="5d0cb-102">SQL Server でのユーザー定義型の使用</span><span class="sxs-lookup"><span data-stu-id="5d0cb-102">Working with User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="5d0cb-103">のユーザー定義型 (UDT) 機能には [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、通常のクエリ構文を使用して、言語からアクセスでき [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5d0cb-103">You can access user-defined type (UDT) functionality in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[tsql](../../includes/tsql-md.md)] language by using regular query syntax.</span></span> <span data-ttu-id="5d0cb-104">UDT は、データベース オブジェクトの定義、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチの変数、関数とストアド プロシージャ、および関数とストアド プロシージャの引数に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d0cb-104">UDTs can be used in the definition of database objects, as variables in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, in functions and stored procedures, and as arguments in functions and stored procedures.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d0cb-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5d0cb-105">In This Section</span></span>  
 [<span data-ttu-id="5d0cb-106">UDT テーブルと UDT 列の定義</span><span class="sxs-lookup"><span data-stu-id="5d0cb-106">Defining UDT Tables and Columns</span></span>](working-with-user-defined-types-defining-udt-tables-and-columns.md)  
 <span data-ttu-id="5d0cb-107">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、テーブルに UDT 列を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0cb-107">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a UDT column in a table.</span></span>  
  
 [<span data-ttu-id="5d0cb-108">UDT データの操作</span><span class="sxs-lookup"><span data-stu-id="5d0cb-108">Manipulating UDT Data</span></span>](working-with-user-defined-types-manipulating-udt-data.md)  
 <span data-ttu-id="5d0cb-109">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で UDT データを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d0cb-109">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to work with UDT data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0cb-110">参照</span><span class="sxs-lookup"><span data-stu-id="5d0cb-110">See Also</span></span>  
 [<span data-ttu-id="5d0cb-111">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="5d0cb-111">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
