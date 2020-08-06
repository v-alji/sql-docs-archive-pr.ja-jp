---
title: データベースミラーリングエンドポイントで着信接続に証明書を使用できるようにする (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- inbound connections
- database mirroring [SQL Server], security
ms.assetid: 5d48bb98-61f0-4b99-8f1a-b53f831d63d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c05397dfbd1740293c4b154ace1ed5704cec11a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632673"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-inbound-connections-transact-sql"></a><span data-ttu-id="28f17-102">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="28f17-102">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="28f17-103">このトピックでは、データベース ミラーリングの着信接続を認証する際に証明書を使用するようにサーバー インスタンスを構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="28f17-103">This topic describes the steps for configuring server instances to use certificates to authenticate inbound connections for database mirroring.</span></span> <span data-ttu-id="28f17-104">着信接続を設定する前に、各サーバー インスタンスで発信接続を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28f17-104">Before you can set up inbound connections, you must configure outbound connections on each server instance.</span></span> <span data-ttu-id="28f17-105">詳細については、「 [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="28f17-105">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
 <span data-ttu-id="28f17-106">着信接続を構成する処理には、次の一般的な手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="28f17-106">The process of configuring inbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="28f17-107">他のシステムへのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="28f17-107">Create a login for other system.</span></span>  
  
2.  <span data-ttu-id="28f17-108">そのログインのユーザー名を作成します。</span><span class="sxs-lookup"><span data-stu-id="28f17-108">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="28f17-109">他のサーバー インスタンスのミラーリング エンドポイント用の証明書を入手します。</span><span class="sxs-lookup"><span data-stu-id="28f17-109">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="28f17-110">手順 2. で作成したユーザーに証明書を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="28f17-110">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="28f17-111">ミラーリング エンドポイント用のログインに CONNECT 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="28f17-111">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="28f17-112">ミラーリング監視サーバーがある場合は、このサーバーでも着信接続の構成を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="28f17-112">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="28f17-113">この場合、どちらのパートナーのミラーリング監視サーバーでも、相手のログイン、ユーザー、証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="28f17-113">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="28f17-114">次の手順では、上記の手順について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="28f17-114">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="28f17-115">各手順では、HOST_A という名前のシステムでサーバー インスタンスを構成するための例を示します。</span><span class="sxs-lookup"><span data-stu-id="28f17-115">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="28f17-116">その後に続く「例」では、HOST_B という名前のシステム上の別のサーバー インスタンスに対する同じ手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="28f17-116">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
### <a name="to-configure-server-instances-for-inbound-mirroring-connections-on-host_a"></a><span data-ttu-id="28f17-117">ミラーリングの着信接続用に (HOST_A 上で) サーバー インスタンスを構成するには</span><span class="sxs-lookup"><span data-stu-id="28f17-117">To configure server instances for inbound mirroring connections (on HOST_A)</span></span>  
  
1.  <span data-ttu-id="28f17-118">他のシステムへのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="28f17-118">Create a login for the other system.</span></span>  
  
     <span data-ttu-id="28f17-119">次の例では、システム HOST_B のログインを HOST_A のサーバー インスタンスの **master** データベースに作成します。この例では、このログインに `HOST_B_login`という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="28f17-119">The following example creates a login for the system, HOST_B, in the **master** database of the server instance on HOST_A; in this example, the login is named `HOST_B_login`.</span></span> <span data-ttu-id="28f17-120">サンプルのパスワードは、独自のパスワードに置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="28f17-120">Substitute a password of your own for the sample password.</span></span>  
  
    ```sql  
    USE master;  
    CREATE LOGIN HOST_B_login   
       WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
     <span data-ttu-id="28f17-121">詳細については、「[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-121">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
     <span data-ttu-id="28f17-122">このサーバー インスタンスのログインを表示するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="28f17-122">To view the logins on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.server_principals;  
    ```  
  
     <span data-ttu-id="28f17-123">詳細については、「[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-123">For more information, see [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql).</span></span>  
  
2.  <span data-ttu-id="28f17-124">そのログインのユーザー名を作成します。</span><span class="sxs-lookup"><span data-stu-id="28f17-124">Create a user for that login.</span></span>  
  
     <span data-ttu-id="28f17-125">次の例では、上記の手順で作成したログイン用のユーザー `HOST_B_user` を作成します。</span><span class="sxs-lookup"><span data-stu-id="28f17-125">The following example creates a user, `HOST_B_user`, for the login created in the preceding step.</span></span>  
  
    ```sql  
    USE master;  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
     <span data-ttu-id="28f17-126">詳細については、「[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-126">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
     <span data-ttu-id="28f17-127">このサーバー インスタンスのユーザーを表示するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="28f17-127">To view the users on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.sysusers;  
    ```  
  
     <span data-ttu-id="28f17-128">詳細については、「[sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-128">For more information, see [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql).</span></span>  
  
3.  <span data-ttu-id="28f17-129">他のサーバー インスタンスのミラーリング エンドポイント用の証明書を入手します。</span><span class="sxs-lookup"><span data-stu-id="28f17-129">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
     <span data-ttu-id="28f17-130">発信接続の構成時にリモート サーバー インスタンスのミラーリング エンドポイント用の証明書のコピーを入手していない場合は、これを入手します。</span><span class="sxs-lookup"><span data-stu-id="28f17-130">If you have not already done so when configuring outbound connections, obtain a copy of the certificate for the mirroring endpoint of the remote server instance.</span></span> <span data-ttu-id="28f17-131">これを行うには、「[データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)」の説明に従って、そのサーバー インスタンスの証明書をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="28f17-131">To do this, back up the certificate on that server instance as described in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span> <span data-ttu-id="28f17-132">証明書を別のシステムにコピーする場合は、セキュリティで保護されたコピー方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-132">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="28f17-133">すべての証明書をセキュリティで保護された状態で保管するよう十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-133">Be extremely careful to keep all of your certificates secure.</span></span>  
  
     <span data-ttu-id="28f17-134">詳細については、「[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-134">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
4.  <span data-ttu-id="28f17-135">手順 2. で作成したユーザーに証明書を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="28f17-135">Associate the certificate with the user created in step 2.</span></span>  
  
     <span data-ttu-id="28f17-136">次の例では、HOST_B の証明書と HOST_B のユーザーを HOST_A で関連付けています。</span><span class="sxs-lookup"><span data-stu-id="28f17-136">The following example, associates the certificate of HOST_B with its user on HOST_A.</span></span>  
  
    ```sql  
    USE master;  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
     <span data-ttu-id="28f17-137">詳細については、「[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-137">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="28f17-138">このサーバー インスタンスの証明書を表示するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="28f17-138">To view the certificates on this server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="28f17-139">詳細については、「[sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-139">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
5.  <span data-ttu-id="28f17-140">リモート ミラーリング エンドポイント用のログインに CONNECT 権限を許可します。</span><span class="sxs-lookup"><span data-stu-id="28f17-140">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
     <span data-ttu-id="28f17-141">たとえば、HOST_A に対する権限を HOST_B 上のリモート サーバー インスタンスに許可し、このローカル ログインに接続 (つまり、`HOST_B_login` に接続) するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="28f17-141">For example, to grant permission on HOST_A to the remote server instance on HOST_B to connect to its local login-that is, to connect to `HOST_B_login`-use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```sql  
    USE master;  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
     <span data-ttu-id="28f17-142">詳細については、「 [GRANT (エンドポイントの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-142">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="28f17-143">これで、HOST_A にログインするための HOST_B の証明書認証の設定が完了します。</span><span class="sxs-lookup"><span data-stu-id="28f17-143">This completes setting up certificate authentication for HOST_B to log in to HOST_A.</span></span>  
  
 <span data-ttu-id="28f17-144">ここで、HOST_B で HOST_A 用の着信接続を構成するために同じ手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28f17-144">You now need to perform the equivalent inbound steps for HOST_A on HOST_B.</span></span> <span data-ttu-id="28f17-145">この手順については、次の「例」のサンプル コードで着信接続の設定部分を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-145">These steps are illustrated in the inbound portion of the example in the Example section, below.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f17-146">例</span><span class="sxs-lookup"><span data-stu-id="28f17-146">Example</span></span>  
 <span data-ttu-id="28f17-147">次の例では、HOST_B の着信接続を構成する方法について示します。</span><span class="sxs-lookup"><span data-stu-id="28f17-147">The following example demonstrates configuring HOST_B for inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28f17-148">この例では、「[データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)」のコード スニペットによって作成される HOST_A 証明書を含む証明書ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="28f17-148">This example uses a certificate file containing the HOST_A certificate that is created by a code snippet in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
```sql  
USE master;  
--On HOST_B, create a login for HOST_A.  
CREATE LOGIN HOST_A_login WITH PASSWORD = 'AStrongPassword!@#';  
GO  
--Create a user, HOST_A_user, for that login.  
CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
GO  
--Obtain HOST_A certificate. (See the note   
--   preceding this example.)  
--Asscociate this certificate with the user, HOST_A_user.  
CREATE CERTIFICATE HOST_A_cert  
   AUTHORIZATION HOST_A_user  
   FROM FILE = 'C:\HOST_A_cert.cer';  
GO  
--Grant CONNECT permission for the server instance on HOST_A.  
GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO HOST_A_login;  
GO  
```  
  
 <span data-ttu-id="28f17-149">自動フェールオーバーを伴う高い安全性モードで実行する場合、発信接続と着信接続の両方に対応するようミラーリング監視サーバーを構成する手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="28f17-149">If you intend to run in high-safety mode with automatic failover, you must repeat the same set up steps to configure the witness for outbound and inbound connections.</span></span>  
  
 <span data-ttu-id="28f17-150">Transact-SQL の例を含む、ミラー データベースを作成する方法の詳細については、「[ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-150">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="28f17-151">高パフォーマンス モードのセッションを確立する Transact-SQL の例については、「[証明書を使用したデータベース ミラーリングの設定の例 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-151">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="28f17-152">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="28f17-152">.NET Framework Security</span></span>  
 <span data-ttu-id="28f17-153">証明書を別のシステムにコピーする場合は、セキュリティで保護されたコピー方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-153">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="28f17-154">すべての証明書をセキュリティで保護された状態で保管するよう十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="28f17-154">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f17-155">参照</span><span class="sxs-lookup"><span data-stu-id="28f17-155">See Also</span></span>  
 <span data-ttu-id="28f17-156">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="28f17-156">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="28f17-157">[GRANT (エンドポイントのアクセス許可の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28f17-157">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 <span data-ttu-id="28f17-158">[暗号化されたミラーデータベースを設定する](set-up-an-encrypted-mirror-database.md) </span><span class="sxs-lookup"><span data-stu-id="28f17-158">[Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md) </span></span>  
 <span data-ttu-id="28f17-159">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="28f17-159">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 [<span data-ttu-id="28f17-160">データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28f17-160">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
