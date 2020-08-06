---
title: 2 台のサーバーでの同じ対称キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- symmetric keys [SQL Server], creating
ms.assetid: a13d0b21-a43b-43c0-9c22-7ba8f3d15e80
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 38eaccffff89b0be7e59f628fcfb9b6e772a02b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741718"
---
# <a name="create-identical-symmetric-keys-on-two-servers"></a><span data-ttu-id="08971-102">2 台のサーバーでの同じ対称キーの作成</span><span class="sxs-lookup"><span data-stu-id="08971-102">Create Identical Symmetric Keys on Two Servers</span></span>
  <span data-ttu-id="08971-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して [!INCLUDE[tsql](../../../includes/tsql-md.md)]で 2 台のサーバーに同じ対称キーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="08971-103">This topic describes how to create identical symmetric keys on two different servers in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="08971-104">暗号化テキストの暗号化を解除するには、暗号化に使用したキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="08971-104">In order to decrypt ciphertext, you need the key that was used to encrypt it.</span></span> <span data-ttu-id="08971-105">1 つのデータベースで暗号化と暗号化解除の両方が行われる場合、データベースに格納されているキーを、権限に応じて暗号化と暗号化解除の両方に使用できます。</span><span class="sxs-lookup"><span data-stu-id="08971-105">When both encryption and decryption occur in a single database, the key is stored in the database and it is available, depending on permissions, for both encryption and decryption.</span></span> <span data-ttu-id="08971-106">一方、暗号化と暗号化解除が別々のデータベースまたは別々のサーバーで行われる場合、一方のデータベースに格納されているキーを他方のデータベースで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="08971-106">But when encryption and decryption occur in separate databases or on separate servers, the key stored in one database is not available for use on the second database</span></span>  
  
 <span data-ttu-id="08971-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="08971-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="08971-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="08971-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="08971-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="08971-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="08971-110">Security</span><span class="sxs-lookup"><span data-stu-id="08971-110">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="08971-111">Transact-SQL を使用して、2 台のサーバーに同じ対称キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="08971-111">To create identical symmetric keys on two different servers, using Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="08971-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="08971-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="08971-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="08971-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="08971-114">対称キーを作成するときには、証明書、パスワード、対称キー、非対称キー、PROVIDER のうち少なくとも 1 つを使用して対称キーを暗号化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08971-114">When a symmetric key is created, the symmetric key must be encrypted by using at least one of the following: certificate, password, symmetric key, asymmetric key, or PROVIDER.</span></span> <span data-ttu-id="08971-115">キーには種類ごとの暗号化を複数指定できます。</span><span class="sxs-lookup"><span data-stu-id="08971-115">The key can have more than one encryption of each type.</span></span> <span data-ttu-id="08971-116">つまり、1 つの対称キーを、複数の証明書、パスワード、対称キー、および非対称キーを使用して同時に暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="08971-116">In other words, a single symmetric key can be encrypted by using multiple certificates, passwords, symmetric keys, and asymmetric keys at the same time.</span></span>  
  
-   <span data-ttu-id="08971-117">データベースのマスター キーの公開キーではなく、パスワードを使用して対称キーを暗号化する場合は、TRIPLE DES 暗号化アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="08971-117">When a symmetric key is encrypted with a password instead of the public key of the database master key, the TRIPLE DES encryption algorithm is used.</span></span> <span data-ttu-id="08971-118">このため、AES など、強力な暗号化アルゴリズムで作成されたキーでも、キー自身はそれより弱いアルゴリズムで保護されます。</span><span class="sxs-lookup"><span data-stu-id="08971-118">Because of this, keys that are created with a strong encryption algorithm, such as AES, are themselves secured by a weaker algorithm.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="08971-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="08971-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="08971-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="08971-120">Permissions</span></span>  
 <span data-ttu-id="08971-121">データベースに対する ALTER ANY SYMMETRIC KEY 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="08971-121">Requires ALTER ANY SYMMETRIC KEY permission on the database.</span></span> <span data-ttu-id="08971-122">AUTHORIZATION を指定する場合は、データベース ユーザーに対する IMPERSONATE 権限、またはアプリケーション ロールに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="08971-122">If AUTHORIZATION is specified, requires IMPERSONATE permission on the database user or ALTER permission on the application role.</span></span> <span data-ttu-id="08971-123">証明書または非対称キーを使用して暗号化する場合は、証明書または非対称キーに対する VIEW DEFINITION 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="08971-123">If encryption is by certificate or asymmetric key, requires VIEW DEFINITION permission on the certificate or asymmetric key.</span></span> <span data-ttu-id="08971-124">対称キーを所有できるのは、Windows ログイン、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログイン、およびアプリケーション ロールだけです。</span><span class="sxs-lookup"><span data-stu-id="08971-124">Only Windows logins, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins, and application roles can own symmetric keys.</span></span> <span data-ttu-id="08971-125">グループとロールは対称キーを所有できません。</span><span class="sxs-lookup"><span data-stu-id="08971-125">Groups and roles cannot own symmetric keys.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="08971-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="08971-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-identical-symmetric-keys-on-two-different-servers"></a><span data-ttu-id="08971-127">2 台のサーバーに同じ対称キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="08971-127">To create identical symmetric keys on two different servers</span></span>  
  
1.  <span data-ttu-id="08971-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="08971-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="08971-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08971-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="08971-130">次の CREATE MASTER KEY、CREATE CERTIFICATE、および CREATE SYMMETRIC KEY ステートメントを実行して、キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="08971-130">Create a key by running the following CREATE MASTER KEY, CREATE CERTIFICATE, and CREATE SYMMETRIC KEY statements.</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'My p@55w0Rd';  
    GO  
    CREATE CERTIFICATE [cert_keyProtection] WITH SUBJECT = 'Key Protection';  
    GO  
    CREATE SYMMETRIC KEY [key_DataShare] WITH  
        KEY_SOURCE = 'My key generation bits. This is a shared secret!',  
        ALGORITHM = AES_256,   
        IDENTITY_VALUE = 'Key Identity generation bits. Also a shared secret'  
        ENCRYPTION BY CERTIFICATE [cert_keyProtection];  
    GO  
    ```  
  
4.  <span data-ttu-id="08971-131">別のサーバー インスタンスに接続し、別のクエリ ウィンドウを開き、前述の SQL ステートメントを実行して、そのサーバーに同じキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="08971-131">Connect to a separate server instance, open a different Query Window, and run the SQL statements above to create the same key on the second server.</span></span>  
  
5.  <span data-ttu-id="08971-132">最初のサーバーで次の OPEN SYMMETRIC KEY ステートメントと SELECT ステートメントを実行して、キーをテストします。</span><span class="sxs-lookup"><span data-stu-id="08971-132">Test the keys by first running the OPEN SYMMETRIC KEY statement and the SELECT statement below on the first server.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    SELECT encryptbykey(key_guid('key_DataShare'), 'MyData' )  
    GO  
    -- For example, the output might look like this: 0x2152F8DA8A500A9EDC2FAE26D15C302DA70D25563DAE7D5D1102E3056CE9EF95CA3E7289F7F4D0523ED0376B155FE9C3  
    ```  
  
6.  <span data-ttu-id="08971-133">他方のサーバーで、上の SELECT ステートメントの結果を次のコードの `@blob` 値として貼り付け、次のコードを実行して、このキーで暗号化テキストの暗号化を解除できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="08971-133">On the second server, paste the result of the previous SELECT statement into the following code as the value of `@blob` and run the following code to verify that the duplicate key can decrypt the ciphertext.</span></span>  
  
    ```  
    OPEN SYMMETRIC KEY [key_DataShare]   
        DECRYPTION BY CERTIFICATE cert_keyProtection;  
    GO  
    DECLARE @blob varbinary(8000);  
    SET @blob = SELECT CONVERT(varchar(8000), decryptbykey(@blob));  
    GO  
    ```  
  
7.  <span data-ttu-id="08971-134">両方のサーバーで対称キーを終了します。</span><span class="sxs-lookup"><span data-stu-id="08971-134">Close the symmetric key on both servers.</span></span>  
  
    ```  
    CLOSE SYMMETRIC KEY [key_DataShare];  
    GO  
    ```  
  
 <span data-ttu-id="08971-135">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="08971-135">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="08971-136">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08971-136">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [<span data-ttu-id="08971-137">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08971-137">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [<span data-ttu-id="08971-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08971-138">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
-   [<span data-ttu-id="08971-139">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08971-139">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [<span data-ttu-id="08971-140">DECRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08971-140">DECRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/decryptbykey-transact-sql)  
  
-   [<span data-ttu-id="08971-141">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="08971-141">OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/open-symmetric-key-transact-sql)  
  
  
