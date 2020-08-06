---
title: 他のサーバーへのデータベースのコピー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcde6185f25129596b4be7a150d4ee230c54c1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715401"
---
# <a name="copy-databases-to-other-servers"></a><span data-ttu-id="46bf2-102">他のサーバーへのデータベースのコピー</span><span class="sxs-lookup"><span data-stu-id="46bf2-102">Copy Databases to Other Servers</span></span>
  <span data-ttu-id="46bf2-103">テスト、一貫性の確認、ソフトウェアの開発、レポートの実行、ミラー データベースの作成、遠隔地の支社での運用などを目的として、データベースをコピーすることが必要になる状況があります。</span><span class="sxs-lookup"><span data-stu-id="46bf2-103">It is sometimes useful to copy a database from one computer to another, whether for testing, checking consistency, developing software, running reports, creating a mirror database, or, possibly, to make the database available to remote-branch operations.</span></span>  
  
 <span data-ttu-id="46bf2-104">データベースは、次の方法でコピーできます。</span><span class="sxs-lookup"><span data-stu-id="46bf2-104">There are several ways to copy a database:</span></span>  
  
-   <span data-ttu-id="46bf2-105">データベース コピー ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="46bf2-105">Using the Copy Database Wizard</span></span>  
  
     <span data-ttu-id="46bf2-106">データベース コピー ウィザードを使用して、サーバー間でデータベースを移動またはコピーしたり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを新しいバージョンにアップグレードしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="46bf2-106">You can use the Copy Database Wizard to copy or move databases between servers or to upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a later version.</span></span> <span data-ttu-id="46bf2-107">詳細については、「 [Use the Copy Database Wizard](use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46bf2-107">For more information, see [Use the Copy Database Wizard](use-the-copy-database-wizard.md).</span></span>  
  
-   <span data-ttu-id="46bf2-108">データベース バックアップの復元</span><span class="sxs-lookup"><span data-stu-id="46bf2-108">Restoring a database backup</span></span>  
  
     <span data-ttu-id="46bf2-109">データベース全体をコピーするため、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの BACKUP と RESTORE を使用できます。</span><span class="sxs-lookup"><span data-stu-id="46bf2-109">To copy an entire database, you can use the BACKUP and RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="46bf2-110">通常、さまざまな理由によりデータベースを別のコンピューターにコピーする場合、データベースの完全バックアップを復元する方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="46bf2-110">Typically, restoring a full backup of a database is used to copy the database from one computer to another for a variety of reasons.</span></span> <span data-ttu-id="46bf2-111">バックアップと復元によるデータベースのコピーの詳細については、「 [バックアップと復元によるデータベースのコピー](copy-databases-with-backup-and-restore.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46bf2-111">For information on using backup and restore to copy a database, see [Copy Databases with Backup and Restore](copy-databases-with-backup-and-restore.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46bf2-112">データベース ミラーリングのミラー データベースを設定するには、RESTORE DATABASE *<database_name>* WITH NORECOVERY を使用して、データベースをミラー サーバーに復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46bf2-112">To set up a mirror database for database mirroring, you must restore the database onto the mirror server by using RESTORE DATABASE *<database_name>* WITH NORECOVERY.</span></span> <span data-ttu-id="46bf2-113">詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="46bf2-113">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="46bf2-114">スクリプトの生成ウィザードを使用したデータベースのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="46bf2-114">Using the Generate Scripts Wizard to publish databases</span></span>  
  
     <span data-ttu-id="46bf2-115">スクリプトの生成ウィザードを使用すると、ローカル コンピューターから Web ホスティング プロバイダーにデータベースを転送できます。</span><span class="sxs-lookup"><span data-stu-id="46bf2-115">You can use the Generate Scripts Wizard to transfer a database from a local computer to a Web hosting provider.</span></span> <span data-ttu-id="46bf2-116">詳細については、「 [スクリプトの生成とパブリッシュ ウィザード](../scripting/generate-and-publish-scripts-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46bf2-116">For more information, see [Generate and Publish Scripts Wizard](../scripting/generate-and-publish-scripts-wizard.md).</span></span>  
  
  
