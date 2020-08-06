---
title: アセンブリを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dea1f8fe57691f05274cac353a1064420309e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720037"
---
# <a name="creating-an-assembly"></a><span data-ttu-id="66d57-102">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="66d57-102">Creating an Assembly</span></span>
  <span data-ttu-id="66d57-103">ストアド プロシージャやトリガーなどのマネージド データベース オブジェクトは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。</span><span class="sxs-lookup"><span data-stu-id="66d57-103">Managed database objects, such as stored procedures or triggers, are compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="66d57-104">マネージ DLL アセンブリは、アセンブリによって提供される機能を使用する前に、に登録する必要があり [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="66d57-104">Managed DLL assemblies must be registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] before the functionality the assembly provides can be used.</span></span> <span data-ttu-id="66d57-105">アセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録するには、CREATE ASSEMBLY ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="66d57-105">To register an assembly in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, use the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="66d57-106">ここでは、CREATE ASSEMBLY ステートメントを使用してアセンブリをデータベースに登録する方法と、アセンブリのセキュリティ設定を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66d57-106">This topic discusses how to register an assembly in a database using the CREATE ASSEMBLY statement, and how to specify the security settings for the assembly.</span></span>  
  
## <a name="the-create-assembly-statement"></a><span data-ttu-id="66d57-107">CREATE ASSEMBLY ステートメント</span><span class="sxs-lookup"><span data-stu-id="66d57-107">The CREATE ASSEMBLY Statement</span></span>  
 <span data-ttu-id="66d57-108">データベースにアセンブリを作成するには、CREATE ASSEMBLY ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="66d57-108">The CREATE ASSEMBLY statement is used to create an assembly in a database.</span></span> <span data-ttu-id="66d57-109">たとえば次のようになります。</span><span class="sxs-lookup"><span data-stu-id="66d57-109">Here is an example:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="66d57-110">FROM 句では、作成するアセンブリのパス名を指定します。</span><span class="sxs-lookup"><span data-stu-id="66d57-110">The FROM clause specifies the pathname of the assembly to create.</span></span> <span data-ttu-id="66d57-111">このパスには、UNC (汎用名前付け規則) パスか、コンピューターにローカルの物理ファイル パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="66d57-111">This path can either be a Universal Naming Convention (UNC) path or a physical file path that is local to the machine.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="66d57-112">は、名前、カルチャ、および公開キーが同じでありバージョンが異なるアセンブリの登録を許可していません。</span><span class="sxs-lookup"><span data-stu-id="66d57-112">does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
 <span data-ttu-id="66d57-113">他のアセンブリを参照するアセンブリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="66d57-113">It is possible to create assemblies that reference other assemblies.</span></span> <span data-ttu-id="66d57-114">でアセンブリが作成されると [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、参照先のアセンブリがデータベースにまだ作成されていない場合は、ルートレベルのアセンブリによって参照されるアセンブリも作成されます。</span><span class="sxs-lookup"><span data-stu-id="66d57-114">When an assembly is created in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates the assemblies referenced by the root-level assembly, if the referenced assemblies are not already created into the database.</span></span>  
  
 <span data-ttu-id="66d57-115">データベース ユーザーまたはユーザー ロールには、データベースにアセンブリを作成して所有する権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="66d57-115">Database users or user roles are given permissions to create, and thereby own, assemblies in a database.</span></span> <span data-ttu-id="66d57-116">アセンブリを作成するには、データベース ユーザーまたはロールに CREATE ASSEMBLY 権限が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d57-116">In order to create assemblies, the database user or role should have the CREATE ASSEMBLY permission.</span></span>  
  
 <span data-ttu-id="66d57-117">アセンブリから他のアセンブリを参照できる条件を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66d57-117">An assembly can only succeed in referencing other assemblies if:</span></span>  
  
-   <span data-ttu-id="66d57-118">呼び出し先または参照先のアセンブリが同じユーザーまたはロールによって所有されている。</span><span class="sxs-lookup"><span data-stu-id="66d57-118">The assembly that is called or referenced is owned by the same user or role.</span></span>  
  
-   <span data-ttu-id="66d57-119">呼び出し先または参照先のアセンブリが同じデータベースに作成されている。</span><span class="sxs-lookup"><span data-stu-id="66d57-119">The assembly that is called or referenced was created in the same database.</span></span>  
  
## <a name="specifying-security-when-creating-assemblies"></a><span data-ttu-id="66d57-120">アセンブリ作成時のセキュリティの指定</span><span class="sxs-lookup"><span data-stu-id="66d57-120">Specifying Security When Creating Assemblies</span></span>  
 <span data-ttu-id="66d57-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースにアセンブリを作成する際には、コードの実行時に適用する異なる 3 つのセキュリティ レベル (`SAFE`、`EXTERNAL_ACCESS`、`UNSAFE`) のうちの 1 つを指定できます。</span><span class="sxs-lookup"><span data-stu-id="66d57-121">When creating an assembly into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, you can specify one of three different levels of security in which your code can run: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="66d57-122">`CREATE ASSEMBLY` ステートメントを実行する際には、アセンブリによる登録を失敗させる可能性があるコード アセンブリに対し、特定のチェックがサーバー上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="66d57-122">When the `CREATE ASSEMBLY` statement is run, certain checks are performed on the code assembly which may cause the assembly to fail to register on the server.</span></span> <span data-ttu-id="66d57-123">詳細については、 [CodePlex](https://msftengprodsamples.codeplex.com/)の Impersonation サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d57-123">For more information, see the Impersonation sample on [CodePlex](https://msftengprodsamples.codeplex.com/).</span></span>  
  
 <span data-ttu-id="66d57-124">`SAFE` は、ほとんどのシナリオに使用できる既定の権限セットです。</span><span class="sxs-lookup"><span data-stu-id="66d57-124">`SAFE` is the default permission set and works for the majority of scenarios.</span></span> <span data-ttu-id="66d57-125">特定のセキュリティ レベルを指定するには、CREATE ASSEMBLY ステートメントの構文を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="66d57-125">To specify a given security level, you modify the syntax of the CREATE ASSEMBLY statement as follows:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="66d57-126">上記のコードの 3 行目を省略しても、`SAFE` 権限セットを持つアセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="66d57-126">It is also possible to create an assembly with the `SAFE` permission set by simply omitting the third line of code above:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="66d57-127">`SAFE` 権限セットで実行されるアセンブリ内のコードでは、インプロセス マネージド プロバイダーを経由して、計算とサーバーのデータへのアクセスのみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="66d57-127">When code in an assembly runs under the `SAFE` permission set, it can only do computation and data access within the server through the in-process managed provider.</span></span>  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a><span data-ttu-id="66d57-128">EXTERNAL_ACCESS および UNSAFE アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="66d57-128">Creating EXTERNAL_ACCESS and UNSAFE Assemblies</span></span>  
 <span data-ttu-id="66d57-129">`EXTERNAL_ACCESS` は、ファイル、ネットワーク、レジストリ、環境変数など、サーバー外部のリソースにコードからアクセスする必要がある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="66d57-129">`EXTERNAL_ACCESS` addresses scenarios in which the code needs to access resources outside the server, such as files, network, registry, and environment variables.</span></span> <span data-ttu-id="66d57-130">サーバーから外部リソースにアクセスする場合、常にマネージド コードの呼び出し元のユーザーのセキュリティ コンテキストが借用されます。</span><span class="sxs-lookup"><span data-stu-id="66d57-130">Whenever the server accesses an external resource, it impersonates the security context of the user calling the managed code.</span></span>  
  
 <span data-ttu-id="66d57-131">`UNSAFE` コード権限は、アセンブリが安全であると検証できない場合や、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API などの制限付きのリソースへの追加アクセスが必要な場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="66d57-131">`UNSAFE` code permission is for those situations in which an assembly is not verifiably safe or requires additional access to restricted resources, such as the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API.</span></span>  
  
 <span data-ttu-id="66d57-132">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で `EXTERNAL_ACCESS` または `UNSAFE` アセンブリを作成するには、次の 2 つの条件のいずれかが満たされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d57-132">To create an `EXTERNAL_ACCESS` or `UNSAFE` assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], one of the following two conditions must be met:</span></span>  
  
1.  <span data-ttu-id="66d57-133">アセンブリが、厳密な名前で署名されているか、または証明書を使用して Authenticode で署名されている。</span><span class="sxs-lookup"><span data-stu-id="66d57-133">The assembly is strong name signed or Authenticode signed with a certificate.</span></span> <span data-ttu-id="66d57-134">この厳密な名前 (または証明書) は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で非対称キー (または証明書) として作成され、それに対応する、`EXTERNAL ACCESS ASSEMBLY` 権限 (外部アクセス アセンブリの場合) または `UNSAFE ASSEMBLY` 権限 (安全でないアセンブリの場合) を持つログインが存在します。</span><span class="sxs-lookup"><span data-stu-id="66d57-134">This strong name (or certificate) is created inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as an asymmetric key (or certificate), and has a corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission (for external access assemblies) or `UNSAFE ASSEMBLY` permission (for unsafe assemblies).</span></span>  
  
2.  <span data-ttu-id="66d57-135">データベース所有者 (DBO) に `EXTERNAL ACCESS ASSEMBLY` (アセンブリの場合 `EXTERNAL ACCESS` ) または `UNSAFE ASSEMBLY` (アセンブリの場合 `UNSAFE` ) アクセス許可があり、データベースの "[信頼できるデータベース" プロパティ](../../security/trustworthy-database-property.md)がに設定 `ON` されている。</span><span class="sxs-lookup"><span data-stu-id="66d57-135">The database owner (DBO) has `EXTERNAL ACCESS ASSEMBLY` (for `EXTERNAL ACCESS` assemblies) or `UNSAFE ASSEMBLY` (for `UNSAFE` assemblies) permission, and the database has the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) set to `ON`.</span></span>  
  
 <span data-ttu-id="66d57-136">上に示した 2 つの条件は、アセンブリの読み込み時 (実行も含む) にもチェックされます。</span><span class="sxs-lookup"><span data-stu-id="66d57-136">The two conditions listed above are also checked at assembly load time (which includes execution).</span></span> <span data-ttu-id="66d57-137">アセンブリを読み込むには、これらの条件の少なくとも 1 つが満たされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d57-137">At least one of the conditions must be met in order to load the assembly.</span></span>  
  
 <span data-ttu-id="66d57-138">データベースの["信頼できるデータベース" プロパティ](../../security/trustworthy-database-property.md)は、 `ON` サーバープロセスで共通言語ランタイム (CLR) コードを実行するためだけに設定されないようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66d57-138">We recommend that the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) on a database not be set to `ON` only to run common language runtime (CLR) code in the server process.</span></span> <span data-ttu-id="66d57-139">代わりに、master データベースのアセンブリ ファイルから非対称キーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="66d57-139">Instead, we recommend that an asymmetric key be created from the assembly file in the master database.</span></span> <span data-ttu-id="66d57-140">その場合、この非対称キーにマップされるログインを作成する必要があります。また、このログインには、`EXTERNAL ACCESS ASSEMBLY` または `UNSAFE ASSEMBLY` 権限を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d57-140">A login mapped to this asymmetric key must then be created, and the login must be granted `EXTERNAL ACCESS ASSEMBLY` or `UNSAFE ASSEMBLY` permission.</span></span>  
  
 <span data-ttu-id="66d57-141">[!INCLUDE[tsql](../../../includes/tsql-md.md)]CREATE ASSEMBLY ステートメントを実行する前の次のステートメント。</span><span class="sxs-lookup"><span data-stu-id="66d57-141">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  <span data-ttu-id="66d57-142">非対称キーに関連付ける新しいログインを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d57-142">You must create a new login to associate with the asymmetric key.</span></span> <span data-ttu-id="66d57-143">このログインは、権限を許可するためにのみ使用します。このログインをユーザーに関連付けたり、アプリケーション内で使用したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66d57-143">This login is only used to grant permissions; it does not have to be associated with a user, or used within the application.</span></span>  
  
 <span data-ttu-id="66d57-144">`EXTERNAL ACCESS` アセンブリを作成するには、作成者に `EXTERNAL ACCESS` 権限が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d57-144">To create an `EXTERNAL ACCESS` assembly, the creator needs to have `EXTERNAL ACCESS` permission.</span></span> <span data-ttu-id="66d57-145">この権限は、アセンブリの作成時に次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="66d57-145">This is specified when creating the assembly:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 <span data-ttu-id="66d57-146">[!INCLUDE[tsql](../../../includes/tsql-md.md)]CREATE ASSEMBLY ステートメントを実行する前の次のステートメント。</span><span class="sxs-lookup"><span data-stu-id="66d57-146">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 <span data-ttu-id="66d57-147">アセンブリを `UNSAFE` 権限で読み込むには、そのアセンブリをサーバーに読み込むときに、次のように `UNSAFE` 権限セットを指定します。</span><span class="sxs-lookup"><span data-stu-id="66d57-147">To specify that an assembly loads with `UNSAFE` permission, you specify the `UNSAFE` permission set when loading the assembly into the server:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 <span data-ttu-id="66d57-148">各設定のアクセス許可の詳細については、「 [CLR 統合のセキュリティ](../security/clr-integration-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d57-148">For more details about the permissions for each of the settings, see [CLR Integration Security](../security/clr-integration-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d57-149">参照</span><span class="sxs-lookup"><span data-stu-id="66d57-149">See Also</span></span>  
 <span data-ttu-id="66d57-150">[CLR 統合アセンブリの管理](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="66d57-150">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="66d57-151">[アセンブリを変更する](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="66d57-151">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="66d57-152">[アセンブリの削除](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="66d57-152">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 <span data-ttu-id="66d57-153">[CLR 統合のコードアクセスセキュリティ](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="66d57-153">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="66d57-154">[TRUSTWORTHY データベース プロパティ](../../security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="66d57-154">[TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="66d57-155">部分的に信頼される呼び出し元の許容</span><span class="sxs-lookup"><span data-stu-id="66d57-155">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
