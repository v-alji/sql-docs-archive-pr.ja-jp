---
title: アセンブリのデザイン |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- designing assemblies [SQL Server]
- assemblies [CLR integration], designing
ms.assetid: 9c07f706-6508-41aa-a4d7-56ce354f9061
author: rothja
ms.author: jroth
ms.openlocfilehash: 785ab80a529140a52ec18ef96ccaaeafd03698cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720073"
---
# <a name="designing-assemblies"></a><span data-ttu-id="6643b-102">アセンブリのデザイン</span><span class="sxs-lookup"><span data-stu-id="6643b-102">Designing Assemblies</span></span>
  <span data-ttu-id="6643b-103">このトピックでは、アセンブリをデザインするときに考慮する必要がある次の項目について説明します。</span><span class="sxs-lookup"><span data-stu-id="6643b-103">This topic describes the following factors you should consider when you design assemblies:</span></span>  
  
-   <span data-ttu-id="6643b-104">アセンブリのパッケージ化</span><span class="sxs-lookup"><span data-stu-id="6643b-104">Packaging assemblies</span></span>  
  
-   <span data-ttu-id="6643b-105">アセンブリセキュリティの管理</span><span class="sxs-lookup"><span data-stu-id="6643b-105">Managing assembly security</span></span>  
  
-   <span data-ttu-id="6643b-106">アセンブリに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="6643b-106">Restrictions on assemblies</span></span>  
  
## <a name="packaging-assemblies"></a><span data-ttu-id="6643b-107">アセンブリのパッケージ化</span><span class="sxs-lookup"><span data-stu-id="6643b-107">Packaging Assemblies</span></span>  
 <span data-ttu-id="6643b-108">アセンブリのクラスやメソッドには、複数の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ルーチンまたは型の機能を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6643b-108">An assembly can contain functionality for more than one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] routine or type in its classes and methods.</span></span> <span data-ttu-id="6643b-109">ほとんどの場合、関連する機能を実行するルーチンの機能を 1 つのアセンブリ内にパッケージ化することが適切です。これは特に、このようなルーチンで、メソッドが相互に呼び出しを行うクラスが共有される場合に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="6643b-109">Most of the time, it makes sense to package the functionality of routines that perform related functions within the same assembly, especially if these routines share classes whose methods call one another.</span></span> <span data-ttu-id="6643b-110">たとえば、CLR (共通言語ランタイム) トリガーと CLR ストアド プロシージャのデータ エントリ管理タスクを実行するクラスを 1 つのアセンブリにパッケージ化することがあります。</span><span class="sxs-lookup"><span data-stu-id="6643b-110">For example, classes that perform data entry management tasks for common language runtime (CLR) triggers and CLR stored procedures can be packaged in the same assembly.</span></span> <span data-ttu-id="6643b-111">これは、これらのクラスのメソッドは、関連性の低いタスクを実行するクラスのメソッドよりも相互に呼び出しを行う可能性が高いためです。</span><span class="sxs-lookup"><span data-stu-id="6643b-111">This is because the methods for these classes are more likely to call each other than those of less related tasks.</span></span>  
  
 <span data-ttu-id="6643b-112">コードをアセンブリにパッケージ化しているときは、次のことを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6643b-112">When you are packaging code into assembly, you should consider the following:</span></span>  
  
-   <span data-ttu-id="6643b-113">CLR ユーザー定義関数に依存する CLR ユーザー定義型とインデックスにより、アセンブリに依存する持続データがデータベースに格納される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6643b-113">CLR user-defined types and indexes that depend on CLR user-defined functions can cause persisted data to be in the database that depends on the assembly.</span></span> <span data-ttu-id="6643b-114">多くの場合、アセンブリに依存する持続データがデータベースに存在すると、アセンブリのコードを変更することが複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="6643b-114">Modifying the code of an assembly is frequently more complex when there is persisted data that depends on the assembly in the database.</span></span> <span data-ttu-id="6643b-115">そのため、一般に、持続データの依存関係があるコード (ユーザー定義関数を使用するユーザー定義型やインデックスなど) とそのような持続データの依存関係がないコードは切り離した方が適切です。</span><span class="sxs-lookup"><span data-stu-id="6643b-115">Therefore, it is generally better to separate code on which persisted data dependencies rely (such as user-defined types and indexes using user-defined functions) from code that does not have such persisted data dependencies.</span></span> <span data-ttu-id="6643b-116">詳細については、「[アセンブリの実装](assemblies-implementing.md)」および「 [transact-sql&#41;&#40;の ALTER ASSEMBLY ](/sql/t-sql/statements/alter-assembly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6643b-116">For more information, see [Implementing Assemblies](assemblies-implementing.md) and [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
-   <span data-ttu-id="6643b-117">マネージド コードの一部分で上位の権限が必要な場合、そのコードは、上位の権限を必要としないコードとは別のアセンブリにパッケージ化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6643b-117">If a piece of managed code requires higher permission, it is better to separate that code into a separate assembly from code that does not require higher permission.</span></span>  
  
## <a name="managing-assembly-security"></a><span data-ttu-id="6643b-118">アセンブリのセキュリティ管理</span><span class="sxs-lookup"><span data-stu-id="6643b-118">Managing Assembly Security</span></span>  
 <span data-ttu-id="6643b-119">アセンブリでマネージド コードが実行されるときに、.NET コード アクセス セキュリティによって保護されているリソースにアセンブリがアクセスできる程度を制御できます。</span><span class="sxs-lookup"><span data-stu-id="6643b-119">You can control how much an assembly can access resources protected by .NET Code Access Security when it runs managed code.</span></span> <span data-ttu-id="6643b-120">この制御は、アセンブリを作成または変更するときに、SAFE、EXTERNAL_ACCESS、または UNSAFE の 3 つの中のいずれかの権限セットを指定して行います。</span><span class="sxs-lookup"><span data-stu-id="6643b-120">You do this by specifying one of three permission sets when you create or modify an assembly: SAFE, EXTERNAL_ACCESS, or UNSAFE.</span></span>  
  
### <a name="safe"></a><span data-ttu-id="6643b-121">SAFE</span><span class="sxs-lookup"><span data-stu-id="6643b-121">SAFE</span></span>  
 <span data-ttu-id="6643b-122">SAFE は既定の権限セットであり、最も強い制限です。</span><span class="sxs-lookup"><span data-stu-id="6643b-122">SAFE is the default permission set and it is the most restrictive.</span></span> <span data-ttu-id="6643b-123">SAFE 権限を指定したアセンブリによって実行されるコードでは、ファイル、ネットワーク、環境変数、またはレジストリなどの外部システム リソースにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="6643b-123">Code run by an assembly with SAFE permissions cannot access external system resources such as files, the network, environment variables, or the registry.</span></span> <span data-ttu-id="6643b-124">SAFE コードでは、ローカルの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースのデータにアクセスしたり、ローカル データベースの外部にあるリソースへのアクセスを必要としない計算やビジネス ロジックを実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="6643b-124">SAFE code can access data from the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases or perform computations and business logic that do not involve accessing resources outside the local databases.</span></span>  
  
 <span data-ttu-id="6643b-125">ほとんどのアセンブリでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の外部にあるリソースにアクセスしなくても計算やデータ管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="6643b-125">Most assemblies perform computation and data management tasks without having to access resources outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6643b-126">そのため、アセンブリの権限セットとして SAFE を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6643b-126">Therefore, we recommend SAFE as the assembly permission set.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="6643b-127">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="6643b-127">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="6643b-128">EXTERNAL_ACCESS を使用すると、アセンブリでファイル、ネットワーク、Web サービス、環境変数、およびレジストリなどの特定の外部システム リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6643b-128">EXTERNAL_ACCESS allows for assemblies to access certain external system resources such as files, networks, Web services, environmental variables, and the registry.</span></span> <span data-ttu-id="6643b-129">EXTERNAL ACCESS 権限を持つ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインだけが EXTERNAL_ACCESS アセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6643b-129">Only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins with EXTERNAL ACCESS permissions can create EXTERNAL_ACCESS assemblies.</span></span>  
  
 <span data-ttu-id="6643b-130">SAFE アセンブリおよび EXTERNAL_ACCESS アセンブリには検証可能なタイプ セーフのコードしか格納できません。</span><span class="sxs-lookup"><span data-stu-id="6643b-130">SAFE and EXTERNAL_ACCESS assemblies can contain only code that is verifiably type-safe.</span></span> <span data-ttu-id="6643b-131">つまり、これらのアセンブリでクラスにアクセスするには、型定義で有効な整形式のエントリ ポイントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6643b-131">This means that these assemblies can only access classes through well-defined entry points that are valid for the type definition.</span></span> <span data-ttu-id="6643b-132">そのため、これらのアセンブリでは、コードによって所有されていないメモリ バッファーに自由にアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6643b-132">Therefore, they cannot arbitrarily access memory buffers not owned by the code.</span></span> <span data-ttu-id="6643b-133">また、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロセスの堅牢性に悪影響を与える可能性がある操作を実行することもできません。</span><span class="sxs-lookup"><span data-stu-id="6643b-133">Additionally, they cannot perform operations that might have an adverse effect on the robustness of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="6643b-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="6643b-134">UNSAFE</span></span>  
 <span data-ttu-id="6643b-135">UNSAFE を使用すると、アセンブリでは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の内外を問わずどちらのリソースにも無制限にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6643b-135">UNSAFE gives assemblies unrestricted access to resources, both within and outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6643b-136">UNSAFE アセンブリの内部で実行されているコードで、アンマネージ コードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6643b-136">Code that is running from within an UNSAFE assembly can call unmanaged code.</span></span>  
  
 <span data-ttu-id="6643b-137">また、UNSAFE を指定すると、CLR 検証機能によってタイプ セーフではないと見なされる操作をアセンブリのコードで実行できます。</span><span class="sxs-lookup"><span data-stu-id="6643b-137">Also, specifying UNSAFE allows for the code in the assembly to perform operations that are considered type-unsafe by the CLR verifier.</span></span> <span data-ttu-id="6643b-138">これらの操作により、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロセス空間のメモリ バッファーに制御なしにアクセスされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6643b-138">These operations can potentially access memory buffers in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process space in an uncontrolled manner.</span></span> <span data-ttu-id="6643b-139">UNSAFE アセンブリでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または共通言語ランタイムのいずれかのセキュリティ システムが妨害されるおそれもあります。</span><span class="sxs-lookup"><span data-stu-id="6643b-139">UNSAFE assemblies can also potentially subvert the security system of either [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the common language runtime.</span></span> <span data-ttu-id="6643b-140">UNSAFE 権限は、経験豊かな開発者や管理者によって信頼性の高いアセンブリにのみ与えるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6643b-140">UNSAFE permissions should be granted only to highly trusted assemblies by experienced developers or administrators.</span></span> <span data-ttu-id="6643b-141">UNSAFE アセンブリを作成できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="6643b-141">Only members of the **sysadmin** fixed server role can create UNSAFE assemblies.</span></span>  
  
## <a name="restrictions-on-assemblies"></a><span data-ttu-id="6643b-142">アセンブリに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="6643b-142">Restrictions on Assemblies</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6643b-143">では、アセンブリのマネージド コードに特定の制限を設けて、これらのコードを信頼性および拡張性の高い方法で実行できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="6643b-143">puts certain restrictions on managed code in assemblies to make sure that they can run in a reliable and scalable manner.</span></span> <span data-ttu-id="6643b-144">つまり、SAFE アセンブリと EXTERNAL_ACCESS アセンブリでは、サーバーの堅牢性を侵害する可能性のある操作を実行できません。</span><span class="sxs-lookup"><span data-stu-id="6643b-144">This means that certain operations that can compromise the robustness of the server are not permitted in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
### <a name="disallowed-custom-attributes"></a><span data-ttu-id="6643b-145">禁止されているカスタム属性</span><span class="sxs-lookup"><span data-stu-id="6643b-145">Disallowed Custom Attributes</span></span>  
 <span data-ttu-id="6643b-146">アセンブリには次のカスタム属性で注釈を付けることができません。</span><span class="sxs-lookup"><span data-stu-id="6643b-146">Assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.ContextStaticAttribute  
System.MTAThreadAttribute  
System.Runtime.CompilerServices.MethodImplAttribute  
System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
System.Runtime.Remoting.Contexts.ContextAttribute  
System.Runtime.Remoting.Contexts.SynchronizationAttribute  
System.Runtime.InteropServices.DllImportAttribute   
System.Security.Permissions.CodeAccessSecurityAttribute  
System.STAThreadAttribute  
System.ThreadStaticAttribute  
```  
  
 <span data-ttu-id="6643b-147">また、SAFE アセンブリと EXTERNAL_ACCESS アセンブリには、次のカスタム属性で注釈を付けることができません。</span><span class="sxs-lookup"><span data-stu-id="6643b-147">Additionally, SAFE and EXTERNAL_ACCESS assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.Security.SuppressUnmanagedCodeSecurityAttribute  
System.Security.UnverifiableCodeAttribute  
```  
  
### <a name="disallowed-net-framework-apis"></a><span data-ttu-id="6643b-148">禁止されている .NET Framework API</span><span class="sxs-lookup"><span data-stu-id="6643b-148">Disallowed .NET Framework APIs</span></span>  
 <span data-ttu-id="6643b-149">許可されていない [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] **hostprotectionattributes**のいずれかで注釈が付けられている API は、SAFE および EXTERNAL_ACCESS アセンブリからは呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="6643b-149">Any [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] API that is annotated with one of the disallowed **HostProtectionAttributes** cannot be called from SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
```  
eSelfAffectingProcessMgmt  
eSelfAffectingThreading  
eSynchronization  
eSharedState   
eExternalProcessMgmt  
eExternalThreading  
eSecurityInfrastructure  
eMayLeakOnAbort  
eUI  
```  
  
### <a name="supported-net-framework-assemblies"></a><span data-ttu-id="6643b-150">サポートされている .NET Framework アセンブリ</span><span class="sxs-lookup"><span data-stu-id="6643b-150">Supported .NET Framework Assemblies</span></span>  
 <span data-ttu-id="6643b-151">カスタム アセンブリで参照されているアセンブリは、CREATE ASSEMBLY を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6643b-151">Any assembly that is referenced by your custom assembly must be loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using CREATE ASSEMBLY.</span></span> <span data-ttu-id="6643b-152">次の [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アセンブリは既に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込まれているため、CREATE ASSEMBLY を使用しなくてもカスタム アセンブリで参照できます。</span><span class="sxs-lookup"><span data-stu-id="6643b-152">The following [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assemblies are already loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and, therefore, can be referenced by custom assemblies without having to use CREATE ASSEMBLY.</span></span>  
  
```  
custommarshallers.dll  
Microsoft.visualbasic.dll  
Microsoft.visualc.dll  
mscorlib.dll  
system.data.dll  
System.Data.SqlXml.dll  
system.dll  
system.security.dll  
system.web.services.dll  
system.xml.dll  
System.Transactions  
System.Data.OracleClient  
System.Configuration  
```  
  
## <a name="see-also"></a><span data-ttu-id="6643b-153">参照</span><span class="sxs-lookup"><span data-stu-id="6643b-153">See Also</span></span>  
 <span data-ttu-id="6643b-154">[アセンブリ &#40;データベースエンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="6643b-154">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="6643b-155">CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6643b-155">CLR Integration Security</span></span>](security/clr-integration-security.md)  
  
  
