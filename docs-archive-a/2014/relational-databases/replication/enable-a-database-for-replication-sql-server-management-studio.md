---
title: レプリケーションのデータベースの有効化 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 307d52e24187e35c1c30f609facd13bfad569216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632366"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a><span data-ttu-id="261eb-102">レプリケーションのデータベースの有効化 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="261eb-102">Enable a Database for Replication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="261eb-103">固定サーバー ロール **sysadmin** のメンバーがパブリケーションの新規作成ウィザードでパブリケーションを作成すると、レプリケーションのデータベースが暗黙的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="261eb-103">A database is implicitly enabled for replication when a member of the **sysadmin** fixed server role creates a publication with the New Publication Wizard.</span></span> <span data-ttu-id="261eb-104">固定サーバー ロール **sysadmin** のメンバーは、レプリケーションのデータベースを明示的に有効にすることもできます。これにより、固定データベース ロール **db_owner** のメンバーが、そのデータベース内に 1 つ以上のパブリケーションを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="261eb-104">A member of the **sysadmin** fixed server role can also enable a database for replication explicitly, so that a member of the **db_owner** fixed database role can create one or more publications in that database.</span></span> <span data-ttu-id="261eb-105">データベースを明示的に有効にするには、 **[パブリッシャーのプロパティ - \<Publisher>]** ボックスの **[パブリケーション データベース]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="261eb-105">To enable a database explicitly, use the **Publication Databases** page of the **Publisher Properties - \<Publisher>** dialog box.</span></span> <span data-ttu-id="261eb-106">このダイアログ ボックスへのアクセスの詳細については、「 [Create a Publication](publish/create-a-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="261eb-106">For more information about accessing this dialog box, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
### <a name="to-enable-a-database-for-replication"></a><span data-ttu-id="261eb-107">レプリケーションのデータベースを有効化するには</span><span class="sxs-lookup"><span data-stu-id="261eb-107">To enable a database for replication</span></span>  
  
1.  <span data-ttu-id="261eb-108">**[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスの **[パブリケーション データベース]** ページで、レプリケートする各データベースの **[トランザクション]** または **[マージ]** チェック ボックス、あるいはその両方をオンにします。</span><span class="sxs-lookup"><span data-stu-id="261eb-108">On the **Publication Databases** page of the **Publisher Properties - \<Publisher>** dialog box, select the **Transactional** and/or **Merge** check box for each database you want to replicate.</span></span> <span data-ttu-id="261eb-109">スナップショット レプリケーションのデータベースを有効にするには、 **[トランザクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="261eb-109">Select **Transactional** to enable the database for snapshot replication.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
