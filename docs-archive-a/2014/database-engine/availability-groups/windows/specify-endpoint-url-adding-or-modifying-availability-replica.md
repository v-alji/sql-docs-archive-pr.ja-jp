---
title: 可用性レプリカを追加または変更するときにエンドポイント URL を指定する (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- endpoints [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], endpoint
- Endpoint URLs (HADR)
ms.assetid: d7520c13-a8ee-4ddc-9e9a-54cd3d27ef1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da1eb2bacd4d5a2f7d0b2a623343f62b5e89597d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741298"
---
# <a name="specify-the-endpoint-url-when-adding-or-modifying-an-availability-replica-sql-server"></a><span data-ttu-id="1604c-102">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1604c-102">Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="1604c-103">可用性グループの可用性レプリカをホストするには、サーバー インスタンスにデータベース ミラーリング エンドポイントが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1604c-103">To host an availability replica for an availability group, a server instance must possess a database mirroring endpoint.</span></span> <span data-ttu-id="1604c-104">サーバー インスタンスでは、このエンドポイントを使用して、他のサーバー インスタンスによってホストされる可用性レプリカから [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のメッセージをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="1604c-104">The server instance uses this endpoint to listen for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] messages from availability replicas hosted by other server instances.</span></span> <span data-ttu-id="1604c-105">可用性グループの可用性レプリカを定義するには、そのレプリカをホストするサーバー インスタンスのエンドポイント URL を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1604c-105">To define an availability replica for an availability group, you must specify the endpoint URL of the server instance that will host the replica.</span></span> <span data-ttu-id="1604c-106">*エンドポイント URL* は、データベース ミラーリング エンドポイントのトランスポート プロトコル (TCP)、サーバー インスタンスのシステム アドレス、およびエンドポイントに関連付けられているポート番号を識別します。</span><span class="sxs-lookup"><span data-stu-id="1604c-106">The *endpoint URL* identifies the transport protocol of the database mirroring endpoint-TCP, the system address of the server instance, and the port number associated with the endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1604c-107">"エンドポイント URL" という用語は、データベース ミラーリングのユーザー インターフェイスとドキュメントで使用される "サーバー ネットワーク アドレス" という用語と同義です。</span><span class="sxs-lookup"><span data-stu-id="1604c-107">The term "endpoint URL" is synonymous with the term "server network address" used by the database mirroring user interface and documentation.</span></span>  
  
-   [<span data-ttu-id="1604c-108">エンドポイント URL の構文</span><span class="sxs-lookup"><span data-stu-id="1604c-108">Syntax for an Endpoint URL</span></span>](#SyntaxOfURL)  
  
-   [<span data-ttu-id="1604c-109">システムの完全修飾ドメイン名の検索</span><span class="sxs-lookup"><span data-stu-id="1604c-109">Finding the Fully Qualified Domain Name of A System</span></span>](#Finding_FQDN)  
  
-   [<span data-ttu-id="1604c-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1604c-110">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="1604c-111">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="1604c-111">Related Content</span></span>](#RelatedContent)  
  
##  <a name="syntax-for-an-endpoint-url"></a><a name="SyntaxOfURL"></a> <span data-ttu-id="1604c-112">エンドポイント URL の構文</span><span class="sxs-lookup"><span data-stu-id="1604c-112">Syntax for an Endpoint URL</span></span>  
 <span data-ttu-id="1604c-113">エンドポイント URL の構文は、次のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="1604c-113">The syntax for an endpoint URL is of the form:</span></span>  
  
 <span data-ttu-id="1604c-114">TCP<strong>://</strong> *\<system-address>* <strong>:</strong> *\<port>*</span><span class="sxs-lookup"><span data-stu-id="1604c-114">TCP<strong>://</strong>*\<system-address>*<strong>:</strong>*\<port>*</span></span>  
  
 <span data-ttu-id="1604c-115">where</span><span class="sxs-lookup"><span data-stu-id="1604c-115">where</span></span>  
  
-   <span data-ttu-id="1604c-116">*\<system-address>* は、ターゲット コンピューター システムを明確に識別する文字列です。</span><span class="sxs-lookup"><span data-stu-id="1604c-116">*\<system-address>* is a string that unambiguously identifies the target computer system.</span></span> <span data-ttu-id="1604c-117">通常、サーバー アドレスは、システム名 (システムが同じドメインに存在する場合)、完全修飾ドメイン名、または IP アドレスになります。</span><span class="sxs-lookup"><span data-stu-id="1604c-117">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="1604c-118">Windows Server フェールオーバー クラスタリング (WSFC) クラスターのノードが同じドメイン内にある場合、コンピューター システムの名前 ( `SYSTEM46`など) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1604c-118">Because the nodes of Windows Server Failover Clustering (WSFC) cluster are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="1604c-119">IP アドレスを使用するには、それが環境内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1604c-119">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="1604c-120">IP アドレスが静的である場合にのみ、IP アドレスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1604c-120">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="1604c-121">IP アドレスには、IP Version 4 (IPv4) または IP Version 6 (IPv6) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1604c-121">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="1604c-122">IPv6 アドレスは、 **[** _<IPv6_address>_ **]** のように、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="1604c-122">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="1604c-123">システムの IP アドレスを参照するには、Windows コマンド プロンプトで、 **ipconfig** コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="1604c-123">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="1604c-124">完全修飾ドメイン名は動作が保証されています。</span><span class="sxs-lookup"><span data-stu-id="1604c-124">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="1604c-125">これは、場所によって異なる形式を使用するローカルに定義されたアドレス文字列です。</span><span class="sxs-lookup"><span data-stu-id="1604c-125">This is a locally defined address string that takes different forms in different places.</span></span> <span data-ttu-id="1604c-126">常にではありませんが多くの場合、完全修飾ドメイン名は、次の形式のようにコンピューター名、およびピリオド区切りの一連のドメイン セグメントを含む複合名になります。</span><span class="sxs-lookup"><span data-stu-id="1604c-126">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="1604c-127">_computer_name_ **.**</span><span class="sxs-lookup"><span data-stu-id="1604c-127">_computer_name_ **.**</span></span> <span data-ttu-id="1604c-128">_domain_segment_[... **.** _domain_segment_]</span><span class="sxs-lookup"><span data-stu-id="1604c-128">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="1604c-129">*computer_name*はサーバー インスタンスを実行しているコンピューターのネットワーク名、および *domain_segment*[... **.** _domain_segment_] はサーバーのその他のドメイン情報です。たとえば、 `localinfo.corp.Adventure-Works.com`のようになります。</span><span class="sxs-lookup"><span data-stu-id="1604c-129">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="1604c-130">ドメイン セグメントの内容と数は、会社内または組織内で決定されます。</span><span class="sxs-lookup"><span data-stu-id="1604c-130">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="1604c-131">詳細については、このトピックの「 [完全修飾ドメイン名の検索](#Finding_FQDN)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1604c-131">For more information, see [Finding the Fully Qualified Domain Name](#Finding_FQDN), later in this topic.</span></span>  
  
-   <span data-ttu-id="1604c-132">*\<port>* は、パートナー サーバー インスタンスのミラーリング エンドポイントによって使用されるポート番号です。</span><span class="sxs-lookup"><span data-stu-id="1604c-132">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span>  
  
     <span data-ttu-id="1604c-133">データベース ミラーリング エンドポイントは、コンピューター システム上の使用可能な任意のポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1604c-133">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="1604c-134">各ポート番号は 1 つのエンドポイントだけに関連付けられている必要があります。また、各エンドポイントは 1 つのサーバー インスタンスに関連付けられています。そのため、1 台のサーバー上に複数のサーバー インスタンスがある場合、各サーバー インスタンスは、ポートが異なる別のエンドポイントでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="1604c-134">Each port number must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="1604c-135">したがって、可用性レプリカを指定するときにエンドポイント URL で指定するポートにより、必ず、エンドポイントがそのポートに関連付けられているサーバー インスタンスに受信メッセージがリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="1604c-135">Therefore, the port you specify in the endpoint URL when you specify an availability replica will always direct incoming messages to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="1604c-136">エンドポイント URL で、ターゲット コンピューターのミラーリング エンドポイントに関連付けられているサーバー インスタンスを識別するのは、ポートの番号だけです。</span><span class="sxs-lookup"><span data-stu-id="1604c-136">IIn the endpoint URL, only the number of the port identifies the server instance that is associated with the mirroring endpoint on the target computer.</span></span> <span data-ttu-id="1604c-137">次の図は、1 台のコンピューターにある 2 つのサーバー インスタンスのエンドポイント URL を示しています。</span><span class="sxs-lookup"><span data-stu-id="1604c-137">The following figure illustrates the endpoint URLs of two server instances on a single computer.</span></span> <span data-ttu-id="1604c-138">既定のインスタンスではポート `7022` が使用され、名前付きインスタンスではポート `7033`が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1604c-138">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="1604c-139">これら 2 つのサーバー インスタンスのエンドポイント URL は、それぞれ `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` と `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`です。</span><span class="sxs-lookup"><span data-stu-id="1604c-139">The endpoint URL for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="1604c-140">アドレスにサーバー インスタンス名が含まれていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1604c-140">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="1604c-141">![既定のインスタンスのサーバー ネットワーク アドレス](../../media/dbm-2-instances-ports-1-system.gif "既定のインスタンスのサーバー ネットワーク アドレス")</span><span class="sxs-lookup"><span data-stu-id="1604c-141">![Server network addresses of a default instance](../../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="1604c-142">サーバー インスタンスのデータベース ミラーリング エンドポイントに現在関連付けられているポートを識別するには、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1604c-142">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql
    SELECT type_desc, port FROM sys.TCP_endpoints  
    ```  
  
     <span data-ttu-id="1604c-143">**type_desc** の値が "DATABASE_MIRRORING" の行を検索し、対応するポート番号を使用します。</span><span class="sxs-lookup"><span data-stu-id="1604c-143">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1604c-144">例</span><span class="sxs-lookup"><span data-stu-id="1604c-144">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="1604c-145">A.</span><span class="sxs-lookup"><span data-stu-id="1604c-145">A.</span></span> <span data-ttu-id="1604c-146">システム名を使用する</span><span class="sxs-lookup"><span data-stu-id="1604c-146">Using a system name</span></span>  
 <span data-ttu-id="1604c-147">次のエンドポイント URL では、システム名 `SYSTEM46`およびポート `7022`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1604c-147">The following endpoint URL specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
 `TCP://SYSTEM46:7022`  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="1604c-148">B.</span><span class="sxs-lookup"><span data-stu-id="1604c-148">B.</span></span> <span data-ttu-id="1604c-149">完全修飾ドメイン名を使用する</span><span class="sxs-lookup"><span data-stu-id="1604c-149">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="1604c-150">次のエンドポイント URL では、完全修飾ドメイン名 `DBSERVER8.manufacturing.Adventure-Works.com`およびポート `7024`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1604c-150">The following endpoint URL specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
 `TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024`  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="1604c-151">C.</span><span class="sxs-lookup"><span data-stu-id="1604c-151">C.</span></span> <span data-ttu-id="1604c-152">IPv4 を使用する</span><span class="sxs-lookup"><span data-stu-id="1604c-152">Using IPv4</span></span>  
 <span data-ttu-id="1604c-153">次のエンドポイント URL では、IPv4 アドレス `10.193.9.134`およびポート `7023`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1604c-153">The following endpoint URL specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
 `TCP://10.193.9.134:7023`  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="1604c-154">D.</span><span class="sxs-lookup"><span data-stu-id="1604c-154">D.</span></span> <span data-ttu-id="1604c-155">IPv6 を使用する</span><span class="sxs-lookup"><span data-stu-id="1604c-155">Using IPv6</span></span>  
 <span data-ttu-id="1604c-156">次のエンドポイント URL では、IPv6 アドレス `2001:4898:23:1002:20f:1fff:feff:b3a3`およびポート `7022`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1604c-156">The following endpoint URL contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
 `TCP://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022`  
  
##  <a name="finding-the-fully-qualified-domain-name-of-a-system"></a><a name="Finding_FQDN"></a> <span data-ttu-id="1604c-157">システムの完全修飾ドメイン名の検索</span><span class="sxs-lookup"><span data-stu-id="1604c-157">Finding the Fully Qualified Domain Name of A System</span></span>  
 <span data-ttu-id="1604c-158">システムの完全修飾ドメイン名を検索するには、そのシステムの Windows コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="1604c-158">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="1604c-159">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="1604c-159">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="1604c-160">完全修飾ドメイン名を作成するには、次に示すように、 *<host_name>* と *<Primary_Dns_Suffix>* の値を連結します:</span><span class="sxs-lookup"><span data-stu-id="1604c-160">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="1604c-161">_<host_name>_ **.**</span><span class="sxs-lookup"><span data-stu-id="1604c-161">_<host_name>_ **.**</span></span> <span data-ttu-id="1604c-162">_<Primary_Dns_Suffix>_</span><span class="sxs-lookup"><span data-stu-id="1604c-162">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="1604c-163">たとえば、次のような IP 構成があるとします。</span><span class="sxs-lookup"><span data-stu-id="1604c-163">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="1604c-164">この場合、完全修飾ドメイン名は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1604c-164">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
> [!NOTE]  
>  <span data-ttu-id="1604c-165">完全修飾ドメイン名に関する情報が必要な場合は、システム管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="1604c-165">If you need more information about a fully qualified domain name, see your system administrator.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1604c-166">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1604c-166">Related Tasks</span></span>  
 <span data-ttu-id="1604c-167">**データベース ミラーリング エンドポイントを構成するには**</span><span class="sxs-lookup"><span data-stu-id="1604c-167">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="1604c-168">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-168">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="1604c-169">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-169">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="1604c-170">データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-170">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="1604c-171">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="1604c-172">データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-172">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="1604c-173">サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-173">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="1604c-174">SQL Server&#41;削除された AlwaysOn 可用性グループ構成 &#40;のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1604c-174">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
 <span data-ttu-id="1604c-175">**データベース ミラーリング エンドポイントに関する情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="1604c-175">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="1604c-176">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-176">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="1604c-177">**可用性レプリカを追加するには**</span><span class="sxs-lookup"><span data-stu-id="1604c-177">**To add an availability replica**</span></span>  
  
-   [<span data-ttu-id="1604c-178">可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="1604c-179">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-179">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="1604c-180">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="1604c-180">Related Content</span></span>  
  
-   [<span data-ttu-id="1604c-181">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="1604c-181">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="1604c-182">参照</span><span class="sxs-lookup"><span data-stu-id="1604c-182">See Also</span></span>  
 <span data-ttu-id="1604c-183">[可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1604c-183">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1604c-184">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1604c-184">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="1604c-185">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1604c-185">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
