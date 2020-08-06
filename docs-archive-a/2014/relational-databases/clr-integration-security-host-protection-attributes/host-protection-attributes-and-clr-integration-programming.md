---
title: ホスト保護属性と CLR 統合プログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 16ca1e4734e66b0eca85523764739e8f8b32634a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720084"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a><span data-ttu-id="9c474-102">ホスト保護属性と CLR 統合プログラミング</span><span class="sxs-lookup"><span data-stu-id="9c474-102">Host Protection Attributes and CLR Integration Programming</span></span>
  <span data-ttu-id="9c474-103">CLR (共通言語ランタイム) には、.NET Framework の一部であるマネージド API (アプリケーション プログラミング インターフェイス) に、特定の属性で注釈を付けるメカニズムが用意されています。このような属性は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降) など CLR のホストのための属性です。</span><span class="sxs-lookup"><span data-stu-id="9c474-103">The common language runtime (CLR) provides a mechanism to annotate managed application programming interfaces (APIs) that are part of the .NET Framework with certain attributes that may be of interest to a host of the CLR, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="9c474-104">このような HPA (ホスト保護属性) の例としては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="9c474-104">Examples of such host protection attributes (HPAs) include:</span></span>  
  
-   <span data-ttu-id="9c474-105">`SharedState`。共有状態 (静的なクラス フィールドなど) を作成または管理する機能が API で公開されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-105">`SharedState`, which indicates whether the API exposes the ability to create or manage shared state (for example, static class fields).</span></span>  
  
-   <span data-ttu-id="9c474-106">`Synchronization`。スレッド間で同期を実行する機能が API で公開されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-106">`Synchronization`, which indicates whether the API exposes the ability to perform synchronization between threads.</span></span>  
  
-   <span data-ttu-id="9c474-107">`ExternalProcessMgmt`。ホスト プロセスを制御する方法が API で公開されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-107">`ExternalProcessMgmt`, which indicates whether the API exposes a way to control the host process.</span></span>  
  
 <span data-ttu-id="9c474-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、これらの属性が与えられると、CAS (コード アクセス セキュリティ) を使用して、ホストされた環境で許可されない HPA の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="9c474-108">Given these attributes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifies a list of HPAs that are disallowed in the hosted environment through code access security (CAS).</span></span> <span data-ttu-id="9c474-109">CAS 要件は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 3 つの権限セット (`SAFE`、`EXTERNAL_ACCESS`、または `UNSAFE`) のいずれかで指定します。</span><span class="sxs-lookup"><span data-stu-id="9c474-109">The CAS requirements are specified by one of three [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission sets: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="9c474-110">アセンブリをサーバーに登録する際に、`CREATE ASSEMBLY` ステートメントを使用して、これら 3 つのセキュリティ レベルのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c474-110">One of these three security levels is specified when the assembly is registered on the server, using the `CREATE ASSEMBLY` statement.</span></span> <span data-ttu-id="9c474-111">`SAFE` 権限セットまたは `EXTERNAL_ACCESS` 権限セット内で実行されるコードでは、`System.Security.Permissions.HostProtectionAttribute` 属性が適用される特定の型またはメンバーを使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c474-111">Code executing within the `SAFE` or `EXTERNAL_ACCESS` permission sets must avoid certain types or members that have the `System.Security.Permissions.HostProtectionAttribute` attribute applied.</span></span> <span data-ttu-id="9c474-112">詳細については、「[アセンブリの作成](../clr-integration/assemblies/creating-an-assembly.md)」および「 [CLR 統合プログラミングモデルの制限](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c474-112">For more information, see [Creating an Assembly](../clr-integration/assemblies/creating-an-assembly.md) and [CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).</span></span>  
  
 <span data-ttu-id="9c474-113">`HostProtectionAttribute` は、ホストで許可されないコード構文 (型またはメソッド) を特定するという点で、信頼性を向上するための手段がセキュリティ権限とは異なります。</span><span class="sxs-lookup"><span data-stu-id="9c474-113">The `HostProtectionAttribute` is not a security permission as much as a way to improve reliability, in that it identifies specific code constructs, either types or methods, that the host may disallow.</span></span> <span data-ttu-id="9c474-114">`HostProtectionAttribute` を使用すると、ホストの安定性確保に役立つプログラミング モデルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="9c474-114">The use of the `HostProtectionAttribute` enforces a programming model that helps protect the stability of the host.</span></span>  
  
## <a name="host-protection-attributes"></a><span data-ttu-id="9c474-115">ホスト保護属性</span><span class="sxs-lookup"><span data-stu-id="9c474-115">Host Protection Attributes</span></span>  
 <span data-ttu-id="9c474-116">HPA は、ホスト プログラミング モデルに適合しない型またはメンバーを識別して、次に示す信頼性に対する脅威を表します (リスクの低いものから順に並べています)。</span><span class="sxs-lookup"><span data-stu-id="9c474-116">HPAs identify types or members that do not fit the host programming model and represent the following increasing levels of reliability threat:</span></span>  
  
-   <span data-ttu-id="9c474-117">他の場合には特に害のない脅威</span><span class="sxs-lookup"><span data-stu-id="9c474-117">Are otherwise benign.</span></span>  
  
-   <span data-ttu-id="9c474-118">サーバーで実行されるマネージ ユーザー コードの不安定化につながる脅威</span><span class="sxs-lookup"><span data-stu-id="9c474-118">Could lead to destabilization of server-managed user code.</span></span>  
  
-   <span data-ttu-id="9c474-119">サーバー プロセス自体の不安定化につながる脅威</span><span class="sxs-lookup"><span data-stu-id="9c474-119">Could lead to destabilization of the server process itself.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9c474-120">、、、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` またはの値を持つ列挙体を指定するを持つ型またはメンバーの使用を許可し `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` `SharedState` `Synchronization` `UI` ません。</span><span class="sxs-lookup"><span data-stu-id="9c474-120">disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="9c474-121">これにより、状態の共有を可能にしたり、同期を実行するメンバーをアセンブリから呼び出すことができなくなります。さらに、終了時にリソース リークを発生させたり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの整合性に影響を与える可能性があるメンバーの呼び出しも禁止されます。</span><span class="sxs-lookup"><span data-stu-id="9c474-121">This prevents the assemblies from calling members that enable sharing state, perform synchronization, might cause a resource leak on termination, or affect the integrity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="disallowed-types-and-members"></a><span data-ttu-id="9c474-122">禁止されている型とメンバー</span><span class="sxs-lookup"><span data-stu-id="9c474-122">Disallowed Types and Members</span></span>  
 <span data-ttu-id="9c474-123">次のトピックでは、`HostProtectionResource` の値が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって許可されない型およびメンバーを示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-123">The following topics identify types and members whose `HostProtectionResource` values are disallowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c474-124">各トピックに含まれる一覧は、サポートされているアセンブリから作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="9c474-124">The lists in these topics were generated from the supported assemblies.</span></span>  <span data-ttu-id="9c474-125">詳細については、「[サポートされている .NET Framework ライブラリ](../clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c474-125">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c474-126">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9c474-126">In This Section</span></span>  
 [<span data-ttu-id="9c474-127">Microsoft.VisualBasic.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="9c474-127">Disallowed Types and Members in Microsoft.VisualBasic.dll</span></span>](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 <span data-ttu-id="9c474-128">HPA の値が許可されない Microsoft.VisualBasic.dll の型およびメンバーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-128">Lists the types and members in Microsoft.VisualBasic.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="9c474-129">mscorlib.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="9c474-129">Disallowed Types and Members in mscorlib.dll</span></span>](disallowed-types-and-members-in-mscorlib-dll.md)  
 <span data-ttu-id="9c474-130">HPA の値が許可されない mscorlib.dll の型およびメンバーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-130">Lists the types and members in mscorlib.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="9c474-131">System.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="9c474-131">Disallowed Types and Members in System.dll</span></span>](disallowed-types-and-members-in-system-dll.md)  
 <span data-ttu-id="9c474-132">HPA の値が許可されない System.dll の型およびメンバーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-132">Lists the types and members in System.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="9c474-133">System.Data.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="9c474-133">Disallowed Types and Members in System.Data.dll</span></span>](disallowed-types-and-members-in-system-data-dll.md)  
 <span data-ttu-id="9c474-134">HPA の値が許可されない System.Data.dll の型およびメンバーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-134">Lists the types and members in System.Data.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="9c474-135">System.Core.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="9c474-135">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
 <span data-ttu-id="9c474-136">HPA の値が許可されない System.Core.dll の型およびメンバーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9c474-136">Lists the types and members in System.Core.dll whose HPA values are disallowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c474-137">参照</span><span class="sxs-lookup"><span data-stu-id="9c474-137">See Also</span></span>  
 <span data-ttu-id="9c474-138">[CLR 統合のコードアクセスセキュリティ](../clr-integration/security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="9c474-138">[CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="9c474-139">[CLR 統合プログラミングモデルの制限事項](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span><span class="sxs-lookup"><span data-stu-id="9c474-139">[CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span></span>  
 [<span data-ttu-id="9c474-140">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="9c474-140">Creating an Assembly</span></span>](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
