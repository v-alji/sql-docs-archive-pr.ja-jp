---
title: データベースミラーリングエンドポイントで発信接続に証明書を使用できるようにする (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- outbound connections [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 464c9096-10d6-4c5e-8bb1-19acba27ad9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f380f268f8d0f8d033db9c28f83d066d3f134571
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632672"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-outbound-connections-transact-sql"></a><span data-ttu-id="3ad11-102">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3ad11-102">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="3ad11-103">このトピックでは、データベース ミラーリングの発信接続を認証する際に証明書を使用するようにサーバー インスタンスを構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-103">This topic describes the steps for configuring server instances to use certificates to authenticate outbound connections for database mirroring.</span></span> <span data-ttu-id="3ad11-104">着信接続を設定する前に、発信接続を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad11-104">Outbound connection configuration must be done before you can set up inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ad11-105">1 つのサーバー インスタンス上のすべてのミラーリング接続では、1 つのデータベース ミラーリング エンドポイントが使用されます。そのため、エンドポイントを作成する際にサーバー インスタンスの認証方法を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad11-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span>  
  
 <span data-ttu-id="3ad11-106">発信接続を構成する処理には、次の一般的な手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3ad11-106">The process of configuring outbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="3ad11-107">**master** データベースで、データベース マスター キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-107">In the **master** database, create a database Master Key.</span></span>  
  
2.  <span data-ttu-id="3ad11-108">**master** データベースで、暗号化された証明書をサーバー インスタンスに作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-108">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="3ad11-109">作成した証明書を使用して、サーバー インスタンスのエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-109">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="3ad11-110">証明書をファイルにバックアップし、そのファイルをセキュリティで保護された状態で他のシステムにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3ad11-110">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="3ad11-111">パートナーおよびミラーリング監視サーバーがある場合は、それぞれで上記の手順を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad11-111">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="3ad11-112">次の手順では、上記の手順について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-112">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="3ad11-113">各手順では、HOST_A という名前のシステムでサーバー インスタンスを構成するための例を示します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-113">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="3ad11-114">その後に続く「例」では、HOST_B という名前のシステム上の別のサーバー インスタンスに対する同じ手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-114">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="3ad11-115">手順</span><span class="sxs-lookup"><span data-stu-id="3ad11-115">Procedure</span></span>  
  
#### <a name="to-configure-server-instances-for-outbound-mirroring-connections-on-host_a"></a><span data-ttu-id="3ad11-116">ミラーリングの発信接続用に (HOST_A 上で) サーバー インスタンスを構成するには</span><span class="sxs-lookup"><span data-stu-id="3ad11-116">To configure server instances for outbound mirroring connections (On HOST_A)</span></span>  
  
1.  <span data-ttu-id="3ad11-117">**master** データベースで、データベース マスター キーが存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-117">On the **master** database, create the database Master Key, if none exists.</span></span> <span data-ttu-id="3ad11-118">データベースの既存のキーを表示するには、 [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) カタログ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-118">To view the existing keys for a database, use the [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) catalog view.</span></span>  
  
     <span data-ttu-id="3ad11-119">データベース マスター キーを作成するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-119">To create the database Master Key, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command:</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
     <span data-ttu-id="3ad11-120">複雑で一意なパスワードを使用し、作成したキーを安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-120">Use a unique, strong password, and record it in a safe place.</span></span>  
  
     <span data-ttu-id="3ad11-121">詳細については、「[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)」と「[データベース マスター キーの作成](../../relational-databases/security/encryption/create-a-database-master-key.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-121">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md).</span></span>  
  
2.  <span data-ttu-id="3ad11-122">**master** データベースで、データベース ミラーリングの発信接続に使用する、暗号化された証明書をサーバー インスタンスに作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-122">In the **master** database, create an encrypted certificate on the server instance to use for its outbound connections for database mirroring.</span></span>  
  
     <span data-ttu-id="3ad11-123">たとえば、HOST_A システム用の証明書を作成するには、次のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-123">For example, to create a certificate for the HOST_A system.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3ad11-124">証明書の使用期間が 1 年を超える場合は、CREATE CERTIFICATE ステートメントの EXPIRY_DATE オプションを使用して、有効期限を UTC 時間で指定してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-124">If you intend to use the certificate for more than one year, specify the expiry date in UTC time by using the EXPIRY_DATE option in your CREATE CERTIFICATE statement.</span></span> <span data-ttu-id="3ad11-125">また、証明書の有効期限が近いことを知らせるポリシー ベースの管理ルールを SQL Server Management Studio で作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3ad11-125">Also, we recommend that you use SQL Server Management Studio to create a Policy-Based Management rule to alert you when your certificates are expiring.</span></span> <span data-ttu-id="3ad11-126">ポリシー管理の **[新しい条件の作成]** ダイアログ ボックスを使用し、 **@ExpirationDate** ファセットの **[@ExpirationDate]** フィールドでこのルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-126">Using the Policy Management **Create New Condition** dialog box, create this rule on the **@ExpirationDate** field of the **Certificate** facet.</span></span> <span data-ttu-id="3ad11-127">詳細については、「 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) 」と「 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-127">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Securing SQL Server](../../relational-databases/security/securing-sql-server.md).</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate for database mirroring',   
       EXPIRY_DATE = '11/30/2013';  
    GO  
    ```  
  
     <span data-ttu-id="3ad11-128">詳細については、「[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-128">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="3ad11-129">**master** データベースの証明書を表示するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ad11-129">To view the certificates in the **master** database, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="3ad11-130">詳細については、「[sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-130">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
3.  <span data-ttu-id="3ad11-131">各サーバー インスタンスにデータベース ミラーリング エンドポイントがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-131">Ensure that the database mirroring endpoint exist on each of the server instances.</span></span>  
  
     <span data-ttu-id="3ad11-132">サーバー インスタンスにデータベース ミラーリング エンドポイントが既に存在する場合、サーバー インスタンス上で確立するその他のセッションにそのエンドポイントを再利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad11-132">If a database mirroring endpoint already exists for the server instance, you should reuse that endpoint for any other sessions you establish on the server instance.</span></span> <span data-ttu-id="3ad11-133">データベース ミラーリング エンドポイントがサーバー インスタンスに存在するかどうかを確認し、その構成を表示するには、次のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-133">To determine whether a database mirroring endpoint exists on a server instance and to view its configuration, use the following statement:</span></span>  
  
    ```  
    SELECT name, role_desc, state_desc, connection_auth_desc, encryption_algorithm_desc   
       FROM sys.database_mirroring_endpoints;  
    ```  
  
     <span data-ttu-id="3ad11-134">エンドポイントが存在しない場合、発信接続にこの証明書を使用し、他のシステムでの検証にその証明書の資格情報を使用するエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-134">If no endpoint exists, create an endpoint that uses this certificate for outbound connections and that uses the certificate's credentials for verification on the other system.</span></span> <span data-ttu-id="3ad11-135">これは、サーバー全体のエンドポイントであり、サーバー インスタンスが参加するすべてのミラーリング セッションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="3ad11-135">This is a server-wide endpoint that is used by all mirroring sessions in which the server instance participates.</span></span>  
  
     <span data-ttu-id="3ad11-136">たとえば、HOST_A 上のサーバー インスタンスの例にミラーリング エンドポイントを作成するには、次のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-136">For example, to create a mirroring endpoint for the example server instance on HOST_A.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
     <span data-ttu-id="3ad11-137">詳細については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-137">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
4.  <span data-ttu-id="3ad11-138">証明書をバックアップし、他のシステムにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3ad11-138">Back up the certificate and copy it to the other system or systems.</span></span> <span data-ttu-id="3ad11-139">この操作は、他のシステムで着信接続を構成するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3ad11-139">This is necessary in order to configure inbound connections on the other system.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
     <span data-ttu-id="3ad11-140">詳細については、「[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-140">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="3ad11-141">任意の安全な方法を使用し、この証明書をコピーします。</span><span class="sxs-lookup"><span data-stu-id="3ad11-141">Copy this certificate using any secure method you choose.</span></span> <span data-ttu-id="3ad11-142">すべての証明書をセキュリティで保護された状態で保管するよう十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-142">Be extremely careful to keep all of your certificates secure.</span></span>  
  
 <span data-ttu-id="3ad11-143">上記の手順のコード例では、HOST_A の発信接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-143">The example code in the preceding steps configure outbound connections on HOST_A.</span></span>  
  
 <span data-ttu-id="3ad11-144">ここで、HOST_B の着信接続を構成するために同じ手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad11-144">You now need to perform the equivalent outbound steps for HOST_B.</span></span> <span data-ttu-id="3ad11-145">この手順については、次の「例」で説明します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-145">These steps are illustrated in the following Example section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ad11-146">例</span><span class="sxs-lookup"><span data-stu-id="3ad11-146">Example</span></span>  
 <span data-ttu-id="3ad11-147">次の例では、発信接続用に HOST_B を構成する方法について示します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-147">The following example demonstrates configuring HOST_B for outbound connections.</span></span>  
  
```  
USE master;  
--Create the database Master Key, if needed.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
GO  
-- Make a certifcate on HOST_B server instance.  
CREATE CERTIFICATE HOST_B_cert   
   WITH SUBJECT = 'HOST_B certificate for database mirroring',   
   EXPIRY_DATE = '11/30/2013';  
GO  
--Create a mirroring endpoint for the server instance on HOST_B.  
CREATE ENDPOINT Endpoint_Mirroring  
   STATE = STARTED  
   AS TCP (  
      LISTENER_PORT=7024  
      , LISTENER_IP = ALL  
   )   
   FOR DATABASE_MIRRORING (   
      AUTHENTICATION = CERTIFICATE HOST_B_cert  
      , ENCRYPTION = REQUIRED ALGORITHM AES  
      , ROLE = ALL  
   );  
GO  
--Backup HOST_B certificate.  
BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
GO   
--Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.  
```  
  
 <span data-ttu-id="3ad11-148">任意の安全な方法を使用し、証明書を他のシステムにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3ad11-148">Copy the certificate to the other system using any secure method you choose.</span></span> <span data-ttu-id="3ad11-149">すべての証明書をセキュリティで保護された状態で保管するよう十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-149">Be extremely careful to keep all of your certificates secure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ad11-150">発信接続を設定した後、各サーバー インスタンスの着信接続を他のサーバー インスタンス用に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ad11-150">After you set up outbound connections, you must configure inbound connections on each server instance for the other server instance or instances.</span></span> <span data-ttu-id="3ad11-151">詳細については、「 [データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ad11-151">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
 <span data-ttu-id="3ad11-152">Transact-SQL の例を含む、ミラー データベースを作成する方法の詳細については、「[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-152">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="3ad11-153">高パフォーマンス モードのセッションを確立する Transact-SQL の例については、「[証明書を使用したデータベース ミラーリングの設定の例 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-153">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3ad11-154">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="3ad11-154">.NET Framework Security</span></span>  
 <span data-ttu-id="3ad11-155">ネットワークがセキュリティで保護されていることを保証できる場合を除いて、データベース ミラーリング接続に対して暗号化を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3ad11-155">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="3ad11-156">証明書を別のシステムにコピーする場合は、セキュリティで保護されたコピー方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="3ad11-156">When copying a certificate to another system, use a secure copy method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad11-157">参照</span><span class="sxs-lookup"><span data-stu-id="3ad11-157">See Also</span></span>  
 <span data-ttu-id="3ad11-158">[暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="3ad11-158">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="3ad11-159">[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ad11-159">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="3ad11-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ad11-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="3ad11-161">[例:証明書を使用したデータベース ミラーリングの設定 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="3ad11-161">[Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span></span>  
 <span data-ttu-id="3ad11-162">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ad11-162">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="3ad11-163">[データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ad11-163">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="3ad11-164">暗号化されたミラー データベースの設定</span><span class="sxs-lookup"><span data-stu-id="3ad11-164">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
