---
title: データベース マスター キーの復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 614ba8bdc494ae7e7e5b3ed7b62390721ef642a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743165"
---
# <a name="restore-a-database-master-key"></a><span data-ttu-id="0e39d-102">データベース マスター キーの復元</span><span class="sxs-lookup"><span data-stu-id="0e39d-102">Restore a Database Master Key</span></span>
  <span data-ttu-id="0e39d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して [!INCLUDE[tsql](../../../includes/tsql-md.md)]でデータベース マスター キーを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e39d-103">This topic describes how to restore the database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0e39d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0e39d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0e39d-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="0e39d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0e39d-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0e39d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0e39d-107">Security</span><span class="sxs-lookup"><span data-stu-id="0e39d-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="0e39d-108">Transact-SQL を使用してデータベース マスター キーを復元するには</span><span class="sxs-lookup"><span data-stu-id="0e39d-108">To restore the database master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0e39d-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="0e39d-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0e39d-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0e39d-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0e39d-111">マスター キーを復元するとき、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では現在アクティブなマスター キーによって暗号化されたすべてのキーの暗号化が解除された後、復元されたマスター キーを使用してこれらのキーが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="0e39d-111">When the master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys that are encrypted with the currently active master key, and then encrypts these keys with the restored master key.</span></span> <span data-ttu-id="0e39d-112">この操作はリソースを大量に消費するため、リソース要求が少ないときに実行するように考慮してください。</span><span class="sxs-lookup"><span data-stu-id="0e39d-112">This resource-intensive operation should be scheduled during a period of low demand.</span></span> <span data-ttu-id="0e39d-113">現在のデータベースのマスター キーが開いていないか、開けない場合、またはマスター キーで暗号化されたキーを 1 つでも暗号化解除できない場合、復元操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="0e39d-113">If the current database master key is not open or cannot be opened, or if any of the keys that are encrypted by it cannot be decrypted, the restore operation fails.</span></span>  
  
-   <span data-ttu-id="0e39d-114">暗号化解除が 1 つでも失敗した場合、復元は失敗します。</span><span class="sxs-lookup"><span data-stu-id="0e39d-114">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="0e39d-115">FORCE オプションを使用するとエラーを無視できますが、暗号化を解除できないデータが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e39d-115">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="0e39d-116">マスター キーがサービス マスター キーで暗号化されている場合は、復元されたマスター キーもサービス マスター キーで暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="0e39d-116">If the master key was encrypted by the service master key, the restored master key will also be encrypted by the service master key.</span></span>  
  
-   <span data-ttu-id="0e39d-117">現在のデータベースにマスター キーが存在しない場合は、RESTORE MASTER KEY を実行するとマスター キーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0e39d-117">If there is no master key in the current database, RESTORE MASTER KEY creates a master key.</span></span> <span data-ttu-id="0e39d-118">この新しいマスター キーは、サービス マスター キーで自動的に暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="0e39d-118">The new master key will not be automatically encrypted with the service master key.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0e39d-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0e39d-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0e39d-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="0e39d-120">Permissions</span></span>  
 <span data-ttu-id="0e39d-121">データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="0e39d-121">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="SSMSProcedure"></a><span data-ttu-id="0e39d-122">Transact-sql での SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0e39d-122">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-restore-the-database-master-key"></a><span data-ttu-id="0e39d-123">データベース マスター キーを復元するには</span><span class="sxs-lookup"><span data-stu-id="0e39d-123">To restore the database master key</span></span>  
  
1.  <span data-ttu-id="0e39d-124">バックアップしたデータベース マスター キーのコピーを、物理バックアップ メディアまたはローカル ファイル システム上のディレクトリから取得します。</span><span class="sxs-lookup"><span data-stu-id="0e39d-124">Retrieve a copy of the backed-up database master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="0e39d-125">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0e39d-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="0e39d-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e39d-126">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="0e39d-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e39d-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="0e39d-128">キーのファイル パスとキーのパスワード (存在する場合) は、実際は上に示したものと異なります。</span><span class="sxs-lookup"><span data-stu-id="0e39d-128">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="0e39d-129">両方がサーバーとキーのセットアップで固有であることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="0e39d-129">Please make sure that both are specific to your server and key set-up.</span></span>  
  
 <span data-ttu-id="0e39d-130">詳細については、「[RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e39d-130">For more information, see [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)</span></span>  
  
  
