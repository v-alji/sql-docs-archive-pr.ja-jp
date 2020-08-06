---
title: Windows 認証でのデータベース ミラーリング エンドポイントの作成 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: baf1a4b1-6790-4275-b261-490bca33bdb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5558bc5684f2eb9053c935543db0c05d6225daf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634032"
---
# <a name="create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql"></a><span data-ttu-id="abdd9-102">Windows 認証でのデータベース ミラーリング エンドポイントの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="abdd9-102">Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="abdd9-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に、Windows 認証を使用するデータベース ミラーリング エンドポイントを [!INCLUDE[tsql](../../includes/tsql-md.md)]で作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-103">This topic describes how to create a database mirroring endpoint that uses Windows Authentication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="abdd9-104">データベース ミラーリングまたは [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] をサポートするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスにデータベース ミラーリング エンドポイントが必要となります。</span><span class="sxs-lookup"><span data-stu-id="abdd9-104">To support database mirroring or [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires a database mirroring endpoint.</span></span> <span data-ttu-id="abdd9-105">サーバー インスタンスは、単一のポートを備えたデータベース ミラーリング エンドポイントを 1 つだけ持つことができます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-105">A server instance can have only one database mirroring endpoint, which has a single port.</span></span> <span data-ttu-id="abdd9-106">データベース ミラーリング エンドポイントは、作成される際に、ローカル システムで利用できる任意のポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-106">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="abdd9-107">サーバー インスタンス上のすべてのデータベース ミラーリング セッションはそのポートでリッスンし、データベース ミラーリングに対するすべての着信接続はそのポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-107">All database mirroring sessions on a server instance listen on that port, and all incoming connections for database mirroring use that port.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="abdd9-108">データベース ミラーリング エンドポイントが存在し、既に使用されている場合、そのエンドポイントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="abdd9-108">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint.</span></span> <span data-ttu-id="abdd9-109">使用中のエンドポイントを削除すると、既存のセッションが切断されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-109">Dropping an in-use endpoint disrupts existing sessions.</span></span>  
  
 <span data-ttu-id="abdd9-110">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="abdd9-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="abdd9-111">**作業を開始する準備:** [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="abdd9-111">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="abdd9-112">**データベース ミラーリング エンドポイントを作成するために使用するもの:** [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="abdd9-112">**To create a database mirroring endpoint, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="abdd9-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="abdd9-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="abdd9-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="abdd9-114">Security</span></span>  
 <span data-ttu-id="abdd9-115">サーバー インスタンスの認証方法と暗号化方法は、システム管理者が設定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-115">The authentication and encryption methods of the server instance are established by the system administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="abdd9-116">RC4 アルゴリズムは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-116">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="abdd9-117">AES を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="abdd9-117">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="abdd9-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="abdd9-118">Permissions</span></span>  
 <span data-ttu-id="abdd9-119">CREATE ENDPOINT 権限、または sysadmin 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-119">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="abdd9-120">詳細については、「 [GRANT (エンドポイントの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abdd9-120">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="abdd9-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="abdd9-121">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-mirroring-endpoint-that-uses-windows-authentication"></a><span data-ttu-id="abdd9-122">Windows 認証を使用するデータベース ミラーリング エンドポイントを作成するには</span><span class="sxs-lookup"><span data-stu-id="abdd9-122">To Create a Database Mirroring Endpoint That Uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="abdd9-123">データベース ミラーリング エンドポイントを作成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-123">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to create a database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="abdd9-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="abdd9-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="abdd9-125">次のステートメントを使用して、データベース ミラーリング エンドポイントが既に存在するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-125">Determine if a database mirroring endpoint already exists by using the following statement:</span></span>  
  
    ```sql
    SELECT name, role_desc, state_desc FROM sys.database_mirroring_endpoints;
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="abdd9-126">サーバー インスタンスにデータベース ミラーリング エンドポイントが既に存在する場合、サーバー インスタンス上に確立する他のセッションにそのエンドポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-126">If a database mirroring endpoint already exists for the server instance, use that endpoint for any other sessions you establish on the server instance.</span></span>  
  
4.  <span data-ttu-id="abdd9-127">Transact-SQL を使用して、Windows 認証を使用するエンドポイントを作成するには、CREATE ENDPOINT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-127">To use Transact-SQL to create an endpoint to use with Windows Authentication, use a CREATE ENDPOINT statement.</span></span> <span data-ttu-id="abdd9-128">ステートメントは、通常、次のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="abdd9-128">The statement takes the following general form:</span></span>  
  
     <span data-ttu-id="abdd9-129">CREATE ENDPOINT *\<endpointName>*</span><span class="sxs-lookup"><span data-stu-id="abdd9-129">CREATE ENDPOINT *\<endpointName>*</span></span>  
  
     <span data-ttu-id="abdd9-130">STATE=STARTED</span><span class="sxs-lookup"><span data-stu-id="abdd9-130">STATE=STARTED</span></span>  
  
     <span data-ttu-id="abdd9-131">AS TCP ( LISTENER_PORT = *\<listenerPortList>* )</span><span class="sxs-lookup"><span data-stu-id="abdd9-131">AS TCP ( LISTENER_PORT = *\<listenerPortList>* )</span></span>  
  
     <span data-ttu-id="abdd9-132">FOR DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="abdd9-132">FOR DATABASE_MIRRORING</span></span>  
  
     <span data-ttu-id="abdd9-133">(</span><span class="sxs-lookup"><span data-stu-id="abdd9-133">(</span></span>  
  
     <span data-ttu-id="abdd9-134">[ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span><span class="sxs-lookup"><span data-stu-id="abdd9-134">[ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span></span>  
  
     <span data-ttu-id="abdd9-135">]</span><span class="sxs-lookup"><span data-stu-id="abdd9-135">]</span></span>  
  
     <span data-ttu-id="abdd9-136">[ **[,]** ENCRYPTION = **REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="abdd9-136">[ [**,**] ENCRYPTION = **REQUIRED**</span></span>  
  
     <span data-ttu-id="abdd9-137">[ ALGORITHM { *\<algorithm>* } ]</span><span class="sxs-lookup"><span data-stu-id="abdd9-137">[ ALGORITHM { *\<algorithm>* } ]</span></span>  
  
     <span data-ttu-id="abdd9-138">]</span><span class="sxs-lookup"><span data-stu-id="abdd9-138">]</span></span>  
  
     <span data-ttu-id="abdd9-139">**[,]** ROLE = *\<role>*</span><span class="sxs-lookup"><span data-stu-id="abdd9-139">[**,**] ROLE = *\<role>*</span></span>  
  
     <span data-ttu-id="abdd9-140">)</span><span class="sxs-lookup"><span data-stu-id="abdd9-140">)</span></span>  
  
     <span data-ttu-id="abdd9-141">where</span><span class="sxs-lookup"><span data-stu-id="abdd9-141">where</span></span>  
  
    -   <span data-ttu-id="abdd9-142">*\<endpointName>* は、サーバー インスタンスのデータベース ミラーリング エンドポイントの一意名です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-142">*\<endpointName>* is a unique name for the database mirroring endpoint of the server instance.</span></span>  
  
    -   <span data-ttu-id="abdd9-143">STARTED によって、エンドポイントが開始され、接続のリッスンが開始されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-143">STARTED specifies that the endpoint is to be started and to begin listening for connections.</span></span> <span data-ttu-id="abdd9-144">データベース ミラーリング エンドポイントは、通常、STARTED 状態で作成されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-144">A database mirroring endpoint typically is created in the STARTED state.</span></span> <span data-ttu-id="abdd9-145">STOPPED 状態 (既定) または DISABLED 状態でセッションを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-145">Alternatively, you can start a session in a STOPPED state (the default) or DISABLED state.</span></span>  
  
    -   <span data-ttu-id="abdd9-146">*\<listenerPortList>* は、サーバーがデータベース ミラーリング メッセージをリッスンする単一のポート番号 (*nnnn*) です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-146">*\<listenerPortList>* is a single port number (*nnnn*) on which you want the server to listen for database mirroring messages.</span></span> <span data-ttu-id="abdd9-147">TCP のみ使用できます。他のプロトコルを指定するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-147">Only TCP is allowed; specifying any other protocol causes an error.</span></span>  
  
         <span data-ttu-id="abdd9-148">ポート番号は、コンピューター システムにつき 1 つだけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-148">A port number can be used only once per computer system.</span></span> <span data-ttu-id="abdd9-149">データベース ミラーリング エンドポイントは、作成される際に、ローカル システムで利用できる任意のポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-149">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="abdd9-150">システムの TCP エンドポイントによって現在使用されているポートを識別するには、次の Transact-SQL ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-150">To identify the ports currently being used by TCP endpoints on the system, use the following Transact-SQL statement:</span></span>  
  
        ```  
        SELECT name, port FROM sys.tcp_endpoints;  
        ```  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="abdd9-151">各サーバー インスタンスには、一意のリスナー ポートが 1 つだけ必要です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-151">Each server instance requires one and only one unique listener port.</span></span>  
  
    -   <span data-ttu-id="abdd9-152">Windows 認証の場合、エンドポイントで接続の認証に NTLM または Kerberos だけを使用する場合を除き、AUTHENTICATION オプションは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-152">For Windows Authentication, the AUTHENTICATION option is optional, unless you want the endpoint to use only NTLM or Kerberos to authenticate connections.</span></span> <span data-ttu-id="abdd9-153">*\<authorizationMethod>* では、次のいずれかで、接続の認証に使用する方法を指定します。NTLM、KERBEROS、NEGOTIATE。</span><span class="sxs-lookup"><span data-stu-id="abdd9-153">*\<authorizationMethod>* specifies the method used to authenticate connections as one of the following: NTLM, KERBEROS, or NEGOTIATE.</span></span> <span data-ttu-id="abdd9-154">既定値の NEGOTIATE を使用すると、エンドポイントでは、使用する Windows ネゴシエーション プロトコルに NTLM または Kerberos のいずれかが選択されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-154">The default, NEGOTIATE, causes the endpoint to use the Windows negotiation protocol to choose either NTLM or Kerberos.</span></span> <span data-ttu-id="abdd9-155">ネゴシエーションでは、相手側のエンドポイントの認証レベルに応じて、認証ありまたは認証なしの接続が可能になります。</span><span class="sxs-lookup"><span data-stu-id="abdd9-155">Negotiation enables connections with or without authentication, depending on the authentication level of the opposite endpoint.</span></span>  
  
    -   <span data-ttu-id="abdd9-156">既定では、ENCRYPTION は REQUIRED に設定されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-156">ENCRYPTION is set to REQUIRED by default.</span></span> <span data-ttu-id="abdd9-157">これは、このエンドポイントへのすべての接続に暗号化を使用する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-157">This means that all connections to this endpoint must use encryption.</span></span> <span data-ttu-id="abdd9-158">ただし、エンドポイントで暗号化を無効にしたり、オプションにできます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-158">However, you can disable encryption or make it optional on an endpoint.</span></span> <span data-ttu-id="abdd9-159">選択肢は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="abdd9-159">The alternatives are as follows:</span></span>  
  
        |<span data-ttu-id="abdd9-160">値</span><span class="sxs-lookup"><span data-stu-id="abdd9-160">Value</span></span>|<span data-ttu-id="abdd9-161">定義</span><span class="sxs-lookup"><span data-stu-id="abdd9-161">Definition</span></span>|  
        |-----------|----------------|  
        |<span data-ttu-id="abdd9-162">DISABLED</span><span class="sxs-lookup"><span data-stu-id="abdd9-162">DISABLED</span></span>|<span data-ttu-id="abdd9-163">接続を経由して送信されたデータが暗号化されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-163">Specifies that data sent over a connection is not encrypted.</span></span>|  
        |<span data-ttu-id="abdd9-164">SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="abdd9-164">SUPPORTED</span></span>|<span data-ttu-id="abdd9-165">反対側のエンドポイントで SUPPORTED または REQUIRED が指定されている場合に限り、データを暗号化することを指定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-165">Specifies that the data is encrypted only if the opposite endpoint specifies either SUPPORTED or REQUIRED.</span></span>|  
        |<span data-ttu-id="abdd9-166">REQUIRED</span><span class="sxs-lookup"><span data-stu-id="abdd9-166">REQUIRED</span></span>|<span data-ttu-id="abdd9-167">接続を経由して送信されるデータを暗号化する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-167">Specifies that data sent over a connection must be encrypted.</span></span>|  
  
         <span data-ttu-id="abdd9-168">あるエンドポイントで暗号化が必要な場合は、他のエンドポイントで ENCRYPTION が SUPPORTED または REQUIRED に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="abdd9-168">If an endpoint requires encryption, the other endpoint must have ENCRYPTION set to either SUPPORTED or REQUIRED.</span></span>  
  
    -   <span data-ttu-id="abdd9-169">*\<algorithm>* には、エンドポイントの暗号化標準を指定するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="abdd9-169">*\<algorithm>* provides the option of specifying the encryption standards for the endpoint.</span></span> <span data-ttu-id="abdd9-170">*\<algorithm>* の値は、次の各アルゴリズムまたはそれらの組み合わせになります。RC4、AES、AES RC4、RC4 AES。</span><span class="sxs-lookup"><span data-stu-id="abdd9-170">The value of *\<algorithm>* can be one following algorithms or combinations of algorithms: RC4, AES, AES RC4, or RC4 AES.</span></span>  
  
         <span data-ttu-id="abdd9-171">AES RC4 では、エンドポイントが暗号化アルゴリズムのネゴシエートを行う際に、AES アルゴリズムを優先することが示されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-171">AES RC4 specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the AES algorithm.</span></span> <span data-ttu-id="abdd9-172">RC4 AES では、エンドポイントが暗号化アルゴリズムのネゴシエートを行う際に、RC4 アルゴリズムを優先することが示されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-172">RC4 AES specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the RC4 algorithm.</span></span> <span data-ttu-id="abdd9-173">両方のエンドポイントで両方のアルゴリズムを異なる順序で指定した場合、接続を受け入れた方のエンドポイントが優先されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-173">If both endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="abdd9-174">RC4 アルゴリズムは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-174">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="abdd9-175">AES を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="abdd9-175">We recommend that you use AES.</span></span>  
  
    -   <span data-ttu-id="abdd9-176">*\<role>* では、サーバーが実行できるロールが定義されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-176">*\<role>* defines the role or roles that the server can perform.</span></span> <span data-ttu-id="abdd9-177">ROLE の指定は必須です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-177">Specifying ROLE is required.</span></span> <span data-ttu-id="abdd9-178">ただし、エンドポイントのロールが適用されるのは、データベース ミラーリングの場合のみです。</span><span class="sxs-lookup"><span data-stu-id="abdd9-178">However, the role of the endpoint is relevant only for database mirroring.</span></span> <span data-ttu-id="abdd9-179">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]では、エンドポイントのロールが無視されます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-179">For [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the role of the endpoint is ignored.</span></span>  
  
         <span data-ttu-id="abdd9-180">サーバー インスタンスが、あるデータベース ミラーリング セッションではあるロールを使用し、他のセッションでは別のロールを使用できるようにするには、ROLE=ALL を指定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-180">To allow a server instance to serve as one role for one database mirroring session and different role for another session, specify ROLE=ALL.</span></span> <span data-ttu-id="abdd9-181">パートナーまたはミラーリング監視サーバーのいずれかになるようにサーバー インスタンスを制限するには、ROLE=PARTNER または ROLE=WITNESS をそれぞれ指定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-181">To restrict a server instance to being either a partner or a witness, specify ROLE=PARTNER or ROLE=WITNESS, respectively.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="abdd9-182">の各エディションのデータベースミラーリングオプションの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abdd9-182">For more information about Database Mirroring options for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
     <span data-ttu-id="abdd9-183">CREATE ENDPOINT 構文の詳細な説明については、「 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)で作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-183">For a complete description of the CREATE ENDPOINT syntax, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="abdd9-184">既存のエンドポイントを変更するには、「 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)で作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-184">To change an existing endpoint, use [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
###  <a name="example-creating-endpoints-to-support-for-database-mirroring-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="abdd9-185">例: データベース ミラーリングをサポートするエンドポイントの作成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="abdd9-185">Example: Creating Endpoints to Support for Database Mirroring (Transact-SQL)</span></span>  
 <span data-ttu-id="abdd9-186">次の例では、3 台の異なるコンピューター システムに既定のサーバー インスタンスのデータベース ミラーリング エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-186">The following example creates database mirroring endpoints for the default server instances on three separate computer systems:</span></span>  
  
|<span data-ttu-id="abdd9-187">サーバー インスタンスの役割</span><span class="sxs-lookup"><span data-stu-id="abdd9-187">Role of server instance</span></span>|<span data-ttu-id="abdd9-188">ホスト コンピューター名</span><span class="sxs-lookup"><span data-stu-id="abdd9-188">Name of host computer</span></span>|  
|-----------------------------|---------------------------|  
|<span data-ttu-id="abdd9-189">パートナー (初期はプリンシパル)</span><span class="sxs-lookup"><span data-stu-id="abdd9-189">Partner (initially in the principal role)</span></span>|`SQLHOST01\.`|  
|<span data-ttu-id="abdd9-190">パートナー (初期はミラー)</span><span class="sxs-lookup"><span data-stu-id="abdd9-190">Partner (initially in the mirror role)</span></span>|`SQLHOST02\.`|  
|<span data-ttu-id="abdd9-191">ミラーリング監視サーバー</span><span class="sxs-lookup"><span data-stu-id="abdd9-191">Witness</span></span>|`SQLHOST03\.`|  
  
 <span data-ttu-id="abdd9-192">この例では、3 つのエンドポイントすべてでポート番号 7022 を使用しますが、利用可能なポート番号であればどれでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="abdd9-192">In this example, all three endpoints use port number 7022, though any available port number would work.</span></span> <span data-ttu-id="abdd9-193">エンドポイントでは既定の Windows 認証を使用するので、AUTHENTICATION オプションは不要です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-193">The AUTHENTICATION option is unnecessary, because the endpoints use the default type, Windows Authentication.</span></span> <span data-ttu-id="abdd9-194">エンドポイントはいずれも Windows 認証の既定動作に従い接続のための認証方法をネゴシエートする仕様なので、ENCRYPTION オプションも不要です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-194">The ENCRYPTION option is also unnecessary, because the endpoints are all intended to negotiate the authentication method for a connection, which is the default behavior for Windows Authentication.</span></span> <span data-ttu-id="abdd9-195">また、すべてのエンドポイントで、既定動作に従い暗号化が必要です。</span><span class="sxs-lookup"><span data-stu-id="abdd9-195">Also, all of the endpoints require the encryption, which is the default behavior.</span></span>  
  
 <span data-ttu-id="abdd9-196">各サーバー インスタンスは、パートナーまたはミラーリング監視サーバーのいずれかとしてのみ機能するように制限します。各サーバーのエンドポイントは役割を明示 (ROLE=PARTNER または ROLE=WITNESS) します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-196">Each server instance is limited to serving as either a partner or a witness, and the endpoint of each server expressly specifies which role (ROLE=PARTNER or ROLE=WITNESS).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="abdd9-197">各サーバー インスタンスにはエンドポイントを 1 つしか作成できません。</span><span class="sxs-lookup"><span data-stu-id="abdd9-197">Each server instance can have only one endpoint.</span></span> <span data-ttu-id="abdd9-198">したがって、1 つのサーバー インスタンスをセッションによってパートナーにしたりミラーリング監視サーバーにしたりする場合は、ROLE=ALL を指定します。</span><span class="sxs-lookup"><span data-stu-id="abdd9-198">Therefore, if you want a server instance to be a partner in some sessions and the witness in others, specify ROLE=ALL.</span></span>  
  
```sql
--Endpoint for initial principal server instance, which  
--is the only server instance running on SQLHOST01.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for initial mirror server instance, which  
--is the only server instance running on SQLHOST02.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for witness server instance, which  
--is the only server instance running on SQLHOST03.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=WITNESS);  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="abdd9-199">関連タスク</span><span class="sxs-lookup"><span data-stu-id="abdd9-199">Related Tasks</span></span>  

### <a name="to-configure-a-database-mirroring-endpoint"></a><span data-ttu-id="abdd9-200">データベース ミラーリング エンドポイントを構成するには</span><span class="sxs-lookup"><span data-stu-id="abdd9-200">To Configure a Database Mirroring Endpoint</span></span>
  
-   [<span data-ttu-id="abdd9-201">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-201">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](../availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="abdd9-202">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-202">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="abdd9-203">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-203">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="abdd9-204">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-204">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="abdd9-205">サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-205">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="abdd9-206">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-206">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="abdd9-207">**データベース ミラーリング エンドポイントに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="abdd9-207">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="abdd9-208">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-208">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="abdd9-209">参照</span><span class="sxs-lookup"><span data-stu-id="abdd9-209">See Also</span></span>  
 <span data-ttu-id="abdd9-210">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abdd9-210">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="abdd9-211">[暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="abdd9-211">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="abdd9-212">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abdd9-212">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="abdd9-213">[サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="abdd9-213">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="abdd9-214">[例:Windows 認証を使用したデータベース ミラーリングの設定 &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="abdd9-214">[Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="abdd9-215">データベース ミラーリング エンドポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="abdd9-215">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
