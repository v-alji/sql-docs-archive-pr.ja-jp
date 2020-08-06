---
title: 別の SQL Server への TDE で保護されたデータベースの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, moving
- TDE, moving a database
ms.assetid: fb420903-df54-4016-bab6-49e6dfbdedc7
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b03b4d9ecf31e9953fd3e22cec5c51bbacc0c25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743169"
---
# <a name="move-a-tde-protected-database-to-another-sql-server"></a><span data-ttu-id="21919-102">別の SQL Server への TDE で保護されたデータベースの移動</span><span class="sxs-lookup"><span data-stu-id="21919-102">Move a TDE Protected Database to Another SQL Server</span></span>
  <span data-ttu-id="21919-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、Transparent Data Encryption (TDE) によってデータベースを保護し、そのデータベースを別の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21919-103">This topic describes how to protect a database by using transparent data encryption (TDE), and then move the database to another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="21919-104">TDE は、データとログ ファイルの I/O 暗号化と複合化をリアルタイムで実行します。</span><span class="sxs-lookup"><span data-stu-id="21919-104">TDE performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="21919-105">暗号化は、復旧中に、可用性のためのデータベース ブート レコードに格納されるデータベース暗号化キー (DEK) を使用します。</span><span class="sxs-lookup"><span data-stu-id="21919-105">The encryption uses a database encryption key (DEK), which is stored in the database boot record for availability during recovery.</span></span> <span data-ttu-id="21919-106">DEK とは、サーバーの `master` データベースに保存されている証明書を使用して保護される対称キー、または EKM モジュールによって保護される非対称キーのことです。</span><span class="sxs-lookup"><span data-stu-id="21919-106">The DEK is a symmetric key secured by using a certificate stored in the `master` database of the server or an asymmetric key protected by an EKM module.</span></span>  
  
 <span data-ttu-id="21919-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="21919-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="21919-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="21919-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="21919-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="21919-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="21919-110">Security</span><span class="sxs-lookup"><span data-stu-id="21919-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="21919-111">**透過的なデータ暗号化で保護されたデータベースを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="21919-111">**To create a database protected by transparent data encryption, using:**</span></span>  
  
     [<span data-ttu-id="21919-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="21919-112">SQL Server Management Studio</span></span>](#SSMSCreate)  
  
     [<span data-ttu-id="21919-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21919-113">Transact-SQL</span></span>](#TsqlCreate)  
  
-   <span data-ttu-id="21919-114">**データベースを移動する方法:**</span><span class="sxs-lookup"><span data-stu-id="21919-114">**To move a database, using:**</span></span>  
  
     [<span data-ttu-id="21919-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="21919-115">SQL Server Management Studio</span></span>](#SSMSMove)  
  
     [<span data-ttu-id="21919-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21919-116">Transact-SQL</span></span>](#TsqlMove)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21919-117">はじめに</span><span class="sxs-lookup"><span data-stu-id="21919-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="21919-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="21919-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="21919-119">TDE で保護されたデータベースを移動するとき、DEK を開くために使用される証明書または非対称キーも移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21919-119">When moving a TDE protected database, you must also move the certificate or asymmetric key that is used to open the DEK.</span></span> <span data-ttu-id="21919-120">が `master` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースファイルにアクセスできるようにするには、証明書または非対称キーが移行先サーバーのデータベースにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="21919-120">The certificate or asymmetric key must be installed in the `master` database of the destination server, so that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can access the database files.</span></span> <span data-ttu-id="21919-121">詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](transparent-data-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21919-121">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
-   <span data-ttu-id="21919-122">証明書を復旧するために、証明書ファイルと秘密キー ファイルの両方のコピーを保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21919-122">You must retain copies of both the certificate file and the private key file in order to recover the certificate.</span></span> <span data-ttu-id="21919-123">秘密キーのパスワードは、データベース マスター キーのパスワードと同じにする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="21919-123">The password for the private key does not have to be the same as the database master key password.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="21919-124">ここで作成したファイルを**C:\Program SERVER\MSSQL12. SQL に格納します。** 既定では MSSQLSERVER\MSSQL\DATA。</span><span class="sxs-lookup"><span data-stu-id="21919-124">stores the files created here in **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA** by default.</span></span> <span data-ttu-id="21919-125">ただし、ファイル名と場所は異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="21919-125">Your file names and locations might be different.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="21919-126">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="21919-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="21919-127">Permissions</span><span class="sxs-lookup"><span data-stu-id="21919-127">Permissions</span></span>  
  
-   <span data-ttu-id="21919-128">データベース `CONTROL DATABASE` `master` マスターキーを作成するには、データベースに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="21919-128">Requires `CONTROL DATABASE` permission on the `master` database to create the database master key.</span></span>  
  
-   <span data-ttu-id="21919-129">`CREATE CERTIFICATE` `master` Dek を保護する証明書を作成するには、データベースに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="21919-129">Requires `CREATE CERTIFICATE` permission on the `master` database to create the certificate that protects the DEK.</span></span>  
  
-   <span data-ttu-id="21919-130">暗号化されたデータベースに対する `CONTROL DATABASE` 権限、およびデータベース暗号化キーの暗号化に使用する証明書または非対称キーに対する `VIEW DEFINITION` 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="21919-130">Requires `CONTROL DATABASE` permission on the encrypted database and `VIEW DEFINITION` permission on the certificate or asymmetric key that is used to encrypt the database encryption key.</span></span>  
  
##  <a name="to-create-a-database-protected-by-transparent-data-encryption"></a><a name="SSMSProcedure"></a> <span data-ttu-id="21919-131">透過的なデータ暗号化で保護されたデータベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="21919-131">To create a database protected by transparent data encryption</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSCreate"></a> <span data-ttu-id="21919-132">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="21919-132">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="21919-133">データベースにデータベースマスターキーと証明書を作成し `master` ます。</span><span class="sxs-lookup"><span data-stu-id="21919-133">Create a database master key and certificate in the `master` database.</span></span> <span data-ttu-id="21919-134">詳細については、「 **Transact-SQL の使用** 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-134">For more information, see **Using Transact-SQL** below.</span></span>  
  
2.  <span data-ttu-id="21919-135">データベースにサーバー証明書のバックアップを作成 `master` します。</span><span class="sxs-lookup"><span data-stu-id="21919-135">Create a backup of the server certificate in the `master` database.</span></span> <span data-ttu-id="21919-136">詳細については、「 **Transact-SQL の使用** 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-136">For more information, see **Using Transact-SQL** below.</span></span>  
  
3.  <span data-ttu-id="21919-137">オブジェクト エクスプローラーで、 **[データベース]** フォルダーを右クリックし、 **[新しいデータベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-137">In Object Explorer, right-click the **Databases** folder and select **New Database**.</span></span>  
  
4.  <span data-ttu-id="21919-138">**[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに新しいデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="21919-138">In the **New Database** dialog box, in the **Database name** box, enter the name of the new database.</span></span>  
  
5.  <span data-ttu-id="21919-139">**[所有者]** ボックスに新しいデータベースの所有者を入力します。</span><span class="sxs-lookup"><span data-stu-id="21919-139">In the **Owner** box, enter the name of the new database's owner.</span></span> <span data-ttu-id="21919-140">または、省略記号 **[...]** をクリックして **[データベース所有者の選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="21919-140">Alternately, click the ellipsis **(...)** to open the **Select Database Owner** dialog box.</span></span> <span data-ttu-id="21919-141">新しいデータベースの作成の詳細については、「 [Create a Database](../../databases/create-a-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-141">For more information on creating a new database, see [Create a Database](../../databases/create-a-database.md).</span></span>  
  
6.  <span data-ttu-id="21919-142">オブジェクト エクスプローラーで、プラス記号をクリックして **[データベース]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="21919-142">In Object Explorer, click the plus sign to expand the **Databases** folder.</span></span>  
  
7.  <span data-ttu-id="21919-143">作成したデータベースを右クリックし、 **[タスク]** をポイントし、 **[データベース暗号化の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-143">Right-click the database you created, point to **Tasks**, and select **Manage Database Encryption**.</span></span>  
  
     <span data-ttu-id="21919-144">**[データベース暗号化の管理]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="21919-144">The following options are available on the **Manage Database Encryption** dialog box.</span></span>  
  
     <span data-ttu-id="21919-145">**暗号化アルゴリズム**</span><span class="sxs-lookup"><span data-stu-id="21919-145">**Encryption Algorithm**</span></span>  
     <span data-ttu-id="21919-146">データベース暗号化で使用するアルゴリズムを表示または設定します。</span><span class="sxs-lookup"><span data-stu-id="21919-146">Displays or sets the algorithm to use for database encryption.</span></span> <span data-ttu-id="21919-147">既定の暗号化アルゴリズムは `AES128` です。</span><span class="sxs-lookup"><span data-stu-id="21919-147">`AES128` is the default algorithm.</span></span> <span data-ttu-id="21919-148">このフィールドを空白にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21919-148">This field cannot be blank.</span></span> <span data-ttu-id="21919-149">暗号化アルゴリズムの詳細については、「 [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-149">For more information on encryption algorithms, see [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md).</span></span>  
  
     <span data-ttu-id="21919-150">**サーバー証明書の使用**</span><span class="sxs-lookup"><span data-stu-id="21919-150">**Use server certificate**</span></span>  
     <span data-ttu-id="21919-151">証明書によって保護するように暗号化を設定します。</span><span class="sxs-lookup"><span data-stu-id="21919-151">Sets the encryption to be secured by a certificate.</span></span> <span data-ttu-id="21919-152">一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="21919-152">Select one from the list.</span></span> <span data-ttu-id="21919-153">サーバー証明書に対する `VIEW DEFINITION` 権限がない場合、このリストは空になります。</span><span class="sxs-lookup"><span data-stu-id="21919-153">If you do not have the `VIEW DEFINITION` permission on server certificates, this list will be empty.</span></span> <span data-ttu-id="21919-154">証明書による暗号化方法が選択されている場合、この値を空にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21919-154">If a certificate method of encryption is selected, this value cannot be empty.</span></span> <span data-ttu-id="21919-155">証明書の詳細については、「 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-155">For more information about certificates, see [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
     <span data-ttu-id="21919-156">**[サーバー非対称キーの使用]**</span><span class="sxs-lookup"><span data-stu-id="21919-156">**Use server asymmetric key**</span></span>  
     <span data-ttu-id="21919-157">暗号化が非対称キーで保護されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="21919-157">Sets the encryption to be secured by an asymmetric key.</span></span> <span data-ttu-id="21919-158">使用可能な非対称キーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-158">Only available asymmetric keys are displayed.</span></span> <span data-ttu-id="21919-159">TDE を使用してデータベースを暗号化できるのは、EKM モジュールによって保護される非対称キーだけです。</span><span class="sxs-lookup"><span data-stu-id="21919-159">Only an asymmetric key protected by an EKM module can encrypt a database using TDE.</span></span>  
  
     <span data-ttu-id="21919-160">**[データベース暗号化をオンに設定]**</span><span class="sxs-lookup"><span data-stu-id="21919-160">**Set Database Encryption On**</span></span>  
     <span data-ttu-id="21919-161">データベースを変更して TDE をオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="21919-161">Alters the database to turn on (checked) or turn off (unchecked) TDE.</span></span>  
  
8.  <span data-ttu-id="21919-162">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-162">When finished, click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlCreate"></a> <span data-ttu-id="21919-163">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="21919-163">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="21919-164">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="21919-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="21919-165">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="21919-166">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a database master key and a certificate in the master database.  
    USE master ;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    CREATE CERTIFICATE TestSQLServerCert   
    WITH SUBJECT = 'Certificate to protect TDE key'  
    GO  
    -- Create a backup of the server certificate in the master database.  
    -- The following code stores the backup of the certificate and the private key file in the default data location for this instance of SQL Server   
    -- (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA).  
  
    BACKUP CERTIFICATE TestSQLServerCert   
    TO FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Create a database to be protected by TDE.  
    CREATE DATABASE CustRecords ;  
    GO  
    -- Switch to the new database.  
    -- Create a database encryption key, that is protected by the server certificate in the master database.   
    -- Alter the new database to encrypt the database using TDE.  
    USE CustRecords;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM = AES_128  
    ENCRYPTION BY SERVER CERTIFICATE TestSQLServerCert;  
    GO  
    ALTER DATABASE CustRecords  
    SET ENCRYPTION ON;  
    GO  
    ```  
  
 <span data-ttu-id="21919-167">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21919-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="21919-168">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-168">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="21919-169">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-169">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="21919-170">BACKUP CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-170">BACKUP CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-certificate-transact-sql)  
  
-   [<span data-ttu-id="21919-171">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-171">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="21919-172">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-172">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [<span data-ttu-id="21919-173">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-173">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
##  <a name="to-move-a-database"></a><a name="TsqlProcedure"></a><span data-ttu-id="21919-174">データベースを移動するには</span><span class="sxs-lookup"><span data-stu-id="21919-174">To move a database</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSMove"></a> <span data-ttu-id="21919-175">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="21919-175">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="21919-176">オブジェクト エクスプローラーで、暗号化したデータベースを右クリックし、 **[タスク]** をポイントして **[デタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-176">In Object Explorer, right-click the database you encrypted above, point to **Tasks** and select **Detach...**.</span></span>  
  
     <span data-ttu-id="21919-177">**[データベースのデタッチ]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="21919-177">The following options are available in the **Detach Database** dialog box.</span></span>  
  
     <span data-ttu-id="21919-178">**[デタッチするデータベース]**</span><span class="sxs-lookup"><span data-stu-id="21919-178">**Databases to detach**</span></span>  
     <span data-ttu-id="21919-179">デタッチするデータベースを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="21919-179">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="21919-180">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="21919-180">**Database Name**</span></span>  
     <span data-ttu-id="21919-181">デタッチするデータベースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="21919-181">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="21919-182">**[接続の削除]**</span><span class="sxs-lookup"><span data-stu-id="21919-182">**Drop Connections**</span></span>  
     <span data-ttu-id="21919-183">指定したデータベースへの接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="21919-183">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21919-184">アクティブな接続があるデータベースをデタッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21919-184">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="21919-185">**統計の更新**</span><span class="sxs-lookup"><span data-stu-id="21919-185">**Update Statistics**</span></span>  
     <span data-ttu-id="21919-186">既定では、データベースをデタッチしても、古い最適化統計情報が保持されます。既存の最適化統計情報を更新するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="21919-186">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="21919-187">**[フルテキスト カタログの保持]**</span><span class="sxs-lookup"><span data-stu-id="21919-187">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="21919-188">既定では、デタッチ操作を行っても、データベースに関連付けられたフルテキスト カタログが保持されます。</span><span class="sxs-lookup"><span data-stu-id="21919-188">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="21919-189">これらのカタログを削除するには、 **[フルテキスト カタログの保持]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="21919-189">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="21919-190">このオプションは、データベースを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]からアップグレードする場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-190">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="21919-191">**状態**</span><span class="sxs-lookup"><span data-stu-id="21919-191">**Status**</span></span>  
     <span data-ttu-id="21919-192">次のどちらかの状態が表示されます: **[準備完了]** または **[準備ができていません]** 。</span><span class="sxs-lookup"><span data-stu-id="21919-192">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="21919-193">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="21919-193">**Message**</span></span>  
     <span data-ttu-id="21919-194">**[メッセージ]** 列に、次のようにデータベースに関する情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="21919-194">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="21919-195">データベースがレプリケーションに含まれている場合、 **[状態]** は **[準備ができていません]** になり、 **[メッセージ]** 列に **[データベースがレプリケートされました]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-195">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="21919-196">データベースに 1 つまたは複数のアクティブな接続がある場合、 **[状態]** は **[準備ができていません]** になり、 **[メッセージ]** 列に _[<アクティブな接続数>_ **のアクティブな接続]** と表示されます。例: **[1 のアクティブな接続]** 。</span><span class="sxs-lookup"><span data-stu-id="21919-196">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="21919-197">データベースをデタッチするには、 **[接続の削除]** を選択してアクティブな接続を切断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21919-197">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="21919-198">メッセージについてより詳しい情報を得るには、ハイパーリンクのテキストをクリックして利用状況モニターを開きます。</span><span class="sxs-lookup"><span data-stu-id="21919-198">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
2.  <span data-ttu-id="21919-199">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-199">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="21919-200">Windows エクスプローラーを使用して、移動元またはコピー元サーバーから移動先またはコピー先サーバーの同じ場所に、データベース ファイルを移動またはコピーします。</span><span class="sxs-lookup"><span data-stu-id="21919-200">Using Windows Explorer, move or copy the database files from the source server to the same location on the destination server.</span></span>  
  
4.  <span data-ttu-id="21919-201">エクスプローラーを使用して、移動元またはコピー元サーバーから移動先またはコピー先サーバーの同じ場所に、サーバー証明書と秘密キー ファイルのバックアップを移動またはコピーします。</span><span class="sxs-lookup"><span data-stu-id="21919-201">Using Windows Explorer, move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.</span></span>  
  
5.  <span data-ttu-id="21919-202">移動先またはコピー先の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスに、データベース マスター キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="21919-202">Create a database master key on the destination instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="21919-203">詳細については、「 **Transact-SQL の使用** 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-203">For more information, see **Using Transact-SQL** below.</span></span>  
  
6.  <span data-ttu-id="21919-204">元のサーバー証明書のバックアップ ファイルを使用して、サーバー証明書を再作成します。</span><span class="sxs-lookup"><span data-stu-id="21919-204">Recreate the server certificate by using the original server certificate backup file.</span></span> <span data-ttu-id="21919-205">詳細については、「 **Transact-SQL の使用** 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21919-205">For more information, see **Using Transact-SQL** below.</span></span>  
  
7.  <span data-ttu-id="21919-206">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、 **[データベース]** フォルダーを右クリックし、 **[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-206">In Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the **Databases** folder and select **Attach...**.</span></span>  
  
8.  <span data-ttu-id="21919-207">**[データベースのインポート]** ダイアログ ボックスで、 **[アタッチするデータベース]** の下の **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-207">In the **Attach Databases** dialog box, under **Databases to attach**, click **Add**.</span></span>  
  
9. <span data-ttu-id="21919-208">[**データベースファイルの検索-**_server_name_ ] ダイアログボックスで、新しいサーバーにアタッチするデータベースファイルを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-208">In the **Locate Database Files -**_server_name_ dialog box, select the database file to attach to the new server and click **OK**.</span></span>  
  
     <span data-ttu-id="21919-209">**[データベースのインポート]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="21919-209">The following options are available in the **Attach Databases** dialog box.</span></span>  
  
     <span data-ttu-id="21919-210">**[アタッチするデータベース]**</span><span class="sxs-lookup"><span data-stu-id="21919-210">**Databases to attach**</span></span>  
     <span data-ttu-id="21919-211">選択されたデータベースに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="21919-211">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="21919-212">アタッチ操作の状態を示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-212">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="21919-213">表示されるアイコンの種類は、下の **[状態]** の説明に示します。</span><span class="sxs-lookup"><span data-stu-id="21919-213">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="21919-214">**[MDF ファイルの場所]**</span><span class="sxs-lookup"><span data-stu-id="21919-214">**MDF File Location**</span></span>  
     <span data-ttu-id="21919-215">選択した MDF ファイルのパスとファイル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-215">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="21919-216">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="21919-216">**Database Name**</span></span>  
     <span data-ttu-id="21919-217">データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-217">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="21919-218">**[次の名前でアタッチ]**</span><span class="sxs-lookup"><span data-stu-id="21919-218">**Attach As**</span></span>  
     <span data-ttu-id="21919-219">データベースを別の名前でアタッチする場合に、その名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="21919-219">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="21919-220">**所有者**</span><span class="sxs-lookup"><span data-stu-id="21919-220">**Owner**</span></span>  
     <span data-ttu-id="21919-221">データベースの所有者のドロップダウン リストです。これを使用して、必要に応じて別の所有者を選択できます。</span><span class="sxs-lookup"><span data-stu-id="21919-221">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="21919-222">**状態**</span><span class="sxs-lookup"><span data-stu-id="21919-222">**Status**</span></span>  
     <span data-ttu-id="21919-223">次の表に示すように、データベースの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="21919-223">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="21919-224">アイコン</span><span class="sxs-lookup"><span data-stu-id="21919-224">Icon</span></span>|<span data-ttu-id="21919-225">状態テキスト</span><span class="sxs-lookup"><span data-stu-id="21919-225">Status text</span></span>|<span data-ttu-id="21919-226">説明</span><span class="sxs-lookup"><span data-stu-id="21919-226">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="21919-227">(アイコンなし)</span><span class="sxs-lookup"><span data-stu-id="21919-227">(No icon)</span></span>|<span data-ttu-id="21919-228">(テキストなし)</span><span class="sxs-lookup"><span data-stu-id="21919-228">(No text)</span></span>|<span data-ttu-id="21919-229">このオブジェクトのアタッチ操作が開始されていないか、保留されています。</span><span class="sxs-lookup"><span data-stu-id="21919-229">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="21919-230">これは、ダイアログ ボックスを開いたときの既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="21919-230">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="21919-231">緑の右向き三角形</span><span class="sxs-lookup"><span data-stu-id="21919-231">Green, right-pointing triangle</span></span>|<span data-ttu-id="21919-232">進行中</span><span class="sxs-lookup"><span data-stu-id="21919-232">In progress</span></span>|<span data-ttu-id="21919-233">アタッチ操作が開始されましたが、完了していません。</span><span class="sxs-lookup"><span data-stu-id="21919-233">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="21919-234">緑のチェック マーク</span><span class="sxs-lookup"><span data-stu-id="21919-234">Green check mark</span></span>|<span data-ttu-id="21919-235">Success</span><span class="sxs-lookup"><span data-stu-id="21919-235">Success</span></span>|<span data-ttu-id="21919-236">オブジェクトは正常にアタッチされました。</span><span class="sxs-lookup"><span data-stu-id="21919-236">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="21919-237">赤い丸の中に白い×印</span><span class="sxs-lookup"><span data-stu-id="21919-237">Red circle containing a white cross</span></span>|<span data-ttu-id="21919-238">エラー</span><span class="sxs-lookup"><span data-stu-id="21919-238">Error</span></span>|<span data-ttu-id="21919-239">アタッチ操作でエラーが発生し、正常に完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="21919-239">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="21919-240">4 つに区切られた丸印 (左右の領域が黒、上下の領域が白)</span><span class="sxs-lookup"><span data-stu-id="21919-240">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="21919-241">停止済み</span><span class="sxs-lookup"><span data-stu-id="21919-241">Stopped</span></span>|<span data-ttu-id="21919-242">ユーザーがアタッチ操作を停止したため、正常に完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="21919-242">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="21919-243">丸の中に反時計回りの矢印</span><span class="sxs-lookup"><span data-stu-id="21919-243">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="21919-244">[ロールバックされました]</span><span class="sxs-lookup"><span data-stu-id="21919-244">Rolled Back</span></span>|<span data-ttu-id="21919-245">アタッチ操作は正常に完了しましたが、他のオブジェクトのアタッチ中にエラーが発生したため、ロールバックされました。</span><span class="sxs-lookup"><span data-stu-id="21919-245">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="21919-246">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="21919-246">**Message**</span></span>  
     <span data-ttu-id="21919-247">空白のメッセージ、または "ファイルが見つかりません" のハイパーリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-247">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="21919-248">**追加**</span><span class="sxs-lookup"><span data-stu-id="21919-248">**Add**</span></span>  
     <span data-ttu-id="21919-249">主な必須データベース ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="21919-249">Find the necessary main database files.</span></span> <span data-ttu-id="21919-250">ユーザーが .mdf ファイルを選択した場合、 **[アタッチするデータベース]** グリッドの対応するフィールドに、対応する情報が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="21919-250">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="21919-251">**Remove**</span><span class="sxs-lookup"><span data-stu-id="21919-251">**Remove**</span></span>  
     <span data-ttu-id="21919-252">選択したファイルを **[アタッチするデータベース]** グリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="21919-252">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="21919-253">**"** _<database_name>_ **" データベースの詳細**</span><span class="sxs-lookup"><span data-stu-id="21919-253">**"** _<database_name>_ **" database details**</span></span>  
     <span data-ttu-id="21919-254">デタッチするファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="21919-254">Displays the names of the files to be attached.</span></span> <span data-ttu-id="21919-255">ファイルのパス名を確認または変更するには、**参照**ボタン ( **[...]** ) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="21919-255">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21919-256">ファイルが存在しなかった場合、 **[メッセージ]** 列に "見つかりませんでした" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-256">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="21919-257">ログ ファイルが見つからない場合は、ログ ファイルが別のディレクトリに置かれているか、削除されています。</span><span class="sxs-lookup"><span data-stu-id="21919-257">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="21919-258">**[データベースの詳細]** グリッドでファイル パスを更新し、正しい場所を指定するか、そのログ ファイルをグリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="21919-258">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="21919-259">.ndf データ ファイルが見つからない場合、グリッドのパスを更新して、正しい場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21919-259">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="21919-260">**[元のファイル名]**</span><span class="sxs-lookup"><span data-stu-id="21919-260">**Original File Name**</span></span>  
     <span data-ttu-id="21919-261">データベースに属している、アタッチされたファイルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-261">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="21919-262">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="21919-262">**File Type**</span></span>  
     <span data-ttu-id="21919-263">ファイルの種類を表します。 **[データ]** または **[ログ]** になります。</span><span class="sxs-lookup"><span data-stu-id="21919-263">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="21919-264">**[現在のファイル パス]**</span><span class="sxs-lookup"><span data-stu-id="21919-264">**Current File Path**</span></span>  
     <span data-ttu-id="21919-265">選択されているデータベース ファイルのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="21919-265">Displays the path to the selected database file.</span></span> <span data-ttu-id="21919-266">このパスは手作業で編集できます。</span><span class="sxs-lookup"><span data-stu-id="21919-266">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="21919-267">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="21919-267">**Message**</span></span>  
     <span data-ttu-id="21919-268">空白のメッセージ、または **"ファイルが見つかりません"** ハイパーリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21919-268">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlMove"></a> <span data-ttu-id="21919-269">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="21919-269">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="21919-270">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="21919-270">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="21919-271">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-271">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="21919-272">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21919-272">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Detach the TDE protected database from the source server.   
    USE master ;  
    GO  
    EXEC master.dbo.sp_detach_db @dbname = N'CustRecords';  
    GO  
    -- Move or copy the database files from the source server to the same location on the destination server.   
    -- Move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.   
    -- Create a database master key on the destination instance of SQL Server.   
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    -- Recreate the server certificate by using the original server certificate backup file.   
    -- The password must be the same as the password that was used when the backup was created.  
  
    CREATE CERTIFICATE TestSQLServerCert   
    FROM FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        DECRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Attach the database that is being moved.   
    -- The path of the database files must be the location where you have stored the database files.  
    CREATE DATABASE [CustRecords] ON   
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords.mdf' ),  
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords_log.LDF' )  
    FOR ATTACH ;  
    GO  
    ```  
  
 <span data-ttu-id="21919-273">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21919-273">For more information, see:</span></span>  
  
-   [<span data-ttu-id="21919-274">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-274">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="21919-275">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-275">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="21919-276">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-276">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="21919-277">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-277">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="21919-278">参照</span><span class="sxs-lookup"><span data-stu-id="21919-278">See Also</span></span>  
 [<span data-ttu-id="21919-279">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="21919-279">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../databases/database-detach-and-attach-sql-server.md)  
  
  
