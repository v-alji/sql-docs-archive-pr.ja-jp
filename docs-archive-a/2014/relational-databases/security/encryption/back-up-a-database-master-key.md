---
title: データベース マスター キーのバックアップ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9a66d28fea8289719d3efb2351409e0f14379ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741726"
---
# <a name="back-up-a-database-master-key"></a><span data-ttu-id="de029-102">データベース マスター キーのバックアップ</span><span class="sxs-lookup"><span data-stu-id="de029-102">Back Up a Database Master Key</span></span>
  <span data-ttu-id="de029-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用してデータベース マスター キーをバックアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de029-103">This topic describes how to back up a database master key in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="de029-104">データベース マスター キーは、データベース内の他のキーや証明書を暗号化する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="de029-104">The database master key is used to encrypt other keys and certificates inside a database.</span></span> <span data-ttu-id="de029-105">データベース マスター キーが削除されるか破損すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、暗号化されたキーの暗号化を解除できなくなる場合があります。さらに、そのキーを使用して暗号化されたデータは事実上失われます。</span><span class="sxs-lookup"><span data-stu-id="de029-105">If it is deleted or corrupted, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may be unable to decrypt those keys, and the data encrypted using them will be effectively lost.</span></span> <span data-ttu-id="de029-106">このため、データベース マスター キーはバックアップして、安全な別の場所に保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="de029-106">For this reason, you should back up the database master key and store the backup in a secure off-site location.</span></span>  
  
 <span data-ttu-id="de029-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="de029-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="de029-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="de029-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="de029-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="de029-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="de029-110">Security</span><span class="sxs-lookup"><span data-stu-id="de029-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="de029-111">Transact-SQL を使用してデータベース マスター キーをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="de029-111">To back up a database master key using Transact-SQL</span></span>](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="de029-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="de029-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="de029-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="de029-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="de029-114">マスター キーは開かれている必要があります。したがって、バックアップ前に暗号化を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de029-114">The master key must be open and, therefore, decrypted before it is backed up.</span></span> <span data-ttu-id="de029-115">マスター キーがサービス マスター キーで暗号化されている場合は、明示的に開く必要はありません。</span><span class="sxs-lookup"><span data-stu-id="de029-115">If it is encrypted with the service master key, the master key does not have to be explicitly opened.</span></span> <span data-ttu-id="de029-116">パスワードのみで暗号化されている場合は、明示的に開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="de029-116">But if the master key is encrypted only with a password, it must be explicitly opened.</span></span>  
  
-   <span data-ttu-id="de029-117">マスター キーは作成後すぐにバックアップし、安全な別の場所に保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="de029-117">We recommend that you back up the master key as soon as it is created, and store the backup in a secure, off-site location.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="de029-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="de029-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="de029-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="de029-119">Permissions</span></span>  
 <span data-ttu-id="de029-120">データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="de029-120">Requires CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio-with-transact-sql"></a><a name="Procedure"></a><span data-ttu-id="de029-121">Transact-sql での SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="de029-121">Using SQL Server Management Studio with Transact-SQL</span></span>  
  
#### <a name="to-back-up-the-database-master-key"></a><span data-ttu-id="de029-122">データベース マスター キーをバックアップするには</span><span class="sxs-lookup"><span data-stu-id="de029-122">To back-up the database master key</span></span>  
  
1.  <span data-ttu-id="de029-123">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、バックアップするデータベース マスター キーが格納されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="de029-123">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance containing the database master key you wish to back up.</span></span>  
  
2.  <span data-ttu-id="de029-124">バックアップ メディアでデータベース マスター キーの暗号化に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="de029-124">Choose a password that will be used to encrypt the database master key on the backup medium.</span></span> <span data-ttu-id="de029-125">このパスワードに対しては、複雑性がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="de029-125">This password is subject to complexity checks.</span></span>  
  
3.  <span data-ttu-id="de029-126">バックアップしたキーのコピーを保存するためにリムーバブル バックアップ メディアを用意します。</span><span class="sxs-lookup"><span data-stu-id="de029-126">Obtain a removable backup medium for storing a copy of the backed-up key.</span></span>  
  
4.  <span data-ttu-id="de029-127">キーのバックアップを作成する NTFS ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="de029-127">Identify an NTFS directory in which to create the backup of the key.</span></span> <span data-ttu-id="de029-128">このディレクトリは、次の手順で指定するファイルの作成先となります。</span><span class="sxs-lookup"><span data-stu-id="de029-128">This is where you will create the file specified in the next step.</span></span> <span data-ttu-id="de029-129">このディレクトリは、制限の厳しいアクセス制御リスト (ACL) で保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de029-129">The directory should be protected with highly restrictive access control lists (ACLs).</span></span>  
  
5.  <span data-ttu-id="de029-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="de029-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
6.  <span data-ttu-id="de029-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de029-131">On the Standard bar, click **New Query**.</span></span>  
  
7.  <span data-ttu-id="de029-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de029-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="de029-133">キーのファイル パスとキーのパスワード (存在する場合) は、実際は上に示したものと異なります。</span><span class="sxs-lookup"><span data-stu-id="de029-133">The file path to the key and the key's password (if it exists) will be different than what is indicated above.</span></span> <span data-ttu-id="de029-134">両方がサーバーとキーのセットアップで固有であることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="de029-134">Please make sure that both are specific to your server and key set-up.</span></span>  
  
8.  <span data-ttu-id="de029-135">ファイルをバックアップ メディアにコピーして、コピーしたファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="de029-135">Copy the file to the backup medium and verify the copy.</span></span>  
  
9. <span data-ttu-id="de029-136">バックアップを安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="de029-136">Store the backup in a secure, off-site location.</span></span>  
  
 <span data-ttu-id="de029-137">詳細については、「[OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql)」と「[BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de029-137">For more information, see [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) and [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).</span></span>  
  
  
