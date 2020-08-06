---
title: サービス マスター キーの復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 2ad99fc9baa518d50678ddd6e6db1ec554658823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743166"
---
# <a name="restore-the-service-master-key"></a><span data-ttu-id="6dc29-102">サービス マスター キーの復元</span><span class="sxs-lookup"><span data-stu-id="6dc29-102">Restore the Service Master Key</span></span>
  <span data-ttu-id="6dc29-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して [!INCLUDE[tsql](../../../includes/tsql-md.md)]でサービス マスター キーを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6dc29-103">This topic describes how to restore the service master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="6dc29-104">サービス マスター キーの復元が必要になることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="6dc29-104">It is unlikely that you will ever need to restore the service master key.</span></span> <span data-ttu-id="6dc29-105">サービス マスター キーを復元する必要が生じた場合は、十分注意して作業を行ってください。</span><span class="sxs-lookup"><span data-stu-id="6dc29-105">If you do, you should proceed with extreme caution.</span></span> <span data-ttu-id="6dc29-106">詳細については、「 [Back Up the Service Master Key](service-master-key.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6dc29-106">For more information, see [Back Up the Service Master Key](service-master-key.md).</span></span>  
  
 <span data-ttu-id="6dc29-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6dc29-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6dc29-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6dc29-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6dc29-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6dc29-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6dc29-110">Security</span><span class="sxs-lookup"><span data-stu-id="6dc29-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="6dc29-111">Transact-SQL を使用してサービス マスター キーを復元するには</span><span class="sxs-lookup"><span data-stu-id="6dc29-111">To restore the service master key using Transact-SQL</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6dc29-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="6dc29-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6dc29-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6dc29-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6dc29-114">サービス マスター キーを復元するとき、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、現在のサービス マスター キーで暗号化されているすべてのキーとシークレットの暗号化が解除され、次にそれらがバックアップ ファイルから読み込まれたサービス マスター キーで暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="6dc29-114">When the service master key is restored, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] decrypts all the keys and secrets that have been encrypted with the current service master key, and then encrypts them with the service master key loaded from the backup file.</span></span>  
  
-   <span data-ttu-id="6dc29-115">暗号化解除が 1 つでも失敗した場合、復元は失敗します。</span><span class="sxs-lookup"><span data-stu-id="6dc29-115">If any one of the decryptions fails, the restore will fail.</span></span> <span data-ttu-id="6dc29-116">FORCE オプションを使用するとエラーを無視できますが、暗号化を解除できないデータが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6dc29-116">You can use the FORCE option to ignore errors, but this option will cause the loss of any data that cannot be decrypted.</span></span>  
  
-   <span data-ttu-id="6dc29-117">暗号化階層の再生成操作はリソースを大量に消費するため、</span><span class="sxs-lookup"><span data-stu-id="6dc29-117">Regenerating the encryption hierarchy is a resource-intensive operation.</span></span> <span data-ttu-id="6dc29-118">リソース要求が少ないときに実行するように考慮してください。</span><span class="sxs-lookup"><span data-stu-id="6dc29-118">You should schedule this during a period of low demand.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6dc29-119">サービス マスター キーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 暗号化階層のルートになります。</span><span class="sxs-lookup"><span data-stu-id="6dc29-119">The service master key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="6dc29-120">サービス マスター キーでは、直接または間接的に、そのツリー内の他のすべてのキーが保護されます。</span><span class="sxs-lookup"><span data-stu-id="6dc29-120">The service master key directly or indirectly secures all other keys in the tree.</span></span> <span data-ttu-id="6dc29-121">強制復元で、依存関係のあるキーの暗号化を解除できなかった場合、そのキーで保護されているデータは失われます。</span><span class="sxs-lookup"><span data-stu-id="6dc29-121">If a dependent key cannot be decrypted during a forced restore, data that is secured by that key will be lost.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6dc29-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6dc29-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6dc29-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="6dc29-123">Permissions</span></span>  
 <span data-ttu-id="6dc29-124">サーバーに対する CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6dc29-124">Requires CONTROL SERVER permission on the server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6dc29-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6dc29-125">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-the-service-master-key"></a><span data-ttu-id="6dc29-126">サービス マスター キーを復元するには</span><span class="sxs-lookup"><span data-stu-id="6dc29-126">To restore the service master key</span></span>  
  
1.  <span data-ttu-id="6dc29-127">バックアップしたサービス マスター キーのコピーを、物理バックアップ メディアまたはローカル ファイル システム上のディレクトリから取得します。</span><span class="sxs-lookup"><span data-stu-id="6dc29-127">Retrieve a copy of the backed-up service master key, either from a physical backup medium or a directory on the local file system.</span></span>  
  
2.  <span data-ttu-id="6dc29-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6dc29-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="6dc29-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6dc29-129">On the Standard bar, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="6dc29-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6dc29-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="6dc29-131">キーのファイル パスとキーのパスワード (存在する場合) は、実際は上に示したものと異なります。</span><span class="sxs-lookup"><span data-stu-id="6dc29-131">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="6dc29-132">両方がサーバーとキーのセットアップで固有であることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="6dc29-132">Please make sure that both are specific to your server and key set-up.</span></span>  
  
  
