---
title: Reporting Services のコード アクセス セキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services]
- permission sets [Reporting Services]
- evidence [Reporting Services]
- code access security [Reporting Services], about code access security
- named permission sets [Reporting Services]
ms.assetid: 97480368-1fc3-4c32-b1b0-63edfb54e472
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebe023b13a003895845bbb119f0bc93a0d01203a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646031"
---
# <a name="code-access-security-in-reporting-services"></a><span data-ttu-id="dd22d-102">Reporting Services のコード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="dd22d-102">Code Access Security in Reporting Services</span></span>
  <span data-ttu-id="dd22d-103">コード アクセス セキュリティの中核を成す概念として、証拠、コード グループ、名前付き権限セットがあります。</span><span class="sxs-lookup"><span data-stu-id="dd22d-103">Code access security centers on these core concepts: evidence, code groups, and named permission sets.</span></span> <span data-ttu-id="dd22d-104">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]、レポート マネージャー、レポート デザイナー、およびレポート サーバー コンポーネントには、それぞれ、データ、配信、表示、セキュリティ拡張機能はもとより、カスタム アセンブリのコード アクセス セキュリティを設定するポリシー ファイルが存在します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-104">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Report Manager, Report Designer, and Report Server components each have a policy file that configures code access security for custom assemblies as well as data, delivery, rendering, and security extensions.</span></span> <span data-ttu-id="dd22d-105">以下のセクションでは、コード アクセス セキュリティの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-105">The following sections provide an overview of code access security.</span></span> <span data-ttu-id="dd22d-106">このセクションで取り上げられているトピックの詳細については、[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK ドキュメントのセキュリティ ポリシー モデルに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd22d-106">For more detailed information about the topics covered in this section, see "Security Policy Model" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="dd22d-107">はコード アクセス セキュリティを使用します。その理由は、レポート サーバーは [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] テクノロジに基づき構築されているものの、一般の [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] アプリケーションとレポート サーバーの間には根本的な相違があるからです。</span><span class="sxs-lookup"><span data-stu-id="dd22d-107">uses code access security because, although the report server is built on [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] technology, there is a substantial difference between a typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application and the report server.</span></span> <span data-ttu-id="dd22d-108">一般的な [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] アプリケーションはユーザー コードを実行しません。</span><span class="sxs-lookup"><span data-stu-id="dd22d-108">A typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application does not execute user code.</span></span> <span data-ttu-id="dd22d-109">一方、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ではオープンで拡張性のあるアーキテクチャが採用されています。これにより、ユーザーが、レポート定義言語の **Code** 要素を使用して、レポート定義ファイルを処理できるプログラムを作成すること、および特殊な機能を開発してレポートで使用するカスタム アセンブリに組み込むことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="dd22d-109">In contrast, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses an open and extensible architecture that allows users to program against the report definition files using the **Code** element of the Report Definition Language and to develop specialized functionality into a custom assembly for use in reports.</span></span> <span data-ttu-id="dd22d-110">さらに、開発者は、レポート サーバーの能力を増強する強力な拡張機能を設計、展開できます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-110">Furthermore, developers can design and deploy powerful extensions that enhance the capabilities of the report server.</span></span> <span data-ttu-id="dd22d-111">この能力と柔軟性のために、最大限の防御とセキュリティが必要です。</span><span class="sxs-lookup"><span data-stu-id="dd22d-111">With this power and flexibility comes the need to provide as much protection and security as possible.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="dd22d-112">の開発者はレポートの中で任意の [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アセンブリを使用でき、グローバル アセンブリ キャッシュに展開されているアセンブリのすべての機能をネイティブに利用できます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-112">developers can use any [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly in their reports and natively call upon all of the functionality of assemblies deployed to the global assembly cache.</span></span> <span data-ttu-id="dd22d-113">レポート サーバーによって制御されることは、レポートの式とロードされたカスタム アセンブリに与えられる権限だけです。</span><span class="sxs-lookup"><span data-stu-id="dd22d-113">The only thing that the report server can control is what permissions are given for report expressions and loaded custom assemblies.</span></span> <span data-ttu-id="dd22d-114">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、カスタム アセンブリに既定で **Execute** 専用アクセス許可が与えられます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-114">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], custom assemblies receive **Execute**-only permissions by default.</span></span>  
  
## <a name="evidence"></a><span data-ttu-id="dd22d-115">証拠</span><span class="sxs-lookup"><span data-stu-id="dd22d-115">Evidence</span></span>  
 <span data-ttu-id="dd22d-116">証拠は、共通言語ランタイム (CLR) がコード アセンブリのセキュリティ ポリシーを決定するために使用する情報です。</span><span class="sxs-lookup"><span data-stu-id="dd22d-116">Evidence is the information that the common language runtime (CLR) uses to determine a security policy for code assemblies.</span></span> <span data-ttu-id="dd22d-117">証拠は、コードが固有の特性を持っていることを、ランタイムに知らせます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-117">Evidence indicates to the runtime that code has a particular characteristic.</span></span> <span data-ttu-id="dd22d-118">証拠の共通の形式には、デジタル署名やアセンブリの場所が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-118">Common forms of evidence include digital signatures and the location of an assembly.</span></span> <span data-ttu-id="dd22d-119">証拠は、アプリケーションにとって意味のある、他の情報を表すようにカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-119">Evidence can also be custom designed to represent other information that is meaningful to the application.</span></span>  
  
 <span data-ttu-id="dd22d-120">アセンブリ ドメインとアプリケーション ドメインはどちらも、証拠に基づいて権限を与えられます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-120">Both assemblies and application domains receive permissions based on evidence.</span></span> <span data-ttu-id="dd22d-121">たとえば、厳密な名前を持たないアセンブリで使用される証拠の一般的な形式の 1 つに、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] がアクセスを試みているアセンブリの場所があります。</span><span class="sxs-lookup"><span data-stu-id="dd22d-121">For example, the location of an assembly that [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is attempting to access is one common form of evidence for weak-named assemblies.</span></span> <span data-ttu-id="dd22d-122">これは URL 証拠として知られています。</span><span class="sxs-lookup"><span data-stu-id="dd22d-122">This is known as URL evidence.</span></span> <span data-ttu-id="dd22d-123">レポート サーバーに展開されたカスタム データ処理拡張機能の URL 証拠の一例は、"C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll" です。</span><span class="sxs-lookup"><span data-stu-id="dd22d-123">URL evidence for a custom data processing extension deployed to a report server might be "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll".</span></span> <span data-ttu-id="dd22d-124">アセンブリの厳密な名前またはデジタル署名もまた、証拠の一般的な形式です。</span><span class="sxs-lookup"><span data-stu-id="dd22d-124">The strong name or digital signature of an assembly is another common form of evidence.</span></span> <span data-ttu-id="dd22d-125">この場合、証拠はアセンブリの公開キーの情報です。</span><span class="sxs-lookup"><span data-stu-id="dd22d-125">In this case, the evidence is the public key information for an assembly.</span></span>  
  
## <a name="code-groups"></a><span data-ttu-id="dd22d-126">コード グループ</span><span class="sxs-lookup"><span data-stu-id="dd22d-126">Code Groups</span></span>  
 <span data-ttu-id="dd22d-127">コード グループは、構成メンバーに対して条件が指定されたコードを論理的にグループ化したものです。</span><span class="sxs-lookup"><span data-stu-id="dd22d-127">A code group is a logical grouping of code that has a specified condition for membership.</span></span> <span data-ttu-id="dd22d-128">構成メンバーの条件を満たすコードは、すべてそのグループに含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-128">Any code that meets the membership condition is included in the group.</span></span> <span data-ttu-id="dd22d-129">管理者は、コード グループとそれに関連する権限セットを管理することによって、セキュリティ ポリシーを構成します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-129">Administrators configure a security policy by managing code groups and their associated permission sets.</span></span>  
  
 <span data-ttu-id="dd22d-130">コード グループの構成メンバーの条件は証拠に基づいています。</span><span class="sxs-lookup"><span data-stu-id="dd22d-130">A membership condition for a code group is based on evidence.</span></span> <span data-ttu-id="dd22d-131">たとえば、コード グループの URL 構成メンバーは URL 証拠に基づいています。</span><span class="sxs-lookup"><span data-stu-id="dd22d-131">For example, a URL membership for a code group is based on URL evidence.</span></span> <span data-ttu-id="dd22d-132">共通言語ランタイム (CLR) では、URL 証拠のような識別特性を使用して、コードを記述し、グループの構成メンバー条件が満たされているかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-132">The common language runtime (CLR) uses identifying characteristics such as URL evidence to describe the code and to determine whether a group's membership condition has been met.</span></span> <span data-ttu-id="dd22d-133">たとえば、コード グループの構成メンバー条件が、"code in the assembly C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll" の場合、ランタイムは証拠を調べて、コードがその場所からのコードかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-133">For example, if the membership condition of a code group is "code in the assembly C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll", the runtime examines the evidence to determine whether the code originates from that location.</span></span> <span data-ttu-id="dd22d-134">たとえば、この種のコード グループの構成のエントリは次のように記述されています。</span><span class="sxs-lookup"><span data-stu-id="dd22d-134">An example of a configuration entry for this type of code group might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="FullTrust"  
   Name="MyCodeGroup"  
   Description="Code group for my data processing extension">  
      <IMembershipCondition class="UrlMembershipCondition"  
         version="1"  
         Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"  
       />  
</CodeGroup>  
```  
  
 <span data-ttu-id="dd22d-135">システム管理者またはアプリケーション展開の専門家と協力して、カスタム アセンブリまたは [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の拡張機能が必要とする、コード アクセス セキュリティとコード グループの種類を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd22d-135">You should work with your system administrator or application deployment expert to determine the type of code access security and code groups that your custom assemblies or [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions require.</span></span>  
  
## <a name="named-permission-sets"></a><span data-ttu-id="dd22d-136">名前付き権限セット</span><span class="sxs-lookup"><span data-stu-id="dd22d-136">Named Permission Sets</span></span>  
 <span data-ttu-id="dd22d-137">名前付き権限セットは、管理者がコード グループに関連付けることができる権限のセットです。</span><span class="sxs-lookup"><span data-stu-id="dd22d-137">A named permission set is a set of permissions that administrators can associate with a code group.</span></span> <span data-ttu-id="dd22d-138">ほとんどの名前付き権限セットは、少なくとも、1 つの権限、名前、および権限セットの説明から構成されます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-138">Most named permission sets consist of at least one permission, a name, and description for the permission set.</span></span> <span data-ttu-id="dd22d-139">管理者は、名前付き権限セットを使用して、コード グループのセキュリティ ポリシーを作成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-139">Administrators can use named permission sets to establish or modify the security policy for code groups.</span></span> <span data-ttu-id="dd22d-140">複数のコード グループを同じ名前付き権限セットに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-140">More than one code group can be associated with the same named permission set.</span></span> <span data-ttu-id="dd22d-141">CLR には、**Nothing**、**Execution**、**Internet**、**LocalIntranet**、**Everything**、**FullTrust** などの、組み込みの名前付きアクセス許可セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="dd22d-141">The CLR provides built-in named permission sets; among these are **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything**, and **FullTrust**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd22d-142">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム データ、配信、表示、およびセキュリティの拡張機能は、**FullTrust** アクセス許可セットの下で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd22d-142">Custom data, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] must run under the **FullTrust** permission set.</span></span> <span data-ttu-id="dd22d-143">システム管理者と協力して、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 拡張機能の適切なコード グループと構成メンバー条件を追加します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-143">Work with your system administrator to add the appropriate code group and membership conditions for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 <span data-ttu-id="dd22d-144">使用するカスタム アセンブリに対する自身のカスタム権限レベルを、レポートに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-144">You can associate your own custom levels of permissions for custom assemblies that you use with reports.</span></span> <span data-ttu-id="dd22d-145">たとえば、アセンブリが特定のファイルにアクセスする場合、その特定のファイルに対する I/O アクセスを許可する名前付き権限セットを作成し、その権限セットをコード グループに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dd22d-145">For example, if you want to allow an assembly to access a specific file, you can create a new named permission set with specific file I/O access and then assign the permission set to your code group.</span></span> <span data-ttu-id="dd22d-146">次の権限セットは、ファイル MyFile.xml に対する読み取り専用のアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="dd22d-146">The following permission set grants read-only access to the file MyFile.xml:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="MyNewFilePermissionSet"  
   Description="A special permission set that grants read access to my file.">  
    <IPermission class="FileIOPermission"  
       version="1"  
       Read="C:\MyFile.xml"/>  
    <IPermission class="SecurityPermission"  
       version="1"  
       Flags="Assertion, Execution"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="dd22d-147">この権限セットが付与されるコード グループは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dd22d-147">A code group that you grant this permission set might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="MyNewFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\MyCustomAssembly.dll"/>  
</CodeGroup>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd22d-148">参照</span><span class="sxs-lookup"><span data-stu-id="dd22d-148">See Also</span></span>  
 [<span data-ttu-id="dd22d-149">セキュリティで保護された開発 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dd22d-149">Secure Development &#40;Reporting Services&#41;</span></span>](secure-development-reporting-services.md)  
  
  
