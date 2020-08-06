---
title: FILESTREAM が有効なデータベースの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79740ee86a89566113650865e3fd6ec54c7cb918
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712050"
---
# <a name="move-a-filestream-enabled-database"></a><span data-ttu-id="5ca66-102">FILESTREAM が有効なデータベースの移動</span><span class="sxs-lookup"><span data-stu-id="5ca66-102">Move a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="5ca66-103">このトピックでは、FILESTREAM が有効なデータベースを移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ca66-103">This topic shows how to move a FILESTREAM-enabled database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ca66-104">このトピックの例では、「 [FILESTREAM が有効なデータベースを作成する方法](create-a-filestream-enabled-database.md)」で作成した Archive データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="5ca66-104">The examples in this topic require the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
### <a name="to-move-a-filestream-enabled-database"></a><span data-ttu-id="5ca66-105">FILESTREAM が有効なデータベースを移動するには</span><span class="sxs-lookup"><span data-stu-id="5ca66-105">To move a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="5ca66-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[新しいクエリ]** をクリックしてクエリ エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="5ca66-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="5ca66-107">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをクエリ エディターにコピーして、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ca66-107">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="5ca66-108">このスクリプトは、FILESTREAM データベースで使用される物理データベース ファイルの場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="5ca66-108">This script displays the location of the physical database files that the FILESTREAM database uses.</span></span>  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  <span data-ttu-id="5ca66-109">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをクエリ エディターにコピーして、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ca66-109">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="5ca66-110">このコードでは、 `Archive` データベースがオフラインに設定されます。</span><span class="sxs-lookup"><span data-stu-id="5ca66-110">This code takes the `Archive` database offline.</span></span>  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  <span data-ttu-id="5ca66-111">`C:\moved_location`というフォルダーを作成し、手順 2. で一覧表示されたファイルとフォルダーをそのフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="5ca66-111">Create the folder `C:\moved_location`, and then move the files and folders that are listed in step 2 into it.</span></span>  
  
5.  <span data-ttu-id="5ca66-112">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをクエリ エディターにコピーして、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ca66-112">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="5ca66-113">このスクリプトでは、 `Archive` データベースがオンラインに設定されます。</span><span class="sxs-lookup"><span data-stu-id="5ca66-113">This script sets the `Archive` database online.</span></span>  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5ca66-114">参照</span><span class="sxs-lookup"><span data-stu-id="5ca66-114">See Also</span></span>  
 [<span data-ttu-id="5ca66-115">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5ca66-115">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
