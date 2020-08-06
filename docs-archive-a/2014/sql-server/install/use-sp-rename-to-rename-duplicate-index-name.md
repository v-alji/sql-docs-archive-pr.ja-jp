---
title: Sp_rename を使用して、重複するインデックス名を変更します |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b8ffe3b9befd0c7239d32094e5738e0fb2947c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742762"
---
# <a name="use-sp_rename-to-rename-duplicate-index-name"></a><span data-ttu-id="675e7-102">sp_rename を使用して重複するインデックス名を変更する</span><span class="sxs-lookup"><span data-stu-id="675e7-102">Use sp_rename to rename duplicate index name</span></span>
  <span data-ttu-id="675e7-103">テーブルまたはビューのインデックス名が重複していることをアップグレード アドバイザーが検出しました。</span><span class="sxs-lookup"><span data-stu-id="675e7-103">Upgrade Advisor has detected duplicate table or view index names.</span></span> <span data-ttu-id="675e7-104">インデックス名を変更して重複を解消した後、アップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="675e7-104">Rename the indexes to remove duplicates before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="675e7-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="675e7-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="675e7-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="675e7-106">Corrective Action</span></span>  
  
1.  <span data-ttu-id="675e7-107">次のクエリを実行して重複したインデックスを探します。</span><span class="sxs-lookup"><span data-stu-id="675e7-107">Locate the duplicate indexes by executing the following query.</span></span>  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  <span data-ttu-id="675e7-108">インデックス名のいずれかを変更するには、 **sp_rename**を使用します。</span><span class="sxs-lookup"><span data-stu-id="675e7-108">Use **sp_rename** to change one of the index names.</span></span> <span data-ttu-id="675e7-109">インデックス名が同じであるため、どのインデックスの名前が変更されるか判断できません。</span><span class="sxs-lookup"><span data-stu-id="675e7-109">Because the index names are the same, you cannot determine which index will be renamed.</span></span> <span data-ttu-id="675e7-110">このステップによってインデックスを区別できます。</span><span class="sxs-lookup"><span data-stu-id="675e7-110">This step allows you to differentiate the indexes.</span></span>  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  <span data-ttu-id="675e7-111">次のクエリを実行して名前が変更されたインデックスを確認します。</span><span class="sxs-lookup"><span data-stu-id="675e7-111">Verify which index was renamed by executing the following query.</span></span> <span data-ttu-id="675e7-112">このクエリは、指定されたテーブルまたはビューのすべてのインデックス (キー列名を含む) を返します。</span><span class="sxs-lookup"><span data-stu-id="675e7-112">This query returns all indexes (including key column names) on the specified table or view.</span></span>  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  <span data-ttu-id="675e7-113">必要に応じて**sp_rename**を再度使用してインデックス名を修正します。</span><span class="sxs-lookup"><span data-stu-id="675e7-113">If necessary, use **sp_rename** again to correct the index names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675e7-114">参照</span><span class="sxs-lookup"><span data-stu-id="675e7-114">See Also</span></span>  
 <span data-ttu-id="675e7-115">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="675e7-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="675e7-116">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="675e7-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
