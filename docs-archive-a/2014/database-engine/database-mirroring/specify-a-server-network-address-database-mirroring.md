---
title: サーバー ネットワーク アドレスの指定 (データベース ミラーリング) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- server network addresses [SQL Server]
ms.assetid: a64d4b6b-9016-4f1e-a310-b1df181dd0c6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c7db7ee6d321229205248059ce09a86f1da101f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641843"
---
# <a name="specify-a-server-network-address-database-mirroring"></a><span data-ttu-id="755b2-102">サーバー ネットワーク アドレスの指定 (データベース ミラーリング)</span><span class="sxs-lookup"><span data-stu-id="755b2-102">Specify a Server Network Address (Database Mirroring)</span></span>
  <span data-ttu-id="755b2-103">データベース ミラーリング セッションを設定するには、サーバー インスタンスごとにサーバー ネットワーク アドレスが必要です。</span><span class="sxs-lookup"><span data-stu-id="755b2-103">Setting up a database mirroring session requires a server network address for each of the server instances.</span></span> <span data-ttu-id="755b2-104">サーバー インスタンスのサーバー ネットワーク アドレスは、システム アドレス、およびインスタンスがリッスンしているポート番号を指定することにより、明確にインスタンスを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="755b2-104">The server network address of a server instance must unambiguously identify the instance by providing a system address and the number of the port on which the instance is listening.</span></span>  
  
 <span data-ttu-id="755b2-105">サーバー ネットワーク アドレスでポートを指定するには、サーバー インスタンスにデータベース ミラーリング エンドポイントが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="755b2-105">Before you can specify a port in a server network address, the database mirroring endpoint must exist on the server instance.</span></span> <span data-ttu-id="755b2-106">詳細については、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="755b2-106">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
  
  
##  <a name="syntax-for-a-server-network-address"></a><a name="Syntax"></a> <span data-ttu-id="755b2-107">サーバー ネットワーク アドレスの構文</span><span class="sxs-lookup"><span data-stu-id="755b2-107">Syntax for a Server Network Address</span></span>  
 <span data-ttu-id="755b2-108">サーバー ネットワーク アドレスの構文は、次のような形式になります。</span><span class="sxs-lookup"><span data-stu-id="755b2-108">The syntax for a server network address is of the form:</span></span>  
  
 <span data-ttu-id="755b2-109">TCP:<strong>//</strong> *\<system-address>* <strong> :<strong>*\<port>*</span><span class="sxs-lookup"><span data-stu-id="755b2-109">TCP<strong>://</strong>*\<system-address>*<strong>:<strong>*\<port>*</span></span> 
  
 <span data-ttu-id="755b2-110">where</span><span class="sxs-lookup"><span data-stu-id="755b2-110">where</span></span>  
  
-   <span data-ttu-id="755b2-111">*\<system-address>* は、ミラーリング先のコンピューター システムを明確に識別する文字列です。</span><span class="sxs-lookup"><span data-stu-id="755b2-111">*\<system-address>* is a string that unambiguously identifies the destination computer system.</span></span> <span data-ttu-id="755b2-112">通常、サーバー アドレスは、システム名 (システムが同じドメインに存在する場合)、完全修飾ドメイン名、または IP アドレスになります。</span><span class="sxs-lookup"><span data-stu-id="755b2-112">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="755b2-113">システムが同じドメイン内にある場合、 `SYSTEM46`などのコンピューター システムの名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="755b2-113">If the systems are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="755b2-114">IP アドレスを使用するには、それが環境内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="755b2-114">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="755b2-115">IP アドレスが静的である場合にのみ、IP アドレスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="755b2-115">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="755b2-116">IP アドレスには、IP Version 4 (IPv4) または IP Version 6 (IPv6) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="755b2-116">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="755b2-117">IPv6 アドレスは、 **[** _<IPv6_address>_ **]** のように、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="755b2-117">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="755b2-118">システムの IP アドレスを参照するには、Windows コマンド プロンプトで、 **ipconfig** コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="755b2-118">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="755b2-119">完全修飾ドメイン名は動作が保証されています。</span><span class="sxs-lookup"><span data-stu-id="755b2-119">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="755b2-120">これは、場所によって異なる形式を持つローカルに定義されたアドレス文字列です。</span><span class="sxs-lookup"><span data-stu-id="755b2-120">This is a locally defined address string that different forms in different places.</span></span> <span data-ttu-id="755b2-121">常にではありませんが多くの場合、完全修飾ドメイン名は、次の形式のようにコンピューター名、およびピリオド区切りの一連のドメイン セグメントを含む複合名になります。</span><span class="sxs-lookup"><span data-stu-id="755b2-121">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="755b2-122">_computer_name_ **.**</span><span class="sxs-lookup"><span data-stu-id="755b2-122">_computer_name_ **.**</span></span> <span data-ttu-id="755b2-123">_domain_segment_[... **.** _domain_segment_]</span><span class="sxs-lookup"><span data-stu-id="755b2-123">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="755b2-124">*computer_name*はサーバー インスタンスを実行しているコンピューターのネットワーク名、および *domain_segment*[... **.** _domain_segment_] はサーバーのその他のドメイン情報です。たとえば、 `localinfo.corp.Adventure-Works.com`のようになります。</span><span class="sxs-lookup"><span data-stu-id="755b2-124">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="755b2-125">ドメイン セグメントの内容と数は、会社内または組織内で決定されます。</span><span class="sxs-lookup"><span data-stu-id="755b2-125">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="755b2-126">使用しているサーバーの完全修飾ドメイン名がわからない場合は、システム管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="755b2-126">If you do not know the fully qualified domain name for your server, see your system administrator.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="755b2-127">完全修飾ドメイン名の検索方法の詳細については、このトピックの「完全修飾ドメイン名の検索」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="755b2-127">For information about how to find a fully qualified domain name, see "Finding the Fully Qualified Domain Name," later in this topic.</span></span>  
  
-   <span data-ttu-id="755b2-128">*\<port>* は、パートナー サーバー インスタンスのミラーリング エンドポイントによって使用されるポート番号です。</span><span class="sxs-lookup"><span data-stu-id="755b2-128">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="755b2-129">エンドポイントの指定の詳細については、「 [Windows 認証でのデータベース ミラーリング エンドポイントを作成する &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="755b2-129">For information about specifying an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
     <span data-ttu-id="755b2-130">データベース ミラーリング エンドポイントは、コンピューター システム上の使用可能な任意のポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="755b2-130">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="755b2-131">コンピューター システム上の各ポート番号は 1 つのエンドポイントだけに関連付けられている必要があります。また、各エンドポイントは 1 つのサーバー インスタンスに関連付けられています。そのため、1 台のサーバー上に複数のサーバー インスタンスがある場合、各サーバー インスタンスは、ポートが異なる別のエンドポイントでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="755b2-131">Each port number on a computer system must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="755b2-132">したがって、データベース ミラーリング セッションを設定するときにサーバー ネットワーク アドレスで指定するポートにより、必ず、エンドポイントがそのポートに関連付けられているサーバー インスタンスにセッションがリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="755b2-132">Therefore, the port you specify in the server network address when you set up a database mirroring session will always direct the session to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="755b2-133">サーバー インスタンスのサーバー ネットワーク アドレスでは、そのミラーリング エンドポイントに関連付けられているポートの番号によってのみ、そのインスタンスがコンピューター上のその他のインスタンスと区別されます。</span><span class="sxs-lookup"><span data-stu-id="755b2-133">In the server network address of a server instance, only the number of the port associated with its mirroring endpoint distinguishes that instance from any other instances on the computer.</span></span> <span data-ttu-id="755b2-134">次の図は、1 台のコンピューターにある 2 つのサーバー インスタンスのサーバー ネットワーク アドレスを示しています。</span><span class="sxs-lookup"><span data-stu-id="755b2-134">The following figure illustrates the server network addresses of two server instances on a single computer.</span></span> <span data-ttu-id="755b2-135">既定のインスタンスではポート `7022` が使用され、名前付きインスタンスではポート `7033`が使用されます。</span><span class="sxs-lookup"><span data-stu-id="755b2-135">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="755b2-136">これら 2 つのサーバー インスタンスのサーバー ネットワーク アドレスは、それぞれ `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` と `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`です。</span><span class="sxs-lookup"><span data-stu-id="755b2-136">The server network address for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="755b2-137">アドレスにサーバー インスタンス名が含まれていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="755b2-137">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="755b2-138">![既定のインスタンスのサーバー ネットワーク アドレス](../media/dbm-2-instances-ports-1-system.gif "既定のインスタンスのサーバー ネットワーク アドレス")</span><span class="sxs-lookup"><span data-stu-id="755b2-138">![Server network addresses of a default instance](../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="755b2-139">サーバー インスタンスのデータベース ミラーリング エンドポイントに現在関連付けられているポートを識別するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="755b2-139">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT type_desc, port FROM sys.tcp_endpoints  
    ```  
  
     <span data-ttu-id="755b2-140">**type_desc** の値が "DATABASE_MIRRORING" の行を検索し、対応するポート番号を使用します。</span><span class="sxs-lookup"><span data-stu-id="755b2-140">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="755b2-141">例</span><span class="sxs-lookup"><span data-stu-id="755b2-141">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="755b2-142">A.</span><span class="sxs-lookup"><span data-stu-id="755b2-142">A.</span></span> <span data-ttu-id="755b2-143">システム名を使用する</span><span class="sxs-lookup"><span data-stu-id="755b2-143">Using a system name</span></span>  
 <span data-ttu-id="755b2-144">次のサーバー ネットワーク アドレスでは、システム名 `SYSTEM46`およびポート `7022`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="755b2-144">The following server network address specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://SYSTEM46:7022';  
```  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="755b2-145">B.</span><span class="sxs-lookup"><span data-stu-id="755b2-145">B.</span></span> <span data-ttu-id="755b2-146">完全修飾ドメイン名を使用する</span><span class="sxs-lookup"><span data-stu-id="755b2-146">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="755b2-147">次のサーバー ネットワーク アドレスでは、完全修飾ドメイン名 `DBSERVER8.manufacturing.Adventure-Works.com`およびポート `7024`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="755b2-147">The following server network address specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://DBSERVER8.manufacturing.Adventure-Works.com:7024';  
```  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="755b2-148">C.</span><span class="sxs-lookup"><span data-stu-id="755b2-148">C.</span></span> <span data-ttu-id="755b2-149">IPv4 を使用する</span><span class="sxs-lookup"><span data-stu-id="755b2-149">Using IPv4</span></span>  
 <span data-ttu-id="755b2-150">次のサーバー ネットワーク アドレスでは、IPv4 アドレス `10.193.9.134`およびポート `7023`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="755b2-150">The following server network address specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://10.193.9.134:7023';  
```  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="755b2-151">D.</span><span class="sxs-lookup"><span data-stu-id="755b2-151">D.</span></span> <span data-ttu-id="755b2-152">IPv6 を使用する</span><span class="sxs-lookup"><span data-stu-id="755b2-152">Using IPv6</span></span>  
 <span data-ttu-id="755b2-153">次のサーバー ネットワーク アドレスでは、IPv6 アドレス `2001:4898:23:1002:20f:1fff:feff:b3a3`およびポート `7022`を指定しています。</span><span class="sxs-lookup"><span data-stu-id="755b2-153">The following server network address contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022';  
```  
  
## <a name="finding-the-fully-qualified-domain-name"></a><span data-ttu-id="755b2-154">完全修飾ドメイン名の検索</span><span class="sxs-lookup"><span data-stu-id="755b2-154">Finding the Fully Qualified Domain Name</span></span>  
 <span data-ttu-id="755b2-155">システムの完全修飾ドメイン名を検索するには、そのシステムの Windows コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="755b2-155">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="755b2-156">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="755b2-156">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="755b2-157">完全修飾ドメイン名を作成するには、次に示すように、 *<host_name>* と *<Primary_Dns_Suffix>* の値を連結します:</span><span class="sxs-lookup"><span data-stu-id="755b2-157">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="755b2-158">_<host_name>_ **.**</span><span class="sxs-lookup"><span data-stu-id="755b2-158">_<host_name>_ **.**</span></span> <span data-ttu-id="755b2-159">_<Primary_Dns_Suffix>_</span><span class="sxs-lookup"><span data-stu-id="755b2-159">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="755b2-160">たとえば、次のような IP 構成があるとします。</span><span class="sxs-lookup"><span data-stu-id="755b2-160">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="755b2-161">この場合、完全修飾ドメイン名は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="755b2-161">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="755b2-162">使用例</span><span class="sxs-lookup"><span data-stu-id="755b2-162">Examples</span></span>  
 <span data-ttu-id="755b2-163">次の例では、別のドメイン内の `REMOTESYSTEM3` という名前のコンピューター システム上にあるサーバー インスタンスのサーバー ネットワーク アドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="755b2-163">The following example shows the server network address for a server instance on a computer system named `REMOTESYSTEM3` in another domain.</span></span> <span data-ttu-id="755b2-164">ドメイン情報は `NORTHWEST.ADVENTURE-WORKS.COM`であり、データベース ミラーリング エンドポイントのポートは `7025`です。</span><span class="sxs-lookup"><span data-stu-id="755b2-164">The domain information is `NORTHWEST.ADVENTURE-WORKS.COM`, and the port of the database mirroring endpoint is `7025`.</span></span> <span data-ttu-id="755b2-165">これらのコンポーネントから、サーバー ネットワーク アドレスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="755b2-165">Given these example components, the server network address is.</span></span>  
  
 `TCP://REMOTESYSTEM3.NORTHWEST.ADVENTURE-WORKS.COM:7025`  
  
 <span data-ttu-id="755b2-166">次の例では、 `DBSERVER1`という名前のコンピューター システム上にあるサーバー インスタンスのサーバー ネットワーク アドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="755b2-166">The following example shows the server network address for a server instance on a computer system named `DBSERVER1`.</span></span> <span data-ttu-id="755b2-167">このシステムはローカル ドメイン内にあり、システム名によって明確に識別されています。</span><span class="sxs-lookup"><span data-stu-id="755b2-167">This system is in the local domain and is unambiguously identified by its system name.</span></span> <span data-ttu-id="755b2-168">データベース ミラーリング エンドポイントのポートは `7022`です。</span><span class="sxs-lookup"><span data-stu-id="755b2-168">The port of the database mirroring endpoint is `7022`.</span></span>  
  
 `TCP://DBSERVER1:7022`  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="755b2-169">関連タスク</span><span class="sxs-lookup"><span data-stu-id="755b2-169">Related Tasks</span></span>  
  
-   [<span data-ttu-id="755b2-170">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="755b2-170">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="755b2-171">参照</span><span class="sxs-lookup"><span data-stu-id="755b2-171">See Also</span></span>  
 <span data-ttu-id="755b2-172">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="755b2-172">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="755b2-173">データベース ミラーリング エンドポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="755b2-173">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
