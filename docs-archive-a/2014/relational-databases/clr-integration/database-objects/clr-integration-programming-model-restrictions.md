---
title: CLR 統合プログラミングモデルの制限 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a32e1460ad9c49061b39b1bdc419c7cd2f1342
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631091"
---
# <a name="clr-integration-programming-model-restrictions"></a><span data-ttu-id="52474-102">CLR 統合プログラミング モデルの制限事項</span><span class="sxs-lookup"><span data-stu-id="52474-102">CLR Integration Programming Model Restrictions</span></span>
  <span data-ttu-id="52474-103">マネージストアドプロシージャまたはその他のマネージデータベースオブジェクトを構築するときに、によって実行される特定のコードチェックでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マネージコードアセンブリが最初にデータベースに登録されたとき、ステートメントを使用して、実行時にもチェックが実行され `CREATE ASSEMBLY` ます。</span><span class="sxs-lookup"><span data-stu-id="52474-103">When you are building a managed stored procedure or other managed database object, there are certain code checks performed by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs checks on the managed code assembly when it is first registered in the database, using the `CREATE ASSEMBLY` statement, and also at runtime.</span></span> <span data-ttu-id="52474-104">マネージド コードが実行時にもチェックされるのは、実行時に決して到達しないコード パスがアセンブリに含まれる場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="52474-104">The managed code is also checked at runtime because in an assembly there may be code paths that may never actually be reached at runtime.</span></span>  <span data-ttu-id="52474-105">このチェックにより、サード パーティ アセンブリを柔軟に登録できます。特に、クライアント環境での実行を目的に作成され、ホストされた CLR では実行されない "安全でない" コードを含むアセンブリをブロックしないようにすることができるため、サード パーティ アセンブリに柔軟に対応できます。</span><span class="sxs-lookup"><span data-stu-id="52474-105">This provides flexibility for registering third party assemblies, especially, so that an assembly wouldn't be blocked where there is 'unsafe' code designed to run in a client environment but would never be executed in the hosted CLR.</span></span> <span data-ttu-id="52474-106">マネージコードが満たす必要のある要件は、アセンブリが、、またはのいずれかとして登録されているかどうかによって異なり、以下に示すようになり `SAFE` `EXTERNAL_ACCESS` `UNSAFE` `SAFE` ます。</span><span class="sxs-lookup"><span data-stu-id="52474-106">The requirements that the managed code must meet depend on whether the assembly is registered as `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`, `SAFE` being the strictest, and are listed below.</span></span>  
  
 <span data-ttu-id="52474-107">マネージド コード アセンブリには、制限事項に加えてコード セキュリティ権限も付与されます。</span><span class="sxs-lookup"><span data-stu-id="52474-107">In addition to restrictions being placed on the managed code assemblies, there are also code security permissions that are granted.</span></span> <span data-ttu-id="52474-108">共通言語ランタイム (CLR) では、マネージド コードに対してコード アクセス セキュリティ (CAS) というセキュリティ モデルがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="52474-108">The common language runtime (CLR) supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="52474-109">このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。</span><span class="sxs-lookup"><span data-stu-id="52474-109">In this model, permissions are granted to assemblies based on the identity of the code.</span></span> <span data-ttu-id="52474-110">`SAFE`、`EXTERNAL_ACCESS`、および `UNSAFE` の各アセンブリには、それぞれ異なる CAS 権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="52474-110">`SAFE`, `EXTERNAL_ACCESS`, and `UNSAFE` assemblies have different CAS permissions.</span></span> <span data-ttu-id="52474-111">詳細については、「 [CLR 統合コードアクセスセキュリティ](../security/clr-integration-code-access-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52474-111">For more information, see [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="create-assembly-checks"></a><span data-ttu-id="52474-112">CREATE ASSEMBLY チェック</span><span class="sxs-lookup"><span data-stu-id="52474-112">CREATE ASSEMBLY Checks</span></span>  
 <span data-ttu-id="52474-113">`CREATE ASSEMBLY` ステートメントを実行する際には、セキュリティ レベルごとに次のチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="52474-113">When the `CREATE ASSEMBLY` statement is run, the following checks are performed for each security level.</span></span>  <span data-ttu-id="52474-114">いずれかのチェックが失敗した場合、`CREATE ASSEMBLY` が失敗し、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="52474-114">If any check fails, `CREATE ASSEMBLY` will fail with an error message.</span></span>  
  
### <a name="global-any-security-level"></a><span data-ttu-id="52474-115">グローバル (すべてのセキュリティ レベル)</span><span class="sxs-lookup"><span data-stu-id="52474-115">Global (any security level)</span></span>  
 <span data-ttu-id="52474-116">参照されるすべてのアセンブリは、次の条件のうち 1 つ以上を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="52474-116">All referenced assemblies must meet one or more of the following criteria:</span></span>  
  
-   <span data-ttu-id="52474-117">既にデータベースに登録されていること。</span><span class="sxs-lookup"><span data-stu-id="52474-117">The assembly is already registered in the database.</span></span>  
  
-   <span data-ttu-id="52474-118">サポートされているアセンブリの 1 つであること。</span><span class="sxs-lookup"><span data-stu-id="52474-118">The assembly is one of the supported assemblies.</span></span> <span data-ttu-id="52474-119">詳細については、「[サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52474-119">For more information, see [Supported .NET Framework Libraries](supported-net-framework-libraries.md).</span></span>  
  
-   <span data-ttu-id="52474-120">を使用し、参照されている `CREATE ASSEMBLY FROM` \* \<location> \*すべてのアセンブリとその依存関係をで使用できるようにし *\<location>* ます。</span><span class="sxs-lookup"><span data-stu-id="52474-120">You are using `CREATE ASSEMBLY FROM`*\<location>,* and all the referenced assemblies and their dependencies are available in *\<location>*.</span></span>  
  
-   <span data-ttu-id="52474-121">を使用していて、 `CREATE ASSEMBLY FROM` すべての参照が空白で区切られたバイトを使用\* \<bytes ...> して\*指定されている。</span><span class="sxs-lookup"><span data-stu-id="52474-121">You are using `CREATE ASSEMBLY FROM`*\<bytes ...>,* and all the references are specified via space separated bytes.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="52474-122">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="52474-122">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="52474-123">すべての `EXTERNAL_ACCESS` アセンブリは、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="52474-123">All `EXTERNAL_ACCESS` assemblies must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="52474-124">静的フィールドが情報の格納に使用されていないこと。</span><span class="sxs-lookup"><span data-stu-id="52474-124">Static fields are not used to store information.</span></span> <span data-ttu-id="52474-125">読み取り専用の静的フィールドは許可されます。</span><span class="sxs-lookup"><span data-stu-id="52474-125">Read-only static fields are allowed.</span></span>  
  
-   <span data-ttu-id="52474-126">PEVerify テストにパスしていること。</span><span class="sxs-lookup"><span data-stu-id="52474-126">PEVerify test is passed.</span></span> <span data-ttu-id="52474-127">.NET Framework SDK には、MSIL コードと関連メタデータがタイプ セーフの要件を満たしていることをチェックするための PEVerify ツール (peverify.exe) が付属しています。</span><span class="sxs-lookup"><span data-stu-id="52474-127">The PEVerify tool (peverify.exe), which checks that the MSIL code and associated metadata meet type safety requirements, is provided with the .NET Framework SDK.</span></span>  
  
-   <span data-ttu-id="52474-128">`SynchronizationAttribute` クラスなどによる同期が使用されていないこと。</span><span class="sxs-lookup"><span data-stu-id="52474-128">Synchronization, for example with the `SynchronizationAttribute` class, is not used.</span></span>  
  
-   <span data-ttu-id="52474-129">ファイナライザー メソッドが使用されていないこと。</span><span class="sxs-lookup"><span data-stu-id="52474-129">Finalizer methods are not used.</span></span>  
  
 <span data-ttu-id="52474-130">`EXTERNAL_ACCESS` アセンブリでは、次のカスタム属性が許可されません。</span><span class="sxs-lookup"><span data-stu-id="52474-130">The following custom attributes are disallowed in `EXTERNAL_ACCESS` assemblies:</span></span>  
  
-   <span data-ttu-id="52474-131">System.ContextStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-131">System.ContextStaticAttribute</span></span>  
  
-   <span data-ttu-id="52474-132">System.MTAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-132">System.MTAThreadAttribute</span></span>  
  
-   <span data-ttu-id="52474-133">System.Runtime.CompilerServices.MethodImplAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-133">System.Runtime.CompilerServices.MethodImplAttribute</span></span>  
  
-   <span data-ttu-id="52474-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span></span>  
  
-   <span data-ttu-id="52474-135">System.Runtime.Remoting.Contexts.ContextAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-135">System.Runtime.Remoting.Contexts.ContextAttribute</span></span>  
  
-   <span data-ttu-id="52474-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span></span>  
  
-   <span data-ttu-id="52474-137">System.Runtime.InteropServices.DllImportAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-137">System.Runtime.InteropServices.DllImportAttribute</span></span>  
  
-   <span data-ttu-id="52474-138">System.Security.Permissions.CodeAccessSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-138">System.Security.Permissions.CodeAccessSecurityAttribute</span></span>  
  
-   <span data-ttu-id="52474-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span></span>  
  
-   <span data-ttu-id="52474-140">System.Security.UnverifiableCodeAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-140">System.Security.UnverifiableCodeAttribute</span></span>  
  
-   <span data-ttu-id="52474-141">System.STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-141">System.STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="52474-142">System.ThreadStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="52474-142">System.ThreadStaticAttribute</span></span>  
  
### <a name="safe"></a><span data-ttu-id="52474-143">SAFE</span><span class="sxs-lookup"><span data-stu-id="52474-143">SAFE</span></span>  
  
-   <span data-ttu-id="52474-144">`EXTERNAL_ACCESS` アセンブリの条件がすべてチェックされていること。</span><span class="sxs-lookup"><span data-stu-id="52474-144">All `EXTERNAL_ACCESS` assembly conditions are checked.</span></span>  
  
## <a name="runtime-checks"></a><span data-ttu-id="52474-145">ランタイムチェック</span><span class="sxs-lookup"><span data-stu-id="52474-145">Runtime Checks</span></span>  
 <span data-ttu-id="52474-146">コード アセンブリは、実行時に次の条件をチェックされます。</span><span class="sxs-lookup"><span data-stu-id="52474-146">At runtime, the code assembly is checked for the following conditions.</span></span> <span data-ttu-id="52474-147">これらの条件のいずれかが見つからなかった場合、マネージド コードの実行が失敗し、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="52474-147">If any of these conditions are found, the managed code will not be allowed to run and an exception will be thrown.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="52474-148">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="52474-148">UNSAFE</span></span>  
 <span data-ttu-id="52474-149">バイト配列からメソッドを呼び出すことによって明示的に、 `System.Reflection.Assembly.Load()` または名前空間を使用して暗黙的にアセンブリを読み込むことは許可されて `Reflection.Emit` いません。</span><span class="sxs-lookup"><span data-stu-id="52474-149">Loading an assembly-either explicitly by calling the `System.Reflection.Assembly.Load()` method from a byte array, or implicitly through the use of `Reflection.Emit` namespace-is not permitted.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="52474-150">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="52474-150">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="52474-151">`UNSAFE` の条件がすべてチェックされていること。</span><span class="sxs-lookup"><span data-stu-id="52474-151">All `UNSAFE` conditions are checked.</span></span>  
  
 <span data-ttu-id="52474-152">サポートされているアセンブリの一覧の中で、次のホスト保護属性 (HPA) 値で注釈を付けられている型およびメンバーはすべて許可されません。</span><span class="sxs-lookup"><span data-stu-id="52474-152">All types and methods annotated with the following host protection attribute (HPA) values in the supported list of assemblies are disallowed.</span></span>  
  
-   <span data-ttu-id="52474-153">SelfAffectingProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="52474-153">SelfAffectingProcessMgmt</span></span>  
  
-   <span data-ttu-id="52474-154">SelfAffectingThreading</span><span class="sxs-lookup"><span data-stu-id="52474-154">SelfAffectingThreading</span></span>  
  
-   <span data-ttu-id="52474-155">Synchronization</span><span class="sxs-lookup"><span data-stu-id="52474-155">Synchronization</span></span>  
  
-   <span data-ttu-id="52474-156">SharedState</span><span class="sxs-lookup"><span data-stu-id="52474-156">SharedState</span></span>  
  
-   <span data-ttu-id="52474-157">ExternalProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="52474-157">ExternalProcessMgmt</span></span>  
  
-   <span data-ttu-id="52474-158">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="52474-158">ExternalThreading</span></span>  
  
-   <span data-ttu-id="52474-159">SecurityInfrastructure</span><span class="sxs-lookup"><span data-stu-id="52474-159">SecurityInfrastructure</span></span>  
  
-   <span data-ttu-id="52474-160">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="52474-160">MayLeakOnAbort</span></span>  
  
-   <span data-ttu-id="52474-161">UI</span><span class="sxs-lookup"><span data-stu-id="52474-161">UI</span></span>  
  
 <span data-ttu-id="52474-162">HPAs と、サポートされているアセンブリの許可されていない型およびメンバーの一覧については、「[ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52474-162">For more information about HPAs and a list of disallowed types and members in the supported assemblies, see [Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).</span></span>  
  
### <a name="safe"></a><span data-ttu-id="52474-163">SAFE</span><span class="sxs-lookup"><span data-stu-id="52474-163">SAFE</span></span>  
 <span data-ttu-id="52474-164">`EXTERNAL_ACCESS` の条件がすべてチェックされていること。</span><span class="sxs-lookup"><span data-stu-id="52474-164">All `EXTERNAL_ACCESS` conditions are checked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52474-165">参照</span><span class="sxs-lookup"><span data-stu-id="52474-165">See Also</span></span>  
 <span data-ttu-id="52474-166">[サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="52474-166">[Supported .NET Framework Libraries](supported-net-framework-libraries.md) </span></span>  
 <span data-ttu-id="52474-167">[CLR 統合のコードアクセスセキュリティ](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="52474-167">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="52474-168">[ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="52474-168">[Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 [<span data-ttu-id="52474-169">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="52474-169">Creating an Assembly</span></span>](../assemblies/creating-an-assembly.md)  
  
  
